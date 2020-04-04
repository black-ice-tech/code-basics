# Part 2
In part 1 you stored the user's selections in a text file, so that the history is maintained even beyond the life of your running program.

Part 2 is going to build on that idea. Your goal is to make your movie and game options be *stored* in 2 text files, one for movies and one for games. One might be `C:\temp\movies.txt` and one might be `C:\temp\games.txt`. It doesn't matter what you call them as long as one contains games and one contains movies. The text files need to contain both the **name** and the **description** of the movie or game and should be separated by a colon, like this:
```
Settlers of Catan: A strategy game where you collect resources and betray your friends.
Monopoly: Buy lots of properties and rake in the $$$.
Hearts: A card game best when played with 4 people.
```

Change your program to read from these files and display as options to the user. If a movie is added to `movie.txt` and then the program is run, that movie should show up in the list of movies to select. The "history" command should work the same way as it did before, store the user's selection in a text file.

Note: for this part, you can assume those text files already exist. I.e., you don't need to handle the case where the program is run and the files cannot be found.

**Hint:** When reading from a file, you will need to figure out how to separate the name and the description of the game or movie. Do some research on how you can "split" a string based on a certain character.
