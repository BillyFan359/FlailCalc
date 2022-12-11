# Python Flail Calc

import tkinter as tk
from ctypes import windll
windll.shcore.SetProcessDpiAwareness(1)

# Create window
window = tk.Tk()
window.title("Flail Base Power CalcuCambriar")

# Set default background color
window.configure(bg='#000000')

# Create labels
lbl_maxHP = tk.Label(window, text="Max HP:", font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
lbl_maxHP.grid(row=0, column=0)

lbl_200BP = tk.Label(window, text="200:", font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
lbl_200BP.grid(row=1, column=0)

lbl_150BP = tk.Label(window, text="150:", font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
lbl_150BP.grid(row=2, column=0)

lbl_100BP = tk.Label(window, text="100:", font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
lbl_100BP.grid(row=3, column=0)

lbl_80BP = tk.Label(window, text="80:", font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
lbl_80BP.grid(row=4, column=0)

# Create entries
entry_maxHP = tk.Entry(window, width=10, font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
entry_maxHP.grid(row=0, column=1)

entry_200BP = tk.Entry(window, width=10, font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
entry_200BP.grid(row=1, column=1)

entry_150BP = tk.Entry(window, width=10, font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
entry_150BP.grid(row=2, column=1)

entry_100BP = tk.Entry(window, width=10, font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
entry_100BP.grid(row=3, column=1)

entry_80BP = tk.Entry(window, width=10, font=('Cambria', 20), bg='#000000', fg='#FFFFFF')
entry_80BP.grid(row=4, column=1)

# Function for calculating base power
def calculate_bp(maxHP):
    maxHP = int(entry_maxHP.get())
    bp200 = int(maxHP * 2/64)
    bp150 = int(maxHP * 6/64)
    bp100 = int(maxHP * 13/64)
    bp80 = int(maxHP * 22/64)

    entry_200BP.delete(0, "end")
    entry_200BP.insert(0, bp200)
    entry_150BP.delete(0, "end")
    entry_150BP.insert(0, bp150)
    entry_100BP.delete(0, "end")
    entry_100BP.insert(0, bp100)
    entry_80BP.delete(0, "end")
    entry_80BP.insert(0, bp80)

# Set command for calculating on entry change
entry_maxHP.bind("<Button-1>", lambda event: entry_maxHP.delete(0, 'end'))
entry_maxHP.bind("<KeyRelease>", calculate_bp)

window.mainloop()
