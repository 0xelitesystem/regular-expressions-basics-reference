# Lookarounds in brief

Lookarounds let a pattern check what comes before or after a position without including those characters in the match. A lookahead `(?=...)` asserts that what follows matches, a negative lookahead `(?!...)` asserts it does not, and the lookbehind forms `(?<=...)` and `(?<!...)` do the same for what precedes. They match positions, not text.

## Lookahead

A positive lookahead `(?=...)` succeeds at a position only if the pattern inside would match starting there, but it consumes nothing, so the match continues from the same spot. For example, `\d(?=px)` matches a digit only when it is followed by "px", but "px" itself is not part of the match. A negative lookahead `(?!...)` is the opposite: it succeeds only if the inner pattern does not match ahead. Lookaheads are how you say "match this, but only in this context."

## Lookbehind

Lookbehind checks the text before the current position. A positive lookbehind `(?<=...)` matches only if the preceding text matches the inner pattern, and a negative lookbehind `(?<!...)` matches only if it does not, again without consuming those characters. For instance, `(?<=\$)\d+` matches digits only when preceded by a dollar sign, without including the sign. Lookbehind support varies by engine, and some engines restrict it to fixed-length patterns, so it is slightly less portable than lookahead.

## Why they are useful

Lookarounds let you make a match conditional on its surroundings while keeping those surroundings out of the captured result. This is valuable when you want to find something only in a certain context, or extract a value that sits next to a marker you do not want in the output. They turn "find X next to Y" into a clean pattern without manually trimming Y afterward. The defining property is that they assert without consuming.

## Keep them simple

Lookarounds are powerful but can make patterns hard to read and, when nested or combined with heavy quantifiers, slow. Reach for them when the alternative is clumsy post-processing, but prefer the simplest pattern that works. For everyday matching you often do not need lookarounds at all; literals, classes, quantifiers, anchors, and groups cover most cases. Treat lookarounds as a precise tool for the specific job of context-sensitive matching, not a default.
