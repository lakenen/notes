# Blink

Greg Simon & Eric Seidel

http://chromestatus.com/features
https://chromeperf.appspot.com/

### Since forked from WebKit
* intent to implement - open process
  * announce intent to add a feature
  * implement it (behind a flag)
  * get feedback
  * announce intent to ship the feature
  * once it's approved it ships in chrome
* -webkit- no more, ~~-blink-~~
* removing broken stuff
* improving consistency of the chrome platform
  * shipped android webview
* improving speed and stability
* improving security

### What's coming in the next 6 months
* web components
* web animations
  * one timeline, unified backend
  * `document.timeline.play(...)`
  * `new Animation(...)`
* partial layout
  * only compute what you need
  * holy shit, awesome!
  * it will only layout enough of the page to get the value you're asking for, then stop
* CSS grid
  * tables are so last century
  * `display: grid;`
* Responsive images
* Consistent subpixel fonts!
  * directwrite vs gdi
* Object.observe


