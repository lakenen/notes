# David Bruant

@davidbruant

how web tech comes to be...
* in ideal world the spec comes first
* in reality the spec comes last

regrets... https://github.com/DavidBruant/ECMAScript-regrets

**regrets in JS**
* `isNaN` is a mess
  * solution: `Number.isNaN`
* `typeof null === 'object'`, should be 'null'
  * solution: use `x === null`
* `undefined`, `NaN`, `Infinity` can be reassigned and declared as fn
  * solution: don't
  * use eslint, etc, to make sure it doesn't happen
* inadequate dynamic `this`
  * solution: `"use strict", var self = this`
  * ES6: arrow `=>` functions
* stateful regexp
  * `var re = /foo/g;`
  * `console.log(re.test('now foo')); // true`
  * `console.log(re.test('foo now')); // false`
* non-intuitive: `! 'property' in object`
  * solution: extra parens, eg `!('property' in object)`

**regrets in css**
* `{box-sizing: border-box; }`

**regrets in dom**
* `node.parentNode.removeChild(node);`

**regrets in html**
* `XMLHttpRequest`...
* `localStorage` - per-origin storage
* why not `<style src="">` vs `<link>`?
