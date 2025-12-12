# 📐 Battleship Game Design Document

## 1. Data Structures and Representation

### 1.1 Game Board
The board is implemented using the `Board` class. Each player maintains **two** $10 \times 10$ boards (Python lists of lists):
* **Own Board (`ship_board`):** Tracks the player's own ships and incoming hits.
* **Tracking Board (`tracking_board`):** Tracks the player's shots fired at the opponent.

| Symbol | Meaning (Own Board) | Meaning (Tracking Board) |
| :---: | :---: | :---: |
| `~` | Water (Empty) | Untried Water |
| `S` | Undamaged Ship Segment | N/A |
| `X` | Hit Ship Segment | Hit (Targeted ship part) |
| `O` | Missed Shot | Miss (Targeted water) |

### 1.2 Ship Objects
The `Ship` class manages the state of each individual vessel. It is initialized with the ship type and length and tracks hits internally.

## 2. Core Game Logic Flow

1.  **Initialization:** `main_game.setup_game()` creates player objects and their boards.
2.  **Ship Placement:** Human placement is handled by `HumanPlayer.manual_place_ships()` with robust coordinate and overlap validation. AI placement is handled by `AIPlayer.random_place_ships()`.
3.  **Game Loop:** `main_game.game_loop()` alternates between player and AI turns.
4.  **Shot Processing:** A target coordinate is passed to the opponent's `Board.receive_shot()` method, which updates the grid and registers the hit on the corresponding `Ship` object.
5.  **State Update:** The attacker's `tracking_board` is updated with the result (`HIT` or `MISS`).
6.  **Win Condition:** After every successful shot, the game checks if `Board.all_ships_sunk()` returns `True`.

## 3. Input Validation

Input validation is essential and occurs at two points:
* **Placement Validation:** Checks for bounds, overlap, and valid orientation.
* **Shot Validation:** Checks for bounds and ensures the target square has not been previously shot (checked against the `tracking_board`).