For any of these, I recommend creating a new solution each time just to get the hang of creating new solutions and projects. You can also just keep updating your existing `Program.cs` file if you find that easier. The purpose of these is to get you some more practice with loops and conditionals.

Instructions to submit:
- Attach your `Program.cs` file in Slack labeled with the practice number
- I'll run test cases that you won't know in advance, your "grade" is the percentage of test cases you get correct
- Submit each one separately and I'll "grade" you for each one

## Practice #1
- Start from 1 and print all numbers up to and including the given number, and then back down to 1.
- Any input below `1` is invalid, print "Number must be 1 or above"
- Any input that is not a number is invalid, print "Argument must be a valid number"
Example:
```
dotnet run 3
1
2
3
2
1
```

## Practice #2
- Print the given arguments in reverse order

Example:
```
dotnet run 3 9 a
a 9 3
```
```
dotnet run foo 2 T 7 1
1 7 T 2 foo
```

## Practice #3
- Print only the vowels given in the arguments
- Assume that only valid input is given (only lower case letters)
```
dotnet run a q e i
Vowels: a e i
``` 
```
dotnet run q w z
No vowels given
```
```
dotnet run o u p q
Vowels: o u
```
