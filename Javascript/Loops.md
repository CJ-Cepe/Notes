### Loops

- repeats a set of instructions until a specified condition, called a **stopping condition** is reached.
    
    - Iterate —> to repeat
- I**nitialization**
    
    - starts the loop and can also be used to declare the iterator variable.
    - Inline variable declaration
        - Here, the “counter” variable i is declared right in the loop. This is called an “inline” variable declaration. Such variables are visible only inside the loop.
- **Stopping condition**
    
    - is the condition that the iterator variable is evaluated against— _if the condition evaluates to true_ the code block will run, and if it evaluates to false the code will stop.
- I**teration statement**
    
    - used to update the iterator variable on each loop.
        - to the point that the condition becomes false is sometimes called the **stop condition**.
    - this is always evaluated (or run) each time the loop has gone through a full iteration
- **Looping in Reverse**
    
    - Iterator = highest desired value
    - Condition = less than the desired amount
    - Iterator = --
- **For Loop**
    
- **For … in (objects)**
    
    ```jsx
    for (key in object) {
      // executes the body for each key among object properties
    }
    ```
    
    ```jsx
    let user = {
      name: "John",
      age: 30,
      isAdmin: true
    };
    
    for (let key in user) {
      // keys
      alert( key );  // name, age, isAdmin
      // values for the keys
      alert( user[key] ); // John, 30, true
    }
    ```
    
- **While Loop**
    
    - ideal when we don’t know in advance how many times the loop should run
- **Do While**
    
    - you want a piece of code to run at least once and then loop based on a specific condition after its initial run.
    - Note that the while and do...while loop are different! Unlike the while loop, do...while will run at least once whether or not the condition evaluates to true.
- Nested Loop
    
- Break & Continue
    
    - _Please note that syntax constructs that are not expressions cannot be used with the ternary operator ?. In particular, directives such as break/continue aren’t allowed there._
        
    - A _**label**_ is an identifier with a colon before a loop:
        
        ```jsx
        labelName: for (...) {
          ...
        }
        ```
        
        The break <labelName> statement in the loop below breaks out to the label:
        
        ```jsx
        outer: for (let i = 0; i < 3; i++) {
        
          for (let j = 0; j < 3; j++) {
        
            let input = prompt(`Value at coords (${i},${j})`, '');
        
            // if an empty string or canceled, then break out of both loops
            if (!input) break outer; // (*)
        
            // do something with the value...
          }
        }
        
        alert('Done!');
        ```
        
        Labels do not allow to “jump” anywhere
        
- Break
    
    - “break” out of the loop from within the loop’s block.
    - the break statement is used to immediately exit a loop when a certain condition is met. When working with nested loops, the break statement can be used to break out of both the inner and outer loops.
    - If a break statement is encountered in the inner loop, only the inner loop will be exited and the outer loop will continue to iterate. However, if the break statement is included in the outer loop, both the outer and inner loops will be exited and the program will continue executing after the loop.
    - Break is a loop control statement along with continue and pass.
    - You can use break to exit for loops and while loops.
    - Break only exits the innermost loop in a nested loop.
    - You can’t use break to exit an if statement unless the if statement is inside of a loop.
    - You can also use the break statement to terminate a switch statement or a labeled statement.
- Continue
    
    - used when you want to restart a new iteration of a loop.
    - This statement can be used in a while loop, for loop or for-in loop.
    - When JavaScript executes the continue statement, any remaining code left in the current iteration of the loop body is skipped. The code will resume execution at the start of the loop (as a new iteration of the loop).