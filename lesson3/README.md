# Lesson #3 - C# Variables and Primitive Data Types
## Variables
### What is a variable?
After lesson #1, you probably already discovered variables and have a basic idea of what they are. I'll try to explain in a little more detail here. 

Let's set up an (imperfect) analogy to describe how variables work. You are moving, and you need to pack up your belongings. You go out and buy a bunch of storage bins, some small, some big, etc. Depending on the type of storage bin, you can fit certain items in it. For example, you obviously can't fit your 60" TV in your small storage bin. Now, in order to make your life easier when you are unpacking, you label all of your storage bins with something meaningful and descriptive. Perhaps something like "Living room decor", "Kitchen Utensils", "Bathroom Necessities", etc. 

You're probably catching the point of the analogy. A variable is a like a storage bin. A variable can be of a certain **type**, and based on it's type it can contain certain data. It's also very important to name your variables well, not things like `x` and `y`. It's important because you are not the only one going to be reading your code, and naming variables descriptively allows the reader to understand it's purpose (even if the reader is yourself 6 months from now). Just like unpacking the storage bins. You wouldn't label your storage bins `x`, `y`, and `z`, would you?

### Data Types
There are 2 kinds of data types in C# (and pretty much any language) "primitive" and "non-primitive". The storage bin analogy doesn't work very well here. A better way to think about primitives is as raw construction materials (lumber, metal, etc.) and non-primitives are the things you make out of them (tables, walls, etc.). A non-primitive is made of up primitive types, but by combining them in a certain way can create something very specific (such as a table).

See a table of primitive data types [here](https://www.tutorialspoint.com/csharp/csharp_data_types)


### Using variables and types
There are 2 ways to declare a variable in C#, one is like this:
```csharp
string myString = "my string";
```
The other is this:
```csharp
var myString = "my string";
```
These are equivalent statements. In the second one, the compiler can infer the type of the variable because of what is on the right side of the declaration (a `string`). In my experience, it's preferred to use the `var` syntax when possible. However, different teams have different preferences, make sure to adjust accordingly.

### Variable scope
When you declare a variable, a few things are happening when your program is running.
TODO: finish me!

## Homework
Update your existing HelloWorld project to do subtraction, multiplication, and division. 
Requirements:
- Input should be take exactly 3 arguments, the 1st is the type of arithmetic (add, multiply, etc.), the 2nd two are positive, whole numbers (you can assume that they will not be larger than an `int`).
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
