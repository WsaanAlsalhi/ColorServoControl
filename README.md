# ColorServoControl
This Arduino project detects colors using a TCS3200 color sensor and controls a servo motor based on the detected color. It counts the number of green detections and automatically opens the servo (e.g., a door) when 5 greens are detected. It also reacts immediately when blue is detected.

## Features

- Detects Red, Green, and Blue using a TCS3200 sensor.
- Counts green detections and triggers the servo when threshold is reached.
- Opens/closes servo immediately when blue is detected.
- Serial monitor displays real-time color readings and detection counts.
- Prevents repeated counting for the same color detection.

## Components Required

- Arduino board (Uno, Nano, etc.)
- TCS3200 Color Sensor
- Servo motor
- Jumper wires
- Breadboard (optional)

## Pin Connections

| Component    | Arduino Pin |
|--------------|-------------|
| S0           | 22          |
| S1           | 23          |
| S2           | 24          |
| S3           | 25          |
| Sensor Out   | 26          |
| Servo Signal | 5           |

## How It Works

1. The TCS3200 sensor outputs frequency proportional to detected color.
2. Arduino reads red, green, and blue frequencies.
3. If green is dominant and hasn't been detected continuously, it increments the green counter.
4. When green count reaches 5, the servo rotates to 90° for 3 seconds (opens door), then returns to 0°.
5. If blue is dominant, the servo rotates immediately for 3 seconds.
6. Color readings are printed in the Serial Monitor for monitoring.

## Notes

- `threshold` value determines sensitivity for color detection (default 30).
- `noColorRange` prevents false detection when colors are nearly equal (default 20).
- `detected` flag ensures the same color is not counted multiple times during continuous detection.
- Adjust servo angles and delay times according to your hardware.

## Usage

1. Connect the sensor and servo as described above.
2. Upload `ColorServoControl.ino` to your Arduino.
3. Open the Serial Monitor at 9600 baud to see color readings and detection messages.
4. Present green or blue objects to the sensor to test the system.
