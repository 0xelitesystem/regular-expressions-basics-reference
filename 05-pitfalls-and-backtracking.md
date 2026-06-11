# Pitfalls and catastrophic backtracking

The most dangerous regex pitfall is catastrophic backtracking, where a poorly structured pattern makes the engine try an exponential number of combinations on certain inputs, freezing the program. Other common mistakes include greedy quantifiers matching too much, forgetting to escape special characters, and forgetting anchors so a partial match passes when a full match was intended.

## What backtracking is

Most regex engines match by trying possibilities and backing up when a path fails, a process called backtracking. Normally this is fine. The problem appears when a pattern lets the engine split the same input many different ways, so a failing match forces it to retry an explosive number of combinations before giving up. The work can grow exponentially with input length, turning a pattern that looks harmless into one that hangs for seconds, minutes, or effectively forever.

## Catastrophic backtracking

Catastrophic backtracking typically comes from nested quantifiers over overlapping patterns, such as `(a+)+` or `(a|a)*`, especially when followed by something that fails to match. On an input like a long run of a's followed by a non-matching character, the engine tries every way to divide the a's among the repetitions before concluding failure. The classic real example is patterns like `(\w+)*$` applied to long strings. These look reasonable but can be exploited or triggered accidentally to cause a denial of service.

## Avoiding the trap

Avoid nesting quantifiers over patterns that can match the same text more than one way. Make sub-patterns non-overlapping so there is only one way to match. Bound repetition with counted quantifiers like `{1,100}` instead of unbounded `+` or `*` where you can. Prefer more specific character classes over `.*`, and anchor patterns so the engine fails fast. Where supported, atomic groups or possessive quantifiers prevent the engine from backtracking into a group at all, which removes the explosion.

## Everyday mistakes

Beyond performance, the routine mistakes are simpler. Greedy `.*` often grabs more than intended; switch to lazy `.*?` or a specific class. Forgetting to escape metacharacters means `.` matches any character when you meant a literal dot. Forgetting anchors means `\d{4}` matches four digits anywhere, including inside a longer number, when `^\d{4}$` was intended. And testing only happy-path inputs hides all of these. Test your patterns against edge cases and unexpected input before trusting them.
