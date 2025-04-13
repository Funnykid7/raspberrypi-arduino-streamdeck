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
* OS must be running on X11 display server, not     
  Wayland
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

## Software Setup
1. **File Location:** Save both the Python script and the JSON setup file in the same directory.
2. **Edit Button bindings:** To edit the JSON config file, open a new terminal window, `cd` to the directory where your scripts are saved. Then type `nano arduino_streamdeck_config.json` and hit enter. Make your desired changes and save the file.
3. **Program Exectution:** Open a new terminal window and `cd` to the directory where you scripts are saved. To run the python file type `sudo python3 arduino_streamdeck.py` and hit enter. **WARNING** do not close this terminal window, only minimize it.
