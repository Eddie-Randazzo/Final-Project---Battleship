# 🤖 AI Strategy Documentation

## Project: Command Line Battleship

### 1. Implemented Strategy: Basic Random Fire

The current AI opponent uses a **Basic Random (Dumb Fire)** strategy. This approach is deterministic and relies on pre-calculated randomness rather than intelligent tactical decisions.

#### 1.1 Placement Strategy
* **Method:** Purely Random.
* **Details:** The AI generates random starting coordinates (row, col) and a random orientation (`H` or `V`). It then calls the `Board.is_valid_placement()` method and retries the entire process until a valid position for the ship is found.

#### 1.2 Targeting Strategy
* **Method:** Non-Repeating Random Shot.
* **Details:**
    1.  During initialization, the AI creates a list of all 100 possible board coordinates (0,0 through 9,9) and shuffles this list (`self.untried_targets`).
    2.  In the `AIPlayer.get_shot_target()` method, it simply `pop()`s the last element from this shuffled list.
* **Key Feature:** This strategy guarantees that the AI will never shoot at the same location twice, but it does **not** possess any "intelligence" to follow up on a successful hit (i.e., it will not look for adjacent squares after a HIT).