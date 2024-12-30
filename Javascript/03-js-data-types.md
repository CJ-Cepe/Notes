# DATA TYPES/Values

+ 2 categories
	+ **Primitive** - store values directly
		+ Immutable - values can't change
			+ variables are not values. variables point to values
		+ There’s nothing I can do in my code that would affect them
		+ If you attempt to set a property on a primitive value, be it a number or a string or something else, JavaScript won’t let you do that. Whether it will silently refuse your request or error depends on which mode your code is running in.
	+ **Complex/compound** - store references
		+ objects and functions
		+ can manipulate them from my code.
+ Expressions are questions that JavaScript can answer. JavaScript answers expressions in the only way it knows how — with values.
	+ Expressions always result in a single value.
+ 8 types of primitive values
	+ boolean, number, bigInt, string, null, undefined, symbols, objects
+ Values
	+ A value is a thing in the JavaScript universe.
	+ There are values, and then there’s everything else. They don’t exist inside our code, but we can refer to them from our code.
+ Variables - We only said it’s the primitive values that can’t change. We didn’t say anything about variables!
	+ Variables are not values. Variables point to values.
	+ console.log(pet);
		+ But note that it is not the pet variable that we pass to console.log. We might say that colloquially, but we can’t really pass variables to functions. We pass the current value of the pet variable.
		+ When we write pet, we’re asking JavaScript a question: “What is the current value of pet?” To answer our question, JavaScript follows the pet’s “wire”, and gives us back the value at the end of this “wire”.
+ Variables always point at values.
	+ Variables are not values. Each variable points to a particular value. We can change which value it points to by using the = assignment operator.



## Primitive
### Boolean  (true and false), used for logical operations.
+ Binary nature - `true` `false`
	+ true - “yes, correct”
	+ false - no, incorrect
+ Boolean values as a result of comparisons
	```js
	let isGreater = 4 > 1;
	alert( isGreater ); // true (the comparison result is "yes")
	```
### Number (-100, 3.14, and others), used for math calculations.
+ represents _integer_ & _floating point_ numbers
	+ displays numbers as **base 10** decimals by default
+ numbers are stored in 64-bit format [IEEE-754](https://en.wikipedia.org/wiki/IEEE_754), also known as [_“double precision floating point numbers"_](https://robotacademy.net.au/lesson/pixel-data-types/)
	+ sign bit (1 bit): determines the sign of the number (0 for positive, 1 for negative)
	+ exponent (11 bits): represents the power of 2 that the significand is multiplied by
	+ significand (52 bits): the actual digits of the number, including the fractional part
		+ Sign (1) + Exponent (11) + Significand (52) = 64 bits
+ highest integer value that a number can go to without losing precision
	+ safe integer range `±(2^53-1)`
	```js
	Number.MAX_SAFE_INTEGER // represents the maximum safe integer value
	Number.MIN_SAFE_INTEGER 
	```
	+ Integers are accurate up to 15 digits
	```jsx
	let x = 999999999999999;   // x will be 999999999999999
	let y = 9999999999999999;  // y will be 10000000000000000
	```
	- the maximum number of decimals is 17
		```jsx
		let x = 0.1 + 0.2; // x will be 0.30000000000000004, not 0.3
		```
- can be written with or without decimals
	```js
	let integer1 = 10;
	let decimal2 = -0.01;
	let billion = 1000000000;

	// _ as the separator (syntactic sugar)
	let billion = 1_000_000_000; // js engine ignores _
	```
+ can be written with Scientific Notation
	```js
	// appending "e" and specifying the zeroes count
	// larger - multiplication by 1 with given zeroes
	let billion = 1e9; // 1 billion, literally: 1 and 9 zeroes
		1e3 === 1 * 1000; // e3 means *1000
		1.23e6 === 1.23 * 1000000; // e6 means *1000000
	// smaller - division by 1 with given zeroes
	let mcs = 1e-6; // five zeroes to the left from 1
		1e-3 === 1 / 1000; // 0.001
		1.23e-6 === 1.23 / 1000000; // 0.00000123
		1234e-2 === 1234 / 100; // 12.34, decimal point moves 2 times
	```
- JS will try to convert strings to numbers in all numeric operations (- * /)
	- except + since it is concatenation
- the JS interpreter works from left to right ??
	```jsx
	let x = 10;
	let y = 20;
	let z = "30";
	let result = x + y + z; // "3030" result
	```
- Supported number system - Hex, Binary and Octal numbers
	```js
	// Hexa - 0x
	alert( 0xff ); // 255
	alert( 0xFF ); // 255 (the same, case doesn't matter)

	// Octal - 0o
	let a = 0o377; // octal form of 255
	
	// Binary - 0b
	let b = 0b11111111; // binary form of 255
	```
#### Special numeric values
##### NaN (Not a Number)
- `NaN`is a number: `typeof NaN`returns `number`
	+ indicates that a number is not a legal number
	+ represents the idea of an "invalid" number.
	+ represents a computational error
	+ result of an incorrect or an undefined mathematical operation
+ `NaN` is sticky
	+ any mathematical operation on NaN returns NaN
		```js
		alert( NaN + 1 ); // NaN
		alert( 3 * NaN ); // NaN
		alert( "not a number" / 2 - 1 ); // NaN
		```
	+ trying to do arithmetic with a non-numeric string will result in `NaN`  (Not a Number)
		```js
		let x = 100 / "Apple";
		isNaN(x); //NaN
		```
+ `isNaN(value)` to check for NaN
	+ why not `===` ?
		+ the value NaN is unique - it does not equal anything, including itself
			```js
			alert( NaN === NaN ); // false
			```
	+ `Number.isNaN(value)` - stricter version checks number type
##### Infinity (-Infinity)
- `Infinity`(or `-Infinity`) is a number: `typeof Infinity`returns `number`
+ represents the mathematical Infinity ∞
+ a special value that’s greater/lesser than any number
+ division by 0 (zero) generates `Infinity`
	```js
	alert( 1 / 0 ); // Infinity
	```
+ if it overflow the 64-bit storage (largest possible number)
	```js
	alert( 1e500 ); // Infinity
	```
+ `isFinite(value)` to check for Infinity
	```js
	alert( isFinite("15") ); // true
	alert( isFinite("str") ); // false, because a special value: NaN
	alert( isFinite(Infinity) ); // false, because a special value: Infinity

	//validate whether a string value is a regular number
	alert( isFinite("15") ); // true
	```
	+ `Number.isFinite(value)` - stricter version checks number type

### BigInt (uncommon and new), used for math on big numbers.
- for integer numbers of arbitrary length
- represent whole numbers larger than `2^53 - 1`
- created by appending `n` or using `BigInt()`
	```js
	//appending n
	let x = 1234567890123456789012345678901234567890n;

	//calling BigInt() (without the new operator)
	let y = BigInt("1234567890123456789012345678901234567890");
	```
+ can mostly be used like a regular number
+ most operators that can be used on a JavaScript `Number` can also be used on a `BigInt`
	+ all operations on `bigints` return `bigints`
	+ arithmetic between a `BigInt` and a `Number` is NOT ALLOWED (type conversion can lose information)
	+ `BigInt` CANNOT be used with methods in the built-in Math object
	+ unary plus is not supported on `BigInts`
+ when inside `if` or other boolean operations, bigints behave like numbers

### String ("hello", "abracadabra", and others), used for text.
+ The internal format for strings is always [UTF-16](https://en.wikipedia.org/wiki/UTF-16)
	+ not tied to the page encoding
	+ JS has no character type
	+ indexes are zero-based
+ Strings are immutable
	```js
	let str = 'Hi';

	//error
	str[0] = 'h'; // error
	alert( str[0] ); // doesn't work

	//workaround
	str = 'h' + str[1]; // replace the string
	alert( str ); // hi
	```
- A string in JavaScript must be surrounded by quotes
	```js
	let str = "Hello";  //double quotes
	let str2 = 'Single quotes are ok too';  //single quotes
	let phrase = `can embed another ${str}`;  //backticks
	
	const sglDbl = 'Would you eat a "fish supper"?';
	const dblSgl = "I'm feeling blue.";
	```
- Escaping characters in a string
	```jsx
	const bigmouth = 'I\'ve got no right to take my place…';
	```
- **Template Literal** (String Interpolation)
	- To join together strings in JavaScript you can use a different type of string, called a _template literal_
	- allows to embed variables and expressions into a string `${expression}`
	- Backticks are “extended functionality” quotes 
	- we can insert, or _interpolate_, variables into strings using _template literals_
	```jsx
	// embed a variable
	const myPet = 'armadillo';
	console.log(`I own a pet ${myPet}.`); // I own a pet armadillo.

	// embed an expression
	alert( `the result is ${1 + 2}` ); // the result is 3
	```
	- Backticks
		- Backticks also allow us to specify a “template function” before the first backtick.
		- func`string`
			- The function `func` is called automatically, receives the string and embedded expressions and can process them
			- This feature is called “tagged templates”
- Multi-line string
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
- Special Characters
	- all special characters start with a backslash character `\` _"escape character"_
		- `\n` newline || `\r\n` windows
		- `\t` tab
		- `\\` backslash
		- `\u...` unicode
	- special character, such as `\n`, is counted as one
- String comparison
	- JavaScript uses the so-called “dictionary” or “lexicographical” order
	- Strings are compared letter-by-letter
	- The algorithm to compare two strings is simple:
		1. Compare the first character of both strings.
		2. If the first character from the first string is greater (or less) than the other string’s, then the first string is greater (or less) than the second. We’re done.
		3. Otherwise, if both strings’ first characters are the same, compare the second characters the same way.
		4. Repeat until the end of either string.
		5. If both strings end at the same length, then they are equal. Otherwise, the longer string is greater.
	- Not a real dictionary, but Unicode order
		- The comparison algorithm given above is roughly equivalent to the one used in dictionaries or phone books, but it’s not exactly the same.
		- For instance, case matters. A capital letter "A" is not equal to the lowercase "a". Which one is greater? The lowercase "a". Why? Because the lowercase character has a greater index in the internal encoding table JavaScript uses (Unicode)
	- A lowercase letter is always greater than the uppercase
	- Letters with diacritical marks are “out of order”
	- avascript are encoded using UTF-16 - each character has a corresponding numeric code
	- The characters are compared by their numeric code. The greater code means that the character is greater
- Accessing characters
	```js
	let str = `Hello`;

	// the first character
	alert( str[0] ); // H
	alert( str.at(0) ); // H
	
	// the last character
	alert( str[str.length - 1] ); // o
	alert( str.at(-1) );
	```
	+ `.at(pos)` method has a benefit of allowing negative position
		+  If pos is negative, then it’s counted from the end of the string
	+ The square brackets always return undefined for negative indexes
+ Iterate over characters using `for..of`
	```js
	for (let char of "Hello") {
	  alert(char); // H,e,l,l,o (char becomes "H", then "e", then "l" etc)
	}
	```

### null (null), used for intentionally missing values.
+ for unknown values – a standalone type
+ represents “nothing”, “empty” or “value unknown”
+ represents the INTENTIONAL absence of value
+ null is also a liar. Due to a bug in JavaScript, it pretends to be an object:
+  It is a primitive value, and it doesn’t behave in any way like an object. Unfortunately, typeof(null) is a historical accident that we’ll have to live with forever
### undefined (undefined), used for unintentionally missing values.
+ for unassigned values – a standalone type
+ represents lack of defined value - “value is not assigned”
+ reserved as a default initial value for unassigned things
	+ will have the value `undefined`
+ implies a variable's existence but lack of assignment

### symbols (uncommon), used to hide implementation details.
+ for unique identifiers
+ __Creation__: a Symbol value is created by calling the Symbol function.
	```jsx
	let sym1 = Symbol();
	let sym2 = Symbol("foo");
	let sym3 = Symbol("foo");
	```
- **Uniqueness**: Every **`Symbol`** is unique. Even if you create many symbols with the same description, they are different values. For example
	```jsx
	let sym2 = Symbol("foo");
	let sym3 = Symbol("foo");
	console.log(sym2 === sym3); // Outputs: false
	```
- **Not Automatically Coerced**: **`Symbol`** values are not automatically coerced to a string or number
	```jsx
	let sym = Symbol("foo");
	console.log("My symbol: " + sym); // TypeError is thrown
	```
- **`Symbol`** can be used as identifiers for object properties
	```jsx
	let myObj = {};
	let sym = Symbol();
	myObj[sym] = "value";
	console.log(myObj[sym]); // Outputs: "value"
	```


## Complex
### Objects ({} and others), used to group related data and code.

### Functions (x => x * 2 and others), used to refer to code.


## Type Conversions

String Conversion
	.String()
Numeric Conversion
	implicit
		operations (-, * /, %)
	explicit
		.Number()
		+Unary
+ Rules
	+ undefined -> NaN
	+ null -> 0
	+ true -> 1
	+ false -> 0
	+ string -> NaN
		+ whitespace + special chars removed start and end is removed
		+ "" -> 0
		+ "non-empty string" -> NaN
```js
alert( Number("   123   ") ); // 123
alert( Number("123z") );      // NaN (error reading a number at "z")
alert( Number(true) );        // 1
alert( Number(false) );       // 0
```
Boolean
+ The conversion rule:
	- Values that are intuitively “empty”, like `0`, an empty string, `null`, `undefined`, and `NaN`, become `false`.
	- Other values become `true`.
- - `undefined` is `NaN` as a number, not `0`.
- `"0"` and space-only strings like `" "` are true as a boolean.



Others (DYK)
```js

alert( 0.1 + 0.2 == 0.3 ); // false
alert( 0.1 + 0.2 ); // 0.30000000000000004

// 0.0001100110011001100110011001100110011001100110011001101
alert(0.1.toString(2));

//0.001100110011001100110011001100110011001100110011001101
alert(0.2.toString(2));

// 0.0100110011001100110011001100110011001100110011001101
alert((0.1 + 0.2).toString(2))

```
+ 0.1 and 0.2 in binary are actually unending fractions 
+ 0.3 === 1/3 an endless fraction 0.33333(3)
Solution
+ method [toFixed(n)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed)
	```js
	let sum = 0.1 + 0.2;
	alert( +sum.toFixed(2) ); // 0.3
	```
+ temporary multiply by 10+ -> turn them into integers
	```js
	alert( (0.1 * 10 + 0.2 * 10) / 10 ); // 0.3
	alert( (0.28 * 100 + 0.14 * 100) / 100); // 0.4200000000000001
	```

For `null` returns `"object"` – this is an error in the language, it’s not actually an object.


casual speech