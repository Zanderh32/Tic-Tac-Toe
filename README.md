# Tic-Tac-Toe Game in C#

This project is a simple implementation of the classic **Tic-Tac-Toe** game using **C#**. Two players take turns placing their marks on a 3x3 grid, with the objective to create a line of three symbols either horizontally, vertically, or diagonally.

## Features

- **Two-Player Gameplay**: Players alternate between X and O, taking turns to place their marks on the board.
- **Board Display**: The game prints the current state of the 3x3 grid after each turn.
- **Winner Detection**: The game automatically checks for a winner after each move by evaluating rows, columns, and diagonals.
- **Tie Condition**: The game checks if the board is full without a winner, resulting in a tie.
- **Replay Option**: After each game, players are prompted to start a new game or exit.

## How to Play

1. **Choose First Player**: At the beginning, players are asked who will go first, X or O.
2. **Make a Move**: Players are asked to provide the row and column where they want to place their symbol (e.g., `0 0` for the top-left corner).
3. **Winning**: The game declares the winner if a player forms a line of three symbols.
4. **Tie**: If the board fills up and no one wins, the game declares a tie.
5. **Replay**: Players are prompted if they would like to play another round.

## Project Structure

- **Main Game Logic**:
  - **`printBoard()`**: Displays the current state of the game board.
  - **`makeMove()`**: Allows the player to place their mark on the board.
  - **`checkWinner()`**: Checks whether a player has won the game.
  - **`checkFull()`**: Determines whether the board is full, resulting in a tie.
  - **Replay option**: After the game ends, players can start over or exit.
