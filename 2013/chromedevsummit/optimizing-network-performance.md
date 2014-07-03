# Optimizing Network Performance

http://bit.ly/cds-network

Ilya Grigorik

> ~70% of the time, we're basically idling on the network

### Core Chrome improvements
* async DNS resolver
  * built-in DNS resolver replaces system default
  * enables chrome to implement new resolve strategies
    * parallel A/AAAA resolution
    * adaptive retry timeout
    * adaptive DNS server selection
  * enables chrome to provide better error pages
* new resource scheduler
  * 5% better speed index score
  * 5% faster firing DOMContentLoaded
  * 3% sooner first paint
  * 2% faster firing load event
  * realized that a lot of pages were competing for bandwidth - over-sharding assets is backfiring on a lot of sites
    * new scheduler only downloads 10 images in parallel to avoid this
* improvements to SPDY
  * much better way to schedule resources
* M30-32 includes many more perf improvements w/scheduling
* Mobile (Android) - "Simple Cache" improvements
  * avoid context switches
* WIP/future
  * preresolve, prerender, prefetch improvements

### Protocols
* SPDY -> HTTP 2.0
* Quick UDP Internet Connections (QUIC)
  * tunneling protocol, running atop UDP, which can multiplex a large number of streams between two endpoints
  * low latency
  * reliable stream support (like SPDY)
  * better congestion avoidance than TCP
* Chrome data compression
  * ~50% data savings
  * available on Android/iOS
  * runs SPDY, so it also secures insecure connections
* WebSocket compression
* DataChannel via SCTP
  * configurable reliability and delivery for ultra-low latency

### Improving measurement tools
* Navigation timing
* User timing
* Resource timing
  * requres `Timing-Allow-Origin: *` header
  * `window.performance.getEntriesyName('http://some.url')`
