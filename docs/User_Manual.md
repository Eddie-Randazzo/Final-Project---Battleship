# 📖 Battleship Game User Manual

## 1. Game Start

1.  Navigate to the `src` directory.
2.  Run the command: `python main_game.py`
3.  The game will greet you and immediately begin the **Ship Placement** phase.

## 2. Ship Placement Guide

The game will prompt you for the placement of 5 ships in order (Carrier, Battleship, etc.).

| Ship Type | Length |
| :--- | :--- |
| Carrier | 5 |
| Battleship | 4 |
| Destroyer | 3 |
| Submarine | 3 |
| Patrol Boat | 2 |

**Input Required:**
* **Starting Coordinates:** Enter the row and column, separated by a comma (e.g., `2,5`). Coordinates are **0-indexed** (0 to 9).
* **Orientation:** Enter `H` for Horizontal or `V` for Vertical.

The board will be displayed after each successful placement, showing your current ship layout (`S`).

## 3. Turn-Based Gameplay

During your turn, two boards will be displayed for reference:

| Board | Purpose | Symbols to Look For |
| :--- | :--- | :--- |
| **Your Target Board** | Shows where you have shot on the AI's grid. | `X` (Hit), `O` (Miss), `~` (Untried) |
| **Your Ship Board** | Shows your ships and the damage the AI has inflicted. | `S` (Undamaged Ship), `X` (Hit Ship Segment) |

**To fire a shot:**
1.  Enter your target coordinates (e.g., `8,1`).
2.  The game will announce: `HIT`, `MISS`, or `SUNK [Ship Name]!`.
3.  The turn then passes to the AI.

## 4. Game End

The game concludes when one player has successfully sunk all five of the opponent's ships. The winner will be announced, and the final state of the opponent's ship board will be displayed.