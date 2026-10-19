# 🖱️ ESP32 Air Mouse & Presentation Controller

A wireless spatial controller (gyroscopic air mouse) designed for PC control and presentations, inspired by the LG Magic Remote. Developed as part of an engineering design laboratory project.

---

## 📌 Key Features
- **In-Air Cursor Tracking:** Translates 6-axis gyroscope movements (MPU-6050) into smooth on-screen cursor motion (X/Y axes).
- **Deadzone Filtering:** Hardware/software noise filtering to eliminate natural hand tremors and jitter.
- **Dynamic Acceleration:** Non-linear speed scaling (slow motions provide pixel-level precision, rapid flicks allow quick screen crossing).
- **Clutch / Freeze Button:** Allows pausing cursor movement to reposition the hand without affecting cursor placement on screen.
- **Scroll Mode:** Holding a secondary function button converts pitch tilt into vertical mouse wheel scrolling.
- **Dual Operating Modes:** Easily toggle between **Mouse Mode** and **Presentation Mode** (flick gestures change PowerPoint slides).
- **Plug & Play (BLE HID):** Emulates a standard Bluetooth Low Energy Human Interface Device (no additional PC drivers required; works on Windows, macOS, and Linux).

---

## 🛠️ Hardware Stack
- **Microcontroller:** ESP32 NodeMCU (integrated Bluetooth Low Energy 4.2)
- **IMU Sensor:** MPU-6050 (3-axis gyroscope + 3-axis accelerometer)
- **Buttons:** 3x tactile microswitches (LMB, RMB, Clutch/Function switch)
- **Power Supply:** 3.7V Li-Po battery + TP4056 USB-C charging module
- **Enclosure:** Custom 3D-printed ergonomic casing

---

## 🔌 Pinout & Wiring Diagram

| Component | Pin | ESP32 GPIO | Description / Mode |
| :--- | :--- | :--- | :--- |
| **MPU-6050** | VCC | **3V3** | Power supply |
| **MPU-6050** | GND | **GND** | Ground |
| **MPU-6050** | SCL | **GPIO 22** | I2C Clock |
| **MPU-6050** | SDA | **GPIO 21** | I2C Data |
| **Left Click (LMB)** | Pin 1 / Pin 2 | **GPIO 18** / **GND** | `INPUT_PULLUP` (Active LOW) |
| **Right Click (RMB)**| Pin 1 / Pin 2 | **GPIO 19** / **GND** | `INPUT_PULLUP` (Active LOW) |
| **Clutch / Function**| Pin 1 / Pin 2 | **GPIO 23** / **GND** | `INPUT_PULLUP` (Active LOW) |

---

## 📅 Development Roadmap & Milestones (Deadline: Mid-December)
- [x] Component selection, requirements specification, and SMART goal definition.
- [ ] **Milestone 1:** Breadboard prototype: MPU-6050 I2C data acquisition & basic BLE HID cursor movement.
- [ ] **Milestone 2:** Firmware refinement: deadzone filtering, dynamic acceleration, and scroll mode implementation.
- [ ] **Milestone 3:** Power circuit integration (Li-Po + TP4056) and CAD modeling / 3D printing of the casing.
- [ ] **Milestone 4:** Final user testing, latency benchmarking, and project documentation.
