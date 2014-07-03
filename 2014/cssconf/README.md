# CSSConf 2014 Notes

1. [Style Guide Driven Development](#style-guide-driven-development)
2. [Styling and Animating SVG with CSS](#styling-and-animating-svg-with-css)
3. [The Chroma Zone](#the-chroma-zone)
4. [Embrace The Vertical](#embrace-the-vertical)
5. [Happy CSS](#happy-css)
6. [Bulletproof Icon Fonts](#bulletproof-icon-fonts)
7. [CSS In Your Pocket](#css-in-your-pocket)
8. [CSS and the Critical Path](#css-and-the-critical-path)
9. [Peachpuffs and Lemonchiffons](#peachpuffs-and-lemonchiffons)
10. [What on Earth is Perspective?](#what-on-earth-is-perspective)
11. [Parallax Performance](#parallax-performance)


## Style Guide Driven Development

Nicole Sullivan

### Use a style guide for front-end development
* https://console.run.pivotal.io/style_guide
* Hologram style guide - http://trulia.github.com/hologram

Break views into components.

### Figuring out how to make a good component (e.g., media block)
* what do we know about it?
    - can be nested?
    - etc
* what we don't know?
    - size may vary
    - content is unknown
    - etc
* separate structure from chrome

### What makes a good component?
* granularity (solve one problem well)
* flexibility (define what you don't know, e.g., width/height)
* low specificity (make rules the same strength)
* encapsulation
* modularity

> unsightly clean spot


## Styling and Animating SVG with CSS

Sara Soueidan - ([@SaraSoueidan](https://twitter.com/SaraSoueidan))

* CSS animations/hover effects are not preserved when embedded as <img> or css background-image.
* Object tag or inline SVG are preferred.
* Without the viewBox attr, preserveAspectRatio has no effect.
* SVG element default `transform-origin` is `0 0`
    - `0 0` is the top left corner of the SVG canvas, not the element you're styling
    - if set using % values, it's relative to the bounding box of the element (including stroke)
        + does not work at all in Firefox :(
        + there is a bug in chrome
        + basically, don't use it yet
    - otherwise it's relative to the SVG canvas
* Chrome does not HW accelerate 3d CSS transforms for SVG elements


### Animating Line Drawing
```css
#cable {
    stroke-dasharray: 4000 4000;
    stroke-dashoffset: 4000;
    transition: stroke-dashoffset 4s;
}
svg:hover #cable {
    stroke-dashoffset: 0;
}
```

Getting the path length:
```js
path.getTotalLength();
```


### Morphing Paths
:( It's not possible in CSS (hopefully some day?). Use [snap.svg](http://snapsvg.io).


### Making SVG Accessible

http://www.sitepoint.com/tips-accessible-svg/


## The Chroma Zone

Lea Verou ([@leaverou](https://twitter.com/leaverou))

https://github.com/LeaVerou
http://leaverou.github.io/contrast-ratio

> RGB is not exactly intuitive for humans

We're stuck with RGB because of how colors were designed in HTML 3.2.

Started with Hex colors.
CSS 1-2.1 gave us rgb() and some named colors.
CSS 3 gave us hsl, rgba/hsla, color names, currentColor.

```css
.box {
    filter: sepia() saturate(2) hue-rotate(90deg); /* chrome */
    background-blend-mode: multiply; /* behind a flag */
}
```

`currentColor` CSS variable.

Stripes

```css
.box {
    color: yellow;
    background: linear-gradient(currentColor 50%, transparent 50%);
    background-size: 0.1em 0.1em;
}
```


Coming soon:

gray()
4 and 8-digit hex (for transparency)
hwb() (hue/whiteness/blackness)
color adjusters (and color() fn)
named hues and <angle> in hsl()
rgb and hsl will (hopefully) accept alpha values (so you don't have to type the a)


## Embrace the Vertical

Antoine Butler ([@aebsr](https://twitter.com/aebsr))

```css
@media (max-width: 600px) {}
@media (max-height: 600px) {}
```

1. Content size is variable, not intrinsic
2. Increases scrolling
3. Device fragmentation
4. Squishy isn't good enough

Vertical media queries are an adaptive solution.

### Case study: Wikipedia
* long form reading
* serves an entirely separate site for mobile

http://bit.ly/WikiProto

Benefits:
* no device detection
* single codebase
* improved SEO and sharability

### Case study: VW.com
* sticky "vertical" nav

requirements:
* primary nav must support up to 6 items
* secondary nav must support unlimited items
* keyboard accessible

http://bit.ly/StickyNav


## Happy CSS

Christoph Burgmer ([@cburgmer](https://twitter.com/cburgmer))

### Tooling
* screenshot-based comparison
    - [CSSCritic](https://github.com/cburgmer/csscritic)
    - [Wraith](https://github.com/BBC-News/wraith)
    - [PhantomCSS](https://github.com/Huddle/PhantomCSS)
* Computed style checks
    - [Hardy](http://hardy.io/)
* More at http://csste.st/tools

### Ideas
* Apply automated CSS tests to a components style guide


# Bulletproof Icon Fonts

Zach Leatherman ([@zachleat](https://twitter.com/zachleat))

### @font-face
> learn everything we can about @font-face

```css
@font-face {
    font-family: name;
    src: url()....
}
```

Lots of hacks to get fonts working in all browsers...

### Unicode
* symbols! ≡★
* accessibility
    - screen readers reads special characters in unexpected ways
* private use area (PUA)
    - used in icon fonts to avoid overloading existing characters

### Loading
* FOIT/FOUT
* timeouts

https://github.com/filamentgroup/a-font-garde
https://github.com/typekit/webfontloader
https://github.com/bramstein/fontloader
http://dev.w3.org/csswg/css-font-loading/

### Fancy
* Transform text to an icon
* Transform unicode glyph to an icon


## CSS In Your Pocket

Angelina Fabbro ([@angelinamagnum](https://twitter.com/angelinamagnum))

### Two types of CSS debugging
* layout
* performance

### Workflow
* Get your layout right early
    - who is your target demographic? decide on target devices and browsers
    - prototype the layout in your browser (don't worry about look/feel yet)
* Design within the context of your constraints
* Start testing on the actual devices
* Layout good? Perf time! Use this point as your baseline

### Tools
* FF responsive design tool
* Chrome device emulation
* `csscoverage` tool - FF nightly
* charles, network link conditioner

https://github.com/scottjehl/Device-Bugs


## CSS and the Critical Path

Patrick Hamann ([@patrickhamann](https://twitter.com/patrickhamann))

* Speed was rated 2nd most important feature by users, only after easy-to-find content
* Our websites should render in under 1000ms

### Browser rendering 101
1. network request
2. parse HTML, CSS
3. create DOM and resolve dependencies (go back to 1.)
4. execute synchronous javascript (blocks rendering)
5. render tree
6. layout
7. paint

HTML + CSS should be the only thing on your critical path. CSS can be inlined to reduce the critical path to a single HTTP request.

### Tools
* pagespeed mod for apache/nginx
* grunt-uncss

### Future
* SPDY/HTTP2
* ServiceWorker

> Performance is a requirement, not a feature


## Peachpuffs and Lemonchiffons

Alex Sexton ([@slexaxton](https://twitter.com/slexaxton))

History of CSS Colors


## What on Earth is Perspective?

Eva Ferreira

### Elements
* point of sight
* horizontal line (horizon)
* vanishing point

```css
.box {
    transform: perspective(500);
    transform: rotate3d(1, 0, 1, 45deg);
}
```


## Parallax Performance

Paul Irish ([@paul_irish](https://twitter.com/paul_irish))

**parallax** - moving elements in different Z layers along with the natural scroll pace
**peeler** - revealing layers along with scroll
**scrolljack** - taking over the natural scroll of the user to display an alternate page velocity

### Jank
* paint storms - excess painting (more than should be happening)

### Jank-free transitions:
* Opacity
* Transform

### Handle input responsibly
For mousewheel/touchstart/scroll
* bind low in the DOM (don't use event delegation)
* bind late
* unbind ASAP
* speed up the handlers
* avoid JS handlers altogether

### Pure-CSS parallax (the Kellum/Keith technique)
http://codepen.io/scottkellum/pen/bHEcA/
