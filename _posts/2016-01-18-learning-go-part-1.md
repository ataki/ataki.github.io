---
layout: post
title: learning go on a weekend
---

I took a brief trip this weekend into goland. Till this point, I've

<ul>
  <li>Worked exclusively with dynamic languages for the past year</li>
  <li>Just finished Go-Tour (completed exercises)</li>
  <li>Seen canonical ways of structuring Go projects</li>
</ul>

Here are 2 things i like and dislike about Go so far.

**+ Pointers and Simplicity**

Go takes the simplest parts of C, combines it with an old-style message-passing abstraction (which I've yet to use extensively), and balances it with simple primitives.

I remember trying to reach for pointers in Java and Ruby / Python. As a developer reading / adding to existing code, you really want to see when someone's passing something into a function to be modified.

**+ Build System**

Go is up-front about how to structure Go projects for your entire system. Because its a new language, developers haven't had time to develop their own preferred way of setting up projects. Which is great, because everyone then follows *the standard way*.

**- Fluency**

I've read a lot of complaints about Go that it's "ugly". I'd say it's not yet "fluent" enough, meaning that it still feels like writing lower-level code and it takes time to express higher-level logic the way you want to with Ruby and Haskell.

The language gets out of your way, but there aren't libraries yet that allow you to do lazy-loading. Everything is done through channels. This is nice, but it would be great to have built-in libraries that allow generators. I've seen some on Github, so high hopes.

**- Concurrency Model**

Related to fluency - I have to think about channels and how to wait for goroutines every time I parallelize an operation? I like SyncWait but I feel like there should be another primitive for an actual Thread that exits when its children have finished.

This would have made the Web-Crawler example in Go Tour much simpler. Instead, we get this: (note: I decided not to use channels)

{% highlight go %}

import "sync"
import "time"

// Synchronized global cache
type SyncMap struct {
  entries map[string]int
  mux sync.Mutex
}

// Semaphore abstraction
type Dispatch struct {
  num_workers int
  mux sync.Mutex
}

// Notify the dispatcher that a single
// worker has finished. Thread-safe
func (d *Dispatch) NotifyHasFinished() {
  d.mux.Lock()
  d.num_workers = d.num_workers - 1
  d.mux.Unlock()
}

// Num current workers. Thread-safe
func (d *Dispatch) GetNumWorkers() int {
  d.mux.Lock()
  n := d.num_workers
  d.mux.Unlock()
  return n
}

func Crawl(url string, depth int, fetcher Fetcher, cache SyncMap, parent *Dispatch) {
  if depth <= 0 {
    parent.NotifyHasFinished()
    return
  }

  // Check the cache and quit if already found
  cache.mux.Lock()
  _, present := cache.entries[url]

  if present {
    cache.mux.Unlock()
    parent.NotifyHasFinished()
    return
  }

  // Fetch url
  cache.entries[url] = 1
  cache.mux.Unlock()

  body, urls, err := fetcher.Fetch(url)
  if err != nil {
    fmt.Println(err)
    parent.NotifyHasFinished()
    return
  }
  fmt.Printf("found: %s %q\n", url, body)

  // Launch separate thread for each url
  dispatch := Dispatch{num_workers: len(urls)}
  for _, u := range urls {
    go Crawl(u, depth-1, fetcher, cache, &dispatch)
  }

  // Await goroutines to finish
  for {
    n := dispatch.GetNumWorkers()

    if n > 0 {
      time.Sleep(10 * time.Millisecond)
    } else {
      break
    }
  }

  parent.NotifyHasFinished()
  return
}

func main() {
  // global cache
  cache := SyncMap{entries: make(map[string]int)}

  // the top-level worker needs to keep a dispatcher itself
  dispatch := Dispatch{num_workers: 1}

  // start this Crawler as the top-level process to launch
  // more parallelized workers
  Crawl("http://golang.org/", 4, fetcher, cache, &dispatch)
}

// ... everything below is unmodified
{% endhighlight %}

