# JSConf 2015 Notes


## Accessibility and JS Side-By-Side

Perceivable
Predictable
Understandable
Robust

Accessibility barriers:
- no js support (or disabled)
- developers lack knowledge in WAI-ARIA


## Building a mobile web you're f**king proud of (Kate Hudson)

Mobile web is broken
The web was not built with mobile in mind

We should stop trying to make mobile web look like mobile native. Focus on the things web is good at.

3 levels of hack
- test new features before their time:
  + service workers
- crap I missed the other 2

issues:
- poor offline experience (appcache sux)
- memory leaks in long-lived apps
- UI performance
- old crappy android browser


## Communicate all the things

(some examples of sites using WebRTC)

(a very basic explanation of how WebRTC works)

(some demos)

https://github.com/ktyacke


## You Won’t Believe This One Weird Way to Rewrite Closure
Jonathan Martin

closures and local vars are slow

5 things
- no function params, local var, or var assignment
- no function memoization
- one global variable
- amnesic function bodies (they don't remember anything about their scope)
- shortcut local variables (access some functions, etc)

(live coding demo)


## Would a sample at any other rate sound as sweet?
An introduction to how our brains interpret sound. Myles Borins

https://github.com/TheAlphaNerd


## Math == art && art == code

@thisisjohnbrown

homework:
- uncontext - use http://www.uncontext.com/ to make something
- codepen - fork something and explore it
- creative code meetups (go to or create one)


## Knitting with JS

@kosamari

hyperbolic geometry == ruffle


## Coldwar

(history of 80s computer displays)
(basic canvas stuff)


## Concurrency and Parallelism in JS

why? cpu speed is maxed out, so need to use multiple cores


parallel js
- casual api
- warmup costs
- memory overhead of functional programming

postmessage
- perf is not there
- dep on evt loop
- no shared state

buffer transfer
- ...

design criteria
- native-like perf
- not dependent on main thread evt loop
- implementation versatility
- support apps and algo based on threads/pthreads
- support extensible web philosophy


SharedArrayBuffer
SynchronicInt32
ChannelSender
ChannelReceiver


## JS on NES

Michael Matuzak


## Rewriting recipe search

Tracy Hinds

neo4j


## Recreating a dialup modem in javascript

Sam Saccone

what is sound / what is data

how to encode data into audio

history:
- morse code
- baudot code ("baud")
- harmonic telegraph / audible telegraphy (audible multiplexing)
- AFSK - audio frequency shift keying (hack to send data over existing telephone infrastructure)
- TTY
- modem - demodulates/modulates data to be sent over standard phone lines

JS time!
- the oscillator node (web audio API)
  + change frequency over time (i.e., AFSK)
- ScriptProcessorNode

1. converting data: string->binary
2. bits->audio (AFSK)
3. data extraction (the hard part)

Goertzel algorithm
- allows us to extract a single target frequency intensity over time
- hamming window (?)

Noisy signals

MOAR speed: multiplexing

what's next?
- air-gapped communications
- dynamic js injection
- webrtc modem???

gh:samccone/noise


## Building a musical instrument with the Web Audio API

Steve Kinney

gh:stevekinney/making-music
gh:stevekinney/octavian

the web audio api
- get an audio context
- connect a sound source to a destination


## If you wish to learn ES6/2015 from scratch, you must first invent the universe

Ashley Williams

what is js trying to solve?
what will be js's legacy?
