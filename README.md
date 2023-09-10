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



### Grouping and Capturing



### Bracket Expressions



### Greedy and Lazy Match



### Boundaries


### Back-references


### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
