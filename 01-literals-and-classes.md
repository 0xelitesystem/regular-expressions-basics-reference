# Literals and character classes

The simplest regex is a literal: characters that match themselves, so `cat` matches the text "cat". A character class, written in square brackets, matches any one character from a set, so `[abc]` matches a single a, b, or c. Literals and classes are the foundation; everything else controls how many of them match and where.

## Literal characters

Most characters in a pattern match themselves exactly. The pattern `dog` matches the three letters d, o, g in sequence. Some characters are special (metacharacters like `.`, `*`, `+`, `?`, `(`, `)`, `[`, `]`, `{`, `}`, `^`, `$`, `\`, and `|`), and to match those literally you escape them with a backslash: `\.` matches a real dot, `\$` matches a real dollar sign. Knowing which characters are special is what tells you when an escape is needed.

## Character classes

A character class `[...]` matches exactly one character from the set inside the brackets. `[aeiou]` matches any single vowel. You can use ranges with a hyphen: `[a-z]` matches any lowercase letter, `[0-9]` any digit, `[A-Za-z0-9]` any letter or digit. A class always matches one character, no matter how many options are listed inside it. To match several, you combine a class with a quantifier, covered next.

## Negated classes

Putting a caret at the start of a class negates it: `[^0-9]` matches any single character that is not a digit. This is useful for "anything except" patterns. The caret only means negation when it is the first character inside the brackets; elsewhere it is a literal caret. A negated class still matches exactly one character, just from the complement of the set. It does not match an empty position, so it requires a character to be present.

## Shorthand classes

Common classes have shorthands. `\d` matches a digit (equivalent to `[0-9]`), `\w` matches a word character (letters, digits, and underscore), and `\s` matches whitespace (spaces, tabs, newlines). Their uppercase versions negate them: `\D` is any non-digit, `\W` any non-word character, `\S` any non-whitespace. The dot `.` is a special wildcard matching any single character except a newline by default. These shorthands make patterns shorter and easier to read than spelling out the equivalent bracket class.
