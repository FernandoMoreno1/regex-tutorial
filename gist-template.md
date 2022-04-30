# Learning REGEX

In the following tutorial, you will be learning what regex is all about and how it works. it may seem hard to understand at first but after breaking it down im sure you will have a better understanding of it.

## Summary

Regex, which is short for regular expression, is a sequence of characters that defines a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
### Anchors

There are two anchors in regex which are the ^ and the $. These are used to match a postiton before or after to indentify characters or text.

`^` – The caret anchor matches the beginning of the text.

`$` – The dollar anchor matches the end of the text.
```
For Example:

The sentence "Hello Jhon" can be match by using the following

^Hello          this will match any string starting with "hello"
Jhon$           this will match any string ending with "jhon"

^Hello Jhon$    setting it up together will match the whole phrase "Hello Jhon"
```
### Quantifiers
characters within the regular expression that specify how many times a character or word must show up in the input to be matched.

`*` - The asterisk match a string that has the "input" followed by zero or more of the last character

`+` - The plus sign match a string that has the "input" followed by one or more of the last character

`?` - The question mark match a string that has the "input" follwoed by zero or one of the last character

`{}` - The curly brackets match a string that has the "input" followed by how ever many the number in the brackets of the last character in the string

`()*` - The parentesis match a string that has any "input"  followed by zero or more copies of the string within the brackets

```
For Example:

abc*        matches a string that has ab followed by zero or more c

abc+        matches a string that has ab followed by one or more c

abc?        matches a string that has ab followed by zero or one c

abc{2}      matches a string that has ab followed by 2 c

abc{2,}     matches a string that has ab followed by 2 or more c

abc{2,5}    matches a string that has ab followed by 2 up to 5 c

a(bc)*      matches a string that has a followed by zero or more copies of the sequence bc

a(bc){2,5}  matches a string that has a followed by 2 up to 5 copies of the sequence bc
```
### OR Operator
used to match a letter followed by two different choices between the brackes or between parenthesis divided by the vertical pipe.

`(|)` - matches a string that has any anterior characters followed by the characters on the left or right of the vertical bar

`[]` - matches a string that has any anterior characters without any characters within the brackets
```
For Example:

a(b|c)     matches a string that has a followed by b or c (and captures b or c)

a[bc]      same as previous, but without capturing b or c
```
### Character Classes
tell the regex to match only one specific character/digit.

```
For Example:

\d         matches a single character that is a digit 

\w         matches a word character (alphanumeric character plus underscore)

\s         matches a whitespace character (includes tabs and line breaks)

.          matches any character

\D         matches a single non-digit character

\$\d       matches a string that has a $ before one digit
```
### Flags
used to find specific searches.

`g` - Global, does not return after the first match, which restarted any subsequest searches from the end of the previous match (Makes the expression search for all occurences)

`m` - Multi-line, when enabled the Anchors (^ $) will match the start and end of a line, rather than the whole string

`i` - Insensitive, makes the entire expression case-insensitive

```
For Example:

/Hello/g   matches all `Hello` in the test

/Hello/m   matches the beginning and ending of each line with `Hello`, rather than the whole string `Hello` itself

/Hello/i   matches all `hello` despite case (Hello, hEllo, heLlo, hellO, hello, HELLO all match)
```
### Grouping and Capturing
a pattern or string so that it is matched as a whole.

```
For Example:

a(bc)           parentheses create a capturing group with value bc

a(?:bc)*        using ?: we disable the capturing group

a(?<foo>bc)     using ?<foo> we put a name to the group
```
### Bracket Expressions
characters enclosed by a bracket `[]` matching any single character within the brackets. 

`[]` - matches any single character within the brackets

`[]%` - matches the string inside the brackets before the `%`

`[^]` - matches any string that has a letter from within the brackets
```
For Example:

[xyz]         matches a string that etiher has x or x y or x z (same as x|y|z)

[x-y]         similar to case above

[u-zU-Z0-9]   a string that represents a single hexadecimal digit, case insensitively

[0-9]%        a string that has a character from 0-9 before a %

[^a-zA-Z]     a string that has a letter from a to z or from A to Z                         
```
### Greedy and Lazy Match
characters such as ( * + {}) are greedy operators, so they expand the match as far as they can through the provided text.
```
For Example:
<.+?>         matches any character one or more times included inside < and >, expanding as needed
<[^<>]+>      matches any character except < or > one or more times included inside < and >
```
### Boundaries
Boundaries simply used to either find whole words or none whole words. \b will be used to find whole words and \B will be used to find none whoel words

`\babc\b`          performs a "whole words only" search

`\Babc\B`          matches only if the pattern is fully surrounded by word characters
```
For Example:
\Bb\B              in "abc" will match the b since its not surrounded by word boundaries

\bstack\b          in "foo stack bar" will match since there is nothing connected to "stack"
```
### Back-references
simply does is match the text and save it into different groups depending on your choosing and will match different inputs
```
For Example:

([abc])\1              using \1 it matches the same text that was matched by the first capturing group

([abc])([de])\2\1      we can use \2 (\3, \4, etc.) to identify the same text that was matched by the second (third, fourth, etc.) capturing group

(?<foo>[abc])\k<foo>   we put the name foo to the group and we reference it later (\k<foo>). The result is the same of the first regex

```
### Look-ahead and Look-behind
simply matches a charcater based on if the letter inside the expression comes before or after the letter that is infront of the expression

```
For Example:

d(?=r)       matches a d only if is followed by r, but r will not be part of the overall regex match

(?<=r)d      matches a d only if is preceded by an r, but r will not be part of the overall regex match

You can use also the negation operator!

d(?!r)       matches a d only if is not followed by r, but r will not be part of the overall regex match

(?<!r)d      matches a d only if is not preceded by an r, but r will not be part of the overall regex match

```
## Author
Fernando Moreno is a junior developer currently enrolled in Rutgers Coding Bootcamp, to become a full stack web developer and break into the tech industry.

[GitHub Profile](https://github.com/Fernandomoreno1)