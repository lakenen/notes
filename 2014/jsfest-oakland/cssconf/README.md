# CSSConf

## What makes something revolutionary?


## The future of CSS

@tabatkins

### The `image()` function

Examples:
- fallback to a color: `image("foo.png", blue)`
- spriting: `image("spritesheet.png#xywh=40,60,20,20", "icon.png")`

### The `image-set()` function

`image-set("normal.png" 1x, "high-res.png" 2x, "print.png" 500dpi)`


### The `cross-fade()` function
Cross-fade btw images
`cross-fade(<percentage> ...)`

### image-scale (?)
smooth-edges pretty cool!!!

### flexbox (yay)

### grid alignment

like tables, but better
grid-template ascii art

tip: use a media query to change layout for portrait vs landscape

rachel andrew's - grid by example
phili walton's - solved by flexbox


### selectors level 4

#### `:nth-child(even of [selector])` (soon to be implemented)

#### `:matches()`

```css
tbale.foo :matches(td, th) p.bar {

}
```


### css variables

see them in 2015


### color!

new color spec

- 4/8 digit hex for alpha
- all alpha accept percentages
- hue accept angles
- `hwb()`
- `gray()`
- `color()`

### media queries

pointer: "coarse" or "fine"
hover: "yes" or "no"

more?

### animation

- web animations spec (css animations that are useful in js)
- motion path (animate around a path in two dimensions)

### polyfilling css

- custom media queries


## SVG Can Do That?!

@brnnbrn

viewbox rules everything around me (v.r.e.a.m.)

overview and examples of a bunch of cool svg stuff


## What's in a name?

stories behind css color names


## Creating responsive emails


## css is 20k
mrmrs
