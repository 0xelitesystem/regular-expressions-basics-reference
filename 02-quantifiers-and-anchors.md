# Quantifiers and anchors

Quantifiers say how many times the preceding element may repeat: `*` is zero or more, `+` is one or more, `?` is zero or one, and `{n,m}` is a specific range. Anchors say where in the string a match must sit: `^` is the start, `$` is the end, and `\b` is a word boundary. Together they turn single-character matchers into patterns that span and position text.

## The basic quantifiers

A quantifier applies to the element just before it. `a*` matches zero or more a's, `a+` matches one or more, and `a?` matches an optional single a. So `colou?r` matches both "color" and "colour" because the u is optional. Quantifiers attach to whatever immediately precedes them, which can be a literal, a class, or a group. `[0-9]+` matches one or more digits, a common way to match a whole number.

## Counted quantifiers

Braces give exact counts. `a{3}` matches exactly three a's, `a{2,4}` matches two to four, and `a{2,}` matches two or more. This is how you match fixed-length things: `[0-9]{4}` matches exactly four digits, useful for a year. Counted quantifiers are more precise than the open-ended ones and often safer, because bounding the repetition limits how much work the engine can do, which matters for performance.

## Greedy vs lazy

By default quantifiers are greedy: they match as much as they can, then give back characters only if the rest of the pattern needs them. Adding a `?` after a quantifier makes it lazy, matching as little as possible. So `.*` grabs everything to the end of the line and backtracks, while `.*?` grabs the minimum. The greedy-versus-lazy distinction explains many surprising matches, especially patterns that swallow more text than intended.

## Anchors

Anchors match positions, not characters, so they consume nothing. `^` matches the start of the string (or line, in multiline mode) and `$` matches the end, so `^abc$` matches a string that is exactly "abc". `\b` matches a word boundary, the position between a word character and a non-word character, so `\bcat\b` matches "cat" as a whole word but not the "cat" inside "category." Anchors are essential for matching whole strings or whole words rather than fragments buried in larger text.
