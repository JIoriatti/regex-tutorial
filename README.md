# Regex Tutorial for Matching a Hex Value

This tutorial will explain the components, syntax, and uses of the regex (Regular Expression) for matching a hex value.

## Summary

This regex can be utilized to search for or match hexidecimal values instead of numeric
values. For instance, hexidecimal values can be used in CSS to denote colors. This regex could also be leveraged in javascript to add color styles using a hex value, or can be used to target specific components in an app with styling of a specific hex value color.

Below is the syntax of the regular expression to match a hex value:

```js
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
```
## Table of Contents

- [Anchors](#anchors)
- [Bracket Expressions](#bracket-expressions)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

Because regular expressions are considered literals, they must be wrapped in slashes (/).
The components that makeup a regex are contained within anchors that are wrapped around the slashes.
In this case, for the hexidecimal regex above, the regex starts by checking if the string starts with the symbol '#' followed by a '?' and then grouping constructs and quantifies which will be discussed in the next sections.

### Anchors

Anchors come before and after the groups of characters you are utilizing the regex for. The '^' symbol starts the expression and will include any characters that come after it as part of the regex. The '$' signifies the end of the regex, meaning any characters preceding it will be checked.

### Bracket Expressions

The next portion of a regular expression to discuss are bracket expressions. They are denoted with square brackets '[]'. We can use bracket expressions to have the regex check for a range of characters included within the brackets. Any string containing any of the characters within a bracket expression with match, regardless of order and length of the string. To denote a range of characters or numbers, we can use the hyphen '-' between two characters of numbes that we want the range to be contained within. For example, [a-f] will match strings with the characters a through f, likewise [1-6] will match strings with numbers between 1 and 6. Note that regex is case sensitive, so case matters in bracket expressions as well. To include special characters in a regex, we can place any special characters to check for after any alphanumeric range set within the bracket expression. For example, [a-z0-9-,=] will denote a through z, 0 through 9, and also include the special characters '-', ',', and '='.

**Note: If a string contains any, not all, of the characters in a bracket expression the regex will match it.**

For the hexidecimal regex we are checking a string if it contains any letter a through f, and any number(0 through 9). The bracket expression is as follows:

```js
[a-f0-9]
```


### Quantifiers

Quantifiers are denoted with the curly brackets '{}'. These are used to limit the number of characters the regex is looking for in a string. The syntax of a quantifier in terms of length alone is { n, x}, where n is the number of times the regex pattern matches the string, and x is the maximum number of times the regex matches the string. There are three indivudal ways to denote quantifiers:
   
    - { n } -- will match the string/pattern exactly n times.
    - { n, } -- will match the string/pattern at least n times.
    - { n, x } -- will match the string pattern a minimum of n times and a maximum of x times.

By default, regular expressions are greedy which means they will match as many occurances as possible. They can also be set to lazy, where they will match as few occorences as possible. This is done by using the the question mark, '?' placed after the quanitifier.

For the hexidecimal value regex we see a '?' after the '#' symbol. This means we are making the regex lazy for matching as few '#' symbols as possible, in this case just one, since hexidecimal values start with a '#' symbol.

If we take a look at the hex value regex, we can see that two quantifiers are used, {6} and {3}, after the bracket expressions. These are used in an OR expression, that of which as well as bracket expressions will be covered in the next two sections.

### Grouping Constructs

Grouping constructs are denoted between the parenthases '()'. Any expression within these parenthases is considered a subexpression.
Subexpressions look for exact matches, unlike bracket expressions which are inclusive or truthy expressions. We can use an OR operator to check for multiple conditions, just like when using logical expression in code. We will look into the OR operator in more detail in a later section, but for now  lets take a look at the hex value regex once more.

```js
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
```

After the regex checks for one pound symbol '#', it then looks into the subexpression witch denotes that exactly either the first bracket expression and quantifier, or the second bracket expression and quantifier must match the string. If a string containes a '#' symbol followed by any combination of 4 letters of a through f or numbers then it would not match the regex, because the quantifiers explicitly check for either 6 or 3 characters. For example, a string of '#fffe' would not match, however '#fff' would.

### Character Classes

Character classes are used to denote groups of related characters, like a shorthand in some sense. Bracket expressions are in fact character classes as well. Two examples of character classes are '\d' and '\s'. These two classes represent or match any Arabic numeral digit (equivilent to [0-9]), and a single whitespace (including tabs and line breaks), respectively. The inverse of these classes is denoted by capitilizing the character, i.e. '\S' will match any string without a single space.

### The OR Operator

We breifly mentioned the OR operator before and it's use in subexpressions. Let's take a deeper look into it. The bracket expression '[fba]' checks a string for the letters f, b, or a. Therefor, we can use the OR operator within a subexpression to represent the same logic as follows: (f|b|a). This can come in handy when dealing with multiple cases of bracket expressions and quantifiers such as the ones in the hex value expression. In this case, we are using the | (OR) operator within a subexpression to match a string with either of the two bracket expressions and quantifiers of '[a-f0-9]{6}' , and '[a-f0-9]{3}'.


### Flags

Flags are placed at the end of the regex after the second slash '/'. Flags denote additional functionality or limitation of the expression.
There are six total flags: i, g, m, s, u, y.
Flags can be used together or individually and in any order, so long as they come after the second slash '/'. The two most common may be the g and i flag, which indicate the regex should be tested against all possible matches in a string, and the regex should ignore case sensitivity, respectively. In our case, the hex value regex does not include any flags.

### Character Escapes

Character escapes are denoted by the backslash. Escapes are used to on characters that would otherwise be interpreted literally. An example of this would be if we wanted to include an opening square bracket in our expression to match against, instead of denoting the beginning of a bracket expression. In this case we would escape the opening square bracket like so: '\['. In the case of the hex value regex, there are no character escapes used.

**Note: All special characters including the backslash lose their special significance inside bracket expressions, therefor you cannot escape characters inside bracket expressions.**

## Author

My name is James Ioriatti and I am currently in the last phase of the Northwestern web-development bootcamp as of creating this regex tutorial. To view my other repo's please feel free to visit my GitHub, linked below!

[GitHub](https://github.com/JIoriatti)
