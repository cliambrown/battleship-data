# battleship-data
Raw data from my online battleship game vs a probabilistic AI

https://cliambrown.com/battleship/play.php

## battleship_game_moves.csv

The numbers of games that took any given number of moves, binned by AI mode, autoplay status, and game winner.

- _id_ (int): auto-incrementing id
- _ai_mode_
  - 1 = "Random": The AI tries squares purely at random.
  - 2 = "Probability": The AI assumes a completely random ship distribution when calculating the best square. Also uses [diagonal skewing](https://cliambrown.com/battleship/methodology.php).
  - 3 = "Learning": The AI uses data about how all previous players have placed their ships (as well as the normal Probability algorithm) to determine likely ship locations.
- _autoplay_
  - 0 = The user has not activated the autoplay option
  - 1 = The user has activated the autoplay option, which tries squares on the user's behalf at random, at some point during the game
- _ai_win_
  - 0 = The user won the game
  - 1 = The AI opponent won the game
- _moves_ (int): the number of moves made by the winning player
- _games_ (int): the number of games played that fit the above criteria

## battleship_game_squares.csv

The number of times a ship was placed on each square of the board by users and by the AI, binned by game settings as above.

- _id_, _ai_mode_, _autoplay_, _ai_win_: same as above
- _ai_ships_
  - 0 = This row relates to user ship placement
  - 1 = This row relates to AI opponent ship placement
- _square_ (int): Board squares numbered from 1 to 100 (row 1 = 1, 2, 3, ...; row 2 = 11, 12, 13, ...)
- _games_ (int): the number of games played that fit the above criteria

## battleship_games.csv

Information about each individual game played.

- _timestampUTC_: UTC timestamp of the end of the game
- _ai_win_, _moves_, _autoplay_, _ai_mode_id_: same as above
