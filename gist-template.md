# Title (Regular Expression Tutorial)

Introductory (This is regular expression tutorial for beignners to get some insight into how a search text or pattern occurrence could be easily found in a search string.)

## Summary

This tutorial intends to cover range of technical aspects as listed below with example code and its meaningful usage in a particular context.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

#### Start (^) - Caret Symbol enforces match has to occur at the start of a line with character or characters followed after the symbol

```
Example Code : ^#?([a-f0-9]{6}|[a-f0-9]{3})$
```
##### Matching Examples : Hexadecimal numbers OR # symbol followed by hexadecimal characters  

- 232EDF 
- #123099 
- 324 
- #fffdef

##### Explanation: Start of the matching line has to be ZERO or ONE occurrence of '#' character and hexadecimal characters as mentioned in the character class in square brackets.  

##### Non-Matching Examples : Hexadecimal numbers OR # OR Both at the start of the line

- se
- ##45 
- 2345p
- #12345 453

#### End ($) - Dollar synbol enforces expected match has to occur at end of the line with characters preceding the symbol

```
Example Code : ^#?([a-f0-9]{6}|[a-f0-9]{3})$
```
##### Matching Examples : Hexadecimal numbers OR # symbol followed by hexadecimal characters  

- 232abc 
- #123011 
- 345 
- #fffdef

##### Explanation: End of the line has to be hexadecimal characters as mentioned in the character class in square brackets.  

##### Non-Matching Examples : Hexadecimal characters at end of the line

- 12re
- ##12rt 
- 2345p
- #12345n

#### Word Boundary : To be Covered later on

### Quantifiers

#### * Asterisk Symbol represents preceding pattern or group of charaters can occur ZERO or more times 

```
Example Code : ^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w\.-]*)*\/?$
```

##### Matching Examples : In below example a URI is being matched ZERO or N number of times at the end of the URL.  

- http://tesla.com
- http://tesla.com.au/
- http://tesla.com32/12
- http://tesla.com/test/21312/p

##### Explanation: In above example URI occurs one or more times with any number of word characters hyphen(-) and dot(.)      

#### + Plus symbol matches the pattern one or more times

```
Example Code : ^#+([a-f0-9]{6}|[a-f0-9]{3})$
```
##### Matching Examples : # Symbol can be one or more time followed by hexadecimal characters  

- #232edf 
- #1230  
- #fffdef

##### Explanation: # symbol can be one or more time as enforced by plus symbol   

#### ? Question Mark symbol matches the pattern zero or one time

```
Example Code : ^#?([a-f0-9]{6}|[a-f0-9]{3})$
```
##### Matching Examples : # Symbol can be ZERO or one time followed by hexadecimal characters  

- 232EDF 
- #123099 
- 324 
- #fffdef

##### Explanation: # symbol can be one or zero time as enforced by question mark   

#### { n } matches the pattern exactly n number of times

```
Example Code : ^#+([a-f0-9]{6}|[a-f0-9]{3})$
```

##### Matching Examples : In below example hexdecimal chracters preceded by # symbol can occur exactly 3 times or 6 times as respresented by a number in curly braces {6} and {3}.  

- ###a45322
- #a45
- #a453ed
- #123

##### Explanation: In above examples hexadecimal characters has to occur either 6 times ([a-f0-9]{6} or  3 times[a-f0-9]{3}. 

#### { n, } matches the pattern at least n number of times

```
Example Code : [1-9]{1}\d{4,}
```

##### Matching Examples : Above code enforces a minimum 5 digit number or greater. 

- 111111
- 111111 11111
- 99991
- 11122 222232

##### Explanation: Quantifier used in this example for first digit is curly bracket with exact number of digits being 1 {1} between 1 and 9. The second quantifier is curly bracket with min value of 4 and max value of none {4, } which makes it any number acceptable if it is greater than four digits and less than 9 digits. 

#### { n, x } matches the pattern from a minimum of n number of times to a maximum of x number of times

```
Example Code : ^(https?:\/\/)?([\da-z\.-]+)\.([a-z]{3,6})$
```

##### Matching Examples : Above code enforces a valid URL with domain name ending between 3 and 6 alphabet characters.  

- https://tesla.com
- http://tesla.com
- https://tesla.gbr
- https://tesla.net
- https://tesla.online

##### Explanation: Quantifier used in this example is curly bracket with min value of 3 and max value of 6 alphabets characters {3, 6}.

### Grouping Constructs

```
Example Code : ^(https?:\/\/){1}([\da-z-]+)\.([a-z]{3,6})$
```

##### Matching Examples : Above code enforces three groups of characters in valid URL with below examples using parenthesis followed by quantifiers applied on the whole group. The second group enforces domain name part of the URL with code being ([\da-z-]+) having alphanumeric characters and hyphen in that. The third part of the    

- https://tesla.com
- http://tesla.com
- https://tes2la.gbr
- https://tesla.net
- https://tesla1.online

##### Explanation: There are three groups used in above code with first group enforcing "http://" or "https://" part of the URL with code being (https?:\/\/){1}. The second group ([\da-z-]+) enforcing alphanumeric or hyphen(-) characters to validate domain name. Before third group a dot(.) is required. The third group is ([a-z]{3,6}) which validates for three to 6 alphabet characters like com, itr, tes, net online etc.         

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

- [Sanjeev Kumar](https://github.com/SanjeevKumar-DEV)