# Operators
__Operand__ (noun)
+ These are the values that operators work on/applied to
+ They can be numbers, strings, variables, or other expressions
__Operator__ (verb)
+ These are symbols that perform specific operations on operands
+ They tell JavaScript what to do with the operands
__Expression__ !! to move
+ Anything that produces a value is an expression in JS
+ An expression in JavaScript is a combination of values, variables, and operators that evaluates to a _single value_. It can be thought of as a "question" posed to JavaScript, where the answer is always a value. For example:
	+ The expression 1 + 2 evaluates to the primitive value 3.
	+ The expression "john " + "smith" evaluates to the primitive value "john smith".
	+ The expression true && false evaluates to the primitive value false.
+ Expressions do not modify the values they work with; instead, they combine them with operators to produce a new value. Every expression resolves to exactly one value, making it a fundamental building block of JavaScript logic.
Type Coercion
Type Casting

## Unary Operators
+ Operators that operate on a single operand
	> `-` unary minus
	> `+` unary plus
	> `++` increment
	> `--` decrement
	> `!` negation
	
> [!WARNING]
> unary plus operator doesn't change the sign of the number
> ```js
> let a = +(-50); // still -50
> let b = !(-50); // false
> ```

## Mathematical Operators

| Operator | Description |
| -------- | ----------- |
| +        |             |
| -        |             |
| *        |             |
| /        |             |
| %        |             |
| **       |             |
|          |             |
| +=       |             |
| -=       |             |
| *=       |             |
| /=       |             |
| %=       |             |

- the exponentiation operator is defined for non-integer numbers as well
	- For example, a square root is an exponentiation by ½
- __Increment/decrement can only be applied to variables__
	- Trying to use it on a value like 5++ will give an error
- __PostFix__ (a++) & __Prefix__ (++a)
	- prefix form returns the new value
	- postfix form returns the old value (prior to increment/decrement)

## Comparison Operators
	    

    
## Logical Operators
    
- If an operand is not a boolean, it’s converted to a boolean for the evaluation.
- The AND `&&` operator does the following:
	- Evaluates operands from left to right.
	- For each operand, converts it to a boolean. If the result is `false`, stops and returns the original value of that operand.
	- If all operands have been evaluated (i.e. all were truthy), returns the last operand.
- The OR `||` operator does the following:
	- considers all falsy
	1. Evaluates operands from left to right.
	2. For each operand, converts it to boolean. If the result is true, stops and returns the original value of that operand.
	3. If all operands have been evaluated (i.e. all were false), returns the last operand.
- `??` Nullish coalescing operator
	- The `??` operator returns its right-hand side operand when its left-hand side operand is null or undefined, and otherwise returns its left-hand side operand
	- consider only null and undefined

| Operator | Description                 |
| -------- | --------------------------- |
| &&       | and                         |
| !!       | or/pipe                     |
| !        | not/bang                    |
| ??       | Nullish Coalescing Operator |
    
## Ternary Operators
- simplify an if...else
- a ternary operator is any operator that takes three arguments.
	- It's usually called the ternary operator because it's the only operator that takes three arguments
- Conditional Operator : ?
- If-else version
	```jsx
	isNightTime ? console.log(''Yes) : console.log('No');
	```     
- else if version
	```jsx
	x = atheletesFinalPosition
	
	console.log(`You get the $ {
		x === 'first place' ? `gold`:
		x === 'second place' ? `silver`:
		x === 'third place' ? `bronze` :
			`tin`} medal!`)
	```
        
## Bitwise Operators
- treat arguments as 32-bit integer numbers and work on the level of their binary representation. These operators are not JavaScript-specific. They are supported in most programming languages.
- These operators are used very rarely, when we need to fiddle with numbers on the very lowest (bitwise) level
- Common in Cryptography
	|Operator|Description|
	|---|---|
	|&|AND|
	|||
	|^|XOR|
	|~|NOT|
	|<<|Left shift|
	|>>|Right shift|
	|>>>|Zero fill right|
	
## Comma
- The comma operator allows us to evaluate several expressions, dividing them with a comma `,`. Each of them is evaluated but only the result of the last one is returned.
	```jsx
	let a = (1 + 2, 3 + 4);
	
	alert( a ); // 7 (the result of 3 + 4)
	```
	
	```jsx
	// three operations in one line
	// actual application
	for (a = 1, b = 3, c = a * b; a < 10; a++) {
	 ...
	}
	```
- Comma has a very low precedence
- Such tricks are used in many JavaScript frameworks
        
- [**Operator precedence**](https://javascript.info/operators#operator-precedence)
    - If an expression has more than one operator, the execution order is defined by their precedence, or, in other words, the default priority order of operators.
    - There are many operators in JavaScript. Every operator has a corresponding precedence number. The one with the larger number executes first. If the precedence is the same, the execution order is from left to right.

        
- Sample
    
    ```jsx
    "" + 1 + 0 = "10" // (1)
    "" - 1 + 0 = -1 // (2)
    true + false = 1
    6 / "3" = 2
    "2" * "3" = 6
    4 + 5 + "px" = "9px"
    "$" + 4 + 5 = "$45"
    "4" - 2 = 2
    "4px" - 2 = NaN
    "  -9  " + 5 = "  -9  5" // (3)
    "  -9  " - 5 = -14 // (4)
    null + 1 = 1 // (5)
    undefined + 1 = NaN // (6)
    " \\t \\n" - 2 = -2 // (7)
    ```
    
    1. The addition with a string `"" + 1` converts `1` to a string: `"" + 1 = "1"`, and then we have `"1" + 0`, the same rule is applied.
    2. The subtraction `` (like most math operations) only works with numbers, it converts an empty string `""` to `0`.
    3. The addition with a string appends the number `5` to the string.
    4. The subtraction always converts to numbers, so it makes `" -9 "` a number `9` (ignoring spaces around it).
    5. `null` becomes `0` after the numeric conversion.
    6. `undefined` becomes `NaN` after the numeric conversion.
    7. Space characters are trimmed off string start and end when a string is converted to a number. Here the whole string consists of space characters, such as `\\t`, `\\n` and a “regular” space between them. So, similarly to an empty string, it becomes `0`.
    
    ```jsx
    z=0;
    z++;
    alert(z); ---> Outputs 1
    
    z=0;
    ++z;
    alert(z); --> Outputs 1
    
    But if we include now these expressions in another expression (alert for example) then we can see
    the difference:
    
    let z=0;
    alert(z++); ---> Outputs 0
    
    z=0;
    alert(++z); --> Outputs 1
    ```
    
- - Operator could be
	|+ operator could be for||
	|---|---|
	||unary positive|
	||binary operation|
	||string concatenation|
	|alert( +true ); // 1||
	|alert( +"" ); // 0|type conversion to number|
        
- typeof