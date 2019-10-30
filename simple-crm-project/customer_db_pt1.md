# Simple CRM - Part 1

## Getting Started
First thing is to create a new Blank Solution in Visual Studio. Do that in the terminal using the `dotnet` CLI. Run the following commands in order (you can just copy and paste into your terminal after running the 1st line):
```bash
cd <wherever you like to keep your code projects>
mkdir simple-crm
cd simple-crm
dotnet new sln
mkdir src\SimpleCrm.Cli
mkdir test\SimpleCrm.Specs
cd src/SimpleCrm.Cli
dotnet new console
cd ../..
dotnet sln add src/SimpleCrm.Cli/SimpleCrm.Cli.csproj
cd test/SimpleCrm.Specs
dotnet new nunit
cd ../..
dotnet sln add test/SimpleCrm.Specs/SimpleCrm.Specs.csproj

```

Now, you should have a file structure that looks like this ![this](file_structure.png?raw=true)

You have 2 projects within your solution now:
- SimpeCrm.Cli: this is the project that will have code related to your CLI
- SimpeCrm.Specs: this is a test project that contains unit tests for your code. Don't worry too much about the Specs project yet, we will focus more on this later. 

Open up your simple-crm.sln file using Visual Studio. 

For this part, all of your code will be in the either the `Program.cs` file or other files you create in the `SimpleCrm.Cli` project.

## Customer Database
Your goal for part 1 is to be able to add and remove customers using the CLI command as follows:
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

Store the customer data into a JSON file called `customers.json` and in the folder `src/SimpleCrm.Cli`. For example, if you have 2 customers in your "database" your json file would look like this:
```json
[
    {
        "id": 1,
        "name": "Billy Bob",
        "phoneNumber": "1-222-333-4444",
        "email": "billy.bob@pizzahut.com",
        "company": "Pizza Hut"
    },
    {
        "id": 2,
        "name": "John Doe",
        "phoneNumber": "1-111-555-7878",
        "email": "john.doe@.toyota.com",
        "company": "Toyota"
    }
]
```

Useful resources for learning JSON:
- https://www.c-sharpcorner.com/article/from-zero-to-hero-in-json-with-c-shar/
- https://www.c-sharpcorner.com/article/working-with-json-in-C-Sharp/
- https://www.newtonsoft.com/json