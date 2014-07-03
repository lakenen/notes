# 60FPS Layout and Rendering

Tom Wiltzius and Nat Duca

jankfree.org, html5rocks.com

### Basics
* Frames are 16ms
* The rendering system is hecka complicated, #yo
* Try to work with the browser when possible:
  * rAF (vs timer), CSS anim (vs JS anim), etc

> interactivity drives engagement

> things feel "webby" when they're slow, jittery

### Painting & Layers
* JS to screen:
  1. dirty the style
  2. recalculate the style, maybe relayout
  3. paint the browsers mental model to a layer
  4. composite all layers into a final image
* Animating CSS properties
  * only opacity and transform will composite
  * the rest will paint and possibly layout
* **paint storm** - painting over and over again, repeating that cost
  * solution: decompose page into layers that animate together
* gotchas:
  * lost LCD text antialiasing? add solid color background
  * auto layer creation is hi-DPI and Android only
  * emulating position:sticky? consider backface-visibility: hidden
  * layers aren't free: hide any you don't need

### From your finger to the screen (Touch Latency)
* options for sticky finger goodness
  1. Hit the fast scroll path - OR -
    * make sure layers were created and working
    * desktop makes different layers than Android
    * HighDPI vs LowDPI matters
  2. *carefully* and *quickly* handle touch in JS
    * keep everything < 7ms a frame on mobile
      * most modern phones are so resource-constrained that there's significant enough overhead that 16ms is heavily shared
    * avoid input foot guns
      * install touch listeners *after* load (or risk 200ms scrolling jank or worse)
      * if listening for touchend, also listen for touchcancel!
      * 300ms tap delay
      * mousewheel listeners block scrolling

> layers are good, but they're very hard to persuade to exist

### Android (Chrome) WebView
* please use h/w acceleration
* watch the DOM size: we paint it all
* UI thread shared with native view

### Making it faster
* make layout, recalc faster
* calming paint storms
* fix image cache

