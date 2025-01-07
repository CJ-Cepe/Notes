# 🌌 Literals
+ __Literals__: fixed values written directly into the code
	+ These are fixed values—not variables—that you literally provide in your script.
	+ Examples
		+ String literals - zero or more characters enclosed in double (") or single quotation marks (')
		+ object literals - a list of zero or more pairs of property names and associated values of an object, enclosed in curly braces ({ })
		+ Others - array literals, numeric literals, Boolean literals, regex literals, etc.
## ☄️ Template Literals
+ informally referred as _Template Strings_
+ literals introduced in ES6 delimited with backtick (`` ` ``) characters
	+ backticks are “extended functionality” quotes 
+ allows multi-line strings, string interpolation with embedded expressions, & special constructs called tagged-templates
+ can also contain other parts called _placeholders_, which are embedded expressions delimited by a dollar sign and curly braces: `${expression}`
	+ The strings and placeholders get passed to a function — either a default function, or a function you supply. The default function (when you don't supply your own) just performs [string interpolation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#string_interpolation) to do substitution of the placeholders and then concatenate the parts into a single string.
### 🛰️ Multi-line string
- Template literals respect the line breaks in the source code, so you can write strings that span multiple lines like this:
	```jsx
	const output = `I like the song.
	I gave it a score of 90%.`;
	console.log(output);
	
	/*
	I like the song.
	I gave it a score of 90%.
	*/
	```
### 🛰️ String Interpolation
+ create strings by doing substitution of placeholders
+ insert, or _interpolate_ | embed, expressions into strings `${expression}`
+ Mild difference between concatenation and template literals
	+ Template literals coerce their expressions directly to strings, while addition coerces its operands to primitives first.
	```jsx
	// embed a variable
	const myPet = 'armadillo';
	console.log(`I own a pet ${myPet}.`); // I own a pet armadillo.

	// embed an expression
	alert( `the result is ${1 + 2}` ); // the result is 3

	// 2nd sample
	// concatenation vs template literals mild diff
	const obj = {
	  toString() {
	    return "I am a string";
	  },
	  valueOf() {
	    return 42;
	  },
	};
	
	const concatResult = "Object: " + obj; // Using concatenation
	const templateResult = `Object: ${obj}`; // Using template literals
	
	console.log("Concatenation Result:", concatResult);
	console.log("Template Literal Result:", templateResult);

	// OUTPUT
	// Concatenation Result: Object: 42
	// Template Literal Result: Object: I am a string
	```

### 🛰️ Tagged Templates
+ customize interpolation - a more advanced form
+ allows you to parse template literals with a function
+ _Tag function_ - `function tag(strings, firstValue, secondValue) {...}`
	+ 1st argument - array of strings
		+ length equal to the number of substitutions (occurrences of ${…}) plus one, and is therefore always non-empty
	+ remaining arguments - expressions
```js
//1st Example
	function tag(strings, ...values) {
	  console.log(strings); // Array of string literals
	  console.log(values);  // Array of interpolated values
	  return strings[0] + values.join(" and ") + strings[1];
	}
	
	const name = "Alice";
	const age = 25;
	
	const result = tag`My name is ${name} and I am ${age} years old.`;
	console.log(result);
	
	//OUTPUT
	// [ 'My name is ', ' and I am ', ' years old.' ]
	// [ 'Alice', 25 ]
	// My name is Alice and I am 25 years old.

//2nd Example
	let x = 10, y = 20, z = 30;
	
	const debug(strngs, ...exps){
		console.log(strs, exps)
	}
	
	debug`${x}${y}${z}` // ['', '', '', ''], [10, 20, 30]
	
	debug`${x}${y}` // ['', '', ''], [10, 20]
	
	debug`${x}` // ['', ''] , [10]

	debug`` // [''], []

	debug`${x + y + z}` // ['', ''], [60]
```