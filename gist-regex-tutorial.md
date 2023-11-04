# Matching a URL - Regex Tutorial

This tutorial will explain in detail how a regular expression (regex) works to match a URL. The intention of this tutorial is to help understand the search pattern the regex defines and its components.

## Summary

The following regex defines a search pattern for a URL that can start with http:// or https://, follwed by a domain name that can contain one or more numbers, lowercase letters, dots and hyphens, followed by a dot, then a top-level domain which can be a set of lowercase letters and/or dots that can be between 2 and 6 characters long. The URL can end with an optional path defined by a slash followed by a set of any alphanumeric characters (word characters), dots, and hyphens, there can be multiple occurences of such path, or it can optionally end with just a slash.
```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```




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

Anchors are used to match a position before or after characters. The regex in question uses the following anchors:  
**^** - matches the beginning of the string, here it indicates that the URL can start with an optional protocol of http:// or https://
```
/^(https?:\/\/)?
```
$ - matches the end of the string, here it indicates that the URL can end with and optional forward slash
```
\/?$/
```
Accepted examples:
```
http://example.com or https://example.com/example/ or example.ca/

```
### Quantifiers

Quantifiers are used to match a specific number of characters. The regex in question uses the following quantifiers, in order of appearance:  
**?** - matches the preceding character 0 or 1 time.  
Here it indicates that the protocol can be either http:// or https://,  as indicated by its position after the 's' in https, or the protocol can be omitted all together as indicated by its position after the closing parenthesis.
```
/^(https?:\/\/)?
```
Accepted examples:
```
http://example.com or https://example.com or example.com
```

**+** - matches the preceding character 1 or more times. Here it indicates that the domain name can contain one or more numbers, lowercase letters, dots and hyphens.
```
([\da-z\.-]+)
```
Accepted examples:
```
example.com or example123.com or example-123.com or example.123.com or e.com or 12.34-56.com
```
Not accepted examples:
```
Example.com or example_123.com or example!123.com or http://.com
```

**{2,6}** - matches the preceding character between 2 and 6 times. Here it indicates that the top-level domain must be between 2 and 6 characters long.
```
([a-z\.]{2,6})
```
Accepted examples:
```
example.com or example.ca or example.co.uk
```
Not accepted examples:
```
example.c or example.co.uk.org
```

**\*** - matches the preceding character 0 or more times. Its position after the closing square bracket indicates that the path can contain 0 or more forward slashes, word characters, dots, and hyphens. The "*" after the closing parenthesis indicates that the path can be omitted all together or it can have multiple occurences.
```
([\/\w \.-]*)*
```
Accepted examples:
```
example.com or example.com/example or example.com/example/example
```

**?** - matches the preceding character 0 or 1 times, seen again near the end.  
 Here it indicates that the path can end with an optional forward slash, or it can be omitted all together.
```
\/?$/
```
Accepted examples:
```
.com or .com/ or .com/example or .com/example/example or .com/example/example/
```

### OR Operator

The OR operator is used to match one of two or more expressions, separated by the pipe character |. The regex in question does not use the OR operator. But here is an example of how it can be used to match one of three top-level domains:
```
(com|net|org)
```

### Character Classes

Character classes are used to match characters from a specific set or by their literal selves. Sets are defined by square brackets []. Literal characters are preceded by a backslash \ and are exact matches (\. is a literal dot).  
Meta-characters are characters that have a special meaning like \d (numbers 0-9), \w (word characters, alphanumeric including underscores, spaces, dots, or hyphens), \s (whitespace like spaces, tabs, and line breaks), and . (any character except line breaks).
The regex in question uses the following character classes:  
**\d** - matches any digit character (0-9). Here it indicates that the domain name can contain one or more numbers.
```
([\da-z\.-]+)
```
Also part of the character class above,  
**a-z** matches any lowercase letter, and  
**\.-** matches a dot or a hyphen.  
Meaning that the domain name can contain one or more numbers, lowercase letters, dots and hyphens.

Accepted examples:
```
example.com or example123.com or example-123.com or example.123.com
```
Not accepted examples:
```
Example.com or example_123.com or example!123.com
```
The top level domain is defined by the following character class:
```
[a-z\.]
```
**a-z** matches any lowercase letter, and  
\. matches a literal dot.

Accepted examples:
```
example.com or example.ca or example.co.uk
```
Not accepted examples:
```
example.123 or example.COM
```
The path is defined by the following character class:
```
[\/\w \.-]
```
**\/** matches a literal forward slash,  
**\w** matches any word character (alphanumeric including underscores), also the class can include dots, and/or hyphens.  

Accepted examples:
```
.com/example or .com/123_example or .com/e-x-a-m-p-l-e or .com/
```
The path can then be ended by an optional literal forward slash, or it can be omitted all together, as indicated by the following character class:
```
\/?
```
Accepted examples:
```
.com or .com/ or .com/example or .com/example/example or .com/example/example/
```

### Flags
Flags are used to perform different types of searches. The regex in question does not use any flags. The two most common flags are:  
**g** - global search, searches for all matches rather than stopping after the first match.  
**i** - case-insensitive search, searches for both uppercase and lowercase matches.
Example:
```
var regex = /[a-z]+/g;
```

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

Written by Milena Allaway, Full Stack Student at University of Toronto.
[Link to my GitHub](https://github.com/milena-allaway)
