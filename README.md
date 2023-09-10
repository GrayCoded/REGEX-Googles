# Welcome to REGEX with GreyCoded!

Thank you for taking your first steps to being a better developer. Through this readme and tutorial. I have include source material that will help in understanding the different facets of REGEX.

<a id='regex'></a>

 Below is an example of a REGEX you may have encountered or seen before without quite undersatnding what it truly is or does.

```JS
const urlRegex =  /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
```
## Summary

Regular expressions are commonly in web development for checking user input. They are also used to validate email addresses, phone numbers, and URLs. Through this tutorial you will learnn about the individual components of regular expressions.

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
Anchors are used at the beginning and end of a string. Below are examples of 2 anchors.

```JS
//Matches a string that starts with '^'
 ^(https?:\/\/)

//Matches a string that ends with '$'
([\/\w \.-]*)*\/?$
```
 >`^` This is the caret (^) symbol at the beginning of the regular expression. It is the start-of-line anchor, which ensures that the matching process starts at the beginning of the input string. In other words, it anchors the match to the start of the string.

 >`$` This is the dollar sign ($) at the end of the regular expression. It is the end-of-line anchor, which ensures that the matching process ends at the end of the input string. In other words, it anchors the match to the end of the string.

### Quantifiers

In the regular expression [above](#regex) there are many quantifiers. Lets go over them.

Specifies that anything preceding the `?` is optional

```JS
(https?:\/\/)?
```

Specifies that the element preceding the `+` should occur one or more times.

```JS
([\da-z\.-]+)
```

Specifies that the preceding element should occur at least "min" times and at most "max" times.

```JS
{2,6}
```

Specifies that the  element preceding `*` can occur zero or more times.

```JS
([\/\w \.-]*)*
```

These quantifiers control the repetition and optionality of different elements within the regular expression, allowing it to match various forms of URLs while accommodating different configurations of protocol, domain name, TLD, and path.

### OR Operator

In the regular expression [above](#regex) there are no logical OR Operators. However, the use of parentheses and the `?` quantifier effectively creates optional alternatives, simulating an "OR" behavior for certain parts of the regular expression.

This is an example of an logical OR operator `|`.

```JS
(https?:\/\/)?
```

This part represents an optional protocol at the beginning of the URL. The `?` quantifier makes the "s" after "http" (indicating "https") optional. So, it effectively matches either "http://" or "https://", providing an "OR" choice between them.


```JS
([\/\w \.-]*)*
```

This part represents an optional path in the URL. The `*` quantifier allows for zero or more occurrences of characters within the brackets, including forward slashes, word characters, spaces, dots, and hyphens. This allows for an "OR" choice of having a path or not having a path in the URL.

>These elements create conditional alternatives within the regular expression, allowing it to match URLs with or without a specified protocol and with or without a path. While they don't use explicit `|` symbols to denote "OR," they achieve similar functionality by making certain parts of the expression optional.

### Character Classes

In the regular expression [above](#regex) there are character classes used with in brackets`[]`.

This character class matches a single character that can be one of the following

```JS
\d
```
Matches Any digit (0-9).

```JS
a-z
```
Matches any lowercase letter from 'a' to 'z'.

```JS
\.  -
```
Matches A period (dot) or a hyphen.

### Flags

In the regular expression [above](#regex) there are no flags used but here are some examples of flags.

```JS
`i`
```
Case-insensitive matching. When this flag is used (e.g., `/regex/i`), the regular expression will match both uppercase and lowercase characters without distinction.

```JS
`g`
```
Global matching. When this flag is used (e.g., `/regex/g`), the regular expression will find all matches in the input string rather than stopping after the first match.

```JS
`m`
```
 Multiline matching. When this flag is used (e.g., `/regex/m`), `^` and `$` anchors will match the start and end of each line within a multi-line input string, rather than just the start and end of the entire string.

```JS
`s`
```
Dot-all mode. When this flag is used (e.g., `/regex/s`), the `.` character in the regular expression will also match newline characters (`\n`), which is not the default behavior.

```JS
`u`
```
Unicode matching. When this flag is used (e.g., `/regex/u`), the regular expression will work with Unicode characters and properties.

```JS
`y`
```
 Sticky matching. This flag indicates that the regular expression should only search from the last match position onwards in the input string.

>NOTE: The availability and behavior of these flags may vary depending on the programming language or regex library you are using.

### Grouping and Capturing

In the regular expression [above](#regex) there are several groups and captures defined by parentheses `()`.

```JS
`(https?:\/\/)?`
```
This capturing group encloses the protocol part of the URL, which can be either "http://" or "https://". The `?` after the group makes it optional.

```JS
`([\da-z\.-]+)`
```
This capturing group encloses the domain name part of the URL. It captures a sequence of characters that can include lowercase letters, digits, dots (.), and hyphens (-).

```JS
`([a-z\.]{2,6})`
```
This capturing group encloses the top-level domain (TLD) part of the URL. It captures a sequence of lowercase letters and dots (.) with a length between 2 and 6 characters.

```JS
`([\/\w \.-]*)*`
```
This capturing group encloses the path part of the URL. It captures a sequence of characters that can include forward slashes (/), word characters (\w), spaces, dots, and hyphens. The `*` at the end allows for zero or more characters in the path.

>NOTE: These capturing groups are used to extract and capture specific portions of the URL from the input string when a match is found. This allows you to access and work with the protocol, domain name, TLD, path, and other parts of the URL separately in your code.

### Bracket Expressions

Bracket expressions, also known as character classes, are used in regular expressions to specify a set of characters that can match at a particular position in the input string. Bracket expressions are enclosed in square brackets `[...]` and allow you to define a character set or a range of characters that should be considered a valid match.

In the regular expression [above](#regex) there are several bracket expressions defined under the [character classes](#character-classes) and captures defined by parentheses `()`.

### Greedy and Lazy Match

The regular expression [above](#regex) does not explicitly use greedy or lazy quantifiers. Instead, it relies on the default greedy behavior of quantifiers.

In this regular expression, you can find quantifiers like `*` and `?`, but they are not made lazy with the `?` modifier. Here's how they behave:

```JS
`*` (asterisk)
```

 The `*` quantifier is greedy by default. It matches as many characters as possible while still allowing the overall pattern to match. For example, in `[\da-z\.-]+`, the `+` (which is one or more) is also greedy, so it will match as many characters as possible from the character class `[\da-z\.-]`.

```JS
`?` (question mark)
```

 The `?` quantifier, when used after another quantifier like `*?` or `+?`, makes that quantifier lazy, but in this expression, it's not applied to any quantifiers. For example, `([\/\w \.-]*)*` uses `*` without `?`, so it is also greedy.

>NOTE: In this expression, without the `?` modifier after any quantifiers, the default behavior is to be greedy, matching as much as possible while still allowing the overall pattern to match. If you have specific requirements for lazy matching in this regex, you would need to modify the quantifiers accordingly.

### Boundaries

The regular expression [above](#regex) does use boundary assertions. Here is what assertions are in this expression.

>Start-of-Line Anchor ^

The ^ symbol at the very beginning of the regex, /^(https?://)?..., is a start-of-line anchor. It asserts that the match must begin at the start of a line or the start of the input string.

>End-of-Line Anchor $

The $ symbol at the end of the regex, .../?$/, is an end-of-line anchor. It asserts that the match must end at the end of a line or the end of the input string.


### Back-references

The regular expression does not have any back-references. However, here is an example.

 ```JS
 `\1`, `\2`, etc.
 ```
 These refer to the first, second, third, etc., capturing group in your regular expression pattern.

   - `\1` refers to the text captured by the first capturing group.
   - `\2` refers to the text captured by the second capturing group.
   - And so on.


>NOTE: Back-references are a powerful feature in regular expressions, allowing you to perform more complex matching tasks, such as finding repeated words, validating repeated patterns, and more.


### Look-ahead and Look-behind

Look-ahead and look-behind assertions are advanced features in regular expressions that allow you to check for the presence or absence of certain patterns ahead of or behind the current matching position without including that text in the match itself. They are also known as zero-width assertions because they do not consume characters in the input string.

Positive Look-ahead Assertion ((?=...)):

```JS
//Example:
 /apple(?=s)/ would match "apple" only if it's followed by "s."
```
This assertion checks whether a pattern is present immediately after the current position.
Syntax: X(?=Y), where X is the pattern you want to match, and Y is the condition that must be satisfied.

Negative Look-ahead Assertion ((?!...)):

```JS
//Example: 
/apple(?!s)/ would match "apple" only if it's not followed by "s."
```

This assertion checks whether a pattern is not present immediately after the current position.
Syntax: X(?!Y), where X is the pattern you want to match, and Y is the condition that must not be present.

Positive Look-behind Assertion (?<=...):

```JS
//Example: 
/(?<=\$)\d+/ would match a sequence of digits that are preceded by a dollar sign, like "$100."
```
This assertion checks whether a pattern is present immediately before the current position.
Syntax: (?<=Y)X, where X is the pattern you want to match, and Y is the condition that must be satisfied.


Negative Look-behind Assertion (?<!...):

```JS
//Example: 
/(?<!\$)\d+/ would match a sequence of digits that are not preceded by a dollar sign.
```
This assertion checks whether a pattern is not present immediately before the current position.
Syntax: (?<!Y)X, where X is the pattern you want to match, and Y is the condition that must not be present.

>NOTE: Look-ahead and look-behind assertions are useful for specifying complex conditions when you want to ensure that certain patterns exist or do not exist before or after the main pattern you're trying to match. They are particularly valuable in situations where you need to extract or validate data based on context.

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
