# Lesson 5 - Methods
### Conceptual Overview
According to the Microsoft [documentation](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods), a **method** "is a code block that contains a series of statements."

Ok, first question is probably "what is a statement"? A statement is essentially an executable piece of code. It roughly translates to a single line a code (not always). Here is a statement:
```csharp
var myVar = 123;
```
And another:
```csharp
Console.WriteLine(myVar);
```

You can group statements together to form a **method**. Up to this point, we've been doing everything inside of the `Main` method. This is entry point for all C# programs. The CLR (Common Language Runtime) looks for the `Main` method when running the program.

### Structure of a method
A method has what's called a *signature*, which is what makes the method unique. The signature consists of several parts:
- The class or struct it belongs to
- Any modifiers (such as `public`, `private`, etc.)
- The return type 
- The parameters
- The method name

In the `Program` class we've been working in, the signature of the `Main` method is:
- Class = `Program`
- Modifiers = `public`, `static`
- Return type = `void`
- Parameters = `string[] args`
- Method name = `Main`

You can generally view the method signature as the line before the curly braces, like this:
```csharp
public void Main(string[] args)
```

### Why are methods useful?
Methods define *behavior* of a class. We will get to classes more in future lessons. Methods are useful to logically separate pieces of code and also allow for code reuse. For example, in the calculator program you wrote, you *could* do something like this:

```csharp
public class Program
{
    public void Main(string[] args)
    {
        int result;
        var command = args[0];
        var num1 = Convert.ToInt32(args[1]);
        var num2 = Convert.ToInt32(args[2]);

        if (command == "add")
        {
            result = Add(num1, num2);   
        }
        else if (command == "subtract")
        {
            result = Subtract(num1, num2);
        }
        // ...
        // you get the idea...

        Console.WriteLine($"Result is {result}");
    }

    public static int Add(int num1, int num2)
    {
        return num1 + num2;
    }

    public static int Multiply(int num1, int num2)
    {
        return num1 * num2;
    }

    public static int Subtract(int num1, int num2)
    {
        return num1 - num2;
    }

    public static int Divide(int num1, int num2)
    {
        return num1 / num2;
    }
}
```
Now you have your methods separated by operation, and you can resuse those methods as needed. Let's do another example, you have a program that does chores. There are different ways to do these chores based on certain *parameters*. In laundry, the process for doing lights and darks is similar, so you want to put that logic in it's own method. Take a look:

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        var choreHelper = new ChoreHelper();
        
        choreHelper.DoLaundry("lights");
        choreHelper.DoLaundry("darks");
        choreHelper.DoDishes(true);
    }
}

public class ChoreHelper
{
    public void DoLaundry(string clothingType)
    {
        Console.WriteLine($"Collecting dirty {clothingType} clothes...");
        Console.WriteLine("Loading into washer...");
        Console.WriteLine("Loading into dryer...");
        Console.WriteLine("Folding clothes...");
        Console.WriteLine("Putting away clothes...");
    }

    public void DoDishes(bool washByHand)
    {
        if (washByHand)
        {
            Console.WriteLine("Washing dishes...");
            Console.WriteLine("Drying dishes...");
        }
        else
        {
            Console.WriteLine("Loading dishes into dishwasher...");
            Console.WriteLine("Running the dishwasher...");
        }

        Console.WriteLine("Putting away dishes...");
    }
}
```
Try to not focus on the line `var choreHelper = new ChoreHelper()` too much at the moment. Just know it's necessary to create a new *instance* of a class in order to call it's methods (unless the method is `static`). More on this in future lessons.

For the `DoLaundry` method, you notice that you called it twice. Without putting the logic into a method, you'd have to copy and paste the exact same code in 2 places. And if you needed to change how to do laundry, maybe you add a step for ironing, you have to change that in 2 places instead of in the single method. 

## Helpful Resources
- This goes into more detail than is needed at the moment, but still helpful: https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods
- https://www.tutorialspoint.com/csharp/csharp_methods.htm

## Homework
Start with this `Program.cs` file template:
```csharp
using System;

namespace Lesson5
{
    // Don't change anything in this Program class
    class Program
    {
        static void Main(string[] args)
        {
            WeatherForecaster forecaster = new WeatherForecaster();

            double degreesF = forecaster.GetTodaysTemp();

            double degreesC = forecaster.ConvertToCelsius(degreesF);

            Console.WriteLine($"The temperature today is {degreesF} degrees Fahrenheit and {degreesC} degrees Celsius");

            bool isFreezing = forecaster.IsFreezing(degreesF);

            Console.WriteLine($"Freezing: {isFreezing}");
        }
    }

    class WeatherForecaster
    {
        // This method returns a random double between 0 and 115
        public double GetTodaysTemp()
        {
            return new Random().NextDouble() * 115.0;
        }

        // Add your code here
    }
}

```

By ONLY adding 2 methods `ConvertToCelsius` and `IsFreezing` to the `WeatherForecaster` class, make your program print the following:
```bash
dotnet run
Calculating celsius...
The temperature today is 9.13328563521303 degrees Fahrenheit and -12.7037302026594 degrees Celsius
Freezing: True
```
```bash
Calculating celsius...
The temperature today is 86.9745435784452 degrees Fahrenheit and 30.5414130991362 degrees Celsius
Freezing: False
```
Note there are 3 lines being printed to the console.

In order for this homework to be valid, you must not change anything in `Program` class. I.e., your `Main` method should not be changed at all, only the `WeatherForecaster` class should have 2 new methods.

**To submit:** In Slack, send me the contents of `Program.cs` file, and I will run it to verify it works and that the code is valid.
