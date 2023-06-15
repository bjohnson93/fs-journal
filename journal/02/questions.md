# Intro to JavaScript
01. Which keywords are used to declare a variable in JavaScript?

    > Var, let, and const are all used to declare variables in JavaScript. However, var is no longer best practice- let can declare a variable but only within its own scope. Let is also hoisted to the top, so you must declare the variable before you can use it, and variables can be updated but not re-defined with let. Const is similar to let as it is also block scoped, but const means 'constant' so it cannot be updated or redeclared, but the VALUE itself can change.

    *Block is everything inside of curly braces

02. What is the definition of a function?

    > A function is (an object) block of code in JS that performs a particular task, it must be called (invoked) for it to perform those tasks. Functions always return a value.

03. What are the `SOLID` principles?

    > | ANSWER HERE |

04. Given this array: How could you remove the `pineapple`?

    ```js
    let fruit = ['apple', 'banana', 'pineapple', 'orange', 'strawberry']
    ```

    > let x = fruit.splice(2, 1)
        console.log(x) // output: ['pineapple']
        console.log(fruit) // output: (4) ['apple', 'banana', 'orange', 'strawberry']

05. Given these two objects: How could you add each to the others friends arrays?

    ```js
    let you = {
        name: "You",
        hair: true,
        friends: []
    }
    let them = {
        name: "Them",
        hair: false,
        friends: []
    }
    ```

    > | ANSWER HERE |

06. Give an example of a JavaScript `Conditional`:

    > if (x + y <= 7) {
        return true
    }
    //the portion in the () provided with the if statement is the conditional.

07. What is the main difference between `parameters` and `arguments`?

    > A parameter is the name used in the parens() of a function when defining that function. Arguments, are the values that get passed into the coordinating parameters. 
    
    ie: (Think ice cream parlor- parameter of arrayType, matching argument would be 'toppings' or 'iceCream'; parameter of name, value of 'Strawberry' or 'Sprinkles').

08. Instead of writing everything to the console, what is a better way to debug your code?

    > In the sources tab (of Dev Tools) there is a Javascript debugger! (I'm excited to have learned this). You can view your 'call stack', see breakpoints you've added or ones based off certain events. You get to see things in real time this way. It 'steps' through each line of code thus finding bugs quicker.

09. What is the difference between a `primitive` value and a `reference` value?

    > | ANSWER HERE |

10. Demonstrate a loop that prints the numbers between -100 and 100?

    > (i = -100; i <= 99; i++)
    // or in a function, see below
    function forLoopExample(){
    for (i = -100; i <= 99; i++){
        console.log(i)
    } console.log(i)
}
forLoopExample()
