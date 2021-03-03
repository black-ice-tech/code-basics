# DB Practice
## Part A
Start with this code:
```csharp
using System;
using System.Data.SQLite;

public class CreateTable
{
    static void Main()
    {
        string connectionString = @"URI=file:C:\Users\PATH_TO_YOUR_SQLITE";

        using var connection = new SQLiteConnection(connectionString);
        connection.Open();

        using var command = new SQLiteCommand(connection);

        // Delete the table and recreate it to start clean
        command.CommandText = "DROP TABLE IF EXISTS cars";
        command.ExecuteNonQuery();

        command.CommandText = @"CREATE TABLE cars(id INTEGER PRIMARY KEY,
                    name TEXT, price INT)";
        command.ExecuteNonQuery();

        command.CommandText = "TODO";
        command.ExecuteNonQuery();

        command.CommandText = "TODO";
        command.ExecuteNonQuery();

        command.CommandText = "TODO";
        command.ExecuteNonQuery();

        string statement = "SELECT * FROM cars";

        using var selectCommand = new SQLiteCommand(statement, connection);
        using SQLiteDataReader rdr = command.ExecuteReader();

        while (rdr.Read())
        {
            Console.WriteLine($"{rdr.GetInt32(0)} {rdr.GetString(1)} {rdr.GetInt32(2)}");
        }
    }
}
```
Update the "TODO" statements to be the correct SQL statements to have a result like this:
```
1 Audi 52642
2 Mercedes 57127
3 Skoda 9000
```

## Part B
Update the statement that says "SELECT * FROM cars" and change it so that the output of the program instead is this:
```
Audi
Mercedes
Skoda
```
This will also require updating the line that says:
```csharp
Console.WriteLine($"{rdr.GetInt32(0)} {rdr.GetString(1)} {rdr.GetInt32(2)}");
```
