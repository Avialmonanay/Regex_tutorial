# Using regex to match an email

A regular expression (regex) is a sequesnce of characters that specifies a search pattern in text. These regex patterns can be used to find all items in a text that match your pattern so you can quickly identify all emails, phone numbers, or anything of your choosing within a given text. Normal search functions look for the exact string you inputted. Regex allows you to find information without knowing what the exact string is.

## Summary

In this tutorial we are going to be reviewing the regex expression - /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ - to search for an email pattern. This will be a powerful expression that can be used to search for emails or verify if a users input matches the pattern for correct email format.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes/Bracket Expressions](#character-classes/bracket-expressions)
- [Grouping and Capturing](#grouping-and-capturing)
- [Full Breakdown](#full-breakdown)


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
The "+" matches one or more times in our expression this means that it can have any amount of Characters as long as there is more than 1
The {2,6} matches from 2 to 6 times. In our expression this means that it can be anywhere from 2 to 6 Characters

### Character Classes/Bracket Expressions
[] Brackets indicate a set of characters to match. Any individual character between the brackets will match, and you can also use a hyphen to define a set.
A character class. Matches any one of the enclosed characters. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first or last character enclosed in the square brackets, it is taken as a literal hyphen to be included in the character class as a normal character. Our expressions classes are "[a-z0-9_\.-]", [\da-z\.-]", and "[a-z\.]"

Lets break these classes down to see what is happening.

[a-z0-9_\.-] - There are a few components to this class we can start with "a-z" This is specifying any charectar between a and z. Then we have "0-9" This is specifying any digit between 0 and 9. Lastly we have "_\.-" these are our special Characters so we can include an underscore "_" a period "\." and a dash "-". The period has it's own function when it comes to regex so we have to make it into a litteral by adding the backslash. This is why you see it presented as "\."

[\da-z\.-] - We are essentially doing the same as the above however it is in a different format and we are excluding the underscore. "\d" is shorthand for matching any digit. So it is equivelant to [0-9]. Then we have our "a-z" to match any charectar. Lastly we have "\.-" which allows for periods and dashes.

[a-z\.] - This is the final class and it accepts "a-z" anything between a to z and "\." which allows for periods.


### Grouping and Capturing
Capturing group: Matches x and remembers the match. For example, /(foo)/ matches and remembers "foo" in "foo bar" in our expression /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ you can see we are grouping around each of our character classes with their respective quantifiers. 

Lets break down these groups further to see how each is acting.

([a-z0-9_\.-]+) - As you can see we are grouping our character class [a-z0-9_\.-] with our quantifier "+" So we will accept any character in this group so long as there is at least 1 character present.

([\da-z\.-]+) - This is the same as above. We are gouping our class [\da-z\.-] with the "+"  quantifier

([a-z\.]{2,6}) - Here we are grouping our class [a-z\.] with our quantifier {2,6} so we will accept any character between a-z and periods with a length between 2-6. Any shorter or longer than the quantifier will ommit it from the results.

## Full Breakdown

Now that we have a full understanding of how regex is working in our expression lets do a full breakdown of the expression.

Our full Expression /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

/^ - we are starting the expression and specifying the pattern string start.
([a-z0-9_\.-]+) - We are specifying any character (letter, digit, or specified special characters) and saying any results with more than one character 
@ - is our literal so we are looking for an @ sign between the first and second groupings
([\da-z\.-]+) - We are specifying any character (letter, digit, or specified special characters) and saying any results with more than one character
\. - is our literal so we are looking for a period "." sign between the second and third groupings
([a-z\.]{2,6}) - We are specifying any letter or specified special character) and saying any results between 2-6 characters long.
$/ - We are specifying the pattern to end and to close out the expression

In the end this allows our regex to find or verify emails as they all should follow this pattern. For example email@email.com, email1424@email.org, and email.email@email.com will all be found. Examples like email$$@email.com, email||email.com, and email@email.website will not be found as they contain unsupported characters or fall outside the qualifiers.

## Author

Rexx Madsen
- I work for a software development company specializing in API and Automations. I have built many applications using JS and Databases and am now expanding my knowledge into regex

Github profile: [Avialmonanay](https://github.com/Avialmonanay)
