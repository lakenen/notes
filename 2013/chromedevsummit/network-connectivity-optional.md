# Network Connectivity: Optional

Jake Archibald
@jaffathecake

### AppCache... fail

### ServiceWorker
* https://github.com/slightlyoff/serviceworker
* all promise-based methods
* 'fetch' event - default preventable
* 'install' event - the first time the browser sees the service worker
    * `event.waitUntil(promise)`
* 'activate' event - when the cache is ready?

> Bring your own magic API

### Cache
* `new Cache`

> We should build our pages "offline first"
