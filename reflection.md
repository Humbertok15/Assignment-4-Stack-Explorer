# Stack Explorer Reflection

## Stack Mechanics

When I ran the recursive factorial function, I could clearly see the stack growing and shrinking. With `factorial(5)`, the program first printed `Entering factorial(5)`, then `factorial(4)`, `factorial(3)`, `factorial(2)`, and `factorial(1)`. Each new call was added to the stack while the previous function waited for the result. When the base case was reached, the functions returned in reverse order. The output showed `factorial(1)` returning first, followed by `factorial(2)`, `factorial(3)`, and so on. This showed how stack frames are added during calls and removed when functions return.

Fibonacci showed a similar pattern, but it made many more recursive calls because each call can create two additional calls. The depth tracking showed how far down the stack the recursion went. When I tested the infinite recursion function, it continued printing calls without stopping until the program eventually crashed from running out of stack space. Depending on the system, this can appear as a stack overflow or segmentation fault. Each function call creates a stack frame that can contain parameters, local variables, and information such as the return address. This information allows the program to continue from the correct location after the function returns.

## Recursion Costs

Factorial and Fibonacci have different recursion costs. Factorial creates one recursive call at a time, so with `factorial(5)` the deepest part of the stack is only the chain from 5 to 1. Fibonacci creates two recursive calls for most values, which causes a much larger number of total function calls. For example, `fibonacci(10)` makes many more calls than `factorial(10)`. The total work of Fibonacci grows very quickly, while the maximum depth tracked by my program grows roughly with the input value.

Python limits recursion depth to prevent a program from creating too many recursive calls and exhausting the call stack. My infinite recursion test demonstrated why this is important. Without a stopping limit or base case, recursive calls continue using more stack space until the program crashes.

## Function Pointers and Callbacks

Function pointers allow a function to be passed as an argument to another function. In my array processor, I used the same `process_array` function with `double_value`, `square_value`, and `negate_value`. This allowed the processor to perform different operations without rewriting the array-processing code. The event system worked in a similar way. I registered multiple callback functions and then triggered them, causing each registered callback to execute with the event value.

A real-world example is a GUI program where clicking a button triggers a callback function. Callbacks are also useful in operating systems, networking, and event-driven programs. Systems programmers use function pointers because they make programs more flexible and reusable. Even though they can be less readable than direct function calls, they allow the program to choose different behavior dynamically without changing the main processing code.
