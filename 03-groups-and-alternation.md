# Groups and alternation

Parentheses group part of a pattern so a quantifier can apply to the whole group and so you can capture what matched, and the pipe `|` means alternation, "this or that." Grouping and alternation are how you build patterns that match structured text with optional and alternative parts.

## Grouping

Parentheses bundle several elements into one unit. `(ab)+` matches one or more repetitions of "ab", such as "ababab", because the `+` now applies to the whole group rather than just the last character. Without the group, `ab+` would mean an "a" followed by one or more "b"s. Grouping is what lets quantifiers and alternation operate on multi-character chunks, which is necessary for most real patterns.

## Capturing groups

A plain `(...)` group also captures: the engine remembers what that group matched, and you can retrieve each captured piece by number after the match. This is how you extract parts of a string, for example pulling the area code and number out of a phone format. Capturing groups are numbered left to right by their opening parenthesis. Many regex tasks are really extraction tasks, and capturing groups are the mechanism that makes extraction possible.

## Non-capturing groups

Sometimes you want grouping without the overhead and numbering of a capture. `(?:...)` is a non-capturing group: it bundles elements for a quantifier or alternation but does not store what it matched. Using non-capturing groups keeps your capture numbers meaningful (only the groups you care about are captured) and signals intent. When you group only to apply a quantifier and do not need the captured text, `(?:...)` is the cleaner choice.

## Alternation

The pipe `|` matches the expression on its left or the one on its right: `cat|dog` matches "cat" or "dog". Alternation has low precedence, so it spans as much as it can unless you bound it with a group. `gr(a|e)y` matches "gray" or "grey", while `gra|ey` would match "gra" or "ey", which is probably not intended. Wrapping alternatives in a group is how you control exactly which part of the pattern the "or" applies to.
