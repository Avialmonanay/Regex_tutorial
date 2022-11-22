# Using regex to match an email

A regular expression (regex) is a sequesnce of characters that specifies a search pattern in text. These regex patterns can be used to find all items in a text that match your pattern so you can quickly identify all emails, phone numbers, or anything of your choosing within a given text. Normal search functions look for the exact string you inputted. Regex allows you to find information without knowing what the exact string is.

## Summary

In this tutorial we are going to be reviewing the regex expression - /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ - to search for an email pattern. This will be a powerful expression that can be used to search for emails or verify if a users input matches the pattern for correct email format.

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
To build a regex you first need to understand the main components of the expression. 
When looking at our expression - /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ - there are several different parts that together can be confusing but once broken down you can easily identify the different sections and their functionality. I will be going into more detail about each component later in the tutorial. For now we are going to break it down into it's individual elements.

"^" and "$" are anchors
"\" lets special characters to be used as a sing character or "escaped"
"[]" matches any single charectar in the range or set enclosed in the brackets
"@" and "\." are our literals
"+" and "{2,6}" are our quantifiers

### Anchors
In this expression we have 2 anchors. The "^" and the "$"

The "^" matches any string where the specified pattern occurs at the begining of the string. For example "^email" matches "email" and "emails" but does no match "noemail". Having this at the begining of our expression ensures that we only look for a pattern like "email@email.com" and not one like "notanemail.email@email.com"

The "$" matches any string where the specified pattern occurs at the end of the string. For example "email$" matches "email" and "noemail" but does not match "emails"

Using bot the anchors together will open and close the expressions pattern so if we were to use "^email$" then we will only return results that match "email"

I like to think about it this way "^" is where you want to begin your pattern and "$" is where you want the pattern to end.

### Quantifiers
Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match. In our expression we have 2 quantifiers the "+" and the {2,6} 

Important Note: If the *, +, ?, {, and } characters are encountered in a regular expression pattern, the regular expression engine interprets them as quantifiers or part of quantifier constructs unless they are included in a character class. To interpret these as literal characters outside a character class, you must escape them by preceding them with a backslash. For example, the string \* in a regular expression pattern is interpreted as a literal asterisk ("*") character.

Lets break down what each of our quantifiers is doing in our expression:
The "+" 

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
