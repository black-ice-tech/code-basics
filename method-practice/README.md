# Practice with Methods
### Method Signatures
For each of the following code snippets, write down the method signature that would allow this code to compile. Feel free to copy and paste the code and try to actually get it to compile in Visual Studio to check your work. For example:
```csharp
class Program
{
    static void Main(string[] args)
    {
        string name = "Bob";
        
        int age = CalculateAge(name);
    }
}
```
The answer is:
`static int CalculateAge(string name)` in class `Program`.

#### Problem #1
```csharp
class Program
{
    static void Main(string[] args)
    {
        RecipeFinder recipeFinder = new RecipeFinder();

        int numberOfServings = 4;
        string typeOfFood = "Italian";
        string recipeName = recipeFinder.FindRecipeName(typeOfFood, numberOfServings);
    }
}
```
#### Problem #2
```csharp
class Program
{
    static void Main(string[] args)
    {
        double num1 = 1.5;
        double num2 = 3.0;
        double num3 = 5.0;

        double sum = Add(num1, num2, num3);
    }
}
```
#### Problem #3
```csharp
class Program
{
    static void Main(string[] args)
    {
        WeatherForecasterFactory factory = new WeatherForecasterFactory();
        WeatherForecaster forecaster = factory.GetWeatherForecaster(args[0], args[1]);
    }
}
```

### Coding Problem
Write a program that takes in 3 arguments:
1) first name
2) last name
3) age
The program outputs `Hello <first name> <last name>, you are (NOT) old enough to drink`.

You can assume that all of the inputs are valid.
Restrictions:
- The `Main` method should **only have statements calling the methods you created**.
- You must use **at least 2 methods** outside of `Main`

Sample inputs / outputs:
```bash
dotnet run Billy Bob 21
Hello Billy Bob, you are old enough to drink! 
```
```bash
dotnet run John Doe 20
Hello John Doe, you are NOT old enough to drink! 
```
