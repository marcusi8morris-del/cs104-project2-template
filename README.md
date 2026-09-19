```
========================================
   ROCK  *  PAPER  *  SCISSORS
   CS 104  |  Project 2  |  Fall 2026
========================================
```

# 🪨📄✂️ Project 2: Rock, Paper, Scissors

## 🎯 Overview

You are building a two-player rock-paper-scissors game that runs in the terminal.

**The rules**
- Rock beats scissors
- Scissors beats paper
- Paper beats rock
- Same shape means a draw

**A game is exactly three rounds.** Win more rounds than your opponent and you win the game. Anything else means no winner. Example: Player 1 wins round 1 and rounds 2 and 3 are draws. Player 1 wins the game, 1 round to 0.

This project is about **decomposition**. You will not write one giant program. You will write **ten small functions** that each do one job, then connect them at the very end.

## 🎓 What you will practice

- Breaking a big problem into small functions with clear jobs
- Reading a docstring and writing code that does exactly what it says
- `input()` and `print()` in an interactive program
- Functions that call other functions
- Returning a value vs printing a value
- Boolean logic with `and`, `or` and `not`
- `if` / `elif` / `else` and loops
- Constants instead of magic numbers
- Checking your own work by trying tricky inputs on purpose

## 📦 What is in your repo

| File | What it is | Do you edit it? |
|---|---|---|
| `rps.py` | Starter code: constants, a spec for every function and the four provided functions | ✅ Yes |
| `start.py` | Runs your game with `python3 start.py` | ❌ No |
| `README.md` | This page | ✅ Only the video link at the bottom |

**How `rps.py` is laid out.** The top has the constants. Below them is every function you need to write, already stubbed. Each stub has a **docstring that is the spec** for that function. A **stub** is the minimum code that lets a function exist and run. Read the docstring, then replace the `TODO` and the placeholder `return` with your own code. The four provided functions sit at the bottom. Do not edit them.

## 🚀 Where to start

You can start as soon as you have your repo. There is no sign-off step.

1. Read this page, then read the docstrings in `rps.py`
2. Sketch pseudocode for `rps()` on paper. It only takes a few minutes and it shows you how the pieces connect
3. Build the functions in the order in the table below
4. Try each function by hand as you finish it

Stuck? Come to office hours.

## 🎮 How the program flows

1. Print the header
2. Ask Player 1 for their name
3. Ask Player 2 for their name
4. Repeat until the user quits:
   1. Show the menu and get a valid choice
   2. Choice **1** plays rock, paper, scissors and announces the winner
   3. Choice **2** prints `Under Construction` (lizard and spock are coming later) and announces no winner
   4. Choice **3** quits
5. Print the closing message

Player names are set once and last for the whole program. They can contain spaces.

## 🔧 Your functions

Build them in this order. It is the same order they appear in `rps.py`.

| # | Function | Job | Calls |
|---|---|---|---|
| 1 | `is_move_good(move)` | Is this a valid move? | nothing |
| 2 | `is_round_winner(move, opponent_move)` | Does the first move beat the second? | nothing |
| 3 | `get_name(player_number)` | Ask for a name. Use a default if empty | `print_error_message` |
| 4 | `get_menu_choice()` | Show the menu. Ask until the choice is valid | `print_menu` |
| 5 | `get_move(player_name)` | Ask for a move. Use a default if invalid | `is_move_good` `print_error_message` |
| 6 | `announce_round_winner(winner_name)` | Print the round result | nothing |
| 7 | `do_round(p1_name, p2_name)` | Play one round. Return `DRAW`, `PLAYER_1` or `PLAYER_2` | `get_move` `is_round_winner` |
| 8 | `announce_winner(winner_name)` | Print the game result | nothing |
| 9 | `do_game(p1_name, p2_name, game_type)` | Play three rounds. Return the winner's name | `do_round` `announce_round_winner` |
| 10 | `rps()` | Connect everything. **Write this last** | all of the above |

**Provided for you:** `print_initial_header`, `print_menu`, `print_error_message` and `print_closer`. Do not change them.

The full spec for each function is the **docstring** inside its stub in `rps.py`. Read it before you write the function.

### Key rules

- A **move** is a one-character string: `"r"`, `"p"` or `"s"`. Uppercase is fine too.
- An **invalid name** is an empty string. Player 1 defaults to `Rocky` and Player 2 defaults to `Creed`.
- An **invalid move** falls back to `"r"` after an error message.
- `do_round` returns a **number** (`DRAW`, `PLAYER_1` or `PLAYER_2`). Functions that deal with a winner's **name** use an empty string `""` for a draw or no winner.
- All three rounds are played every time, even if someone already won the first two.
- Use the constants at the top of `rps.py`. Do not type `3` or `"r"` in the middle of your code.

## ✍️ Exact output

The output must match the spec **exactly**. Copy and paste these strings.

```
Player 1, enter your name: 
Choice --> 
<name>, enter your move: 
Invalid menu choice
ERROR: Illegal name given, using default
ERROR: Illegal move given, using default
<name> wins the round!
This round is a draw!
Congratulations <name>!
You won CS 104 Rock, Paper, Scissors!
No winner!
Under Construction
```

Extra spaces and blank lines are ignored when your output is checked. Spelling, punctuation and capitalization are not. One typo can fail most checks.

## 📺 Sample output

Everything after a prompt on the same line is what the user typed.

**Sample Run 1: a normal game**

```
----------------------------------------
                CS 104
          Rock, Paper, Scissors
----------------------------------------
Player 1, enter your name: Anna Mae
Player 2, enter your name: David Nunez

Menu Options
------------
1) Play rock, paper, scissors
2) Play rock, paper, scissors, lizard, spock
3) Quit

Choice --> 1
Anna Mae, enter your move: r
David Nunez, enter your move: p
David Nunez wins the round!

Anna Mae, enter your move: r
David Nunez, enter your move: r
This round is a draw!

Anna Mae, enter your move: p
David Nunez, enter your move: s
David Nunez wins the round!

Congratulations David Nunez!
You won CS 104 Rock, Paper, Scissors!

Menu Options
------------
1) Play rock, paper, scissors
2) Play rock, paper, scissors, lizard, spock
3) Quit

Choice --> 3

----------------------------------------
           Thanks for playing
          Rock, Paper, Scissors!
----------------------------------------
```

**Sample Run 2: an invalid menu choice and lizard-spock**

```
----------------------------------------
                CS 104
          Rock, Paper, Scissors
----------------------------------------
Player 1, enter your name: Anna Mae
Player 2, enter your name: David Nunez

Menu Options
------------
1) Play rock, paper, scissors
2) Play rock, paper, scissors, lizard, spock
3) Quit

Choice --> 4
Invalid menu choice

Menu Options
------------
1) Play rock, paper, scissors
2) Play rock, paper, scissors, lizard, spock
3) Quit

Choice --> 2
Under Construction
No winner!

Menu Options
------------
1) Play rock, paper, scissors
2) Play rock, paper, scissors, lizard, spock
3) Quit

Choice --> 3

----------------------------------------
           Thanks for playing
          Rock, Paper, Scissors!
----------------------------------------
```

**Sample Run 3: default names, mixed case moves and a tied game**

```
----------------------------------------
                CS 104
          Rock, Paper, Scissors
----------------------------------------
Player 1, enter your name: 
ERROR: Illegal name given, using default
Player 2, enter your name: 
ERROR: Illegal name given, using default

Menu Options
------------
1) Play rock, paper, scissors
2) Play rock, paper, scissors, lizard, spock
3) Quit

Choice --> 1
Rocky, enter your move: R
Creed, enter your move: p
Creed wins the round!

Rocky, enter your move: s
Creed, enter your move: S
This round is a draw!

Rocky, enter your move: S
Creed, enter your move: P
Rocky wins the round!

No winner!

Menu Options
------------
1) Play rock, paper, scissors
2) Play rock, paper, scissors, lizard, spock
3) Quit

Choice --> 3

----------------------------------------
           Thanks for playing
          Rock, Paper, Scissors!
----------------------------------------
```

**Sample Run 4: an invalid move**

```
Anna Mae, enter your move: r
David Nunez, enter your move: a
ERROR: Illegal move given, using default
This round is a draw!
```

David's `a` was invalid, so he played the default `r`. Rock against rock is a draw.

## 🧪 Checking your own work

There is no test file to submit. Your instructor and Tech Fellows run their own checks on your code, so you need to run yours. Play the game and try to break it on purpose.

**Try these by hand**
- Every one of the nine move combinations, in lowercase and uppercase
- An invalid move such as `a`, `rock` or just pressing Enter
- An empty name for Player 1, then for Player 2
- A menu choice of `0`, `4`, `-1`, `abc` and just pressing Enter
- A game where one player wins the first two rounds (are all three still played?)
- A game that ends 1 to 1
- Two games in a row before you quit
- Both players entering the same name

**Check one function at a time while you build.** Call it from the bottom of your file and print what you get:

```python
print(is_move_good("r"))
print(is_round_winner("r", "s"))
```

Remove these lines before you submit.

## ▶️ Running your program

```
python start.py
```
