# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

When I first ran the game, it accepted any input as a valid guess — even 
letters like "abc", and numbers outside the 1-100 range like 0 or 101. 
Two concrete bugs I noticed: (1) typing "abc" crashed the app or got 
silently accepted, and (2) entering 0 or 101 was treated as a normal 
guess instead of being rejected as out of range.

**Bug Reproduction Log**

| abc | Show "invalid input" error | Accepted as attempt | none |
| 0 | Show "out of range" error | Accepted as attempt | none |
| 101 | Show "out of range" error | Accepted as attempt | none |
| | | | |
| | | | |

---

## 2. How did you use AI as a teammate?

I used Claude (built into VS Code) for this project. One example of a 
correct AI suggestion was when I asked it to explain why parse_guess 
didn't validate input — it correctly identified that the function was 
just a placeholder raising NotImplementedError, and helped me move the 
real validation logic from app.py into logic_utils.py.
---

## 3. Debugging and testing your fixes
I decided a bug was fixed by manually testing the same bad inputs again 
in the running app and confirming I got the correct error message instead 
of a crash or silent acceptance. I also ran pytest, which initially failed 
because the tests expected check_guess to return a string, but the 
function returns a tuple (outcome, message) by design. AI helped me 
realize this was a test mismatch, not a code bug, so I asked it to update 
the tests instead of changing the function's intended behavior.
- Did AI help you design or understand any tests? How?

I learned that Streamlit reruns the entire script from top to bottom 
every time you interact with the page (like clicking Submit Guess). This 
means any value you want to keep between interactions, like the secret 
number or attempt count, has to be stored in st.session_state, otherwise 
it resets every time the script reruns.

## 4. What did you learn about Streamlit and state?
One habit I want to reuse is asking AI to explain a bug before asking it 
to fix it — this helped me actually understand the root cause instead of 
just accepting a fix blindly. Next time, I would read the test file first 
before fixing bugs, so I know the expected behavior from the start instead 
of discovering mismatches afterward. This project changed how I think 
about AI-generated code — I now expect placeholder functions and unclear 
edge cases, and I review AI's fixes more carefully instead of assuming 
they're correct.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
