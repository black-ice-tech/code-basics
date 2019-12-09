# Lesson 7 - Arrays and Lists
## Arrays
An array is a collection of objects of the same *type*. You have already seen arrays from the `Main` method in all of the programs:
```csharp
static void Main(string[] args)
{
    // ...
}
```
The `args` parameter is an array of `string`. You can also have arrays of any type, for example `int[]` or `double[]`, or even `Car[]` (from the `Car` class you created in a previous homework).

### Initializing
There are a few different ways to initialize an array in C#, you can initialize by indicating the size of the array:
```csharp
int[] myArray = new int[3]; // Initializes an array that can contain 3 elements.
```
Note, an array cannot change size, whatever size it is initialized with, that is the permanent size of the array. There are a handful of ways to initialize, I recommend doing a Google search for "initializing C# array" and you should see plenty of examples.

### Inserting a value
Now we have an array `myArray`, that can contain 3 elements. In order to add values of an array, you have to insert it at a particular index:
```csharp
myArray[0] = 1;
myArray[1] = 2;
myArray[2] = 3;
```

### Accessing values
You can access the item of an array at a particular *index*:
```csharp
Console.WriteLine(myInts[0]); // 1
Console.WriteLine(myInts[2]); // 6

Console.WriteLine(myDoubles[1]); // 3.4
Console.WriteLine(myDoubles[2]); // 9.8
```
You've probably already experienced what happens if you try to access an array's index that is beyond it's size:
```csharp
myInts[3]; // IndexOutOfRangeException
```

## Lists
A C# `List` is a type that abstracts some of the complexities of an array. For example, you don't have to specify a size, and the size of the list can change dynamically. It's more common to use Lists rather than arrays, although each have their pros and cons.

### Initializing
```csharp
var myIntList = new List<int>(); // list of ints
var myStringList = new List<string>(); // list of strings
var myCarList = new List<Car>(); // list of Cars
```
### Adding values
```csharp
myIntList.Add(3);
myStringList.Add("abcdef");

var car = new Car();
myCarList.Add(car);
```

## Conclusion
There are a lot of different types of lists, there are linked lists, array lists, and many others. We won't go over them, but I recommend doing some research on data structures and getting a good conceptual understanding of:
- Linked lists
- Stacks
- Queues
- Dictionaries

Gain an understanding of how they work, and which situations you would choose one over another.

## Homework
#### Problem 1
```csharp
See comments in program:
class Program
{
    public static void Main(string[] args)
    {
        // Initialize an array of integers with size 5
    }
}
```

#### Problem 2
```csharp
See comments in program:
class Program
{
    public static void Main(string[] args)
    {
        string[] names = new string[3];
        // Part A: Insert values into the "names" array so that there are 3 elements in the array

        // Part B: Write a statement that would cause an IndexOutOfBoundsException
    }
}
```

#### Problem 3
```csharp
See comments in program:
class Program
{
    public static void Main(string[] args)
    {
        // Initialize a List of integers
    }
}
```

#### Problem 4
See comments in program:
```csharp
class Program
{
    public static void Main(string[] args)
    {
        List<double> myDoubles = new List<double>();

        // Part A: Add 5 doubles to myDoubles

        // Part B: Iterate through myDoubles list and print to the console the sum of all of the numbers
    }
}
```

#### Problem 5
Create a class `Person` that has a constructor that takes a `List<string>` representing the person's nicknames. Then, add 2 methods:
1) First method `PrintNicknames` should take no parameters and have a return type `void`. It should print out all of the person's nicknames to the console.
2) Second method `AddNickname` should take a `string` as a parameter and a return type `void`. It should add the passed in string to the list of nicknames.

Here is an example of how the `Person` class would be used:
```csharp
class Program
{
    public static void Main(string[] args)
    {
        var nicknames = new List<string>();

        nicknames.Add("Bob");
        nicknames.Add("Bobby");
        nicknames.Add("Bob Dog");

        var person = new Person(nicknames);

        person.PrintNicknames();
        // Bob
        // Bobby
        // Bob Dog

        person.AddNickname("Big Bobby");

        person.PrintNicknames();
        // Bob
        // Bobby
        // Bob Dog
        // Big Bobby
    }
}
```

Submit the solution to each problem separately.