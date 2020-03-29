# Part 1
In "inheritance-practice", you created a program that allows the person running the program to choose if they want to play a game or watch a movie. This project is going to expand on that program.

Part 1 is going to introduce the concept of *persistence*. Your goal is to add an option to your program that lets a user see the history of their selections. Here is an example:
```bash
dotnet run history
Movie: Remember the Titans
Game: Settlers of Catan
```

This requires data to live beyond the lifecycle of the program. Remember memory vs disk from the early lessons? In all programs you've run so far, everything lives in *memory*. Now you need to figure out how to get data to live on *disk*, so that you can access it each time you run the program.

**Hint:** Use a text file to store the game/movie selection. Take a look at this: https://docs.microsoft.com/en-us/dotnet/api/system.io.file?view=netcore-3.1
