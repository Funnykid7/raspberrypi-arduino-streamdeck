# Raspberry Pi Arduino Stream Deck

Turn a simple Arduino Uno with four buttons into a customizable macro pad / Stream Deck emulator for your Raspberry Pi!

This project allows you to map button presses on an Arduino to various actions on your Raspberry Pi, including:

* **Simulating Key Presses:** Act as any keyboard key (e.g., Arrow keys, WASD, modifiers like Shift/Ctrl). Supports press-and-hold.
* **Running Shell Commands:** Launch applications, run scripts, or execute any command line instruction.
* **Typing Text:** Automatically type predefined sentences or code snippets.
* **Executing Key Sequences (Macros):** Perform complex multi-key actions like copy/paste (Ctrl+C -> Ctrl+V) with optional delays.
* **Opening Websites:** Quickly launch your favorite URLs.



## Hardware Requirements

* Raspberry Pi (Tested on Pi 5, should work on older models with sufficient performance)
* Arduino Uno R3 (or compatible board like Nano, etc.)
* 4 x Push Buttons (Tactile Switches)
* Breadboard
* Jumper Wires
* USB Cable (Type A to Type B for Arduino Uno)

## Software Requirements

* Raspberry Pi OS (or a similar Linux distribution)
* Python 3
* Arduino IDE (Installed on any computer to upload the sketch to the Arduino)
* Required Python Libraries: `pyserial`, `pynput`
* A terminal emulator application on the Pi (e.g., `lxterminal`, `gnome-terminal`) for the `run_command` action if launching terminals.

## Hardware Setup

1.  **Place Buttons:** Put the four push buttons onto the breadboard.
2.  **Ground:** Connect one leg of *each* button to a common ground rail on the breadboard. Connect this ground rail to a `GND` pin on the Arduino.
3.  **Signal Pins:** Connect the other leg of each button to the Arduino's digital input pins:
    * Button 1 -> Pin 2 (Will send 'U'/'u')
    * Button 2 -> Pin 3 (Will send 'L'/'l')
    * Button 3 -> Pin 4 (Will send 'D'/'d')
    * Button 4 -> Pin 5 (Will send 'R'/'r')
4.  *(Internal pull-up resistors are used in the Arduino code, so no external resistors are needed for the buttons).*
