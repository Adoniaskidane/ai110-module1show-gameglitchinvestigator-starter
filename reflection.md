# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?

  Answer: The game looks great when starting. It has very user friendly built and apealing inferface/UI. It seems like highly interactive, buttons work and production ready appliation.

- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

  Answer: 
    1, when entering number in the prompt it tell to Go Higher despite the secret number is lower and vise verse for the lower number.
    2, After winning the game new game button rests the game but when submitting it doesn't work

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| | 10  | Go Higher         Go lower(secret=38)   no error
|newgame| take new values       doesn't work       Game over. Start a...
| string| stop at 0 attempt | goes to negative attempt | no error
|attempt| start from 1         start from 0       no error
| Hard  | expected >100         1 to 50           no error
| Normal| 8 iteration         7 iteration,1 miss


---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
  Answer: Copilot

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
  Answer:
  1, In the try block, guess > secret returns “Go HIGHER,” and the else returns “Go LOWER.” In the except block, the string-comparison fallback does the same.
  
  extra AI suggesion result
  2, When a game ends, status is changed from "playing" to "won" or "lost". The New Game handler resets the attempts and secret, but doesn’t reset status to "playing". After the rerun, the app still sees the old finished status, displays the game-over message, and stops before it can process a guess.For a fully fresh game, you may also reset score and history in this block.
  3, in the if submit: block, parse the input first and increment attempts only when the guess is valid. Move the increment from the start of that block into the else:
  make the initial attempt count 0, since no guess has been made yet

- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.
  Answer:
  1, Find the block that converts the secret to a string on even-numbered attempts:
  parse_guess() already returns an integer, and the secret is also an integer. Keep it numeric for every attempt by assigning secret = st.session_state.secret instead. That prevents the TypeError and avoids the fallback’s string comparison, where, for example, "9" is considered greater than "10".

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
  1, first I have restarted the application and tested
  2, verfied using AI if the issue is fixed and evaluated the ai response
  3, Generated test cases to evalute the internal functionality and bug fixs.

- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
  function: test_parse_guess_rejects_non_numeric_string
  Answer: takes string and see if it reject the result

- Did AI help you design or understand any tests? How?
  yes I am able to generate specific test and I needed. instead of manually implementing it, I have utlized ai to generate by explicitly emphasising what test cases i need.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
  streamlit runs everying in our code and it controls it. It also use st.session_state to set data, preserve data, to control the ui and user interaction.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.

  that fixing one bug at a time. allows me to document easily. use separate session for every bug.

- What is one thing you would do differently next time you work with AI on a coding task?
 
   every bug fix, i need to commit, missng multilpy layer of commit.

- In one or two sentences, describe how this project changed the way you think about AI generated code.
   
   very much deep hands on, helps me learn how to keep human in the loop with ai to debug(understand the core issue), allow ai to guied how to fix it, generate code and review (for any unnecassary fix or halucination), then after fully understood the change approve and documents. make sure to inlcude test cases in the project because every code need to be tested.