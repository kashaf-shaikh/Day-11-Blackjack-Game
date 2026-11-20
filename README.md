# Day 11 – Blackjack Game

## Project Overview

This project is a command-line Blackjack card game built using Python. In this game, the player competes against the computer to get a card score as close to 21 as possible without going over 21.

The player starts with two cards and can choose whether to draw another card or pass. After the player finishes their turn, the computer automatically draws cards until its score reaches at least 17.

The program then compares both scores and announces the winner.

This project is part of my **100 Days of Python** learning journey.

## Game Rules

The game follows these basic Blackjack rules:

- Each player starts with two cards.
- Number cards have their face value.
- Face cards (10, Jack, Queen, King) are worth 10 points.
- An Ace is worth 11 points initially.
- If the score goes above 21 and the player has an Ace, its value changes from 11 to 1.
- A score of 21 with exactly two cards is considered Blackjack.
- The player can choose to draw another card or pass.
- The computer keeps drawing cards while its score is below 17.
- The player with the better score wins, provided they do not go over 21.

## Features

- **Random Card Generation:** Generates random cards using Python's random module.
- **Player vs Computer:** Allows the user to play against the computer.
- **Score Calculation:** Calculates the total value of the cards.
- **Blackjack Detection:** Identifies a Blackjack score of 21 with two cards.
- **Ace Adjustment:** Changes an Ace's value from 11 to 1 when necessary.
- **Hit or Pass:** Allows the player to draw another card or stop drawing.
- **Automatic Computer Turn:** The computer draws cards until its score reaches at least 17.
- **Winner Comparison:** Compares the final scores and displays the result.
- **Replay Option:** Allows the user to start another game.

## How the Program Works

### 1. Importing Modules

The project uses Python's `random` module to generate random cards and imports the game logo from `art.py`.

```python
import random
from art import logo
```

- `random` is used to select cards randomly.
- `logo` displays the Blackjack game logo.

### 2. Creating the deal_card() Function

This function selects and returns one random card from the deck.

```python
def deal_card():
    cards = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]
    card = random.choice(cards)
    return card
```

The deck contains:
- Ace represented by `11`.
- Number cards from 2 to 10.
- Four entries worth 10 to represent 10, Jack, Queen and King.

`random.choice()` selects one card randomly from the list.

### 3. Creating the calculate_score() Function

This function calculates the total score of a player's cards.

```python
def calculate_score(cards):
    if sum(cards) == 21 and len(cards) == 2:
        return 0

    if 11 in cards and sum(cards) > 21:
        cards.remove(11)
        cards.append(1)

    return sum(cards)
```

**Important logic:**

- `sum(cards)` calculates the total card score.
- `len(cards)` checks how many cards are present.
- If the player has exactly two cards with a total of 21, the function returns `0` to represent Blackjack.
- If the score exceeds 21 and an Ace (11) is present, its value changes to 1.
- Finally, the function returns the total score.

### 4. Creating the compare() Function

This function compares the user's score with the computer's score and decides the result.

```python
def compare(u_score, c_score):
    if u_score == c_score:
        return "Draw"

    elif c_score == 0:
        return "Lose, opponent has Blackjack"

    elif u_score == 0:
        return "Win with a Blackjack"

    elif u_score > 21:
        return "You went over. You lose"

    elif c_score > 21:
        return "Opponent went over. You win"

    elif u_score > c_score:
        return "You win"

    else:
        return "You lose"
```

The function checks different conditions in order, such as:
- Draw.
- Computer has Blackjack.
- Player has Blackjack.
- Player goes over 21.
- Computer goes over 21.
- Player has a higher score.
- Otherwise, the computer wins.

### 5. Creating the play_game() Function

This is the main function responsible for running one complete game.

It performs the following tasks:

1. Displays the game logo.
2. Creates two empty lists: `user_cards` and `computer_cards`.
3. Deals two cards to both the player and the computer.
4. Calculates both scores.
5. Displays the player's cards and the computer's first card.
6. Asks the player whether they want another card or want to pass.
7. Continues the player's turn until the game-ending condition is reached.
8. Allows the computer to draw cards while its score is below 17.
9. Displays both final hands and scores.
10. Calls `compare()` to display the game result.

### 6. Playing Again

At the end of the program, a `while` loop asks whether the player wants to play another game.

```python
while input("Do you want to play a game of Blackjack? Type 'y' or 'n': ") == "y":
    print("\n" * 20)
    play_game()
```

- If the user enters `y`, another game starts.
- If the user enters `n`, the loop ends.
- `print("\n" * 20)` prints multiple blank lines to separate games in the terminal.

## Example Output

The following is an illustrative example. Actual cards and scores will vary because they are generated randomly.

```text
Do you want to play a game of Blackjack? Type 'y' or 'n': y

Your cards: [10, 7], current score: 17
Computer's first card: 9

Type 'y' to get another card, type 'n' to pass: n

Your final hand: [10, 7], final score: 17
Computer's final hand: [9, 8], final score: 17

Draw 🙃

Do you want to play a game of Blackjack? Type 'y' or 'n': n
```

## Python Concepts Used

| Concept | How It Is Used |
|---|---|
| Functions | Dividing the game into smaller reusable tasks |
| Parameters | Passing card lists and scores to functions |
| Return Statement | Returning cards, scores and game results |
| Lists | Storing player and computer cards |
| `random.choice()` | Selecting random cards |
| `sum()` | Calculating the total card score |
| `len()` | Checking the number of cards |
| `in` Operator | Checking whether an Ace is present |
| `remove()` | Removing an Ace valued at 11 |
| `append()` | Adding a new card or adjusted Ace value |
| For Loop | Dealing initial cards using `range(2)` |
| While Loop | Repeating turns and allowing another game |
| If-Elif-Else | Checking game conditions and deciding the winner |
| Boolean Variables | Controlling when the game ends |
| Modules | Importing the random module and game logo |
| Nested Function Calls | Calling helper functions inside the main game function |

## Project Structure

```text
Day-11-Blackjack-Game/
│
├── main.py       # Main Blackjack game logic
├── art.py        # Game logo and ASCII art
└── README.md     # Project documentation
```

## How to Run the Project

### Prerequisites

- Python 3 installed on your system.
- VS Code, PyCharm or any Python code editor.

### Steps

**1. Clone the repository**

```bash
git clone YOUR_REPOSITORY_URL
```

**2. Navigate to the project folder**

```bash
cd Day-11-Blackjack-Game
```

**3. Run the program**

```bash
python main.py
```

## Current Project Limitations

- This is a simplified version of Blackjack.
- It does not include betting or money management.
- It does not implement advanced actions such as splitting or doubling down.
- Card generation uses a simplified card list rather than tracking a complete physical deck.

## What I Learned

Through this project, I practised:

- Breaking a larger program into smaller functions.
- Working with lists to store and manage cards.
- Using random selection to generate cards.
- Applying conditions to implement game rules.
- Handling special cases such as Blackjack and Ace value adjustment.
- Using loops to control player and computer turns.
- Comparing scores to determine the game result.
- Organizing a Python project using multiple files.

## Learning Journey

**100 Days of Python – Day 11**

This project helped me combine multiple Python concepts to build an interactive card game and understand how different functions work together in a larger program.