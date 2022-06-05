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

##### Matching Examples : Above code enforces three groups of characters in valid URL with below examples using parenthesis followed by quantifiers applied on the whole group. The second group enforces SLD(Sub level domain) part of the URL with code being ([\da-z-]+) having alphanumeric characters and hyphen in that. The third part of the group enforces TLD (top level domain) part of the URL.      

- https://tesla.com
- http://tesla.com
- https://tes2la.gbr
- https://tesla.net
- https://tesla1.online

##### Explanation: There are three groups used in above code with first group enforcing "http://" or "https://" part of the URL with code being (https?:\/\/){1}. The second group ([\da-z-]+) enforcing alphanumeric or hyphen(-) characters to validate domain name. Before third group a dot(.) is required. The third group is ([a-z]{3,6}) which validates for three to 6 alphabet characters like com, itr, tes, net online etc.         

### Bracket Expressions

```
Example Code : ^(https?:\/\/){1}([\da-z-]+)\.([a-z]{3,6})$
```

##### Matching Examples : The second group of code in above URL in square[] bracket enforces SLD(Sub level domain) part of the URL with code being [\da-z-]+

- https://tesla.com
- http://tesla.com
- https://tes2la.gbr
- https://tesla.net
- https://tesla1.online

##### Explanation: The second group [\da-z-]+ enforcing alphanumeric or hyphen(-) characters to validate domain[Second level domain] name with number of occurrence being 1 or more. Characters in the bracket have OR relationship in terms of match finding. Therefore it can be read as any digit or any alphabet or hyphen with + symbol after the bracket being the quantifier. 

### Character Classes

```
Example Code : ^(https?:\/\/){1}([\da-zA-Z]+)\.([\w]{3,6})$
```

##### Matching Examples : The second group of code in above URL in square[] bracket enforces SLD(Sub level domain) part of the URL with code being [\da-zA-Z]+ and third group [\w] as an example of character classes usage. There are mainly 5 groups of character classes. dot(.) represents any character, \d represents any digit from 0 to 9, \w any alphnumeric character including underscore, a-z any alphabet non-capital letters, A-Z any alphabet capital letters, 0-9 any digits from 0 to 9, \s any space character whitespace, TABS, line breaks, newlines   

- https://teslW.com_
- http://tesla.com_P
- https://tes2Ma.gbr
- https://tesla.net
- https://tesla1.online

##### Explanation: The second group [\da-zA-Z]+ enforcing alphanumeric characters capital or non-capital to validate domain[Second level domain] name with number of occurrence being 1 or more with examples being (teslW, tes2Ma, tesla1). The second example [\w] denotes any alphanumeric character including underscore in TLD domain name as in above examples (com_, com_P). 

### The OR Operator

```
Example Code : ^(https?:\/\/){1}(\d|[a-z]|[A-Z]|-)+\.([\w]{3,6})$
```

##### Matching Examples :  Second group using OR operator with code as (\d|[a-z]|[A-Z]|-])+ 

- https://tesl1W-.com_
- http://tesla.com_P
- https://tes2Ma.gbr
- https://tesla.net
- https://tesla1.online

##### Explanation: The second group (\d|[a-z]|[A-Z]|-])+ enforcing numeric (\d) OR alphabet characters non-capital(a-z) OR capital (A-Z) OR hyphen(-) to validate domain[Second level domain] name with number of occurrence being 1 or more with examples being (tesl1W-, tesla, tes2Ma).

### Flags

### Character Escapes

## Author

- [Sanjeev Kumar](https://github.com/SanjeevKumar-DEV)