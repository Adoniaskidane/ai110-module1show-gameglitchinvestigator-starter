# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ What we fixed

1. **Refactored the game logic.** We moved the pure functions into `logic_utils.py` so the UI and the game rules are separated cleanly.
2. **Fixed the broken hints.** The comparison logic now correctly tells the player when the guess is too high or too low.
3. **Fixed invalid input handling.** Non-numeric values are rejected before they can affect the game state or attempt counting.
4. **Fixed the attempt counter.** Attempts only increase for valid guesses, and the counter is reset correctly on a new game.
5. **Reset the game state cleanly.** New game starts reset the `attempts`, `status`, `score`, and `history` values.

## 📝 Project summary

This game is a number guessing app built with Streamlit. The goal is to guess the hidden number within the allowed attempts. The original version had several bugs: reversed hints, invalid string input, inconsistent attempt counting, and game state that did not reset correctly when starting a new game.

We fixed the core logic and verified the behavior with pytest.

## 📸 Demo Walkthrough

1. Open the app and select a difficulty level.
2. Enter a valid integer guess.
3. Read the corrected hint: too high means the number should go lower, and too low means the number should go higher.
4. Keep guessing until you match the secret number or run out of attempts.
5. Start a new game to reset the score, attempts, and history.

**Screenshot** *(optional)*: Add a screenshot of a completed successful round here.

## 🧪 Test Results

```bash
.venv/bin/python -m pytest -q
```

Result:

```text
4 passed in 0.00s
```

## 🚀 Stretch Features

- [x] Refactored game logic into `logic_utils.py`
- [x] Added regression tests for invalid input and comparison logic
- [ ] Additional UI polish or advanced game features (optional)
