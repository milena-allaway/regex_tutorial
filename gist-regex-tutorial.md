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
^ - matches the beginning of the string, here it indicates that the URL can start with an optional protocol of http:// or https://
```
/^(https?:\/\/)?
```
$ - matches the end of the string, here it indicates that the URL can end with and optional forward slash
```
\/?$/
```

### Quantifiers

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

Written by Milena Allaway, Full Stack Student at University of Toronto.
[Link to my GitHub](https://github.com/milena-allaway)
