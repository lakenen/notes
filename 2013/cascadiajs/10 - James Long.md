# James Long

@jlongster

High Perf webgl apps with lljs and asm.js

**machine types**
* 32-bit ints all the way == fast for JIT

**ASM.js**
"use asm" - AOT (AheadOfTime - Firefox only) vs JIT (JustInTime - Chrome, Firefox)

**emscripten**
* compile llvm bytecode to JS (asm.js target)
* it's fast because
  * 100% type consistency (types are known at compile time)
  * no garbage collection (manually managed memory in large typed array)

**[LLJS](https://github.com/jlongster/lljs)**
* compiles down to asm js

