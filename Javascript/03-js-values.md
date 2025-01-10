# 🌌 Values

## ☄️ Core
+ __Expressions__ - questions that JavaScript can answer
	+ JS answers expressions in the only way it knows how — with _values_
	+ Expressions always result in a single value
+ __Values__ - a thing in JS universe
	+ they don't exist inside the code, but we can refer to them from our code
+ __Variables__ - We only said it’s the primitive values that can’t change. We didn’t say anything about variables!
## ☄️ Categories of Values
+ **Primitive** - store values directly
	+ _Immutable_
		+ values can't change
		+ property can't be set
		+ nothing in the code can affect them
+ **Complex/compound** - store references
	+ _objects_ and _functions_
	+ can manipulate them from my code

> [!IMPORTANT]
>  - _Variables_ are NOT _Values_. Variables point to Values
>  - Primitive values can't change, Variables can
>  - In function parameters, we are not passing Variables, but the current content of it
>  > What is the current value of the variable?” To answer our question, JS follows the variable’s “wire”, and gives us back the value at the end of this “wire

## ☄️ 8 Types of Primitive Values
### 🛰️ Boolean
+ Used for logical operations.
+ Binary nature - `true` `false`
	+ `true` - “yes, correct”
	+ `false` - "no, incorrect"
+ Boolean values as a result of comparisons
	```js
	let isGreater = 4 > 1;
	alert( isGreater ); //true (the comparison result is "yes")
	```
### 🛰️ String 
+ Used for text
+ The internal format for strings is always [UTF-16](https://en.wikipedia.org/wiki/UTF-16)
	+ not tied to the page encoding
	+ JS has no `character` type
	+ indexes are zero-based
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
	
	console.log(`string text line 1 \
	string text line 2`);
	// "string text line 1 string text line 2"
	```
+ Iterate over characters using `for..of`
	```js
	for (let char of "Hello") {
	  alert(char); // H,e,l,l,o (char becomes "H", then "e", then "l" etc)
	}
	```
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
	- JS are encoded using UTF-16 - each character has a corresponding numeric code
	- The characters are compared by their numeric code. The greater code means that the character is greater

### 🛰️ Number
+ used for math calculations
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
	+ represents the idea of an "invalid" number
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

### 🛰️ BigInt 
+ used for math on big numbers (uncommon & new)
+ for integer numbers of arbitrary length
+ represent whole numbers larger than `2^53 - 1`
+ created by appending `n` or using `BigInt()`
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
### 🛰️ Null 
+ used for _intentionally_ unknown/missing values – a standalone type
+ represents “nothing”, “empty” or “value unknown”
+ represents the INTENTIONAL absence of value
+ null is also a liar. Due to a bug in JavaScript, it pretends to be an object:
+ It is a primitive value, and it doesn’t behave in any way like an object. Unfortunately, `typeof(null)` is a historical accident that we’ll have to live with forever
### 🛰️ Undefined 
+ used for _unintentionally_ unassigned/missing values – a standalone type
+ represents lack of defined value - “value is not assigned”
+ reserved as a _default initial value_ for unassigned things
	+ will have the value `undefined`
+ implies a variable's existence but lack of assignment

### 🛰️ Symbols 
+ used to hide implementation details (uncommon).
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




## ☄️ 2 Types of Complex Values
### 🛰️ Objects 
+ ({} and others), used to group related data and code.

### 🛰️ Functions 
+ (x => x * 2 and others), used to refer to code.




## ☄️ Type Conversions
### 🚀 Primitive --> Primitive
+ _String Conversion_: Happens in `string concatenation (`+`)` or `String()`
	+ JS specification defines string conversion for all primitive types except symbols. Conversion always succeed ensuring compatibility and predictable behavior
	```js
	// Number to String
	console.log(String(123));  // "123"
	console.log("" + 123);     // "123"
	console.log(String(NaN));    // "NaN"
	console.log(String(Infinity)); // "Infinity"
	
	// Boolean to String
	console.log(String(true));  // "true"
	console.log("" + false);    // "false"
	
	// Null to String
	console.log(String(null));  // "null"
	console.log("" + null);     // "null"
	
	// Undefined to String
	console.log(String(undefined));  // "undefined"
	console.log("" + undefined);     // "undefined"
	
	// BigInt to String - "n" suffix removed
	console.log(String(123n));  // "123"
	console.log("" + 123n);     // "123"
	```
+ _Numeric Conversion_: Happens in mathematical operations or explicit use of `Number()`
	+ IMPLICIT CONVERSION (via arithmetic operations:` -, *, /, %`)
		```js
		// String to Number
		console.log("123" - 0);      // 123
		console.log("123" * 1);      // 123
		console.log("123" / 1);      // 123
		console.log("123" % 5);      // 3
		console.log("abc" * 1);      // NaN (invalid number)
		
		// Boolean to Number
		console.log(true * 2);       // 2
		console.log(false - 1);      // -1
		
		// Null to Number
		console.log(null + 5);       // 5 (null converts to 0)
		
		// Undefined to Number
		console.log(undefined + 5);  // NaN (undefined converts to NaN)
		
		// BigInt with Implicit Conversion 
		console.log(123n - 10);      // Throws TypeError
								     // (Cannot mix BigInt and other types)
		```
	+ EXPLICIT CONVERSION (Number() and Unary +)
		```js
		// String to Number
		console.log(Number("123"));  // 123 (valid number)
		console.log(+"123");         // 123
		
		console.log(Number("abc"));  // NaN (invalid number)
		console.log(+"");            // 0 (empty string becomes 0)
		console.log(+" ");           // 0 (whitespace are ignored)
		console.log(+"\n\t");        // 0
		
		console.log(+("   123   ")); // 123
		console.log(+("123z"));      // NaN (error reading a number at "z")
		
		// Boolean to Number (true -> 1 | false -> 0)
		console.log(Number(true));   // 1
		console.log(+false);         // 0
		
		// Null to Number (null -> 0)
		console.log(Number(null));   // 0
		console.log(+null);          // 0
		
		// Undefined to Number (undefined -> NaN)
		console.log(Number(undefined)); // NaN
		console.log(+undefined);        // NaN
		
		// BigInt to Number (explicit -> valid)
		console.log(Number(123n));  // 123 
		```
+ _Boolean Conversion_: Happens in conditions (if, while, etc.) or explicit use of Boolean()
	+ Values that are intuitively “empty”, like `0`, `""`, `null`, `undefined`, and `NaN`, become `false`.
	- Other values become `true`. `"0"` and space-only strings like `" "` are true
	- Conditionals (if, while, ?:) - values are coerced to Boolean when used in logical contexts 
	- Logical Operators (&&, ||, !) - logical operators trigger Boolean coercion (implicit conversion)

	```js
	console.log(Boolean(0));        // false (number zero is falsy)
	console.log(Boolean(-0));        // false (number zero is falsy)
	console.log(Boolean("0"));      // true (non-empty string is truthy)
	console.log(Boolean(""));       // false (empty string is falsy)
	console.log(Boolean(" "));      // true (string with space is truthy)
	console.log(Boolean(1));        // true
	console.log(Boolean(-1));       // true
	console.log(Boolean(null));     // false
	console.log(Boolean(undefined));// false
	console.log(Boolean(NaN));      // false
	console.log(Boolean([]));       // true (empty array is truthy)
	console.log(Boolean({}));       // true (empty object is truthy)
	console.log(Boolean(Symbol())); // true (symbols are truthy)
	```

	```js
	//IMPLICIT Conversion
	// In Conditionals
	if ("0") {} //true
	if (" ") {} //true
	if (0) {}   //false
	
	// With Logical Operators
	console.log(!0);        // true (negation of falsy value)
	console.log(!!" ");     // true (double negation of a string with space)
	console.log([] || 0);   // [] (truthy value returned by ||)
	console.log(null && 1); // null (falsy value short-circuits)
	```







