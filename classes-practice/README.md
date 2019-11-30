# Coffee Maker Practice Problem
Similar to lesson 6, the goal is to start with the code below and make it work. The class is `CoffeeMaker`, and it has 5 methods, here are the method signatures:
```csharp
void Clean();
void FillWithWater();
void AddCoffeeFilter();
void FillWithCoffeeGrinds();
bool MakeCoffee(); // returns true if successfully made coffee, returns false otherwise
```
This coffee maker is very simple, it can't make coffee unless it:
- has been filled with water
- has a coffee filter
- has coffee grinds

If it has all 3 of those things, then it can make coffee. Otherwise, it should fail (return false). 

Once the coffee maker has been "cleaned", everything is emptied and all of those things above need to be added again in order to make coffee again.

Here is the expected output for the `Program` below:
```bash
Unable to make coffee
Unable to make coffee
Unable to make coffee
Made coffee!
Unable to make coffee
```

Here is the sample program to start with:
```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        var coffeeMaker = new CoffeeMaker();

        coffeeMaker.MakeCoffee();                // Unable to make coffee
        coffeeMaker.AddCoffeeFilter();
        coffeeMaker.MakeCoffee();                // Unable to make coffee
        coffeeMaker.FillWithCoffeeGrinds();
        coffeeMaker.MakeCoffee();                // Unable to make coffee
        coffeeMaker.FillWithWater();
        coffeeMaker.MakeCoffee();                // Made coffee!

        // Clean to reset everything
        coffeeMaker.Clean();
        // Should fail because coffee maker has nothing in it
        coffeeMaker.MakeCoffee();                // Unable to make coffee
    }
}
```
