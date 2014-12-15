# NodeConf One-Shot Oakland

## The Node Way

Fred Schott!

- structure
- async
- community

### Structure

- small, single-purpose modules

### Async

- use async I/O whenever possible
- avoid cpu-bound tasks
- return early in async callbacks
- get help with control flow (e.g., 'async' module)

### Community

- leverage the ecosystem (there's a module for that)
- contribute to the ecosystem


## Dat in Action

Max Ogden

reproducible science

data sharing is a mess

try-dat.org
dathub
gasket


## Dat/docker stuff

Mathias Buus

torrent-stream
torrent-docker

streaming files in docker images via bittorrent. pretty cool!


## Open source is magic

Carter Rabasa

open sourcing community

### How to contribute

- set expectations, both good and bad
- be explicit about where you need help
- facilitate conversation as much as possible
- encourage documentation and sharing of experiences
- provide a clear CoC


## A security carol

### the ghost of security past
- most problems in security have already been solved in other langs

#### confidentiality

Buffers are not 0-filled (leak random mem)

#### integrity

- input validation

#### availability


#### resources

owasp.org
nodesecurity.io

### the ghost of security present

- node core security process (?)
- npmjs.com/security
- known vulnerabilities
  + npm i -g nsp

### the ghost of security future

- audit logging
- run fire drills


## The hacker's guide to IoT via nodejs

@sedouard

understand GPIO pins - they connect the "things"


## nodbots outfit: v0.1.0 to v2.5.0

cassandra perch


## JS Flow Control
@sprjrx

recursive deferral w/ setimmediate

`setimmediate` - queue function behind any i/o events already in the queue
`process.nextTick` - queue the function at the head of the event queue to be called next


## monkeypatch the planet

forrest norvell and brian fjord

methods of changing all instance of code
- search and replace
- falafel (js parser)
  + replace all function with a function that checks for window.alert
- window.alert = console.log.bind(console)

intermediately-sized-hadron-collider


## the node community and you

cj

