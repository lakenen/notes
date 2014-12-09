# Browserified

## Browserify All The Things!

This talk was just a brief history and overview of what module/dependency management stuff exists for client-side javascript, including an overview of browserify and why it's useful. Some stuff about API design, good documentation, and build automation. Kinda all over the place...

### Poser
Extending natives safely:
- in browser, create iframe, pull in the native object from that frame
- in node `vm.runInNewContext`


## Browserify big projects with minimal rage

- gradual conversion by adding new entry-points (read: globals)
- use transforms
  + includify (inject a file in place)
  + deamdify (converts AMD-style to commonjs)
  + debowerify


## brick the web
(@substack)

appcache "manifesto" that bricks your website (you get it once...)

htmlb.in

## hyperboot
hyperboot.org


## page bus
local message bus between pages

## keyboot
> single sign-on as a bricked static web page

## browserify as a service
wzrd.in

## browserified browserify
browserify in the browser


## winning the internet with browserify
r/perfectloops

sweet looping gifs made with canvas and browserify

