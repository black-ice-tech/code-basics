# Lesson 8 - Interfaces
## Overview
You can think of an interface as a *contract* of methods that must be implemented by a class "implementing" the interface. This probably makes very little sense, so instead, let's take a look at some examples.

```csharp
public interface IVehicle // C# convention is to prefix interface names with an "I"
{
    void Drive(int miles);
}
```

Note `Drive`, does it look familiar? It's a method *signature*, but there is no implementation. Now let's *implement* the interface:
```csharp
public class Car : IVehicle
{
    public void Drive(int miles)
    {
        Console.WriteLine($"Car just drove {miles} miles");
    }
}
```
The compiler will not allow a class to implement an interface - denoted by the `: IVehicle` notation - without implementing *all* of the methods defined in the interface. 

## Benefits of interfaces
So why on earth would I want to use an interface? What's wrong with just using a class? Interfaces allow you to have many implementations for the same method signatures. Looking back at the `IVehicle` example, let's add another implementation:
```csharp
public class Truck : IVehicle
{
    public void Drive(int miles)
    {
        Console.WriteLine($"Truck just drove {miles} miles");
    }
}
```
So now we have 2 classes implementing the same interface: `Car` and `Truck`. Now let's look at some interesting things we can do with this:
```csharp
public static void Main(string[] args)
{
    IVehicle car = new Car();
    IVehicle truck = new Truck();
    List<IVehicle> vehicles = new List<IVehicle>();

    vehicles.Add(car);
    vehicles.Add(truck);

    foreach (var vehicle in vehicles)
    {
        vehicle.Drive();
    }
}
```
Note how both `car` and `truck` are of type `IVehicle` on the left, but they are initialized with `new Car()` and `new Truck()`. How is this possible? Since `Car` and `Truck` both implement the `IVehicle` interface, the C# compiler knows that both of those classes have "fulfilled the contract", therefore a `Car` is an `IVehicle` and a `Truck` is also an `IVehicle`. 

Interfaces can often be confusing to grasp, so I would suggest doing some extra reading on it to make sure the concept is solidified. Here are some useful resources:
- https://stackoverflow.com/a/6878726
- https://stackoverflow.com/a/1042173
- https://dzone.com/articles/c-interfaces-what-are-they-and

## Homework
The objective is to create 4 classes that implement the `IComputable` interface below, that will produce the expected output below:
```csharp
using System;
using System.Collections.Generic;

public interface IComputable
{
    double Compute(double num1, double num2);
}

class Program
{
    public static void Main(string[] args)
    {
        var operations = new List<IComputable>();

        var addOperation = new AddOperation();
        var subtractOperation = new SubtractOperation();
        var multiplyOperation = new MultiplyOperation();
        var divideOperation = new DivideOperation();

        operations.Add(addOperation);
        operations.Add(subtractOperation);
        operations.Add(multiplyOperation);
        operations.Add(divideOperation);

        foreach (var operation in operations)
        {
            var result = operation.Compute(10, 5);
            Console.WriteLine($"{operation.GetType()}: {result}");
        }

        Console.WriteLine("-----------------");

        foreach (var operation in operations)
        {
            var result = operation.Compute(3, 3);
            Console.WriteLine($"{operation.GetType()}: {result}");
        }

        Console.WriteLine("-----------------");

        foreach (var operation in operations)
        {
            var result = operation.Compute(8, 4);
            Console.WriteLine($"{operation.GetType()}: {result}");
        }
    }
}
```

The expected output is:
```bash
AddOperation: 15
SubtractOperation: 5
MultiplyOperation: 50
DivideOperation: 2
-----------------
AddOperation: 6
SubtractOperation: 0
MultiplyOperation: 9
DivideOperation: 1
-----------------
AddOperation: 12
SubtractOperation: 4
MultiplyOperation: 32
DivideOperation: 2
```
