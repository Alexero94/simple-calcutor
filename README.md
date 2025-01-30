# import tkinter module for gul creation
import tkinter as tk
from tkinter import ttk

# create the window application window
root = tk.Tk()
root.title("Feet to Meter")                     # set window title

# create frame to hold widgets with padding for spacing
frame = ttk.Frame(root, padding="10")
frame.grid(row=0, column=0)                   # place the frame in the window

# -------------------------------- input field
# label for "feet"
feet_Label = ttk.Label(frame, text="feet:")
feet_Label.grid(row=0, column=0)

# Entry widget to take feet input from the user
feet_entry = ttk.Entry(frame, width=10)
feet_entry.grid(row=0, column=1)

# ------------------------------------------------ output field
# Label to indicate result description
result_Label = ttk.Label(frame, text="is equivalent to")
result_Label.grid(row=1, column=0)

# stringVar to store the conversion result dynamically
meters_value = tk.StringVar()

# Label to display the converted meters
meters_Label = ttk.Label(frame, textvariable=meters_value)
meters_Label.grid(row=1, column=1)

# Label to indicates "meters"
unit_Label = ttk.Label(frame, text="meters")
unit_Label.grid(row=1, column=2)

# --------------------------------------------------- conversion
# function
def calculate():
    """convert feet to meters and update the result Label."""
    try:
        feet = feet_entry.get().strip()                       # get input and convert to float
        print("input received:", feet)
        if not feet:
            meters_value.set("")
        feet = float(feet)
        meters = feet * 0.3048                                # conversion formula: 1 foot = 0.3048 meters
        meters_value.set(f"{meters:.4f}")                     # update result with 4 decimal places
        print("converted value:", meters)
        
    except ValueError:
        meters_value.set("Invalid input")                      # handle non- numeric input gracefully
        print("Error: Invalid input")
# --------------------------------------------------------- BUTTON and event
# Binding ---------------------------------------------- 
# Button to trigger the conversion 
calc_button = ttk.Button(frame, text="calculate", command=calculate)
calc_button.grid(row=2, column=1)

# bind the enter key to trigger conversion when passed
root.bind("<Return>", lambda event: calculate())

# ------------------------------------------------------------- START THE GUI 
# --------------------------------------------------------- event loop 
root.mainloop()                                        # Run the Tkinter event loop



