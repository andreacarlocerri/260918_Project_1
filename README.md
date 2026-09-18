# Italian Hangman

A text-based Hangman game written in Python, built as the mini project for the **Python Analytics Quest** in the Ironhack Data Analytics Bootcamp.

Every secret word is an Italian food or drink. Guess it one letter at a time before you run out of lives.

---

## Objective

Find the secret word by guessing its letters.

- **Win:** every letter of the word is found
- **Lose:** all 6 lives are used up

## How to Play

1. The secret word is shown as blanks: `_ _ _ _ _ _ _`
2. Type a single letter and press Enter
3. Correct letters are revealed in the word
4. Wrong letters cost one life
5. At the end, choose whether to play again

### Example turn

```
Remaining lives: 5
Letters guessed: a, n, z

Secret Word: _ n _ _ _ _ _

Please guess a letter: c
Nice! You guessed a letter!
```

## Features

- Random secret word from a list of 12 Italian foods and drinks
- Input validation: only single letters are accepted
- Repeated letters and invalid input don't cost a life
- Capitals and extra spaces are accepted (`" A"` counts as `a`)
- Tracks every letter already tried
- Short pauses for suspense
- Win and lose banners
- Play-again option

## How to Run

**Requirements:** Python 3 and Jupyter (JupyterLab or Notebook). No external libraries are needed; the game only uses Python's built-in `random` and `time` modules.

1. Clone the repository:
```bash
   git clone <repository-url>
```
2. Open `main.ipynb` in Jupyter.
3. Select **Kernel → Restart Kernel and Run All Cells**.
4. Type your guesses in the input box below the last cell.

## Code Overview

### Data structures

| Structure | Name | Purpose |
|---|---|---|
| List | `words` | the 12 possible secret words |
| Dictionary | `game_state` | everything the game needs to remember |
| Set | `guessed_letters` | tracks guessed letters and prevents duplicates |

### Game state

```python
game_state = {
    "secret_word": random.choice(words),
    "guessed_letters": set(),
    "lives": 6,
    "game_over": False
}
```

### Functions

| Function | Purpose |
|---|---|
| `start_game(words)` | creates a new game state with a random secret word |
| `show_status(game_state)` | prints lives, guessed letters and the word with blanks |
| `player_guess(game_state)` | asks for a letter, validates it and updates the state |
| `check_game_over(game_state)` | checks for a win or a loss and ends the game |

### Game flow

```
Start game
   ↓
Show status → Player guesses → Check win / lose
   ↑                                 ↓
   └──────── game not over ──────────┘
                                     ↓
                               Play again?
```

### Win check

The game turns the secret word into a set (each letter once) and removes the guessed letters. If nothing is left, every letter has been found:

```python
len(set(game_state["secret_word"]) - game_state["guessed_letters"]) == 0
```

## Project Structure

```
.
├── main.ipynb    # the complete game
└── README.md     # this file
```

## Author

**Andrea Cerri**
Ironhack Data Analytics Bootcamp, September 2026