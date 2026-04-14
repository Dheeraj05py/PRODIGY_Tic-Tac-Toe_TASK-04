# PRODIGY_Tic-Tac-Toe_TASK-04
The Task is here to perform tic tac toe  app generation via Python langage.
import tkinter as tk
from tkinter import messagebox

# Create window
root = tk.Tk()
root.title("Tic Tac Toe")

current_player = "X"
board = [""] * 9

# Check winner
def check_winner():
    win_combinations = [
        (0,1,2),(3,4,5),(6,7,8),   # rows
        (0,3,6),(1,4,7),(2,5,8),   # columns
        (0,4,8),(2,4,6)            # diagonals
    ]

    for a,b,c in win_combinations:
        if board[a] == board[b] == board[c] and board[a] != "":
            return board[a]

    if "" not in board:
        return "Draw"

    return None

# Handle button click
def click(i):
    global current_player

    if board[i] == "":
        board[i] = current_player
        buttons[i].config(text=current_player)

        winner = check_winner()

        if winner:
            if winner == "Draw":
                messagebox.showinfo("Game Over", "It's a Draw!")
            else:
                messagebox.showinfo("Game Over", f"Player {winner} Wins!")
            reset_game()
        else:
            current_player = "O" if current_player == "X" else "X"

# Reset game
def reset_game():
    global board, current_player
    board = [""] * 9
    current_player = "X"
    for button in buttons:
        button.config(text="")

# Create grid buttons
buttons = []
for i in range(9):
    button = tk.Button(root, text="", font=("Arial", 20), width=5, height=2,
                       command=lambda i=i: click(i))
    button.grid(row=i//3, column=i%3)
    buttons.append(button)

# Reset button
reset_btn = tk.Button(root, text="Reset Game", font=("Arial", 12), command=reset_game)
reset_btn.grid(row=3, column=0, columnspan=3, pady=10)

root.mainloop()[Tic Tac Toe game.py](https://github.com/user-attachments/files/26697191/Tic.Tac.Toe.game.py)
