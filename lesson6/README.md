# Lesson 6 - Classes and Objects
## Conceptual Overview
Classes are a language construct that allows you to create custom types. You've already encountered C# primitive *types*, but with classes you can create your own types.

The great thing about object-oriented programming is that it maps really well to real life and how we think about the world. For example, in the real world, everything is of a certain class, and is a specific *instance* of that class. For example, a chair is a classification of a thing, and a chair has certain *fields*. A chair has a certain number of legs, it has a color, type of materials, etc. The *specific* chair you are sitting on, however, is a manifestation (or *instance*) of the classification "chair".

It's the exact same in code, you create classifications of things (a "class") and then you can *instantiate* that class to create an *object*, or *instance* of that class. 

## Structure of a Class
Here is a class with nothing in it:
```csharp
public class Dog
{
}
```

Now if I wanted to create an *instance* of this class, I would do this:
```csharp
Dog myDog = new Dog();
```

This is pretty useless at the moment, because there is nothing in the class `Dog`, but there are a few concepts to introduce here. The first is the **new** keyword. It does exactly what it sounds like, it creates a new instance of the type `Dog` in memory. Remember value and reference types? Instances of classes are reference types, which means the variable `myDog` actually contains a reference to where the value lives in memory. 

What about the parantheses on the right? Doesn't that look kind of like a method call? It's a special method called a *constructor*. A constructor is respnsible for instantiating the object. In our example above, it's not actually doing any work, but let's create our own constructor for `Dog`:

```csharp
public class Dog
{
    public Dog()
    {
        Console.WriteLine("Creating an instance of dog!");
    }
}
```

Now when you instantiate a `Dog`, you'll see the message `Creating an instance of dog!` printed to the console.

Let's make our dog class a little more useful. Some fields of a dog could be "name" and the "breed". So let's add those to our constructor:
```csharp
public class Dog
{
    public string Name;
    public string Breed;

    public Dog(string name, string breed)
    {
        Name = name;
        Breed = breed;
    }
}
```
There are a few things happening here:
1) We added *parameters* to our constructor. Remember, a constructor is just a special method that returns the type itself.
2) We added *fields* to our class at the top. This allows us to access the values passes in to the constructor.

Now that we have our new constructor, let's create a new instance:
```csharp
Dog myDog = new Dog("Spot", "Husky");
Console.WriteLine($"Name is: {myDog.Name}");  // "Name is: Spot"
Console.WriteLine($"Breed is: {myDog.Breed}"); // "Breed is: Husky"
```

## Adding behavior to classes
At this point, you should have a decent grasp on the concept of classes, and how they can have fields to describe it. But what about behavior? I don't know of any dogs that simply exist but don't do anything. This is where methods come in. Classes can also have methods, which describe the behavior of the objects. Let's add some behavior to our dog class:

```csharp
public class Dog
{
    public string Name;
    public string Breed;

    public Dog(string name, string breed)
    {
        Name = name;
        Breed = breed;
    }

    public void Bark()
    {
        Console.WriteLine($"{Name} is barking!");
    }

    public void RollOver()
    {
        Console.WriteLine($"{Name} is rolling over!");
    }
}
```
We added 2 methods to our class: `Bark` and `RollOver`. So let's use them:
```csharp
Dog myDog = new Dog("Spot", "Husky");
myDog.Bark();
// prints "Spot is barking!" to the console
myDog.RollOver();
// prints "Spot is rolling over!" to the console
```

Now we have a useful class `Dog` that has some fields AND some behavior.

## Why are classes useful?
Similar to methods, classes are another layer that allow us to group together related attributes and behavior into a single entity. When designing complex system, it allows you to break down the problem into smaller, composable and reusable chunks of code.

## Helpful Resources
**I highly recommend looking at these!**
- https://www.youtube.com/watch?v=t2SPg6IuT3k
- https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/intro-to-csharp/introduction-to-classes
- https://www.tutorialsteacher.com/csharp/csharp-class

## Homework
**This homework is going to be more challenging than the previous ones! Make sure you start early on this one and ask lots of questions.**

In this homework you will start off with the following code:
```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        Car myCar = new Car("Toyota", "Camry", 2019);

        Console.WriteLine($"New car created. Make: {myCar.Make}. Model: {myCar.Model}. Year: {myCar.Year}"); // New car created. Make: Toyota. Model: Camry. Year: 2019

        Console.WriteLine($"Total miles: {myCar.TotalMiles}"); // Total miles: 0
        Console.WriteLine($"Last oil change mileage: {myCar.LastOilChange}"); // Last oil change mileage: 0
        Console.WriteLine($"Due for an oil change: {myCar.IsDueForAnOilChange()}"); // Due for an oil change: False
        Console.WriteLine();

        myCar.Drive(200);

        Console.WriteLine($"Total miles: {myCar.TotalMiles}"); // Total miles: 200
        Console.WriteLine($"Last oil change mileage: {myCar.LastOilChange}"); // Last oil change mileage: 0
        Console.WriteLine($"Due for an oil change: {myCar.IsDueForAnOilChange()}"); // Due for an oil change: False
        Console.WriteLine();

        myCar.Drive(5200);

        Console.WriteLine($"Total miles: {myCar.TotalMiles}"); // Total miles: 5400
        Console.WriteLine($"Last oil change mileage: {myCar.LastOilChange}"); // Last oil change mileage: 0
        Console.WriteLine($"Due for an oil change: {myCar.IsDueForAnOilChange()}"); // Due for an oil change: True
        Console.WriteLine();

        myCar.ChangeOil();

        Console.WriteLine($"Total miles: {myCar.TotalMiles}"); // Total miles: 5400
        Console.WriteLine($"Last oil change mileage: {myCar.LastOilChange}"); // Last oil change mileage: 5400
        Console.WriteLine($"Due for an oil change: {myCar.IsDueForAnOilChange()}"); // Due for an oil change: False
    }
}

// Your code here
```

Your goal is to create a class `Car` that will make this code work. No code in the `Program` class should be changed, only new code in the class `Car` should be written (similar to the lesson 5 homework). In the comments to the right of the `Console.WriteLine` statements, it displays **exactly** what should be printed to the console. So, if your program runs correctly, the output you will see is the the following:
```
New car created. Make: Toyota. Model: Camry. Year: 2019
Total miles: 0
Last oil change mileage: 0
Due for an oil change: False

Total miles: 200
Last oil change mileage: 0
Due for an oil change: False

Total miles: 5400
Last oil change mileage: 0
Due for an oil change: True

Total miles: 5400
Last oil change mileage: 5400
Due for an oil change: False
```

The basic idea is that you have a `Car`, and every 5000 miles it needs an oil change. Your job is to create a class `Car` that will allow you to do everything in the program above. This class will contain all of the types of things we learned about in this lesson: a constructor with parameters, fields, and methods.

**Method requirements:**
- `Drive(int mileage)`: the mileage passed in as a parameter is added to the `TotalMiles`
- `ChangeOil()`: this sets `LastOilChange` to the current total mileage
- `IsDueForAnOilChange()`: returns true if the last oil change was more than 5000 miles ago, otherwise returns false
  
**Tips and hints:**
- Start by commenting out all but the first `Console.WriteLine` statement and above, get that to work as expected, and then uncomment each piece one at a time. **This lets you solve each piece one at a time.**
- Think about what each method should do to the *fields* in your class. Should the method change the values? Should it add to existing values? Should the method compare fields? These are good questions to ask yourself.
