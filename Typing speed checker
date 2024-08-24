import tkinter as tk
from tkinter import messagebox
import time

class TypingSpeedTest:
    def __init__(self, root):
        self.root = root
        self.root.title("Typing Speed Test")
        self.root.geometry("600x400")

        self.sample_text = "The quick brown fox jumps over the lazy dog."
        self.start_time = None
        self.is_started = False

        self.sample_text_label = tk.Label(root, text=self.sample_text, wraplength=500)
        self.sample_text_label.pack(pady=20)

        self.user_input = tk.Text(root, height=4, width=60)
        self.user_input.pack(pady=20)
        self.user_input.bind('<KeyRelease>', self.check_text)

        self.start_button = tk.Button(root, text="Start Test", command=self.start_test)
        self.start_button.pack(pady=20)

        self.result_label = tk.Label(root, text="")
        self.result_label.pack(pady=20)

    def start_test(self):
        self.user_input.delete("1.0", tk.END)
        self.result_label.config(text="")
        self.start_time = time.time()
        self.is_started = True
        self.start_button.config(state=tk.DISABLED)

    def check_text(self, event):
        if not self.is_started:
            return

        typed_text = self.user_input.get("1.0", tk.END).strip()
        if typed_text == self.sample_text:
            end_time = time.time()
            elapsed_time = end_time - self.start_time
            words = len(self.sample_text.split())
            wpm = (words / (elapsed_time / 60))
            self.result_label.config(text=f"Your typing speed: {wpm:.2f} words per minute")
            self.is_started = False
            self.start_button.config(state=tk.NORMAL)

if __name__ == "__main__":
    root = tk.Tk()
    app = TypingSpeedTest(root)
    root.mainloop()
