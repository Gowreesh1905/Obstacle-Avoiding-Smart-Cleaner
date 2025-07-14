# Obstacle-Avoiding-Smart-Floor-Cleaner

This project is a smart floor-cleaning robot that autonomously avoids obstacles and collects dust using a vacuum system. It combines ultrasonic sensing, motor control, and a basic vacuum mechanism in a compact Arduino-based setup.

---

## Features

- Obstacle Avoidance using an ultrasonic distance sensor and servo for directional scanning.
- Dust Collection System using a fan to create suction in a sealed container with a mesh filter.
- Automatic Pathfinding: The robot reverses and changes direction when an obstacle is detected.
- Smooth Motor Control using L293D motor shield and gradual speed changes.

---

## Working Principle

1. **Detection**: An ultrasonic sensor (HC-SR04) mounted on a servo scans for nearby obstacles.
2. **Movement Logic**: If an obstacle is detected within 15 cm, the robot:
   - Stops
   - Moves backward
   - Rotates to the direction with more space (left or right)
   - Continues forward
3. **Cleaning**: A high-speed fan creates negative pressure inside a sealed bottle, drawing in dust through a mesh.

---

## Hardware Used

- Arduino Uno
- L293D Motor Shield (Adafruit AFMotor Library)
- 4x DC Motors (2 per side for balanced drive)
- Ultrasonic Sensor (HC-SR04)
- Servo Motor (SG90 or compatible)
- Mini Fan (vacuum motor)
- Airtight plastic bottle + mesh (for dust collection)
- Power Supply (Battery Pack or Adapter)

---

## Software Used

- Arduino IDE
- Libraries:
  - `AFMotor`
  - `NewPing`
  - `Servo`

---

## Code Structure

The code uses structs to organize the robot's components and state:

- `MotorConfig`: Contains motor instance and speed.
- `SensorData`: Stores distance readings in front, left, and right.
- `RobotState`: Overall robot state including all motors, sensors, and the servo.

## Key Functions

- `lookDirection()`: Rotates servo to scan specific angles
- `readPing()`: Measure distance using ultrasonic sensor
- `moveForward()`, `moveBackward()`: Controlled motor movement
- `turnLeft()`, `turnRight()`: Navigation maneuvers

## Main functional flow:
- `loop()` constantly reads sensor data and decides motion.
- If an obstacle is too close, the robot turns away from it.
- Servo scans left and right using `lookDirection()`.
- Motors are controlled via `moveForward()`, `moveBackward()`, `turnLeft()`, `turnRight()`, and `moveStop()`.