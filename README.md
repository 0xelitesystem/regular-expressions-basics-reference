# Regular Expressions Basics

A plain-language reference on regular expressions: the building blocks (literals, character classes, quantifiers, anchors, groups, alternation), a brief look at lookarounds, and the common pitfalls including catastrophic backtracking. It is aimed at someone who wants to read and write everyday regexes with a correct mental model rather than copy-pasting patterns they do not understand.

## The core idea

A regular expression is a small pattern language for describing and matching sets of strings, built from literal characters plus special metacharacters that mean "any of these," "this many times," "at this position," and "this or that." You combine a handful of pieces (character classes, quantifiers, anchors, groups, and alternation) to express what text you want to find. Most real patterns use only these basics, and most regex bugs come from a few predictable mistakes rather than deep complexity.

## What is inside

- [01-literals-and-classes.md](01-literals-and-classes.md) matching exact characters and sets of characters.
- [02-quantifiers-and-anchors.md](02-quantifiers-and-anchors.md) how many, and where in the string.
- [03-groups-and-alternation.md](03-groups-and-alternation.md) grouping, capturing, and "this or that."
- [04-lookarounds-in-brief.md](04-lookarounds-in-brief.md) matching based on what is around without consuming it.
- [05-pitfalls-and-backtracking.md](05-pitfalls-and-backtracking.md) the common mistakes and catastrophic backtracking.

## The stance

This reference treats regex as a readable tool, not a write-only puzzle. Understanding what each piece does lets you build patterns deliberately and debug them when they misbehave. The goal is correct, maintainable patterns and an awareness of the traps, especially the performance trap of catastrophic backtracking.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT. Copyright 0xelitesystem 2026.
