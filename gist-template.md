# RegEx URL Validation

This tutorial will walk you through a basic URL validation using the below regular expression.

/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

## Summary

This regular expression is designed to validate URLs with:
* (https?:\/\/)?    | an optional HTTP/HTTPS protocol;
* ([\da-z\.-]+)     | a domain name consisting of letters, numbers, dots, and hyphons;
* \.                | a literal dot character, separating the domain from the top-level domain;
* ([a-z\.]{2,6})    | a valid top-level domain with a length of 2-6 characters; and
* ([\/\w \.-]*)*\/? | an optional path and optional trailing slash.


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

/<strong>^</strong>(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?<strong>$</strong>/

The emboldened caret (^) and dollar ($) symbols above represent anchors within our regular expression. The caret matches the beginning of the text, and the dollar matches the end. Both anchors together (^...$) are utilized to test whether a string matches a specific regex pattern.

### Quantifiers

Quantifiers are utilized to quantify the number of times an element of the regular expression should be repeated. Quantifiers are written after elements of the regular expression to specify how many times it should be repeated. Common quantifiers include the question mark (?), asterisk (*), plus sign (+), and a range quantifier, i.e. {N,M}.

/^(https<strong>?</strong>:\/\/)<strong>?</strong>([\da-z\.-]<strong>+</strong>)\.([a-z\.]<strong>{2,6}</strong>)([\/\w \.-]<strong>*</strong>)<strong>*</strong>\/?$/

Our URL validation regular expression above demonstrates a number of common quantifiers:

1. (https<strong>?</strong>:\/\/)<strong>?</strong>: The question mark makes the element optional. This element matches the protocol part of the URL, which is either https:// or http://. The question mark after the s makes the "s" optional. The question mark after the entire group makes the entire group optional, thereby allowing URLs without a designated protocol.
2. ([\da-z\.-]<strong>+</strong>): The plus sign means that this element is one or more characters. This element matches the domain name of the URL, which consists of digits, lowercase letters, periods, or hyphens.
3. ([a-z\.]<strong>{2,6}</strong>): The {2,6} range quantifier means the preceding element is repeated 2 to 6 times. This element matches the top-level domain. The element in brackets specifies that the content must consist of lower case letters and dots. The range quantifier then specifies that the top-level domain must consist of between 2 and 6 characters. This is consistent with common top-level domains like ".com" or ".org".
4. ([\/\w \.-]<strong>*</strong>)<strong>*</strong>\/?: The aterisk allows for zero or more occurrences of the preceding pattern, which means the path is optional. This element matches 0 or more characters that can consist of a forward slash, letters, digits, underscores, spaces, dots, or hyphens. The asterisk quantifier allows for zero or more occurrences of the preceding pattern.

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

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
