# Tooling Techniques for the Performance Ninja

Colt McAnlis

> what you can **measure** you can **optimize**

### Three steps to perf tooling
1. get data
2. get insight
3. take action
4. repeat

### Three pillars of web perf
* Network
  * optimize critical path
* Rendering
  * reduce \# of paints
* Compute
  * reduce JS execution time

### Network
* ~~load time~~
* *critical path*
  * not just about loading - about what pixels are needed to get to the screen
  * assets that are requested with HTML content in the critical path
  * you cannot paint until **critical path** is resolved
  * optimize!
    * reduce **\# of dependencies** in critical path
    * reduce **size of dependencies** in critical path

### Rendering
* When you modify the DOM, all the properties have to be recalculated and repainted

> we got cat pictures and we want to deliver the cat pictures in a cat-friendly way because it's a cat picture world that we live in

>scrolling isn't the only place that painting occurs

### Compute
* 16ms frame shared between rAF/JS, and browser (paints, GC, etc)