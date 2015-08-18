# Code-Along: Speaking Grandma

## Objectives

1. Convert a string to its uppercase version.
2. Capture the result of a comparison method into a `BOOL` variable.
3. Practice flow control by using an `if`/`else` statement.
4. Use the negation operator (`!`) to perform an inverted check.

##### Advanced

1. Change the compared objects after capturing the result of the comparison into a `BOOL` variable. See what happens. 

## Instructions

This code-along lab will walk you through creating an `if`/`else` statement, comparing strings, and creating a `BOOL` variable to pass into a conditional.

Open the `objc-speaking-grandma.xcodeproj` file and navigate to the `FISAppDelegate.m` implementation file. You'll enter all of your code in the `application:didFinishLaunchingWithOptions:` method body (between the curly braces `{``}` but before the `return YES;` statement).

### Code-Along I: Talk To Grandma

1 — Create an `NSString` variable called `talkToGrandma` and set it equal to any regular sentence that you like:
  
  * `NSString *talkToGrandma = @"Hi, Grandma!";`

2 — Create an `NSString` variable called `shoutAtGrandma` and set it equal to the result of calling the `uppercaseString` method on  `talkToGrandma`:
  
  * `NSString *shoutAtGrandma = [talkToGrandma uppercaseString];`

3 — Create a `BOOL` variable called `shouting` and set it equal to the result of comparing `talkToGrandma` and `shoutAtGrandma` with the `isEqualToString:` method:
  
  * `BOOL shouting = [talkToGrandma isEqualToString:shoutAtGrandma];`  
  **Top-tip:** *Remember that* `BOOL`*s are declared* ***without*** *using a* `*` *symbol.*

4 — Write an `if` statement that evaluates `shouting` as its conditional. If the `if` statement passes, print what Grandma says when she (thinks she) hears you: "NO, NOT SINCE 1938!" by using an `NSLog()`:

```objc
if (shouting) {  
    NSLog(@"NO, NOT SINCE 1938!"); 
}
```
5 — Add an `else` statement that prints what Grandma says when she *definitely* can't hear you: "WHAT'S THAT? SPEAK UP, DEAR!" by using an `NSLog()`:

```objc
if (shouting) {  
    NSLog(@"NO, NOT SINCE 1938!"); 
} else {
    NSLog(@"WHAT'S THAT? SPEAK UP, DEAR!");
}
```

* Run your program using `⌘` `R` to see how Grandma replies to what you said to her. If you didn't type your `talkToGrandma` string in all capitals, then you should see `WHAT'S THAT? SPEAK UP, DEAR!` printed to your console.

6 — Change your `talkToGrandma` string declaration to a sentence that's in all uppercase letters:

  *  `NSString *talkToGrandma = @"HI, GRANDMA!";`
  *  Run your program again using `⌘` `R`, you should now see `NO, NOT SINCE 1938!` printed to your console.

### Code-Along II: Direct Evaluation

1 — Add a new version of your `if`/`else` statement that doesn't use the `shouting` boolean, but directly evaluates the result of comparing `talkToGrandma` with `shoutAtGrandma` using the `isEqualToString:` method:

```objc
if ([talkToGrandma isEqualToString:shoutAtGrandma]) {
    NSLog(@"NO, NOT SINCE 1938!");
} else {
    NSLog(@"WHAT'S THAT? SPEAK UP, DEAR!");
}
```

  * Run your program again using `⌘` `R`, you should now see `NO, NOT SINCE 1938!` printed to your console.

2 — Change your `talkToGrandma` string declaration back to a regular sentence containing lowercase letters:

  * `NSString *talkToGrandma = @"Hi, Grandma!";`
  * Run your program again using `⌘` `R`, you should now see `WHAT'S THAT? SPEAK UP, DEAR!` printed to your console.

### Code-Along III: Inverted Check

1 - Add a new version of your `if`/`else` statement from Code-Along I that uses the negation operator (`!`) to invert the evaluation of the `shouting` boolean. Switch the order of your `NSLog()`s so that Grandma still gives the appropriate reply:

```objc
if (!shouting) {
    NSLog(@"WHAT'S THAT? SPEAK UP, DEAR!");
} else {
    NSLog(@"NO, NOT SINCE 1938!");
}
```

  * Run your program again using `⌘` `R`, you should still see `WHAT'S THAT? SPEAK UP, DEAR!` printed to your console.

2 - Add a new version of your `if`/`else` statement from Code-Along II that instead uses the negation operator (`!`) to invert the evaluation of the result of comparing `talkToGrandma` and `shoutAtGrandma` with the `isEqualToString:` method. Switch the order of your `NSLog()`s so that Grandma still gives the appropriate reply:

```objc
if (![talkToGrandma isEqualToString:shoutAtGrandma]) {
    NSLog(@"WHAT'S THAT? SPEAK UP, DEAR!");
} else {
    NSLog(@"NO, NOT SINCE 1938!");
}
```

  * Run your program again using `⌘` `R`, you should still see `WHAT'S THAT? SPEAK UP, DEAR!` printed to your console.

3 — Change your `talkToGrandma` string one last time to an uppercase string (`NSString *talkToGrandma = @"HI, GRANDMA!"`) and run the program using `⌘` `R`. You should see `NO, NOT SINCE 1938!` printed to your console.

### Advanced

Immediately after declaring the `shouting` boolean and setting it to the return from the `isEqualToString:` method, redefine the `talkToGrandma` string back to your regular sentence containing lowercase letters. Also redefine `shoutAtGrandma` to capture the return of the same `uppercaseString` method call:

```objc
NSString *talkToGrandma = @"HI, GRANDMA!";
NSString *shoutAtGrandma = [talkToGrandma uppercaseString];
BOOL shouting = [talkToGrandma isEqualToString:shoutAtGrandma];

talkToGrandma = @"Hi, Grandma!";
shoutAtGrandma = [talkToGrandma uppercaseString];
```

Now run (`⌘` `R`) your program again and see what happens. You should get different print outs by your `if`/`else` statements that evaluated the `shouting` boolean versus your `if`/`else` statements that directly evaluated the comparison with the `isEqualToString:` method:

```
NO, NOT SINCE 1938!            // boolean
WHAT'S THAT? SPEAK UP, DEAR!   // method
```
This is because the `shouting` boolean holds the evaluation of the `isEqualToString:` method from **the point in our code at which it was last set.** Since we changed the `talkToGrandma` and `shoutAtGrandma` strings *after* we set the `shouting` boolean, the result of directly comparing the strings will differ from the result that was captured into the `shouting` boolean above.

Booleans can useful for preserving the result of a comparison from a particular point in your code for later use. But, evaluating a boolean variable instead the direct result of a comparison will not give you a "live" result based on the present state of your code.
