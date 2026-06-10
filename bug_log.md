## Bug Log

| Input Used | Expected Behavior | Actual Behavior | Error Output |
|---|---|---|---|
| abc | Show "invalid input" error | Accepted as attempt | none |
| 0 | Show "out of range" error | Accepted as attempt | none |
| 101 | Show "out of range" error | Accepted as attempt | none |
## AI Explanations

**Bug 1 (parse_guess):**
The function only raises NotImplementedError. No validation logic exists
to check if input is a number or within range. It accepts anything.

**Bug 2 (get_range_for_difficulty):**
The function raises NotImplementedError immediately so it never returns
anything. It should return a (low, high) tuple based on difficulty level.

**Bug 3 (check_guess):**
No comparison exists. The function raises NotImplementedError before doing
anything so it never checks if guess is Too High, Too Low, or a Win.