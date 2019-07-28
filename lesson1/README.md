# Lesson #1 - Using the tools
Assuming you are running Windows, make sure you have the following things installed / setup:
- Create a GitHub account
- Visual Studio Community Edition (preferably 2019, 2017 is ok too)
- Git for Windows (we will primarily only use Git Bash): https://gitforwindows.org/

## Navigating your Terminal
Git Bash is a terminal that allows you to run Unix commands in Windows. If that sounds like gibberish to you, that's OK. Learning basic Unix commands is a good skill to have. We will start with navigating the file system. Open up Git Bash, you'll see a directory listed at the top, this is your current directory. You can open up a file browser and navigate to that directory as well.
To see all the files listed in that directory, execute the command:
```bash
ls
```
You'll see a list files and directories. Now execute:
```bash
cd ..
```
`cd` stands for "change directory", and the `..` takes you up one level. You can run `ls` here again to see the files listed. Running `cd` with nothing after will take you to your home directory. On Windows, will usually be something like `C:\users\<your_name>`. Ensure you are in your home directory:
```bash
cd
```
Now make a directory for your new project:
```bash
mkdir hello-world
```

To get more familiar with your terminal, here are some good resources:
```
TBD
```

Now that you know how to navigate in your terminal, let's create a "Hello World!" C# program.

## C# Hello World!
Open up Visual Studio, and select "Create New Project". Select `Console App (.NET Core)`, and then name your project `BlackIceTech.HelloWorld` and select the Location `C:\users\your_name\hello-world\src`.

In Visual Studio, you should see a file called `Program.cs` with code that looks like this:
```csharp
using System;

namespace BlackIceTech.HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```
Now, let's run it. First, we'll run it in Visual Studio. At the top in your toolbar, you should see a green arrow with `BlackIceTech.HelloWorld` next to it. Click that to run your program. You will probably see a terminal pop up and then immediately disappear, this is because your program finished executing, so Visual Studio closed it. If it kept your terminal open, then ignore the steps below.

Go to `Tools -> Options -> Debugging -> General` and uncheck the box `Automatically close the console when debugging stops`.

Now run your program again, you should see `Hello World!` in the terminal that pops up. Alternatively, you can run your program from the terminal. So open up your Git Bash, and navigate to the directory of your new project. 
```bash
cd ~/projects/hello-world/BlackIceTech.HelloWorld/BlackIceTech.HelloWorld
```
Now run:
```bash
dotnet run
```
You should see the same `Hello World!` output in your terminal.

## Homework -  Simple Addition
**Note**: Homework requires you to do some searching / googling on your own. It's not meant to be a regurgitation of the lesson. Some things you will need to figure out for this one:
- How to accept command line arguments in .NET Core
- How to print to console string with a variable

This work is updating your hello world program to take in 2 arguments, both integers. The program will output the sum in the format `Sum is {num}`.  
Input:
```bash
dotnet run 4 5
```

Output:
```bash
Sum is 9
```

Once finished, commit your work to your GitHub repository (we will go over how to set this up face to face) and submit a pull request (we'll go over this too). Don't worry about making it pretty or anything, just put the code up there and I will give feedback.