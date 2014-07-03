# Peter McLachlan

@b1tr0t

Six Bottles of RUM

Real User Measurement

> 1s delay in response time can result in 7% loss in user

RUM: collect data on how web page / app works in real world
+ more scale than in synthetic testing
+ more comprehensive results

mobile: 200-250 ms to download absolutely nothing... :(

modern browsers make 4-6+ requests to same domain
keep connections open to prevent the 200+ms penalty of opening a connection

sharding domains
* http 1.1: won't hurt much, but don't do it
* http 2.0: MAJOR anti-pattern

data:uri is slow :(

summary
* mobile latency is a big problem that's not going away
* key optimization: use "just enough" connections
  * and good values for connection timeouts
* use < 400 bytes of cookies to prevent header taking multiple packets
* domain sharding is bad
* css sprites are faster than data:uri (but why?)
