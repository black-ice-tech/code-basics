# Simple CRM

## Getting Started
- First, create a GitHub repository for this, and clone it using GitHub Desktop (or whatever you prefer)
- Then, in your cloned repository, create a new Blank Solution in Visual Studio. Do that in the terminal using the `dotnet` CLI. Run the following commands in order (you can just copy and paste into your terminal after running the 1st line):
```bash
cd <wherever you like to keep your code projects>
mkdir simple-crm
cd simple-crm
dotnet new sln
mkdir src\SimpleCrm.Cli
cd src/SimpleCrm.Cli
dotnet new console
cd ../..
dotnet sln add src/SimpleCrm.Cli/SimpleCrm.Cli.csproj
```

Now, you should have a file structure that looks like this:
```
src/
  SimpleCrm.Cli/
    Program.cs
    SimpleCrm.Cli.cproj
```

Open up your simple-crm.sln file using Visual Studio. 

After setup, push your changes to your GitHub repository.

## Customer Database
Your goal for this project is to be able to add, update, get, and remove customers using the CLI command as follows:
```bash
cd src/SimpleCrm.Cli
dotnet run customer new
Enter customer name >>> Billy Bob
Enter customer phone number >>> 1-222-333-4444
Enter customer email >>> billy.bob@pizzahut.com
Enter customer company >>> Pizza Hut 
Customer "Billy Bob" added and has id "1"!
```
Now that the customer has been added, you should be able to retrieve it like:
```bash
dotnet run customer get 1
Successfully found customer with id "1":
Name: Billy Bob
Phone Number: 1-222-333-4444
Email: billy.bob@pizzahut.com
Company: Pizza Hut
```
You can also update it:
```bash
dotnet run customer update 1
Enter customer name >>> Billy Jean
Enter customer phone number >>> 1-222-333-4444
Enter customer email >>> billy.jean@pizzahut.com
Enter customer company >>> Pizza Hut 
Customer with id "1" successfully updated!
```
Make sure it got updated correctly:
```bash
dotnet run customer get 1
Successfully found customer with id "1":
Name: Billy Jean
Phone Number: 1-222-333-4444
Email: billy.jean@pizzahut.com
Company: Pizza Hut
```
And, finally, remove it:
```bash
dotnet run customer remove 1
Successfully removed customer with id "1"
```
If you try to retrieve it again, you should get an error:
```bash
dotnet run customer get 1
Customer with id "1" not found!
```

Store the customer data into a Database of your choice (SQLite, Postgres, Mongo, etc.)
