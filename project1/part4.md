# Part 4
Your goal for this part is to add 2 features:
1) Update your program to support labels at the top of the database (text file).
2) Instead of hardcoding the text files in your code, accept the text files in the arguments of the program. The 1st argument is the path to the history text file, the 2nd is games, and the 3rd is movies.

## Examples for 1)
```
Name|Description|Rating|Length
Finding Nemo|A fish gets lost|****|100m
Batman: The Dark Knight|I am Batman|*****|152m
```
OR
```
Description|Name|Rating|Length
A fish gets lost|Finding Nemo|****|100m
I am Batman|Batman: The Dark Knight|*****|152m
```
OR
```
Length|Description|Name|Rating
100m|A fish gets lost|Finding Nemo|****
152m|I am Batman|Batman: The Dark Knight|*****
```

## Examples for 2)
This should work for both relative AND absolute paths.

Relative path example:
```
dotnet run path/to/history.txt path/to/games.txt path/to/movies.txt
```

Absolute path example:
```
dotnet run C:/Users/your_user/path/to/history.txt C:/Users/your_userpath/to/games.txt C:/Users/your_user/path/to/movies.txt
```