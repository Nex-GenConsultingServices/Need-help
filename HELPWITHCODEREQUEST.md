# Need-help

Please help me if you are good with Tkinter code.

Stuck with some code for a Graphic User Interface (GUI)
for a AI Assistive Chatbot. The code that I am currently
having problems with will be below including the rest of
the code as well as the modules that I have imported for
the GUI and the rest of the code that I am currently
writing.

MODULES:

from tqdm import tqdm
from datetime import datetime
from tkinter import Tk
from tkinter import scrolledtext
import random
import time
import os
import webbrowser
import subprocess
import platform
import math
import sys
import re

Code:

class AmeliaChatbot:
    def __init__(self, root):
        self.root = root
        self.root.title("Amelia Chatbot")
        
        self.chat_display = scrolledtext.ScrolledText(root, wrap=Tk.WORD, width=50, height=20)
        self.chat_display.pack(pady=10)
        self.chat_display.config(state=Tk.DISABLED)

        self.user_input = Tk.Entry(root, width=50)
        self.user_input.pack(pady=10)
        self.user_input.bind("<Return>", self.send_message)

        self.send_button = Tk.Button(root, text="Send", command=self.send_message)
        self.send_button.pack(pady=10)

        self.responses = {
            "hello": ["Hi there!", "Hello!", "Hey! How can I assist you today?"],
            "how are you": ["I'm just a bunch of code, but I'm doing great! How about you?", "I'm an AI, so I don't have feelings, but I'm here to help you!"],
            "bye": ["Goodbye!", "See you later!", "Have a great day!"]
        }

    def send_message(self, event=None):
        user_message = self.user_input.get().lower()  # Convert to lowercase for consistency
        if user_message:
            self.chat_display.config(state=Tk.NORMAL)
            self.chat_display.insert(Tk.END, "You: " + user_message + "\n")
            self.chat_display.config(state=Tk.DISABLED)

            response = self.get_response(user_message)
            self.chat_display.config(state=Tk.NORMAL)
            self.chat_display.insert(Tk.END, "Amelia: " + response + "\n")
            self.chat_display.config(state=Tk.DISABLED)

            self.user_input.delete(0, Tk.END)

    def get_response(self, message):
        # Check if the message has a predefined response
        if message in self.responses:
            response = random.choice(self.responses[message])
        else:
            response = self.custom_response_logic(message)
        return response

    def custom_response_logic(self, message):
        # Default response if no predefined response is found
        return "I'm not sure how to respond to that. Could you please clarify?"

    def add_custom_response(self, trigger, responses):
        # Add or update custom responses for a specific trigger
        self.responses[trigger] = responses

if __name__ == "__main__":
    root = Tk.tk()
    app = AmeliaChatbot(root)
    
    # Example of adding custom responses
    app.add_custom_response("what is your name", ["My name is Amelia.", "I'm Amelia, your AI assistant."])
    app.add_custom_response("thank you", ["You're welcome!", "Happy to help!"])
    
    root.mainloop()


The code that I am having troubles with is on line 83.
the code is root = Tk.tk()

