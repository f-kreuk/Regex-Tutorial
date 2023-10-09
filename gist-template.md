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

In regular expressions, OR operators are denotated using the vertical line (|) symbol. The URL validation regular expression above does not readily utilize any OR operators; however, they can be better understand when looking at the domain name element of the URL. For example, in ([\da-z\.-]+), the "a-z" represents [abcdefghijklmnopqrstuvwxyz] or alternatively [a|b|c|d|e|f|g|h|i|j|k|l|m|n|o|p|q|r|s|t|u|v|w|x|y|z]. 


### Character Classes

Character classes are often orgnized with opening and closing square brackets and define a set of characters, any one of which can occur in an input for the match to succeed.

/^(https?:\/\/)?(<strong>[\da-z\.-]</strong>+)\.(<strong>[a-z\.]</strong>{2,6})(<strong>[\/\w \.-]</strong>*)*\/?$/

Our URL validation regular expression above demonstrates a number of character classes:

1. (<strong>[\da-z\.-]</strong>+): In this example, "\d" is a digit character, which includes the standard digits of 0 to 9; "a-z" matches any lowercase characters from a to z; "\." is a literal period character with a backslash used to escape it; and "-" is a literal hyphen character. Note: in regular expressions, certain characters have special meanings, and if you want to match them literally, then you need to escape them with a backslash. By default, the "." is used as a wildcard, and in order to use it literally, you must escape it.
2. (<strong>[a-z\.]</strong>{2,6}): In this example, "a-z" matches any lowercase characters from a to z and "\." is a literal period character.
3. (<strong>[\/\w \.-]</strong>*)*\/?: In this example, "\/" is a literal forward slash character; "\w" represents a word character, which includes upper and lowercase letters, digits, and underscores; " " is a literal space character; "\." is a literal period character; and "-" is a literal hyphen character.


### Flags

A regular expression flag is an optional parameter that modifies its behavior of searching. In JavaScript regular expressions, there are six flags:

1. Ignore Casing (i): Makes an expression look for its matches while ignoring chracter casing.
2. Global (g): Makes an expression look for all its matches, rather than stopping at the first one.
3. Dot All (s): Makes the dot (.) character meatch everything, even newlines.
4. Multiline (m): Makes the caret (^) and money ($) anchor tokens match the beginning and end of each line.
5. Sticky (y): Makes an expression search from the position specified in its lastIndex property.
6. Unicode (u): Makes an expression treat characters in a given test string as code points, rather than code units.


### Grouping and Capturing

Grouping is a useful feature of regular expressions that is capable of simplifying complex patterns. Any subpattern enclosed within parentheses () is a group. We have already been looking at various groups within our URL validation regular expression, namely:

* (https?:\/\/)
* ([\da-z\.-]+)
* ([a-z\.]{2,6})
* ([\/\w \.-]*)


### Bracket Expressions

A bracket expression is an expression enclosed in square brackets used to create flexible and specific patterns for matching characters in regular expressions. A bracket expression allows you to define a set of characters to match at a specific position in a string. We have already been looking at various bracket expressions within our URL validation regular expression, namely:

* [\da-z\.-]
* [a-z\.]
* [\/\w \.-]


### Greedy and Lazy Match

By default, a quantifier is <strong>greedy</strong> and tells the engine to match its subpattern or quntified token with as many instances as possible. For example, with the plus sign (+) quantifier in our example: ([\da-z\.-]+), we are matching one or more characters within the domain name of the URL, which consists of digits, lowercase letters, periods, or hyphens. If a greedy quantifier in this context is matching the domain of "google" starting from the left position, g, go, goo, goog, googl, or google would constitute a match. Notwithstanding, because the default quantifier is greedy, as many digits are matched as possible, and the longest match is returned, i.e. "google". 

A <strong>lazy</strong> quantifier, on the other hand, tells the engine to match as few quantified tokens as possible. A regular expression is made lazy by appending a question mark (?) to it. If we were to add a question mark following the plus sign quantifier in our previous example, i.e. ([\da-z\.-]+<strong>?</strong>), then lazily matching the domain of "google" starting from the left position would simply return "g", as the smallest match returned.

### Boundaries

Boundaries are similar to anchors in that they are assertions about the engine's current position in the string. As seen above, anchors assert that the current position in a string matches a certain position, i.e. the beginning or the end. A boundary, on the other hand, makes assertions about what can be matched to the left or right of the current position.

### Back-references

Back-references can be leveraged to use the contents of capturing groups in the pattern itself. Namely, it allows you to refer back to a portion of text that you already matched within the regular expression. Back-references are generally in the form of a backslash followed by a number, i.e. "\1" or "\2", where the number corresponds with the of-interest capturing group.

In our example, we have four possible back-references, including:

1. \1: (https?:\/\/)
2. \2: ([\da-z\.-]+)
3. \3: ([a-z\.]{2,6})
4. \4: ([\/\w \.-]*)

### Look-ahead and Look-behind

Look-aheads and look-behinds are useful tools/tests within regular expressions that facilitate the finding of matches for patterns followed or preceded by other patterns. 

A positive lookahead assertion, i.e. "goo(?=gle)" will match "goo" only if its immediately followed by "gle", which is not included in the match. As demonstrated in this example, a positive lookahead assertion checks if a pattern follows the current position without including that pattern in the match. A negative lookahead assertion, i.e. "goo(?!gle)", will match "goo" as long as it is not followed by "gle" (like in goober, goose, etc.).

A positive lookbehind assertion, on the other hand, checks if a certain pattern precedes the current position without including that pattern in the match. For example, "(?<=goo)gle" will match "gle" when preceded by "goo". A negative lookbehind assertion, i.e. "(?<!goo)gle" will match "gle" only if not preceded by "goo" (like in eagle, angle, etc.).

## Author

This tutorial was created as part of the 2023 UCONN Full Stack Coding Bootcamp. For more information about the author of this post, please visit his GitHub portfolio: https://github.com/f-kreuk.
