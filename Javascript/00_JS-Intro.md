# JS-Introduction
---
## What is JS
+ a programming language.
> 	Single Treaded (one-at-a-time) event loop queue that drives all "events" (async function invocations). non-blocking in nature.
+ a core tech (alongside HTML and CSS), that makes web run.
+ a “safe” programming language. 
	+ It does not provide low-level access to memory or the CPU, because it was initially created for browsers which do not require it.
	+ limited to protect the user’s safety.
+ LiveScript - initial name
	+ changed to JavaScript to leverage Java’s popularity
	+ positioned as a “younger brother” to Java
	+ now it has no relation to Java at all
+ __Scripts__ - program in JS
	+ run automatically as page loads
	+ executed as plain text
	+ don't need special preparation/compilation to run
+ Engine - JS runs in any device with JS engine
	+ JavaScript virtual machine - browsers have an embedded engine


### ECMAScript
+ **ECMAScript** - is a standard. 
	+ **JavaScript** is the most popular _implementation_ of that standard. Other implementations include: [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey), [V8](https://en.wikipedia.org/wiki/Chrome_V8), and [ActionScript](https://en.wikipedia.org/wiki/ActionScript).
	+ [The ECMA-262 specification](https://www.ecma-international.org/publications/standards/Ecma-262.htm) contains the most in-depth, detailed and formalized information about JavaScript
+ Manual - 
	+ [MDN JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) is the main manual with examples and other information.
+ Compatibility tables 
	+ https://caniuse.com – per-feature tables of support



### Why is it called JavaScript

## Mental Model


## Security/Limitation (to fill)
+ JavaScript’s abilities in the browser are limited to protect the user’s safety.
+ JavaScript’s capabilities greatly depend on the environment it’s running in.
+ Same Origin Policy

- **IDE (Integrated Development Environment)**: Full-featured software with tools like debugging, code suggestions, and project management, all-in-one.
- **Lightweight Editor**: Simple and fast code editor focused on editing text, with fewer built-in tools, but often customizable with extensions.


That had the benefit of never breaking existing code. But the downside was that any mistake or an imperfect decision made by JavaScript’s creators got stuck in the language forever.

This was the case until 2009 when ECMAScript 5 (ES5) appeared. It added new features to the language and modified some of the existing ones. To keep the old code working, most such modifications are off by default. You need to explicitly enable them with a special directive: `"use strict"`

- **Number**: Numeric values (e.g., `42`, `3.14`).
- **String**: Text data (e.g., `"Hello"`).
- **Boolean**: `true` or `false`.
- **Undefined**: Variable declared but not assigned a value.
- **Null**: Represents no value.
- **Object**: Collection of key-value pairs.
- **Symbol**: Unique and immutable identifier.
- **BigInt**: For numbers larger than `Number` can handle.



> References
> - https://javascript.info/
> - https://www.theodinproject.com/
