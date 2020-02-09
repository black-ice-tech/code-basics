# Practice Problems for Inheritance and Abstract Classes
## Problem 1
For each of the following code blocks, answer "compiles", "compiles with warning", or "does not compile". If you answer either "compiles with warning" or "does not compile", explain both WHAT the issue is and HOW to resolve it.

Try to answer first without copying the code into your IDE.

a)
```csharp
public abstract class Car
{
    public abstract void Drive()
    {
        System.Console.WriteLine("Driving...");
    }
}
```

b)
```csharp
public abstract class Car
{
    public virtual void Drive()
    {
        System.Console.WriteLine("Driving...");
    }
}
```

c)
```csharp
public class Car
{
    public abstract void Drive();
}
```

d)
```csharp
public class Car
{
    public void Drive()
    {
        System.Console.WriteLine("Driving...");
    }
}

public class Convertible : Car
{
    public void OpenTop()
    {
        System.Console.WriteLine("Opening top...");
    }
}

public class Program 
{
    public static void Main(string[] args)
    {
        var myCar = new Car();
        myCar.OpenTop();
    }
}
```

e)
```csharp
public class Car
{
    public void Drive()
    {
        System.Console.WriteLine("Driving...");
    }
}

public class Convertible : Car
{
    public override void Drive()
    {
        System.Console.WriteLine($"Driving convertible...");
    }
}
```

f)
```csharp
public class Car
{
    public virtual void Drive()
    {
        System.Console.WriteLine("Driving...");
    }
}

public class Convertible : Car
{
    public override void Drive()
    {
        System.Console.WriteLine("Driving convertible...");
    }
}
```

g)
```csharp
public abstract class Car
{
    private string _make = "Toyota";

    public abstract void Drive();
}

public class Convertible : Car
{
    public override void Drive()
    {
        System.Console.WriteLine($"Driving convertible with make: {_make}");
    }
}
```

h)
```csharp
public abstract class Car
{
    protected string Make = "Toyota";

    public abstract void Drive();
}

public class Convertible : Car
{
    public override void Drive()
    {
        System.Console.WriteLine($"Driving convertible with make: {Make}");
    }
}
```

i)
```csharp
public abstract class Car
{
    public string Make = "Toyota";

    public abstract void Drive();
}

public class Convertible : Car
{
    public override void Drive()
    {
        System.Console.WriteLine($"Driving convertible with make: {Make}");
    }
}
```

j)
```csharp
public abstract class Car
{
    public abstract void Drive();
}

public class Convertible : Car
{
    public override void Drive()
    {
        System.Console.WriteLine("Driving convertible...");
    }
}
```

k)
```csharp
public abstract class Car
{
    public abstract void Drive();
}

public class Program
{
    public static void Main(string[] args)
    {
        var car1 = new Car();
        car1.Drive();
    }
}
```

l)
```csharp
public abstract class Car
{
    public abstract void Drive();
}

public class Convertible : Car
{
    public override void Drive()
    {
        System.Console.WriteLine("Driving convertible...");
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        var car1 = new Convertible();
        car1.Drive();
    }
}
```

m)
```csharp
public class Car
{
    public void Drive()
    {
        System.Console.WriteLine("Driving...");
    }
}

public class Convertible : Car
{
    public void Drive()
    {
        System.Console.WriteLine("Driving convertible...");
    }
}
```

## Problem 2
In 1-2 sentences, answer each of the following questions:
- What is the difference between an abstract class and an interface?
- What is the difference between the keyword `virtual` and `abstract`?
- What is the purpose of the `new` keyword on a method?
- Identify 2 or 3 situations where you would use abstract classes instead of regular classes

## Problem 3
Write a program that allows a user to select whether they want to play a game or a movie, and then select the movie they want to watch or the game they want to play. Once they select the movie or game, print out the name, followed by the description of what they selected.

Note: you don't have to have the movies and games from the samples, those are just examples.

Sample output:
```bash
dotnet run
Do you want to watch a movie or play a game?
movie   # this is user input
Select a movie:
1) Batman: The Dark Knight
2) Remember the Titans
3) Instant Family
2       # this is user input
You selected "Remember the Titans": A feel good sports movie about a high school football team.
```

```bash
dotnet run
Do you want to watch a movie or play a game?
game    # this is user input
Select a game:
1) Settlers of Catan
2) Monopoly
3) Hearts
1       # this is user input
You selected "Settlers of Catan": A strategy game where you collect resources and betray your friends.
```

Bonus points for:
- Making your program run in a loop, so that the user doesn't have to type `dotnet run` to select a new movie or game.
- Incorporating techniques learned in previous lessons (interfaces, abstract classes) where appropriate
