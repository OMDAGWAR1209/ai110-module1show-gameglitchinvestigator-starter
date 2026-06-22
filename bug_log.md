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

## Fixes Applied

**Bug 1 (abc / non-integer input):**
Fixed — parse_guess now validates the input is a number, returns 
"That is not a number." for invalid input.

**Bug 2 (0 / out of range):**
Fixed — parse_guess now checks the value against the difficulty range 
using get_range_for_difficulty, returns "out of range" error.

**Bug 3 (101 / out of range):**
Fixed — same range check as Bug 2 now correctly rejects values above 
the max range.

**Test mismatch found:**
test_game_logic.py originally expected check_guess to return just a 
string ("Win"), but the function returns a tuple (outcome, message) 
by design. Updated tests to check result[0] instead. All 3 tests now pass.