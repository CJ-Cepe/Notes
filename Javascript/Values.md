# DATA TYPES

+ 2 categories
	+ **Primitive** - store values directly
	+ **Complex/compound** - store references
+ 8 types
	+ boolean, number, bigInt, string, null, undefined, symbols, objects

## Primitive

### Boolean
+ Binary nature - `true` `false`
	+ true - “yes, correct”
	+ false - no, incorrect
+ Boolean values as a result of comparisons
	```js
	let isGreater = 4 > 1;
	alert( isGreater ); // true (the comparison result is "yes")
	```
### Number
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

### BigInt
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

### String
+ The internal format for strings is always [UTF-16](https://en.wikipedia.org/wiki/UTF-16)
	+ not tied to the page encoding
	+ JS has no character type
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
- Special Characters ??
	- all special characters start with a backslash character `\` _"escape character"_
	- `\n` newline || `\r\n` windows
	- `\t` tab
	- `\\` backslash
	- `\u...` unicode
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

### null
+ for unknown values – a standalone type
+ represents “nothing”, “empty” or “value unknown”
+ represents the INTENTIONAL absence of value
### undefined
+ for unassigned values – a standalone type
+ represents lack of defined value - “value is not assigned”
+ reserved as a default initial value for unassigned things
	+ will have the value `undefined`
+ implies a variable's existence but lack of assignment

### symbols
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
### objects

## Type Conversions










- **Object**
        
        - Facts
            
            - built-in data type for storing key-value pairs
                
            - Used to model real-world things.
                
            - Collection of data (properties) and actions (methods). Storing related data and functionality (unordered data), organized into _key-value pairs_
                
                ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f15ed4b6-82b5-4276-b310-75f76989344c/Untitled.png)
                
            - Objects are mutable
                
                - JavaScript objects are mutable, meaning their contents can be changed, even when they are declared as const. New properties can be added, and existing property values can be changed or deleted.
                - It is the reference to the object, bound to the variable, that cannot be changed.
            - Objects are _passed by reference_
                
            - We can add, remove and read files from it at any time.
                
        - Built-in Objects methods
            
            - Built-in objects contain methods that can be called by appending the object name with a period ., the method name, and a set of parentheses.
                
                ```jsx
                Math.random();
                // ☝️ Math is the built-in object
                ```
                
        - Declaration
            
            ```jsx
            let user = new Object(); // "object constructor" syntax
            let user = {};  // "object literal" syntax
            ```
            
        - **Object Literal**
            
            ```jsx
            let spaceship = {
              'Fuel Type': 'diesel',
              color: 'silver'
            };
            ```
            
            ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/28e18702-d114-47f3-8f52-f7d841c4ad90/Untitled.png)
            
        - **Members**
            
            - Properties (what an object has)
                
                - Properties are the values associated with a JavaScript object
                    
                - an association between a name (or _key_) and a value
                    
                - **Accessing Properties (2 ways)**
                    
                    - dot notation ( . )
                        
                        - If we try to access a property that does not exist on that object, `undefined`will be returned.
                        - The last property in the list may end with a comma.
                            - That is called a “trailing” or “hanging” comma. Makes it easier to add/remove/move around properties, because all lines become alike.
                        
                        ```jsx
                        let spaceship = {
                          homePlanet: 'Earth',
                          color: 'silver',
                        	"is fast": true, // multiword property name must be quoted
                        };
                        spaceship.homePlanet; // Returns 'Earth',
                        spaceship.color; // Returns 'silver',
                        ```
                        
                        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/22938433-7411-4433-89c9-3a3faa2ef746/Untitled.png)
                        
                    - bracket notation ( [ ] )
                        
                        - We **must** use bracket notation when accessing keys that have numbers, spaces, or special characters in them.x
                            
                            ```jsx
                            let spaceship = {
                              'Fuel Type': 'Turbo Fuel',
                              'Active Duty': true,
                              homePlanet: 'Earth',
                              numCrew: 5
                            };
                            spaceship['Active Duty'];   // Returns true
                            spaceship['Fuel Type'];   // Returns  'Turbo Fuel'
                            spaceship['numCrew'];   // Returns 5
                            spaceship['!!!!!!!!!!!!!!!'];   // Returns undefined
                            ```
                            
                            ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9bfcf6c1-d14b-4b91-8bcf-119d5db0bc99/Untitled.png)
                            
                            Square brackets also provide a way to obtain the property name as the result of any expression – as opposed to a literal string – like from a variable as follows: Here, the variable key may be calculated at run-time or depend on the user input. And then we use it to access the property. That gives us a great deal of flexibility. The dot notation cannot be used in a similar way
                            
                            ```jsx
                            let key = "likes birds";
                            
                            // same as user["likes birds"] = true;
                            user[key] = true;
                            ```
                            
                        - Computed properties
                            
                            - We can use square brackets in an object literal, when creating an object. That’s called computed properties.
                                
                                ```jsx
                                let fruit = prompt("Which fruit to buy?", "apple");
                                
                                let bag = {
                                  [fruit]: 5, // the name of the property is taken from the variable fruit
                                };
                                
                                alert( bag.apple ); // 5 if fruit="apple"
                                ```
                                
                                ```jsx
                                let fruit = prompt("Which fruit to buy?", "apple");
                                let bag = {};
                                
                                // take property name from the fruit variable
                                bag[fruit] = 5;
                                ```
                                
                        - We can use more complex expressions inside square brackets:
                            
                            - Square brackets are much more powerful than dot notation. They allow any property names and variables. But they are also more cumbersome to write.
                                
                            - So most of the time, when property names are known and simple, the dot is used. And if we need something more complex, then we switch to square brackets.
                                
                                ```jsx
                                let fruit = 'apple';
                                let bag = {
                                  [fruit + 'Computers']: 5 // bag.appleComputers = 5
                                };
                                ```
                                
                - **Property Assignment**
                    
                    - One of two things can happen with property assignment:
                        - If the property already exists on the object, whatever value it held before will be replaced with the newly assigned value.
                        - If there was no property with that name, a new property will be added to the object.
                    - const
                        - although we can’t reassign an object declared with `const`, we can still mutate it, meaning we can add new properties and change the properties that are there.
                            
                            ```jsx
                            const spaceship = {type: 'shuttle'};
                            spaceship = {type: 'alien'}; // TypeError: Assignment to constant variable.
                            spaceship.type = 'alien'; // Changes the value of the type property
                            spaceship.speed = 'Mach 5'; // Creates a new key of 'speed' with a value of 'Mach 5'
                            ```
                            
                - Property value shorthand
                    
                    ```jsx
                    function makeUser(name, age) {
                      return {
                        name: name,
                        age: age,
                        // ...other properties
                      };
                    }
                    
                    let user = makeUser("John", 30);
                    alert(user.name); // John
                    ```
                    
                    ```jsx
                    function makeUser(name, age) {
                      return {
                        name, // same as name: name
                        age,  // same as age: age
                        // ...
                      };
                    }
                    ```
                    
                    ```jsx
                    let user = {
                      name,  // same as name:name
                      age: 30
                    };
                    ```
                    
                - Property name limitation
                    
                    - As we already know, a variable cannot have a name equal to one of the language-reserved words like “for”, “let”, “return” etc. But for an object property, there’s no such restriction: In short, there are no limitations on property names. They can be any strings or symbols (a special type for identifiers, to be covered later).
                    - Other types are automatically converted to strings., For instance, a number 0 becomes a string "0" when used as a property key:
                    - **proto**
                        - There’s a minor gotcha with a special property named **proto**. We can’t set it to a non-object value: As we see from the code, the assignment to a primitive `5` is ignored.
                            
                            ```jsx
                            let obj = {};
                            obj.__proto__ = 5; // assign a number
                            alert(obj.__proto__); // [object Object] - the value is an object, didn't work as intended
                            ```
                            
                - Deleting property
                    
                    - You can delete a property from an object with the `delete`  operator.
                        
                        ```jsx
                        const spaceship = {
                          'Fuel Type': 'Turbo Fuel',
                          homePlanet: 'Earth',
                          mission: 'Explore the universe' 
                        };
                         
                        delete spaceship.mission;  // Removes the mission property
                        ```
                        
                - Property existence test, “in” operator
                    
                    - A notable feature of objects in JavaScript, compared to many other languages, is that it’s possible to access any property. There will be no error if the property doesn’t exist!
                        
                    - Reading a non-existing property just returns undefined. So we can easily test whether the property exists:
                        
                        ```jsx
                        let user = {};
                        
                        alert( user.noSuchProperty === undefined ); // true means "no such property"
                        ```
                        
                    - special operator "**in**”
                        
                        ```jsx
                        //Syntax
                        
                        "key" in object
                        ```
                        
                        ```jsx
                        let user = { name: "John", age: 30 };
                        
                        alert( "age" in user ); // true, user.age exists
                        alert( "blabla" in user ); // false, user.blabla doesn't exist
                        ```
                        
                        - Please note that on the left side of in there must be a property name. That’s usually a quoted string. If we omit quotes, that means a variable should contain the actual name to be tested. For instance:
                        
                        ```jsx
                        let user = { age: 30 };
                        
                        let key = "age";
                        alert( key in user ); // true, property "age" exists
                        ```
                        
                - Ordered like an object
                    
                    - Are objects ordered? In other words, if we loop over an object, do we get all properties in the same order they were added? Can we rely on this?
                        
                        - The short answer is: “ordered in a special fashion”:
                            - integer properties are sorted,
                            - if the keys are non-integer, then they are listed in the creation order.
                        
                        ```jsx
                        let codes = {
                          "49": "Germany",
                          "41": "Switzerland",
                          "44": "Great Britain",
                          // ..,
                          "1": "USA"
                        };
                        
                        for (let code in codes) {
                          alert(code); // 1, 41, 44, 49
                        }
                        ```
                        
                    - to fix integer properties sorted. we can “cheat” by making the codes non-integer. Adding a plus `"+"` sign before each code is enough.
                        
                        ```jsx
                        let codes = {
                          "+49": "Germany",
                          "+41": "Switzerland",
                          "+44": "Great Britain",
                          // ..,
                          "+1": "USA"
                        };
                        
                        for (let code in codes) {
                          alert( +code ); // 49, 41, 44, 1
                        }
                        ```
                        
            - Method (what an object does)
                
                - An action: That allow us to handle instances of that data type
                    
                - When the data stored on an object is a function we call that a method.
                    
                - Creating
                    
                    - We can include methods in our object literals by creating ordinary, colon-separated key-value pairs. The key serves as our method’s name, while the value is an anonymous function expression.
                        
                        ```jsx
                        const alienShip = {
                          invade: function () { 
                            console.log('Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.')
                          }
                        };
                        ```
                        
                    - With the new method syntax introduced in ES6 we can omit the colon and the `function`keyword.
                        
                        ```jsx
                        const alienShip = {
                          invade () { 
                            console.log('Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.')
                          }
                        };
                        ```
                        
                - Invoking
                    
                    - Object methods are invoked by appending the object’s name with the dot operator followed by the method name and parentheses:
                        
                        ```jsx
                        alienShip.invade();
                        ```
                        
                        ```jsx
                        let retreatMessage = 'We no longer wish to conquer your planet. It is full of dogs, which we do not care for.';
                        
                        // Write your code below
                        let alienShip = {
                          retreat: function (){
                            console.log(retreatMessage)
                          },
                          takeOff(){
                            console.log('Spim... Borp... Glix... Blastoff!')
                          }
                        }
                        
                        alienShip.retreat()
                        alienShip['takeOff']()
                        ```
                        
        - **Key (property name)**
            
            - like a variable name that points to a location in memory that holds a value.
            - Keys are strings, but when we have a key that does not have any special characters in it, JavaScript allows us to omit the quotation marks
        - **Value**
            
            - A key’s value can be of any data type in the language including functions or other objects.
        - **Nested Objects**
            
            - In application code, objects are often nested— an object might have another object as a property which in turn could have a property that’s an array of even more objects
                
            - We can chain operators to access nested properties. We’ll have to pay attention to which operator makes sense to use in each layer.
                
                ```jsx
                let spaceship = {
                  passengers: null,
                  telescope: {
                    yearBuilt: 2018,
                    model: "91031-XLT",
                    focalLength: 2032 
                  },
                  crew: {
                    captain: { 
                      name: 'Sandra', 
                      degree: 'Computer Engineering', 
                      encourageTeam() { console.log('We got this!') },
                     'favorite foods': ['cookies', 'cakes', 'candy', 'spinach'] }
                  },
                  engine: {
                    model: "Nimbus2000"
                  },
                  nanoelectronics: {
                    computer: {
                      terabytes: 100,
                      monitors: "HD"
                    },
                    'back-up': {
                      battery: "Lithium",
                      terabytes: 50
                    }
                  }
                }; 
                
                let capFave = spaceship.crew['captain']['favorite foods'][0]
                spaceship.passengers = [{name: 'jonathan'}, {}, {}]
                let firstPassenger = spaceship.passengers[0]
                console.log(spaceship.passengers[0].name)
                ```
                
        - **Passed by Reference**
            
            - when we pass a variable assigned to an object into a function as an argument, the computer interprets the parameter name as pointing to the space in memory holding that object. As a result, functions which change object properties actually mutate the object permanently (even when the object is assigned to a `const`variable).
                
                ```jsx
                const spaceship = {
                  homePlanet : 'Earth',
                  color : 'silver'
                };
                 
                let paintIt = obj => {
                  obj.color = 'glorious gold'
                };
                 
                paintIt(spaceship);
                 
                spaceship.color // Returns 'glorious gold'
                ```
                
            - However, reassignment of the `spaceship` variable wouldn’t work in the same way:
                
            - the reassignment didn’t stick (even though calling `console.log()`on the object produced the expected result).
                
                - When we passed `spaceship` into that function, `obj` became a reference to the memory location of the `spaceship` object, but _not_ to the `spaceship` variable. This is because the `obj` parameter of the `tryReassignment()` function is a variable in its own right. The body of `tryReassignment()` has no knowledge of the `spaceship` variable at all!
                - When we did the reassignment in the body of `tryReassignment()`, the `obj` variable came to refer to the memory location of the object `{'identified' : false, 'transport type' : 'flying'}`, while the `spaceship` variable was completely unchanged from its earlier value.
                
                ```jsx
                let spaceship = {
                  homePlanet : 'Earth',
                  color : 'red'
                };
                let tryReassignment = obj => {
                  obj = {
                    identified : false, 
                    'transport type' : 'flying'
                  }
                  console.log(obj) // Prints {'identified': false, 'transport type': 'flying'}
                 
                };
                tryReassignment(spaceship) // The attempt at reassignment does not work.
                spaceship // Still returns {homePlanet : 'Earth', color : 'red'};
                 
                spaceship = {
                  identified : false, 
                  'transport type': 'flying'
                }; // Regular reassignment still works.
                ```
                
        - **Looping Through Objects**
            
            - We learned how to iterate through arrays using their numerical indexing, but the key-value pairs in objects aren’t ordered! JavaScript has given us alternative solution for iterating through objects with the for...in syntax . for...in will execute a given block of code for each property in an object.
                
            - for…in
                
                - crewMember type is String not object reference
                
                ```jsx
                // for...in
                for (let crewMember in spaceship.crew) {
                  console.log(`${crewMember}: ${spaceship.crew[crewMember].name}`);
                }
                ```
                
        - Advance Objects /
            
            - Advanced objects are not a different type of object, they are mentioned as _advanced_, because of the advanced features we can implement to our objects
                
            - The object that a method belongs to is called the _calling object_
                
                - The `this` keyword refers to the calling object and can be used to access properties of the calling object.
                - Methods do not automatically have access to other internal properties of the calling object.
            - This
                
                - In accessing other properties in methods, we don’t automatically have access to other properties., that is why we need to use this keyword
                    
                - The `this`keyword references the _calling object_ which provides access to the calling object’s properties.
                    
                    - `this`keyword always refers to the properties of an object.
                        
                        ```jsx
                        const goat = {
                          dietType: 'herbivore',
                          makeSound() {
                            console.log('baaa');
                          },
                          diet() {
                            console.log(this.dietType);
                          }
                        };
                         
                        goat.diet(); 
                        // Output: herbivore
                        ```
                        
                - **Arrow Functions and this**
                    
                    - Arrow functions inherently _bind_, or tie, an already defined `this`value to the function itself that is NOT the calling object. the value of `this`is the _global object_, or an object that exists in the global scope
                        
                    - _avoid_ using arrow functions when using `this`in a method!
                        
                        ```jsx
                        const goat = {
                          dietType: 'herbivore',
                          makeSound() {
                            console.log('baaa');
                          },
                          diet: () => {
                            console.log(this.dietType);
                          }
                        };
                         
                        goat.diet(); // Prints undefined
                        ```
                        
                    
                    JavaScript arrow functions do not have their own this context, but use the this of the surrounding lexical context. Thus, they are generally a poor choice for writing object methods.
                    
                    ```jsx
                    const myObj = {
                        data: 'abc',
                        loggerA: () => { console.log(this.data); },
                        loggerB() { console.log(this.data); },
                    };
                    
                    myObj.loggerA();    // undefined
                    myObj.loggerB();    // 'abc'
                    ```
                    
                    `loggerA` is a property that uses arrow notation to define the function. Since `data` does not exist in the global context, accessing `this.data` returns `undefined`.
                    
                    `loggerB` uses method syntax. Since `this` refers to the enclosing object, the value of the `data` property is accessed as expected, returning `"abc"`.
                    
                - What is "this"?
                    
                    - The this keyword refers to the current object the code is being written inside
                    - This isn't hugely useful when you are writing out object literals by hand, but it will be essential when we start using constructors to create more than one object from a single object definition, and that's the subject of the next section.
                - **javascript function this**
                    
                    - Every JavaScript function or method has a this context.
                        - For a function defined inside of an object, this will refer to that object itself.
                        - For a function defined outside of an object, this will refer to the global object (window in a browser, global in Node.js).
            - Privacy
                
                - Accessing and updating properties is fundamental in working with objects. However, there are cases in which we don’t want other code simply accessing and updating an object’s properties.
                    
                - When discussing _privacy_ in objects, we define it as the idea that only certain properties should be mutable or able to change in value.
                    
                - Certain languages have privacy built-in for objects, but JavaScript does not have this feature.
                    
                    - Rather, JavaScript developers follow naming conventions that signal to other developers how to interact with a property.
                    - One common convention is to place an underscore `_`before the name of a property to mean that the property should not be altered.
                    
                    ```jsx
                    const bankAccount = {
                      _amount: 1000
                    }
                    ```
                    
                - Side-effect of type-coercion
                    
                    - it’s important to understand that you can cause unwanted side-effects when mutating objects and their properties.
                        - for instance, if a method used this keyword to used a property supposedly a number datatype and perform mathematical operations, but you mutated it to become a string. this would instead concatenates the mathematical operation to the string thus side-effect of type-coercion
                - Getters and Setters
                    
                    - Both methods are used to respect the intention of properties prepended, or began, with `_`
                        
                    - protection from unwanted manipulation
                        
                    - If there is a getter, then use it. IF there is a setter, then use it. Accessing the attribute directly will be considered trespass and a corruption of the code.
                        
                    - Looks like a normal property but a method (weird)
                        
                    - could be same name
                        
                    - Getters
                        
                        - methods that get and return the internal properties of an object.
                        - `get` keyword
                        - Advantages (instead of a normal function)
                            - Getter methods do not need to be called with a set of parentheses. Syntactically, it looks like we’re accessing a property.
                            - Getters can perform an action on the data when getting a property.
                            - Getters can return different values using conditionals.
                            - In a getter, we can access the properties of the calling object using `this`.
                            - The functionality of our code is easier for other developers to understand.
                                - Using the extra `get` keyword makes the functionality and privacy aspects of the code clearer to other developers;
                            - A getter won’t accept any arguments as parameters;
                            - A getter cannot have it’s value reassigned.
                        - keep in mind when using getter (and setter) methods is that properties cannot share the same name as the getter/setter function. If we do so, then calling the method will result in an **infinite call stack error**. One workaround is to add an underscore before the property name like we did in the example above.
                    - Setters
                        
                        - reassign values of existing properties within an object
                        - `set`keyword
                        - do not need to be called with a set of parentheses. Syntactically, it looks like we’re reassigning the value of a property
                        
                        ```jsx
                        const robot = {
                          _model: '1E78V2',
                          _energyLevel: 100,
                          _numOfSensors: 15,
                        	  get numOfSensors(){
                            if(typeof this._numOfSensors === 'number'){
                              return this._numOfSensors;
                            } else {
                              return 'Sensors are currently down.'
                            }
                          },
                          
                          set numOfSensors(num){
                            if(typeof num === 'number'&& num >= 0){
                              this._numOfSensors=num
                            } else {
                              console.log('Pass in a number that is greater than or equal to 0')
                            }
                          }
                        };
                        
                        robot.numOfSensors=100
                        console.log(robot.numOfSensors)
                        ```
                        
            - **Factory Functions**
                
                - A factory function is a function that returns an object and can be reused to make multiple object instances.
                - Factory functions can also have parameters allowing us to customize the object that gets returned.
                
                ```jsx
                const monsterFactory = (name, age, energySource, catchPhrase) => {
                  return { 
                    name: name,
                    age: age, 
                    energySource: energySource,
                    scare() {
                      console.log(catchPhrase);
                    } 
                  }
                };
                
                const ghost = monsterFactory('Ghouly', 251, 'ectoplasm', 'BOO!');
                ghost.scare(); // 'BOO!'
                ```
                
            - Object destructuring
                
                - _destructuring_
                    - ES6 introduced some new shortcuts for assigning properties to variables
                        
                    - _property value shorthand_
                        
                        - a destructuring technique
                            
                        - we don’t have to repeat ourselves for property assignments!
                            
                        - Not compatible with internet Explorer 11
                            
                        - Factory Function (version)
                            
                            ```jsx
                            const monsterFactory = (name, age) => {
                              return { 
                                **name: name,
                                age: age
                              }
                            };
                            ```
                            
                        - _property value shorthand (version)_
                            
                            ```jsx
                            const monsterFactory = (name, age) => {
                              return { 
                                name,
                                age 
                              }
                            };
                            ```
                            
                    - _destructured assignment_
                        
                        - In destructured assignment we create a variable with the name of an object’s key that is wrapped in curly braces `{ }`  and assign to it the object.
                            
                            ```jsx
                            const vampire = {
                              name: 'Dracula',
                              residence: 'Transylvania',
                              preferences: {
                                day: 'stay inside',
                                night: 'satisfy appetite'
                              }
                            };
                            
                            const residence = vampire.residence; 
                            console.log(residence); // Prints 'Transylvania'
                            
                            const { residence } = vampire; 
                            console.log(residence); // Prints 'Transylvania'
                            ```
                            
                            ```jsx
                            const obj = {
                              name: 'Mr. Obj',
                              pastTime: 'Volley Ball',
                              yearsTraining: [1992, 1993, 1994, 1995, 1996],
                            }
                            
                            const {name, pastTime, yearsTraining} = obj
                            
                            console.log(`${name} has trained in ${pastTime} during ${yearsTraining.join(', ')}.`)
                            
                            name = 'Mrs. Obj'; //if name is a constant variable this line will throw an error
                            
                            Mr. Obj has trained in Volley Ball during 1992, 1993, 1994, 1995, 1996.
                            TypeError: Assignment to constant variable.
                            ```
                            
            - Shorthand property name syntax for object creation
                
                - The shorthand property name syntax in JavaScript allows creating objects without explicitly specifying the property names (ie. explicitly declaring the value after the key). In this process, an object is created where the property names of that object match variables which already exist in that context. Shorthand property names populate an object with a key matching the identifier and a value matching the identifier’s value.
                
                ```jsx
                const activity = 'Surfing';
                const beach = { activity };
                console.log(beach); // { activity: 'Surfing' }
                ```
                
            - **Built-in Object Methods**
                
                - Object.keys()
                - Object.entries()
                - Object.assign()
        - Constructors /
            
            - Using object literals is fine when you only need to create one object, but if you have to create more than one, as in the previous section, they're seriously inadequate. We have to write out the same code for every object we create, and if we want to change some properties of the object - like adding a height property - then we have to remember to update every object.
                
            - We would like a way to define the "shape" of an object — the set of methods and the properties it can have — and then create as many objects as we like, just updating the values for the properties that are different.
                
                - 1st version (a function)
                    
                    ```jsx
                    function createPerson(name) {
                      const obj = {};
                      obj.name = name;
                      obj.introduceSelf = function () {
                        console.log(`Hi! I'm ${this.name}.`);
                      };
                      return obj;
                    }
                    
                    const salva = createPerson("Salva");
                    salva.name;
                    salva.introduceSelf();
                    // "Hi! I'm Salva."
                    
                    const frankie = createPerson("Frankie");
                    frankie.name;
                    frankie.introduceSelf();
                    // "Hi! I'm Frankie."
                    ```
                    
                    - This works fine but is a bit long-winded: we have to create an empty object, initialize it, and return it.
                - constructor
                    
                    ```jsx
                    function Person(name) {
                      this.name = name;
                      this.introduceSelf = function () {
                        console.log(`Hi! I'm ${this.name}.`);
                      };
                    }
                    
                    //To call Person() as a constructor, we use new:
                    const salva = new Person("Salva");
                    salva.name;
                    salva.introduceSelf();
                    // "Hi! I'm Salva."
                    
                    const frankie = new Person("Frankie");
                    frankie.name;
                    frankie.introduceSelf();
                    // "Hi! I'm Frankie."
                    ```
                    
            - A constructor is just a function called using the [`new`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new) keyword.
                
                - When you call a constructor, it will:
                    - create a new object
                    - bind `this` to the new object, so you can refer to `this` in your constructor code
                    - run the code in the constructor
                    - return the new object.
            - Constructors, by convention, start with a capital letter and are named for the type of object they create
                
                ```jsx
                function Person(name) {
                  this.name = name;
                  this.introduceSelf = function () {
                    console.log(`Hi! I'm ${this.name}.`);
                  };
                }
                
                //To call Person() as a constructor, we use new:
                const salva = new Person("Salva");
                salva.name;
                salva.introduceSelf();
                // "Hi! I'm Salva."
                
                const frankie = new Person("Frankie");
                frankie.name;
                frankie.introduceSelf();
                // "Hi! I'm Frankie."
                ```
                
        
        ---
        
        - Ways to create Objects
            
            - making an Instance
                - bind obj to itself then calls constructor
                - Each object is unique but share the same type
            - Depends on needs (instance or single object)
                - Single Object
                    
                    - **Object Literal Syntax**
                        
                        - This is a simple and straightforward way to create objects, especially when you’re dealing with a single object or objects that don’t have complex behaviors. It’s great for creating simple data structures.
                            
                            ```jsx
                            let obj = {
                                property1: 'value1',
                                property2: 'value2'
                            };
                            ```
                            
                    - **Object Constructor**
                        
                        - not preferred. can be overwritten
                            
                        - become properties of Object
                            
                        - The Object constructor creates an object wrapper for a given value. If the value is **`null`** or **`undefined`**, it will create and return an empty object. Otherwise, it will return an object of a type that corresponds to the given value. If the value is an object already, it’ll return the value.
                            
                            ```jsx
                            let myCar = new Object();
                            
                            myCar.make = 'Toyota';
                            myCar.model = 'Corolla';
                            ```
                            
                    - **Singleton Pattern**
                        
                        ```jsx
                        let obj = new function() {
                            this.property1 = 'value1';
                            this.property2 = 'value2';
                        }
                        ```
                        
                - Multiple Instance
                    
                    - **Constructor Functions**
                        
                        - If you need to create multiple objects with the same structure and behavior, constructor functions can be a good choice. They allow you to define a “blueprint” for your objects.
                            
                            ```jsx
                            function Car(make, model) {
                                this.make = make;
                                this.model = model;
                            }
                            
                            let myCar = new Car('Toyota', 'Corolla');
                            ```
                            
                            ```jsx
                            function Person(name, age) {
                                this.name = name;
                                this.age = age;
                            
                                this.greet = function() {
                                    return "Hello, my name is " + this.name;
                                };
                            }
                            ```
                            
                            ```jsx
                            function Person(name, age) {
                                this.name = name;
                                this.age = age;
                            }
                            
                            Person.prototype.greet = function() {
                                return "Hello, my name is " + this.name;
                            };
                            ```
                            
                            - more memory efficient
                                
                                When you add methods directly to the constructor, a new copy of the method is created for each instance of the object. This means that if you create a thousand objects, you’ll end up with a thousand copies of the method in memory, one for each object. This can consume a significant amount of memory if you’re creating many objects.
                                
                                On the other hand, when you add methods to the prototype, only one copy of the method is created, regardless of how many objects you create. All instances of the object share the same method, which is stored in the prototype. This is much more memory-efficient, especially when creating many objects.
                                
                                Here’s a simple analogy: think of the constructor as a recipe for baking a cake. If you add the method to the constructor, it’s like writing “decorate with icing” on every individual recipe card. If you have a thousand recipe cards, you’ll end up writing “decorate with icing” a thousand times. But if you add the method to the prototype, it’s like writing “decorate with icing” on a master recipe card that all the other cards refer to. You only need to write it once, and all the recipe cards can use it.
                                
                                So, using the prototype to add methods is more memory-efficient because it avoids creating multiple copies of the same method for each object.
                                
                            - applies to data properties
                                
                                Yes, this concept applies to data properties as well. When you add data properties directly to the constructor, a new copy of the property is created for each instance of the object. This means that if you create a thousand objects, you’ll end up with a thousand copies of the property in memory, one for each object.
                                
                                However, when you add data properties to the prototype, only one copy of the property is created, regardless of how many objects you create. All instances of the object share the same property, which is stored in the prototype.
                                
                                But there’s a crucial difference between methods and data properties. Methods usually don’t change - they perform the same operation regardless of the object they’re called on. But data properties often hold different values for different objects. If you add a data property to the prototype and then change it on one object, it will change for all objects, because they all share the same property. This is usually not what you want.
                                
                                So while adding data properties to the prototype can be more memory-efficient, it can lead to unexpected behavior if you’re not careful. In general, it’s best to add data properties directly to the constructor, and add methods to the prototype.
                                
                    - **Factory Functions**
                        
                        - If you need more control over object creation, or if you want to encapsulate the creation logic in one place, factory functions can be useful. They return a new object each time they’re called.
                            
                            ```jsx
                            function createCar(make, model) {
                                return {
                                    make: make,
                                    model: model
                                };
                            }
                            
                            let myCar = createCar('Toyota', 'Corolla');
                            ```
                            
                    - **Class Syntax (ES6)**
                        
                        - If you’re working in a large codebase or with a team that prefers object-oriented programming, the class syntax introduced in ES6 can be a good choice. It provides a clear and concise way to create objects and manage inheritance.
                            
                            ```jsx
                            class Car {
                                constructor(make, model) {
                                    this.make = make;
                                    this.model = model;
                                }
                            }
                            
                            let myCar = new Car('Toyota', 'Corolla');
                            ```
                            
                    - **Object.create()**
                        
                        - creates a new object, using an existing object as the prototype of the newly created object.
                            
                        - can be useful when you want to create an object that inherits from another object without having to define a constructor function or class.
                            
                            ```jsx
                            let carPrototype = {
                                start: function() {
                                    return 'Engine started';
                                }
                            };
                            
                            let myCar = Object.create(carPrototype);
                            console.log(myCar.start()); // 'Engine started'
                            ```
                            
        - Classes
            
            - JavaScript does not have classes in the same sense as other Object Oriented languages like Java or Ruby
            - ES6, however, did introduce a syntax for object creation that uses the class keyword
                - It is basically a new syntax that does the _exact_ same thing as the object constructors and prototypes we learned about in the constructor lesson.
        - **ES6 Modules**
            
            - Node Package Manager (NPM)
                - a command-line tool
                    - that gives you access to a gigantic repository of plugins, libraries and tools



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