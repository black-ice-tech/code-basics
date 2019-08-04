# Lesson #3 - Binary, C# Variables and Data Types
## Binary crash course
Before we can talk about variables, you need to have basic understanding of binary. Binary is the language of computers, everything is stored as 1s and 0s, ultimately. Programming languages were invented to translate from something more human readable into 1s and 0s. Some do it through a process called *compilation*, other languages are *interpreted*. Compiled languages (like C#) translate your code into binary before running the program. Interpreted languages do it during executiong of your program (like Python).

A couple of terms:
- **Bit**: the smallest unit in computing, a bit can either be a 1 or a 0. Think of it like a light switch, it's either "on" (1), or "off" (0).
- **Byte**: 8 bits, in programming, we don't typically deal with bits, we deal with bytes.

Let's say that me and you needed a code to communicate because we've been kidnapped and now we're tied up with our mouths gagged. Pretend we already created this code before we were kidnapped (very realistic, I know) where we communicate using only single stomps and double stomps. A single stomp means "yes" and a double stomp means "no". This only gets you so far, and since we are both tied up, it makes no sense to just say "yes" and "no" back and forth to each other. But let's say we add a 3rd option, "Are you injured?", and it's a single stomp, followed by a double stomp. And a 4th option, "Can you breath?", and it's a double stomp, followed by a single stomp.

The first 2 options, "yes" and "no", can be captured in one action that has two options, a single or double stomp. You can't represent anymore data without adding another stomp. To add the 3rd and 4th options, you needed to add a 2nd stomp. This 2nd stomp allows you to represent up to 4 options. So far you have "yes", "no", "Are you injured?", "Can you breath?". If you wanted to add anything else to your secret code, you'd need to add a 3rd stomp. With a 3rd stomp, you can now represent 8 options (2^3). With a 4th, 16 options, etc.

Bits are the same way, the more bits you have, the more data you can represent:

Binary | Decimal
--- | ---
0 | 0
1 | 1
10 | 2
11 | 3
100 | 4
101 | 5
110 | 6
111 | 7
1000 | 8

TLDR:
- Binary is the language of computers
- Programming languages take code and translate into binary
- The more bits you have, the more data you can represent

## What is a variable?
After lesson #1, you probably already discovered variables and have a basic idea of what they are. I'll try to explain in a little more detail here. 

Let's set up an (imperfect) analogy to describe how variables work. You are moving, and you need to pack up your belongings. You go out and buy a bunch of storage bins, some small, some big, etc. Depending on the type of storage bin, you can fit certain items in it. For example, you obviously can't fit your 60" TV in your small storage bin. Now, in order to make your life easier when you are unpacking, you label all of your storage bins with something meaningful and descriptive. Perhaps something like "Living room decor", "Kitchen Utensils", "Bathroom Necessities", etc. 

You're probably catching the point of the analogy. A variable is a like a storage bin. A variable can be of a certain **type**, and based on it's type it can contain certain data. It's also very important to name your variables well, not things like `x` and `y`. It's important because you are not the only one going to be reading your code, and naming variables descriptively allows the reader to understand it's purpose (even if the reader is yourself 6 months from now). Just like unpacking the storage bins. You wouldn't label your storage bins `x`, `y`, and `z`, would you?

## Data Types
There are 2 kinds of data types in C# (and pretty much any language) "value" and "reference". Attempting to continue the storage bin analogy (although it's beginning to fall apart), a "value" type storage bin contains the actual value. For example, you open up storage bin labeled "toothbrush" and you'd find the toothbrush in the bin. If you stored your toothbrush using a reference type, instead of opening it and seeing a toothbrush, you see another label that tells you where the storage bin is that contains the toothbrush.

Ok, no more storage bin analogy, as I'm starting to cringe the more I use it. Let's take a step back. To understand value types and references types better, we need to understand a little bit more about how your computer is running your program. There are 2 ways that the runtime stores information about your program: 1) memory 2) disk. Memory is cleared whenever your computer is turned off. It does not *persist*. Disk, on the other hand, is *persisted* and lives on even when your computer restarts. When your program is running, the CLR (C# Language Runtime), which is the thing executing your program, puts the data in memory. 

Time for another analogy, your brain. Yes, memory in computers is very similar to memory in the human brain. As you go about your life, you have all kinds of information being stored in your brain. The route you take to work, the breakfast you buy from McDonald's every morning, your favorite flavor of ice cream, etc. If you die, all of that information is gone. It's not stored anywhere that *persists*, it's only stored in your brain. And when you are dead, so is all of the information stored in your brain. What if you had some information that you wanted to store in case you died? You would write it down, of course. Once it's written down, your brain doesn't have to hold on to it anymore. If you forget, you can always go read it wherever you placed it. You can give that piece of paper to someone else. You can make copies of it so everyone can read it. You get the point. Writing down your information in your brain is like writing data to the disk on your computer. 

Back to value and reference types, here's a diagram to help you visualize what's happening in memory. We are oversimplifying here, but you'll get the concept. We start with some slots in memory, and they are all empty:
![Step 1](step1.png?raw=true)
Then you declare a value type `myAge` (`int` is a value type. For a list of value types in C#, see [here](https://www.tutorialspoint.com/csharp/csharp_data_types)):
```csharp
int myAge = 27; // an int is a value type of 4 bytes
```
![Step 2](step2.png?raw=true)
Then you declare a value type `mySoulAge`:
```csharp
int mySoulAge = 96; // also 4 bytes
```
![Step 3](step3.png?raw=true)
Then you declare a reference type `myName` (the size of a reference varies on different operating systems, but is typically 64 bits, which is 8 bytes):
```csharp
string myName = "My name is Bob"; // a string is a reference type (a collection char types, which are 2 bytes), because it can be any size. This particular string is 28 bytes (14 chars).
```
![Step 4](step4.png?raw=true)

Like I said, this is an oversimplification, because value and reference types are stored in different locations in memory. Value type is stored in the *stack*, and reference types in the *heap*. We won't go into more detail on this, but feel free to research more on your own if interested.

Don't worry, I didn't forget about disk. It's just not critical to use at this point. We will get to it later in the course. With simple programs, we have no need to persist data so disk does not come into play.

## Declaring variables
There are 2 ways to declare a variable in C#, one is like this (explicitly):
```csharp
string myString = "my string";
int myInt = 3;
```
The other is this:
```csharp
var myString = "my string";
var myInt = 3;
```
The top section and bottom section are equivalent. In the second one, the compiler can *infer* the type of the variable because of what is on the right side of the declaration (called *type inference*). In my experience, it's preferred to use the `var` syntax when possible. However, different teams have different preferences, make sure to adjust accordingly.

## Variable scope
When you declare a variable, it only exists within *scope* that it's defined in. For example, if the variable is defined within a conditional statement (such as an "if" statement or loop), it is only available within that context. A variable declared inside of a method, only exists within that method. We could spend a lot of time on variable scope and what is going on under the hood, but it's not *necessary* to understand fully at this point. If you are interested, ask your instructor for more details.

For clarity purposes, I'll be using explicit variable declaration.

```csharp
public void MyMethod() // More on methods later
{
    int myNum = 5;

    if (myNum < 5)
    {
        string myString = "abc";

        Console.WriteLine(myString); // In scope and compiles
        Console.WriteLine(myNum); // In scope and compiles
        Console.WriteLine(isNumGreaterThanFive); // Not in scope and won't compile
    }
    else
    {
        bool isNumGreaterThanFive = false;

        Console.WriteLine(myString); // Not in scope and won't compile
        Console.WriteLine(myNum); // In scope and compiles
        Console.WriteLine(isNumGreaterThanFive); // In scope and compiles
    }

    Console.WriteLine(myString); // Not in scope and won't compile
    Console.WriteLine(myNum); // In scope and compiles
    Console.WriteLine(isNumGreaterThanFive); // Not in scope and won't compile
}
```
Take a moment to look at this, you'll notice it's actually a pretty intuitive thing to determine a variable's scope. It might be a little tricky at first, but before long it will be second nature.

## Homework
Update your existing HelloWorld project to do subtraction, multiplication, and division. 
Requirements:
- Input should take exactly 3 arguments, the 1st is the type of arithmetic (add, multiply, etc.), the 2nd two are positive, whole numbers (you can assume that they will not be larger than an `int`).
- If not exactly 3 arguments are given, display the error (below)
- If the arithmetic command given is invalid, display the error
- If input is invalid, print the string `Usage: <add|subtract|multiply|divide> <num1> <num2>` to the console

Example input and output:
```bash
$ dotnet run add 1 3
Sum is 4
$ dotnet run substract 8 6
Difference is 2
$ dotnet run multiply 3 3
Product is 9
$ dotnet run divide 25 5
Quotient is 5
```
Example error cases:
```bash
$ dotnet run ade 1 3
Usage: <add|subtract|multiply|divide> <num1> <num2>
$ dotnet run
Usage: <add|subtract|multiply|divide> <num1> <num2>
$ dotnet run subtract 10
Usage: <add|subtract|multiply|divide> <num1> <num2>
```

Before coding, make sure you switch to branch `master` by running
`git checkout master`. Then do `git pull` to ensure you have all the changes that were merged from less #2. Create a new branch called `git checkout -b feature/L3-multiply-and-divide` and start coding!

When finished, follow the same steps from lesson #2 to submit a PR (`add`, `commit`, `push`, and create PR through GitHub web page) and add your instructor as a reviewer.
