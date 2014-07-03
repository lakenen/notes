# JSConf 2014 Notes

---
# TO WATCH:
* G. C. Marty - Play DVDs in JavaScript for the sake of interoperability
* Kawandeep Virdee - Open Web Art: JavaScript for Interactive, Collaborative, and Hackable Art

---

## Writing Custom DSLs

Neil Green

### Model your domain
### Implement the domain model
* write tests first
* then write code to pass the test
* then refactor

DSLs make complex problems simpler

1. review conversation with customer
2. remove meaningless words
3. separate nouns and verbs
4. identify idioms
5. review grammar
6. implement grammar


## Emotional Safety FTW

Jenn Turner


## Battle Hardened Node.js for the Enterprise

meh


## Front End Ops Tooling

Nicolas Bevaqua


TL:DR use grunt or gulp


## UI Algorithms

Mark DiMarco @bazaarvoice

Defining "algorithm" -


## Native Code on the Web

Nick Bray

### The web is:
* secure
* portable - works everywhere
* ephemeral - you don't have to install anything

### Solutions:
* Plugins
* PNaCl
* Emscripten

pepper.js (JS polyfill for the PNaCl pepper interface)

### Why Threads?
* structure
* throughput
* latency
* cores (taking advantage of hw resources)

side note: parallelism != concurrency


## Montage JS

Ryan Paul @segphault

meh


## Yield Ahead: Regenerator in Depth

Ben Newman @benjamn

### How can ES6 avoid the python 3 trap?
Ease into the language by simulating its most useful features in the current version of JS

1. parse code into AST (recast)
2. traverse and modify the syntax tree
3. print the new code

facebook/regenerator


## Everything is broken and I don't know why

Matt Robenolt

Error.prototype.stack is a string ಠ_ಠ

* Browser errors are not standardized
* Minification/obfuscation makes debugging difficult (line numbers are meaningless)


### V8 CallSite API

```js
Error.prepareStackTrace = function (error, frames) {
    return frames;
};

var frame = err.stack[0];
frame.getFunctionName();
frame.getLineNumber();
frame.getColumnNumber();
```

### Sentry/raven.js

Monkeypatching native objects and popular libraries, for better error handling
Sentry will fetch source maps and give a nice clean view of the error


## Engineers as Makers

Edward Kim @edwardjkim


## ES6 Modules

Guy Bedford @guybedford

jspm.io

### Module Loader
gh:moduleloader/es6-module-loader

### Browser Loader
* promise-based loader

gh:systemjs/systemjs
* compatibility layers for AMD, CommonJS, globals
* map, shim, plugins
* bundles, versions

### Package Manager

#### Http2
* no more bundling
* fine-grained caching
* allow unique versioned URLs

#### Dependency MGMT
* version conflicts
* support multi-versions / auto-deduping
* semantic versioning
* central dependency manifest

### Demo

```
npm install -g jspm
jspm install github:guybedford/markdown-component
```

index.html
```html
<html>
    <head>
        <script src="jspm_packages/system@0.6.js"></script>
        <script src="config.js"></script>
        <script>
            System.import('app');
        </script>
    </head>
    <body>
        <x-markdown-component>
            # this is some markdown
            ```js
            System.import('app').then(function () {
                // yay
            });
            ```
        </x-markdown-component>
    </body>
</html>
```

app.js
```js
require('github:guybedford/markdown-component');
```


### Next Steps

* conditional loading
* build tooling for plugins and conditionals


## Modular Frontend with NPM and Pals

Jake Verbaten @Raynos

* how to use modules in your app
* authoring small modules is great for collab
* author self-contained ui widgets as modules
* how to build your own custom flexible "framework" from modules

### Tools
* npm
* browserify
* unix

See: browserify handbook (by substack)

### Using (small) modules

#### why?
* pick the best of everything
* use exactly what you need, no more
* no lockin, freedom to switch whenever

#### where?
* nice groups on gh
    - npm-dom
    - modulesGL
    - voxelJS
    - levelDB
    - streams handbook
* ask people!

### Modules and Collaboration
People can reuse and expand on small self-contained modules

### Building a modular "framework"

* decompose the problem space
* work from the ground up
* solve each small problem well in isolation

test UI widget npm modules - requirebin.com


## canvas performance
how 2 pixels good

Angelina Fabbro @angelinamagnum

> optimizations are a last step, best practices should be every step

shaders:
programs that run on the GPU that give your 3d drawings "life"
vertex shaders transform position


### tools
* FF canvas inspector
* FF shader editor

### perf best practices
* whole-pixel rendering (round when possible)
* cache drawing in an offscreen canvas (img copying is faster than redrawing)
* multiple layers should use multiple canvases
* only draw what you have to (don't draw hidden stuff, don't draw pats that haven't changed)
* use HTML/CSS for unchanging background
* realtime data (including UI events) should use a queue and rAF to draw instead of drawing as it comes in
* use css3 3d transform to scale a canvas
* avoid frequent calls to localStorage (or do it when you're not animating a lot of stuff)
* reuse objects to avoid GC
* misc
    - use bitwise operations instead of math.floor
    - clear arrays with length = 0


## Hacking HTML renderer in JS

Christoph Burgmer @cburgmer

### What are we doing?
* misuse new browser features
* use js to manip html/css/js/ svg

1. trigger html rendering from JS
2. get a screenshot from the page
3. render html to cavas

ff can draw window to canvas, but only in a plugin :(

### SVG foreignObject to the rescue?
* svg is xml and only allows aml in foreignObject
* firefox can do it, shim for other browsers

### SVG and external resources
Inline all the things!
* imgs with blob/data:uri
    - ajax + binary = :(
* CSS
    - Create a CSS document and load the rules


## Distributed Complex Computing Using Node.js

Dan Silivestru

0mq

fourism


## Paving Cowpaths and Finding New Ones

Forrest Norvell @othiym23

### Who defines JS?
* TC39
* stakeholders
* the JS dev community

### ES6 as a reaction to ES4
* led by stakeholders, but not implementors
* changed the language too much
* forked the lang and standards body
* NEVER IMPLEMENTED

### Harmony
1. don't break the web
2. new lang features require concrete implementations
3. keep the lang pleasant for casual devs
4. improve interop
5. preserve harmony

### Community standards
* modularity
    - browserify and commonJS
    - require.js and AMD
* async control flow
    - promises/A+

### Links
* gh:rwaldron/tc39-notes
* esdiscuss.org
* bugs.ecmascript.org
* gh:tc39/test262

### Status?
* current forecast: end of 2014!
* in a browser: ?
* in node: ???

### Beyond ES6
* strawman proposals
* championed by delegates and subcommittees
* example implementations

### Now plz?
* ff dev channel
* traceur
* es6-shim
* es6-module-transpiler
* es6-module-loader
* sweet.js

### Conflicts
* "flattening" vs "monadic" promises, DOMFutures vs Promises/A+
* AMD vs CommonJS vs ES6 modules
* only room for one standard in the lang


## Deployment for the 99%

Mikeal Rogers @mikeal


## Immutability

David Nolen

To read: "the dream machine" by M. Mitchell Waldorp

MVC is nice as an abstract concept, but implementations use stateful objects everywhere

### Functional programming and data
* immutable values, *not* mutable objects
* "change" returns a new value, leaving the old one unmodified
* they're persistent (you are not destroying previous values)
* they're fast

### Bitmapped vector trie
* data lives in the leaves
* prefix tree for string lookup
* bitwise lookup
* array of arrays (of the same size)

mori (npm module)

Om

## Reactive Game Development for the Discerning Hipster

Bodil Stokke @bodil

Live-coding a game UI in RxJS


## Modules for the browser

Kevin Whinnery

### Design to be browserified
* expose a browser-specific entry point
* define any custom shims for dependencies as needed
* setup source transforms (e.g., coffeescript)

### package.json
* "browser" property
    - string: relative path in the directory to a file to use in the browser
    - object: override specific files (key is the file to override, value is the new file)
* "browserify" property (object)
    - "transforms": array of strings of modules to use to transform (e.g., ["coffeeify"])

### Use case - twilio clinet (voip)
* enable voip calling btw browsers, mobile apps, and standard pstn phones

**SIDE NOTE**: ngrok.com - assign a public-facing URL to a local port on your machine


## Eval Everything

Adam Fortuna

* using iframes to run user code
* web workers for running jshint asynchronously

### Client-side execution

> if iframes aren't working for you, you aren't using enough of them

sandboxed stuff:
* gh:codecademy/stuff.js

rewrite code to prevent infinite loops:
* gh:constellation/escodegen
* gh:benjamn/recast


## Fearless browser test automation

John-David Dalton (@jdalton)

Manual testing sucks

### Services
* Sauce labs
* testling
* travis-ci

### npm deps
* chalk (coloring)
* ecstatic (static file server)
* request
* sauce-tunnel

### sauce labs stuff
* test IE compat modes
* concurrent tunnels
* auto retry
    - tunnel from travis to sauce might fail due to network issues, etc
* make grunt do it
    - gh:axemclion/grunt-saucelabs

### weird stuff
* gem install travis
* travis engrypt SAUCE_ACCESS_KEY=""
* window.global_test_results
* android testing
