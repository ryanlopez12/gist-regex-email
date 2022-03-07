# Email Regex Breakdown

This breakdown and tutorial will explain the function of the following expression.  

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

This email regex verifies the characters entered for an email are valid and allowed.  This will breakdown all of the components that make up this Regex and how they all function to validate an email address.

## Summary

Definition of a Regular Expression (regex) as from Wikipedia.org.
A regular expression (shortened as regex or regexp; also referred to as rational expression) is a sequence of characters that specifies a search pattern in text. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. It is a technique developed in theoretical computer science and formal language theory.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Back-references](#back-references)


## Regex Components

### Anchors

Anchors do not match any characters, instead match a position beofre or after characters.

*Examples of Anchors:*

`^` - The caret anchor matches the beginning of the text.  
`$` - The dollar anchor matches the end of the text.

*Anchors included in this regex:*

`^`, `$`

`/^([a-z0-9_\.-]+)` - With the caret symbol at the beginning of the string means that the characters that are after must be at the beginning of the query. `([a-z\.]{2,6})$/` - Also with the dollar symbol at the end of the string means that the characters preceding it must be at the end of the string.

### Quantifiers

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.  

Quantifiers are inherently greedy and will match as many of a certain pattern as possible.  But, quantifiers can be made lazy by adding a `?` symbol after it, meaning it will match as few patterns possible.

*Examples of Quantifiers:*

`*` - Match Zero or more times.
`+` - Match one or more times.
`?` - Match zero or one time.
`{n}` - match exactly n times.
`{n,}` - match at least n times.
`{n,m}` - match from n to m times.

*Quantifiers included in this regex:*

`*`, `+`, `{}`

`{2,6})$` - Looking at this section of the regex we can see that when using {} syntax followed by the )$ character means that the end of an email must contain at least 2 characters, but no more than 6 characters. 

`([a-z0-9_\.-]+)` and `([\da-z\.-]+)` means that after following the `+` character they must include the character shown after. `([a-z0-9_\.-]+)` must be proceeded by an `@` character and `([\da-z\.-]+)` must be proceeded by a `.` one or more times.

### Character Classes

Character classes are a set of characters that can occur in an input string to fill a match.  Character classes typically are between an expression bracket.

*Examples of Character Classes:*

- `.` - Matches any character except a newline \n.
- `\d` - Match any digit.
- `\D` - Match any non-digit.
- `\s` - Match space symbols, tabs, newlines.
- `\S` - Match any, but \s.
- `\w` - Match any letters, digits, underscore.
- `\W` - Match any, but \w.

*Examples of Character Classes within this regex:*

`[\da-z\.-]` - The \d is referring to any digit and letters A through Z and a literal period or a dash.

`[0-9a-z\.-]` is another way that this expression could have been written.

### Grouping and Capturing

Capturing groups are used to break the string a regex is being applied to by placing an expression inside matching open and close parentheses. 

Open and close parentheses are used three times within this regex.

1. `([a-z0-9_\.-]+)` 2. `([\da-z\.-]+)` 3. `([a-z\.]{2,6})`

Meaning that each group must have the included values determined inside of the parentheses group.  Other quantifiers and anchors can then be applied these groups to form a string determing where the groups should be located or what else must be included. These smaller groups create sub groups that are a part of the larger complete regex expression group.

### Bracket Expressions

A bracket expression (an expression inclosed in `[]`) is a specific set of single characters, and may match a specific set of multi-character collating elements based on the non-empty set of list expressions contained in the bracket expression.  

It can be either a matching list exxpression or a non matching list expression. It can also consist of one or more expressions with characters, collating elements, range expressions, classes, equivalence classes, or collating symbols.

*Examples of Bracket Expressions in this regex:*

1. `[a-z0-9_\.-]` - The first bracket expression must contain lowercase letters A through Z or numbers 0 through 9, also can contain an underscore, period, or dash as well.

2. `[\da-z\.-]` - The second bracket expression must contain lowercase letters A - Z, `/d` is equal to 0 through 9 (d is shorthand for "digit"), and also can contain a period or a dash.

3. `[a-z\.]` - This bracket expression can only contain lowercase letters A through Z or a period.

### Greedy and Lazy Match

Greedy matches will consume as much as possible, lazy will do the opposite.  Greedy with match the values determined as many possible times and ways it can.  While lazy matches will consume the first value found and consume no more.

*Examples of Greedy Matches:*

`+` - Match any and all values.
`?` - Match any as few times possible.

*Example of Greedy Matches in this regex:*

`([a-z0-9_\.-]+)@` - The `+` symbol here is a greedy match and is instructing this group to be followed by the `@` symbol and the proceeding values as well.

There are no lazy matches in this regex.

### Back-references

Back References are used to match the same text previously matched by a capturing group.  The helps in using previous parts of your pattern and ensuring that two pieces of a string match.

## Author

Ryan Lopez
Github: rlopez12
