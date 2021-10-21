# EmailRegexTutorial

Regular expressions may look like a text message from an angry robot or the musings of that one uncle after too many egg noggs on Christmas, but, they are actually extremely powerful functions used for searching strings. They can be used for everything from user input validation to language processing to web scraping.

## Summary

In this tutorial we will be disecting the expression below which is used to validate an email address input.
    
    /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

In the next few sections, We will be going over the intended use of each part of the expression as well as some common use cases. 
    

## Table of Contents

- [Anchors](#anchors)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Character Escapes](#character-escapes)
- [Quantifiers](#quantifiers)


## Regex Components

### Anchors
The first, and last, component in our email verifier expression is called an anchor. Anchors traditionally start or end an expression.The carrot `^` is used to match to the first position of a string, before the first character. For example, if we were to apply `/^b` to the email string "berlic12345@berlic.com", our expression would match to only the first b.

Similarly, the dollar sign `$` on the end of the expression will match to the position after the last character in the string. In out case `/m$` would match to the m at the end of the  example string. 

These anchors are useful in our case because without them, we could possibly match a valid email if it was contained within non-permitted characters.

### Grouping Constructs
In our regex expression, `( )` are considered grouping constructs. They are used to group togeather other elements of the regular expresion into subexpression. In our case the parenthesis are used to capture a match to  the expression they contain. Going back to our example email validation function, grouping contructs great three groups which check for valiing inputs in three parts. they are the characters before the "@", characters between "@" and the ".". and finally the characters after the ".". 

### Bracket Expressions
Braket expressions are exactly what the name emplies, and a subexpression contained withing opening and closing brackers, `[]`. For a bracket expression to function properly there must both an opening and closing bracket. 
Using out example function, the braket functions are used to match to the character classes within each set of brakets.

### Character Classes
Speaking of character classes, they are expressions used to specify which characters to match.  Also called "character sets", character classes can be as simple as a single character or contain complex description of the desired characters. In our example, the first character class we see in the expression is `[a-z0-9_\.-]`. This incorporates two character ranges. The first `a-z` matches any lower case letter character between a and z. The second `0-9` will match any digit between 0 and 9.  If you look at the next bracket expression in line, we are using another notation `\d`  this will match and character which is a digit between 0-9 and is equivilent to writing out 0-9.  There are many other similar expressions to  `\d` such as `\w` which will match word charcters such as letters. Finally this includes other characters which are neither letter nor number and are individually called which are `_`, `.`, and `-`.

### Character Escapes
The astute amoung readers may have noticed the `\` was not mentioned as a matching non-alpphanumeric characters. In this case, the `\` is whats called a character escape. Using a `\` before any other character telles the regular expression engine to interpert the next character in the expression literally. This is how we are able to negate the normal function of the . which is to match any single character. 

### Quantifiers
Our final component of our regex expression are called qualifiers. Specifically in our example, the `+` and `{2,6}` are the two quantifiers. As the name implies, quantifiers dictate the number of matches the expression is looking for and act on the expression imidiately proceeding. The traditional quantifier is contained between curly braces ,`{n,m}`, containing up to two arguments. the first argument n is the minimum number of matches required. If present, m is the maximum number of matches for the expression to be true. In the above example the last bracket expression must cointain between 2 and 6 matches to be true. The other Quantifier is `+`. In regular expressions a `+` stands for one or more. In our case there must be one or more matching character for the bracketted expression to match true.


## About the Author

Brandon Sorrell aka BerlicTheHunter is a degreed chemical engineer from the Georgia Institute of Technology holding an MBA from Georgia College and State University. An avid gamer, auto enthusiest, and tech junky, he decided to delve into development though the Georgia Tech Coding Bootcamp to broaden his technical knowledge for both personal and professional fulfillment.  
