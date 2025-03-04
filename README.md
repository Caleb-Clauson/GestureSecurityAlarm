# GestureSecurityAlarm
The Gesture-Activated Security Alarm Detects "Thumbs Up" to light a green LED (authorized) and "Not Authorized" for a red LED + 1 second buzzer pulse (alert), using a Teachable Machine model and Arduino via Python serial.

## Overview
This is my IT 254 Project 1 submission—a gesture-based security system combining a TensorFlow vision model with Arduino hardware:
- **Thumbs Up**: Signals "Authorized," lighting a green LED to indicate an authorized gesture.
- **Not Authorized**: Triggers an "Unathorized User" with a red LED and a buzzer pulsing every 1 second.
- **Purpose**: A fun, simple demo of Artificial Intelligence and microelectronics—thumbs-up grants access, other gestures sound a controlled alarm.
- **YouTube Video**: Here is a YouTube video that shows an overview of the project
- https://youtu.be/rwfLX1uKJag

Built using Google's Teachable Machine for training, Python for gesture detection, and serial communication to control an Arduino with two LED lights and a buzzer.

## Files
- **`Python Code`**: Python script for webcam capture, gesture prediction, and serial communication with Arduino.
- **`Arduino Code`**: Arduino sketch to control green LED (pin 13), red LED (pin 12), and buzzer (pin 11) based on serial commands.
- **`labels.txt`**: Class labels from Teachable Machine ("0 Thumbs Up," "1 Not Authorized").
- **`keras_model.h5`**: Trained TensorFlow model (Can be retrained if needed)

## Requirements
- **Hardware**:
  - Arduino (e.g., Uno).
  - Green LED (pin 13), Red LED (pin 12), Buzzer (pin 11)—use 220-330 ohm resistors for LEDs.
  - Breadboard, jumper wires, USB cable.
- **Software**:
  - Python 3.11+ with `tensorflow`, `opencv-python`, `pyserial`, `numpy` (`pip install` these).
  - Arduino IDE for uploading `.ino`.
  - Teachable Machine (optional, used for retraining).

## Setup
1. **Hardware Setup**:
   - Connect green LED (anode to pin 8, cathode to GND via 220-330 ohm resistor).
   - Connect red LED (anode to pin 10, cathode to GND via resistor).
   - Connect buzzer (positive to pin 7, negative to GND—resistor optional if active type).
   - Plug Arduino into your computer via USB.
2. **Software Setup**:
   - Open `Arduino Code` in Arduino IDE, upload to your board (Tools > Port: check your port, e.g., `/dev/cu.usbmodem1101`).
   - Install Python dependencies: `pip install tensorflow opencv-python pyserial numpy`.
   - Update `Pythin Code` with your serial port (e.g., `port = "/dev/cu.usbmodem1101"`) if different.
3. **Running**:
   - Close Arduino IDE to free the serial port.
   - Run: `Python Code` (or your env’s path, e.g., `/Users/calebclauson/Desktop/Python/tf-env/bin/python`).
   - Press 'q' or Esc to exit the program safely.

## Usage
- **Thumbs Up**: Center your hand in the frame (fill ~70-80%)—green LED lights up.
- **Not Authorized**: Other gestures (e.g., peace sign, fingers) trigger red LED + 1s buzzer pulses.
- **Tips**:
  - Ensure good lighting and a centered hand for best detection.
  - Works best when the camera background is blurred out.
  - Test hardware first in Arduino Serial Monitor: type "ON" (green LED) or "OFF" (red LED + buzzer).
  - Close other serial apps (e.g., Arduino IDE) before running Python.

## License
This project is licensed under the MIT License—see [LICENSE](#) for details.

## Notes
- Trained with Teachable Machine’s blurred-background webcam—real-world backgrounds may need model retraining for perfection.
- Usually works the best when the users face is centered in the camera. Usually having the camera bottom start at the shoulders on up.
- See `labels.txt` for class order—adjust thresholds in `AdruinoModel.py` if needed.
