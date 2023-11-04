# Regex Tutorial

A regex, which is short for regular expression, is a sequence of characters that defines a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input.

It is a technique commonly developed in theoretical computer science.

## Summary

The below code will be used throughout this tutorial to give specific examples for how the components of regex can be used. For example, the following regular expression can be used to verify that user input is a valid email address. This tutorial will follow the different components of regular expressions.

Matching Email-

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
The anchor is what starts and ends the regular expression. 

In the matching email code, 

`/^`([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})`$/`, 

the anchors are the `^` and the `$`, which are highlighted. The caret `^` defines the beginning of the string and the dollar sign `$` defines the end of the string.

This code specifically is saying that we are looking for something that starts with 

`^([a-z0-9_\.-]+)` 

what the anchor means is that if we are to find a match it has follow those initial guidelines. It also has to end with 

`.([a-z\.]{2,6})$`.

So, it must start and end with the given parameters within the code. 


### Quantifiers

A quantifier is a repitition operator. Quantifiers let the system know to match the preceding token a set number of times. It is used to determine how many times a specific character or group of characters needs to be present in order to have a match.

For instance, if we used the following code in our regex, xyz+ then this will match any string xy followed by at least one z. So, if we look at our code for matching the email:

`([a-z0-9_\.-]+)`

this will match any string that contains a-z, 0-9, _, ., or -. The quantifier + means that it has to contain at least one of this in order to have a match.

The following are examples of quantifiers that are not found in our example:

* The star `*` will match zero or more of the preceding token.
* The question mark `?` will match zero or one of the preceding token. This makes said token optional. It also makes the preceding quantifier lazy.

### OR Operator

It is not present in the code for the given matching email code, but in order to talk about the OR Operator `|`, we will look at the following code for matching a hex code.

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

The pipe `|` is considered an alternation. It matches the expression before or after it. This quantifier can affect specific characters, or a whole expression. 

What this will do is it will match where it starts with the # and that has to come first followed by one of the following:

`[a-f0-9]{6}` which will match a 6 character long string that contains a combination of a-f letters and 0-9 numbers.

`|` OR Operator

`[a-f0-9]{3}` it will match a 3 character long string that contains a combination of a-f letters and 0-9 numbers.

### Character Classes

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

`\d` is present in the given matching email code and what it will match a single letter character, a-z, after the `@` sign in the email address. Basically ensuring that a letter is matched after the `@ `in the email and not a number or special character.

The following are additional examples of character classes that are not found in our example:

* A negated set contains a caret first thing within the square brackets `[^ABC]` and matches any character that is not in the set.
* A `.` will match any character except line breaks. The . in our example actually refer to actually periods, and are not a character class.
* Match any `[/s/S]` will match any character.
* Word `/w` will match any word.
* Not word `/W` will match any character that is not a word.
* Digit `/d` matches any number.
* Not digit `/D` will match any character that is not a number.
* Whitespace `\s` will match any character that leaves whitespace (spaces, tabs, line breaks, etc.).
* Not whitespace `\S `will match any character that is not a whitespace character.

### Flags

There are no regex flags in our example. Flags will always follow the closing forward slash of an expression, and change how it is interpreted.

However, the following are some examples.

* Ignore case `i` will make the entire expression case-sensitive. So capitals and lower-case letters will not deture the matching.
* `g` which stands for "global" which will allow for matching all the instances within a string that follow the matching guidelines set in the regular expression..
* Multiline `m` will cause the beginning and end anchors to match the start and end of a line instead of the whole string.It will search line by line rather than searching through a string as a whole.
* Unicode `u` allows extended unicode escapes in the form `\x{FFFFF}`.
* Sticky `y` will only match from its last index position and ignores the global search flag.
* Dotall `s` causes dot (.) to match any character.

### Grouping and Capturing

Groups allow a group of tokens to be combined to operate on them together. In the below regex  code for matching an email:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Capturing group `(ABC)` groups multiple tokens together for extracting a substring

`([a-z0-9_\.-]+) `is the first group that appears in our regex. This must be true before moving on to "match" the next part of the code. `([\da-z\.-]+)` is the second group that appears in our regex. `([a-z\.]{2,6})` is the third group that appears in our regex.

When matching, we have to make sure we are following the guidelines of the group before moving on to the next group.

### Bracket Expressions

In the below regex  code for matching an email:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

We can talk about Bracket Expressions.

`[a-z0-9_\.-]`

The guidelines for matching the group. In this code snippet, it can contain letters a-z, numbers 0-9, an underscore, hyphen, or period. The period is an escaped character, so it required the backslash in order to be able to be matched. 

### Greedy and Lazy Match

In the given regex for matching an email, there isn't a greedy or lazy match included.

Quantifers can be either greedy or lazy. A greedy quantifer will attempt to match as many characters as possible as it goes backwards through the regex string. A lazy quantifier will attempt to match as few characters as possible as it goes back through the regex string. By default, quantifiers are greedy unless affected by another quantifier.

### Look-ahead and Look-behind

A look-ahead or look-behind has to match in a certain order.  Lookarounds will match a group of characters either before or after a pattern, but will allow for it to not be included as part of the result. Lookbehinds are specific for groups that are before the pattern, and lookaheads are for groups after the pattern.

The given regex for matching an email does not contain lookarounds; however, the following are some examples.

* A positive lookahead, (?=ABC), will match a group after the pattern without including it in the result.
* A negative lookahead, (?!ABC), will specify a group that cannot match after the pattern; otherwise, the result is unsuccessful.
* A positive lookbehind, (?<=ABC), will match a group before the pattern without including it in the result.
* A negative lookbehind, (?<!ABC), will specify a group that cannot match before the pattern; otherwise, the result is unsuccessful.

## Author

This tutorial was developed by Sajith Aravindan, who loves coding! Please feel free to check out his GitHub at [GitHub](https://github.com/SajithAravindan).


