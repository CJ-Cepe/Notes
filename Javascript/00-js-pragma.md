# Pragma/Directives
---
__Pragma (Directive)__
: a special instruction in code that:
+ Guides Behavior: Informs the compiler (or other translator) on how to process its input.
	+ these strings have no effect during runtime. But at compile time, the compiler is configured to notice these strings and change the output accordingly
+ Not Part of Code Logic: Doesn’t directly affect the code’s output.
+ Common Examples: `"use strict"` in JavaScript or `#pragma` in C/C++ for optimizations.

## JS Directives
**StrictMode using `"use strict"`**
+ What is StrictMode
	+ Enables a stricter mode in JS - follows stricter rules.
		+ allows you to place a program, or a function, in a “strict” operating context
		+ ECMAScript 5 is backwards-compatible with ECMAScript 3,
			+ all of the “features” that were in ECMAScript 3 that were “deprecated” are just disabled (or throw errors) in strict mode, instead.
		+ the JS engine enforces additional constraints. This means you may be able to catch some common errors that would have otherwise gone unnoticed.
	+ History - introduced in ECMAScript 5 (ES5) 2009
		+ JS evolved for a long time without compatibility issues - new feats added while old functionalities didn't change
		+ ES5 added new feats and modified some existing ones
		+ to keep old working, most modifications are OFF by default.
		+ explicitly enable them with a special directive: `"use strict"`
	+ Benefits :
		+ Prevents Errors: Stops using unsafe features.
			+ It disables features that are confusing or poorly thought out.
		+ Disallows Mistakes: Like using undeclared variables.
		+ Improves Performance: Helps engines optimize code.
		+ Reserved Keywords: Blocks use of future JavaScript keywords.
+ Explicitly enable by placing on:
	+ top of the script - strict mode in the whole script
		```js
		"use strict";

		// this code works the modern way
		...
		```
	+ beginning of a function - strict mode in that function only
		```js
		function imStrict(){
		  "use strict";
		  // ... your code ...
		}
		```
+ Implicitly enabled / Strict Mode by Default
	+ ES6 classes - anything inside
	+ ES6 modules
	+ Arrow functions
	+ Tagged template literals
	+ Compilation tools: webpack, etc.
+ ==!==Remember
	+ make sure that `"use strict"` is at the top of your scripts, otherwise strict mode may not be enabled.
	+ only _comments_ may appear above `"use strict"`
	+ there’s _NO_ way to cancel `"use strict"`
	+ if you're only writing code for modules, you won't have to include `"use strict"` anywhere because its already implied
	+ in developer console, it doesn’t `"use strict"` by default
+ Developer Console - enabling
	+ Multiple lines via <kbd>Shift+Enter</kbd>
		```JS
		'use strict'; <Shift+Enter for a newline>
		//  ...your code
		<Enter to run>
		```
	+ Inside a wrapper
		```javascript
		(function() {
		  'use strict';
		
		  // ...your code here...
		})()
		```
+ Changes & Feats 
	+ Variables and Properties
		+ Assigning an undeclared variable (`foo = "bar";`) throws an error instead of attaching to the global object. 
			+ in non-strict `foo = "bar"` == `windows.foo = "bar"`
			+ disallows global variables - catches missing `var` declarations
		+ Deleting a variable, function, or argument results in an error.
			- (`delete myVar;`)
			- (`delete myFunction;`)
			- (`delete arg;`)
		- Writing to non-writable properties, deleting non-configurable properties, or adding properties to non-extensible objects throws errors.
			- (`delete Object.prototype`)
		- Defining a property more than once in an object literal throws an exception.
		- Forbids octal syntax 
			- (`var x = 023;`)
	+ Functions
		+ Overwriting the `arguments` object results in an error. 
		+ Duplicate parameter names in functions are disallowed
			- (`function sum (x, x) {...}`)
		- The `arguments` and `caller` properties of functions are no longer accessible or definable.
		- A bug preventing `null` or `undefined` from becoming the global object has been fixed, and an exception is now thrown.
	- Objects
		- Requires all property names in an object literal to be unique 
			- (`var x = {x1: "1", x1: "2"}`)
	+ with(){}
		+ Forbids the `with` keyword
+ Questions
	+ How come`"use strict"`is for enabling StrictMode when based on its history it is for turning on modifications in ES5? (ans by gpt)
		+ **Original Purpose**: `"use strict"` was introduced with ES5 to enable modifications and improvements without breaking existing code.
		- **Strict Mode**: These modifications created a stricter version of JavaScript, enforcing better practices.
		- **Unified Meaning**: So, `"use strict"` not only turns on ES5 features but also applies stricter rules, like disallowing undeclared variables or certain syntax mistakes.
		+ In essence, it's both enabling new ES5 features and enforcing stricter standards, which is why the term "strict mode" is often used to describe it.


References
+ [js.info](https://javascript.info/strict-mode)
+ [ES5 strictmode](https://johnresig.com/blog/ecmascript-5-strict-mode-json-and-more/)
+ [stackoverflow](https://stackoverflow.com/questions/1335851/what-does-use-strict-do-in-javascript-and-what-is-the-reasoning-behind-it)
+ gpt

