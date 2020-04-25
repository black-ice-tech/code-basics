# Part 3
In part 2 we added support for reading from a file. Now you have 3 files related to this program:
- A file containing games
- A file containing movies
- A file containing the history of the user's selection

The format of the games and movies files looks like this:
```
{name}: {description}
```

Your goal for this part is to add 2 new attributes in the game and movie files: "rating" and "length".

Update your program so that the games and movies files look like this
```
{name}|{description}|{rating}|{length}
```

## Example
Here is an example of how your program should work with these new requirements.

movies.txt:
```
Finding Nemo|A fish gets lost|****|100m
Batman: The Dark Knight|I am Batman|*****|152m
```

games.txt:
```
Exploding Kittens|Crazy game of luck.|****|10m
Candy Land|I'm getting tired of coming up with descriptions.|*|22m
```

```bash
dotnet run
Do you want to watch a movie or play a game?
game
Select a game:
1) Exploding Kittens
2) Candy Land
1
You selected "Exploding Kittens": Crazy game of luck.

Would you like to see more details?
yes     # user input
Rating: ****
Length: 10m
```

### Requirements
- The history functionality should work exactly as it did before, storing only the activity type (Movie or Game) and the name.
- The separator is now a "|" rather than a ":" in the movie and game files

### Hints
- This part requires you add 2 new attributes, a "rating" and a "length". Consider your design and how difficult it would be if in the future you are asked to add 5 or 10 new attributes. Is it easy to update your program to make that change?
- Consider your design and how difficult it would be if in the future you are asked to add more activity "types" (e.g. listening to a song, or watching a tv show). Is it easy to update your program to make that change?

If the answer to either of the above questions is "no", start thinking about how you could better design your program to accomdate those types of changes.