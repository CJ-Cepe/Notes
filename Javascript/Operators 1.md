Terms
Operands (arguments) - is what operators are applied to.
Operator 
+ _unary_ if it has a single operand
	+ For example, the unary negation `-` reverses the sign of a number:
+ An operator is _binary_ if it has two operands
	+ two different operators that share the same symbol: the negation operator, a unary operator that reverses the sign, and the subtraction operator, a binary operator that subtracts one number from another.

+ Just like in maths, the exponentiation operator is defined for non-integer numbers as well
	+ For example, a square root is an exponentiation by ½:
	+ alert( 4 ** (1/2) ); // 2 (power of 1/2 is the same as a square root)
	+ alert( 8 ** (1/3) ); // 2 (power of 1/3 is the same as a cubic root)

Operator precedence
+ If an expression has more than one operator, the execution order is defined by their precedence, or, in other words, the default priority order of operators.

Assignment Operator
### [Assignment = returns a value](https://javascript.info/operators#assignment-returns-a-value)

The fact of `=` being an operator, not a “magical” language construct has an interesting implication.

All operators in JavaScript return a value. That’s obvious for `+` and `-`, but also true for `=`.

The call `x = value` writes the `value` into `x` _and then returns it_.

### [Chaining assignments](https://javascript.info/operators#chaining-assignments)

Chained assignments evaluate from right to left.

> Short “modify-and-assign” operators exist for all arithmetical and bitwise operators: `/=`, `-=`, etc.
> Such operators have the same precedence as a normal assignment, so they run after most other calculations:

[](https://javascript.info/operators# "run")

Increment/decrement
+ Increment/decrement can only be applied to variables. Trying to use it on a value like 5++ will give an error.
+ postfix 
+ prefix
+ To summarize:

If the result of increment/decrement is not used, there is no difference in which form to use:

let counter = 0;
counter++;
++counter;
alert( counter ); // 2, the lines above did the same
If we’d like to increase a value and immediately use the result of the operator, we need the prefix form:

let counter = 0;
alert( ++counter ); // 1
If we’d like to increment a value but use its previous value, we need the postfix form:

let counter = 0;
alert( counter++ ); // 0

The operators ++/-- can be used inside expressions as well. Their precedence is higher than most other arithmetical operations.


Bitwise operators
 treat arguments as 32-bit integer numbers and work on the level of their binary representation.
- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )
These operators are used very rarely, when we need to fiddle with numbers on the very lowest (bitwise) level.


Comma
The comma operator , is one of the rarest and most unusual operators.
The comma operator allows us to evaluate several expressions, dividing them with a comma ,. Each of them is evaluated but only the result of the last one is returned.

Comma has a very low precedence
Please note that the comma operator has very low precedence, lower than =, so parentheses are important in the example above.

Without them: a = 1 + 2, 3 + 4 evaluates + first, summing the numbers into a = 3, 7, then the assignment operator = assigns a = 3, and the rest is ignored. It’s like (a = 1 + 2), 3 + 4.

Why do we need an operator that throws away everything except the last expression?
Sometimes, people use it in more complex constructs to put several actions in one line.
// three operations in one line
for (a = 1, b = 3, c = a * b; a < 10; a++) {
 ...
}

Comparisons
Boolean is the result
All comparison operators return a boolean value:

true – means “yes”, “correct” or “the truth”.
false – means “no”, “wrong” or “not the truth”.

String comparison
To see whether a string is greater than another, JavaScript uses the so-called “dictionary” or “lexicographical” order.

In other words, strings are compared letter-by-letter.
Not a real dictionary, but Unicode order
The comparison algorithm given above is roughly equivalent to the one used in dictionaries or phone books, but it’s not exactly the same.

Comparison of different types
When comparing values of different types, JavaScript converts the values to numbers.

**A strict equality operator `===` checks the equality without type conversion.**

In other words, if `a` and `b` are of different types, then `a === b` immediately returns `false` without an attempt to convert them.

