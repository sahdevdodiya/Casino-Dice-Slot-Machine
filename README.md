# Casino-Dice-Slot-Machine
This is a Python code for a simple game simulator that includes three games: Dice Roll Game, Casino Game, and Slot Machine Game. It uses the Tkinter module to create a graphical user interface (GUI) with buttons to play each game.
import random
import tkinter as tk
from tkinter import messagebox

class GameSimulator:
    def __init__(self, master):
        self.master = master
        self.master.title("Game Simulator")
        
        # Create GUI elements for the dice roll game
        dice_roll_frame = tk.LabelFrame(self.master, text="Dice Roll Game")
        dice_roll_frame.pack(pady=10)
        dice_roll_button = tk.Button(dice_roll_frame, text="Roll Dice", command=self.dice_roll_game)
        dice_roll_button.pack(padx=10, pady=5)
        
        # Create GUI elements for the casino game
        casino_frame = tk.LabelFrame(self.master, text="Casino Game")
        casino_frame.pack(pady=10)
        casino_button = tk.Button(casino_frame, text="Spin Reels", command=self.casino_game)
        casino_button.pack(padx=10, pady=5)
        
        # Create GUI elements for the slot machine game
        slot_machine_frame = tk.LabelFrame(self.master, text="Slot Machine Game")
        slot_machine_frame.pack(pady=10)
        slot_machine_button = tk.Button(slot_machine_frame, text="Spin Reels", command=self.slot_machine_game)
        slot_machine_button.pack(padx=10, pady=5)
    
    def dice_roll_game(self):
        dice_rolls = [random.randint(1, 6) for i in range(3)]
        message = f"Dice rolls: {dice_rolls}\n"
        if dice_rolls[0] == dice_rolls[1] == dice_rolls[2]:
            message += "You win!"
        else:
            sorted_rolls = sorted(dice_rolls)
            if sorted_rolls == list(range(sorted_rolls[0], sorted_rolls[0] + 3)):
                message += "Missed it by that much."
            else:
                message += "You lose."
        messagebox.showinfo("Dice Roll Game", message)
    
    def casino_game(self):
        symbols = ["cherry", "lemon", "orange", "plum", "bell", "bar"]
        reel_1 = random.choice(symbols)
        reel_2 = random.choice(symbols)
        reel_3 = random.choice(symbols)
        message = f"Spin the reels...\n\n{reel_1}  {reel_2}  {reel_3}\n"
        if reel_1 == reel_2 == reel_3:
            message += "Jackpot!"
        elif reel_1 == reel_2 or reel_1 == reel_3 or reel_2 == reel_3:
            message += "You win a small prize."
        else:
            message += "You lose."
        messagebox.showinfo("Casino Game", message)
    
    def slot_machine_game(self):
        symbols = ["cherry", "lemon", "orange", "plum", "bell", "bar"]
        reels = [random.choice(symbols) for i in range(3)]
        message = f"Spin the reels...\n\n{'  '.join(reels)}\n"
        if reels[0] == reels[1] == reels[2]:
            message += "You win!"
        else:
            message += "You lose."
        messagebox.showinfo("Slot Machine Game", message)

# Create the main window for the app
root = tk.Tk()
root.geometry("300x350")

# Create an instance of the GameSimulator class
game_simulator = Game
