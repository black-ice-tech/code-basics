# Lesson 9 - Inheritance & Abstract classes
## Overview
In previous lessons we've learned about classes, and they can represent objects. In this lesson, we're going to learn about how to use inheritance and abstract classes to write cleaner, simpler code.

## Inheritance
Inheritance is creating a class that "inherits" characteristics from another class, called the "base" class. In order to illustrate this concept, it's best to start with an example:
```csharp
public class Truck
{
    public int TotalMiles { get; private set; }

    public Truck()
    {
        TotalMiles = 0;
    }

    public void Drive(int mileage)
    {
        TotalMiles += mileage;
    }
}
```
Here we have a class `Truck`, and so far it does one thing: `Drive`, and it has one *property*: `TotalMiles`. Now let's say we need to add 2 more classes `Sedan` and `Van`:
```csharp
public class Sedan
{
    public int TotalMiles { get; private set; }

    public Sedan()
    {
        TotalMiles = 0;
    }

    public void Drive(int mileage)
    {
        TotalMiles += mileage;
    }
}

public class Van
{
    public int TotalMiles { get; private set; }

    public Van()
    {
        TotalMiles = 0;
    }

    public void Drive(int mileage)
    {
        TotalMiles += mileage;
    }
}
```
The code looks awfully similar in each class, doesn't it? This is where *inheritance* can help. Before we go any further, ask yourself the following question:

What is the **abstraction** common to all of these classes?

> It's worth noting that there is not one right answer to this question, but it's an exercise you will find yourself going through often as a software developer.

In this case, an abstraction that could make sense (again, no single right answer) is a `Vehicle`. So let's use `inheritance` to make this code a little simpler and cleaner:
```csharp
public class Vehicle
{
    public int TotalMiles { get; private set; }

    public Vehicle()
    {
        TotalMiles = 0;
    }

    public void Drive(int mileage)
    {
        TotalMiles += mileage;
    }
}

public class Truck : Vehicle
{
}

public class Sedan : Vehicle
{
}

public class Van : Vehicle
{
}

public static void Main(string[] args)
{
    var vehicle = new Vehicle();
    vehicle.Drive(10);
    Console.WriteLine($"Vehicle total miles: {vehicle.TotalMiles}");

    var truck = new Truck();
    truck.Drive(20);
    Console.WriteLine($"Truck total miles: {truck.TotalMiles}");

    var sedan = new Sedan();
    sedan.Drive(30);
    Console.WriteLine($"Sedan total miles: {sedan.TotalMiles}");

    var van = new Van();
    van.Drive(30);
    Console.WriteLine($"Van total miles: {van.TotalMiles}");
}
```
What's happening here? How can we call the `Drive` method on `Truck`, `Sedan`, and `Van` when there is nothing in the body of those classes? It's because of inheritance. The compiler sees that `Truck`, `Sedan`, and `Van` are *derived* types from the class `Vehicle`, so the derived types *inherit* the properties and methods from the `Vehicle` class. Therefore, we can call the `Drive` method on those classes, as well as access the `TotalMiles` property.

> Notice the similarity to interfaces? Interfaces and inheritance are often used together. There are a lot of "best practices" that go into deciding when to use interfaces, inheritance, or both, but that discussion is beyond the scope of this lesson.

## Abstract classes
### The Problem
Let's make the `Vehicle` class a little more interesting:
```diff
public class Vehicle
{
    public int TotalMiles { get; private set; }

    public Vehicle()
    {
        TotalMiles = 0;
    }

    public void Drive(int mileage)
    {
        TotalMiles += mileage;
    }

+   public void Assemble()
+   {
+   }
}
```
We added an `Assemble` method, this method is responsible for putting together the vehicle (e.g., in a factory). But what should go in here? Won't the implementation be different for every derived type? Assembling a `Sedan` will be different than assembling a `Truck` and from assembling a `Van`. Well, one option is to move the `Assemble` method to the derived types, something like this:
```diff
public class Vehicle
{
    public int TotalMiles { get; private set; }

    public Vehicle()
    {
        TotalMiles = 0;
    }

    public void Drive(int mileage)
    {
        TotalMiles += mileage;
    }

-   public void Assemble()
-   {
-   }
}

public class Truck : Vehicle
{
+   public void Assemble()
+   {
+       Console.WriteLine("Assembled truck!");
+   }
}

public class Sedan : Vehicle
{
+   public void Assemble()
+   {
+       Console.WriteLine("Assembled sedan!");
+   }
}

public class Van : Vehicle
{
+   public void Assemble()
+   {
+       Console.WriteLine("Assembled van!");
+   }
}
```
That kind of works... Here's the problem:
```csharp
public static void Main(string[] args)
{
    var truck = new Truck();
    var sedan = new Sedan();
    var van = new Van();

    var vehicles = new List<Vehicle>();
    vehicles.Add(truck);
    vehicles.Add(sedan);
    vehicles.Add(van);
    
    foreach (var vehicle in vehicles)
    {
        // Does NOT compile!
        vehicle.Assemble();
    }
}
```
We lose some of the value we gained from inheritance, because now we can't call `Assemble` on the type `Vehicle`. Even though the actual types are `Truck`, `Sedan`, and `Van`, we are trying to put them all in a list of `Vehicle`, and now we've lost the method becuase it doesn't exist in the `Vehicle` class at all. How do we solve this? This is a good situation to use *abstract classes*.

### The Solution
We'll change our code first and then we will discuss what it happening:
```csharp
// "abstract" keyword added
public abstract class Vehicle
{
    public int TotalMiles { get; private set; }

    public Vehicle()
    {
        TotalMiles = 0;
    }

    public void Drive(int mileage)
    {
        TotalMiles += mileage;
    }

    // "abstract" keyword added, and body of method removed
    public abstract void Assemble();
}

public class Truck : Vehicle
{
    // "override" keyword added
    public override void Assemble()
    {
        Console.WriteLine("Assembled truck!");
    }
}

public class Sedan : Vehicle
{
    // "override" keyword added
    public override void Assemble()
    {
        Console.WriteLine("Assembled sedan!");
    }
}

public class Van : Vehicle
{
    // "override" keyword added
    public override void Assemble()
    {
        Console.WriteLine("Assembled van!");
    }
}
```
Let's break each new piece apart:
```csharp
public abstract class Vehicle
```
We added `abstract`, this keyword tells the compiler that you cannot instantiate the class. For example, this code will no longer compile:
```csharp
var vehicle = new Vehicle();
```
This is useful for defining types that you don't want to be instantiated, but you want to define common properties and behavior.

Next:
```csharp
public abstract void Assemble();
```
This marks the method itself as `abstract`, and tells the compiler that it will find the implementation of that method in the derived type(s). Note how similar this is to creating an `interface`, where you define the method signature but no implementation. Also much like an interface, this enforces a contract that all derived types MUST implement the `Assemble` method.

Next, in each derived type:
```csharp
public override void Assemble()
```
We added the `override` keyword. This tells the compiler that it is providing the implementation for the `abstract` method `Assemble`, which is declared in the `Vehicle` class.

Finally, let's go back to our `Main` method and see how that helps us now:
```csharp
public static void Main(string[] args)
{
    var truck = new Truck();
    var sedan = new Sedan();
    var van = new Van();

    var vehicles = new List<Vehicle>();
    vehicles.Add(truck);
    vehicles.Add(sedan);
    vehicles.Add(van);
    
    foreach (var vehicle in vehicles)
    {
        // Now this DOES compile!
        vehicle.Assemble();
    }
}
```
Because `Assemble` is declared in the `Vehicle` abstract class, the code above now will compile.

## Additional Information
There was a lot of information in this lesson, and we didn't cover everything related to inheritance and abstract classes. Here are some additional concepts you should research on your own:
- virtual methods
- difference between `public`, `protected`, `private`, and `internal` keywords
- implicit inheritance from `object`
- `override` vs `new` keywords
- `sealed` keyword

### Helpful resources
- https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/inheritance
- https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/polymorphism
- https://en.wikibooks.org/wiki/C_Sharp_Programming/Inheritance

## Homework
Create 2 classes `GermanShepherd` and `Dachshund` to make the following program work:
```csharp
public abstract class Dog
{
    public void Speak()
    {
        Console.WriteLine("Woof!");
    }

    public abstract void ProtectOwner();

    public abstract void CrawlUnderCouch();
}

public static void Main(string[] args)
{
    Console.WriteLine("German Shepherd:");
    var germanShepherd = new GermanShepherd();
    germanShepherd.ProtectOwner();
    germanShepherd.CrawlUnderCouch();
    germanShepherd.Speak();

    Console.WriteLine("---------");

    Console.WriteLine("Dachshund:");
    var dachshund = new Dachshund();
    dachshund.ProtectOWner();
    dachshund.CrawlUnderCouch();
    dachshund.Speak();
}
```

The output should be the following:
```bash
German Shepherd:
Successfully protected owner and attacked the intruder.
Could not crawl under the couch because German Shepherds are too big.
Woof!
---------
Dachshund:
Failed to protect owner because Dachshunds are so small.
Crawled under the couch successfully.
Woof!
```



