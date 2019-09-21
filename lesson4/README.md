# Lesson #4 - Conditional Statements
## if statements
In code you often need to execute some behavior based on a *condition*: "if X, then do Y" or "if X, then do Y, otherwise do Z", etc. "if" statements are the more intuitive of conditional statements, it generally reads how you would expected it to behave. For example, let's look at lesson 3's homework as an example. You were required to take input like this:
```bash
$ dotnet run add 1 2
$ dotnet run multiply 4 5
```
You probably did something like this in order to change behavior:
```bash
if (args[0] == "add")
{
    Console.WriteLine(args[1] + args[2]);
}
else if (args[1] == "multiply")
{
    ...
}
...
```
This introduces some new concepts: *assignment* and *equality*. You may be wondering what the `==` means. When assigning variables, you've seen `=`, but what does the double equals mean? In C#, the single equals (`=`) is *assignment*, and the double equals (`==`) is testing for *equality*. In other words, if you want to *assign* a value to a variable, or change the value of a variable, use `=`. If you want to test if 2 variables are equal, use `==`. 
```csharp
if (1 = 2) {} // not valid
if (1 == 2) {} // valid
var a == 2; // not valid
var a = 2; // valid
```
However, you can do this:
```csharp
var a = 1 == 1;
```
That looks strange, but it's a valid statement. The value of `a` is `true`, but why? Let's decompose this statement. The right side, `1 == 1` is evaluated to `true`, because 1 in fact does equal 1. This statement is silly, because you know 1 always equals 1, so you might as well just type:
```csharp
var a = true;
```
Let's use a more realistic example, from the calculator program. You *could* do something like this:
```csharp
var isAddition = args[0] == "add";
var isMultiplication = args[0] == "multiply";

if (isAddition)
{
    // blah blah
}
else if (isMultiplication)
{
    // blah blah
}
```
If the input is `dotnet run add 1 2`, then the value of `isAddition` will be `true`, and the value of `isMultiplication` will be `false`. 

### Structure of if statements
Simple if:
```csharp
if (condition)
{
    // some code;
}
```
If-else:
```csharp
if (condition)
{
    // some code;
}
else
{
    // some other code
}
```
If and else ifs:
```csharp
if (condition)
{
    // some code;
}
else if (condition)
{
    // ...
}
else if (condition)
{
    // ...
}
else
{
    // ...
}
```
After looking at this, you probably noticed a couple things:
- All if statements begin with an `if`
- An `else` statement marks the end of the `if` statement

For example, this is not valid:
```csharp
if (condition)
{
    // ...
}
else 
{
    // ..
}
else if (condition)
{
    // ..
}
```
Why? The `else` tells the compiler that the `if` statement has ended. Since an if statement MUST begin with an `if`, the `else if` is invalid, and therefore this code won't compile. 

## Loops
### while loops
With if statements, we can change behavior based on a condition, but what if we want to execute something repeatedly? Here's a situation, let's say we want to write a program that prints out all between 1 and 100. Without loops, we'd have to do something like this:
```csharp
class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine(1);
        Console.WriteLine(2);
        Console.WriteLine(3);
        // ...
        Console.WriteLine(100);
    }
}
```
Not only is that tedious, but what if the requirements changed and it was 1 - 1,000,000,000? It'd be impossible to do in this lifetime. This is where loops come in handy. The first loop we'll look at is the `while` loop.

#### Structure of a while loop
```csharp
while (condition)
{
    // ...
}
```
Take the counting to 100 example, here is one way to solve that problem:
```csharp
var currentNumber = 1;

while (currentNumber <= 100)
{
    Console.WriteLine(currentNumber);
    currentNumber = currentNumber + 1; // This increases the value of currentNumber by 1
}
```
This will print all numbers from 1 - 100. The last statement is what makes the while loop work correctly, it increments the value of currentNumber by one. Another equivalent statement for incrementing a number by one is:
```csharp
currentNumber++;
```
If we didn't have this statement, we'd have what is called an *infinite loop*, and the code would continue executing until the program is forcefully stopped, so don't forget to increment!

We don't have to use numbers inside the `while` loop, the condition inside the parantheses is evaluated to a boolean (just like an if statement), so it can be any condition that evaluates to a boolean. Here's another way we could print all numbers between 1 and 100 using a `while` loop:
```csharp
var is100 = false;

while (!is100) // The "!" means "not". This statement reads "while the value of is100 is false, execute ..."
{
    var currentNumber = 1;
    Console.WriteLine(currentNumber);

    if (currentNumber == 100)
    {
        is100 = true;
    }

    currentNumber++;
}
```
This statement is a little more complicated. Until loops become second nature sometimes it's helpful to write down each iteration of the loop to understand how it's behaving. Let's take it one iteration at a time:

1st iteration:
- `is100` is equal to false 
- `currentNumber` = 1
- Console output will be `1`
- `currentNumber` is not equal to 100, so the code in the if statement is not executed
- `currentNumber` is incremented to 2

2nd iteration:
- `is100` is still equal to false 
- `currentNumber` = 2
- Console output will be `2`
- `currentNumber` is still not equal to 100, so the code in the if statement is not executed

You see the pattern, but sometimes it's helpful to write this out like this, because loops are not always intuitive to read at first.

### for loops
For loops are probably the most commonly used loops, but also can be the trickiest to grasp at first. Let's use a for loop to solve the counting to 100 problem:
```csharp
for (var i = 1; i <= 100; i++)
{
    Console.WriteLine(i);
}
```
Let's look at the structure.
#### Structure of a for loop
```csharp
for (initialization; condition; increment)
{
    // ...
}
```
In the first section, you are initializing the variable that you intend to increment and evaluate the condition against. In condition section, this is the condition that evaluates to a boolean (just like an if statement and while loop). The last section increments the variable you initialized in the first section.

At this point, it might be difficult to imagine situations where you would use a `while` loop versus a `for` loop. That's ok, as you continue it will become more and more clear when to use which one. As you are first starting off, a general rule of thumb to follow is: if you want to execute code based on a number (like counting to 100), `for` loops are probably the better choice. If you want to execute code until a condition is no longer true, then use `while` loops.

## Other loops
There are other types of loops, but `for` and `while` are by far the most common. Once we get into data structures such as lists, we will explore an even more common loop, the `foreach` loop. It will be difficult to understand that loop without a little more foundation knowledge first. Another loop is the `do while` loop. I personally don't remember ever using it in my professional career, or seeing it in any code other than tutorials explaining loops, so we won't bother going over it now. If you are interested, feel free to research it.

## Homework
Continue adding on to your existing hello world project. For the `add` command, allow the user to input between 2 and 20 numbers to add. For the `multiply` command, allow the user to input between 2 and 5 numbers together. For the subtract and divide commands, **they should behave exactly as they did for lesson 3**.
  
Things that may be helpful to search for:
- "How to find the length of an array"
- "How to take any number of arguments in C# console app"
- "How to loop through an array"

Examples:
```bash
$ dotnet run add 4 6 8 3 9 10 8 50 104 3 500 29 4 4 6 8 3 9 10 8
Sum is 786
$ dotnet run add 4
Error: The "add" command must take between 2 and 20 numbers
$ dotnet run add 5 6
Sum is 11
$ dotnet run add 4 6 8 3 9 10 8 50 104 3 500 29 4 4 6 8 3 9 10 8 10 10 10 10
Error: The "add" command must take between 2 and 20 numbers
$ dotnet run multiply 3 3 2 10 1
Product is 180
$ dotnet run multiply
Error: The "multiply" command must take between 2 and 5 numbers
$ dotnet run multiply 1 2 3 4 5 6
Error: The "multiply" command must take between 2 and 5 numbers
```


























