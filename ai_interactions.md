# AI Interactions Log

> **Stretch features only.** Only fill in the sections that apply to stretch features you attempted. If you did not attempt a stretch feature, leave its section blank or delete it. This file is not required for the core project.

---

## Agent Workflow (SF8)

> Document your experience using an AI agent (e.g., Cursor Agent, Claude, Copilot) to make multi-step changes autonomously.

**What task did you give the agent?**

I asked Copilot to help debug the guessing game, refactor the game logic out of the UI, and guide me through fixing the incorrect higher/lower messages, invalid input handling, and attempt-counter logic.

**What did the agent do?**

Copilot inspected the game logic and the Streamlit app, explained the root causes in `app.py`, and guided me toward moving the pure logic into `logic_utils.py`. It also helped identify the string-input bug and the issue where attempts were being counted before validation. I then implemented the refactor and added a regression test for invalid input.

**What did you have to verify or fix manually?**

I verified that the fixes matched the actual code in `logic_utils.py` and `app.py`, and I confirmed the refactor with the project tests. The main manual checks were making sure the logic stayed in the utility file, invalid strings were rejected before counting attempts, and the tests still passed after the refactor.

---

## Test Generation (SF7)

> Document how you used AI to help generate or improve tests.

| Edge Case | Prompt Used | AI-Suggested Test | Did It Pass? | Your Reasoning |
|-----------|-------------|-------------------|--------------|----------------|
| Invalid string input | "Add a pytest case for a non-numeric guess such as 'abc' to ensure it is rejected cleanly." | `test_parse_guess_rejects_non_numeric_string` | Yes | This covers the bug where invalid text was allowed to reach the game flow and could interfere with attempt counting and game state. |
| Winning guess | "Add a test that verifies a correct guess returns 'Win'." | `test_winning_guess` | Yes | This confirms the refactored logic still recognizes a correct match after moving it into `logic_utils.py`. |
| Higher and lower comparison | "Add tests for guesses above and below the secret." | `test_guess_too_high`, `test_guess_too_low` | Yes | These validate the corrected comparison logic and ensure the hint direction matches the actual value. |

---

## Linting & Style (SF9)

> Document your use of AI for linting or code style improvements.

**Prompt used:**

```
<!-- Paste the prompt you gave the AI -->
```

**Linting output before:**

```
<!-- Paste relevant linter warnings/errors -->
```

**Changes applied:**

<!-- Describe what you changed based on the AI's suggestions -->

---

## Model Comparison (SF11)

> Compare two AI models on the same task.

**Task given to both models:**

<!-- Describe what you asked each model to do -->

| | Model A | Model B |
|-|---------|---------|
| **Model name** | | |
| **Response summary** | | |
| **More Pythonic?** | | |
| **Clearer explanation?** | | |

**Which did you prefer and why?**

<!-- Your conclusion -->
