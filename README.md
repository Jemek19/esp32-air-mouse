# 🖱️ STM32 Air Mouse & Spatial Controller

A native USB spatial controller (gyroscopic air mouse) implemented in pure C on an ARM Cortex-M4 (STM32F411) microcontroller. Designed to eliminate ergonomic and precision flaws of traditional air mice in desktop computing environments.

Developed as an interdisciplinary project bridging Product Design (Design Laboratory) and Embedded Systems (Microprocessor Engineering).

---

## 📌 Project Overview & Problem Statement

Traditional in-air mice suffer from a major ergonomic defect known as **Click-Jitter**: the physical force applied to press a button inadvertently tilts the hand, causing the cursor to slip away from small desktop GUI targets (such as window close buttons or checkboxes).

This project modernizes the air mouse concept by introducing:

1. **Anti-Jitter Click Stabilization (Core Innovation):** A software algorithm that locks/stabilizes cursor coordinates for 120 ms during switch actuation to ensure pinpoint click accuracy.
2. **Clutch / Freeze Control:** An integrated momentary clutch allowing the user to reposition their arm without displacing the cursor.
3. **Pure C Embedded Architecture:** Developed completely from scratch without high-level abstraction frameworks (no Arduino), utilizing native ARM registers, STM32 HAL, and bare-metal USB middleware.

---

## 🚀 Key Features

- **6-Axis Motion Tracking:** Reads angular velocity and linear acceleration from the MPU-6050 sensor via I2C at 100 Hz.
- **Native USB HID Emulation:** Uses the STM32 on-chip Full-Speed USB controller to emulate a hardware mouse. Plug & Play on Windows, macOS, and Linux (no drivers required).
- **Dynamic Speed Scaling (Acceleration):** Non-linear mapping—slow gestures provide pixel-level precision, while quick flicks enable rapid multi-monitor traversal.
- **Scroll Mode:** Holding the secondary function switch converts pitch inclination into vertical mouse-wheel scrolling.
- **Deadzone Noise Filtering:** Rejects natural physiological tremors when holding the device stationary.

---

## 🛠️ Hardware Specification (Bill of Materials)

| Component | Model / Spec | Role |
| :--- | :--- | :--- |
| **Microcontroller** | STM32F411CEU6 ("Black Pill") | ARM Cortex-M4 @ 100 MHz, Hardware USB FS |
| **IMU Sensor** | MPU-6050 (GY-521 breakout) | 3-axis gyro + 3-axis accelerometer |
| **Switches** | 3x Tactile Microswitches (6x6 mm) | Left Click, Right Click, Clutch/Scroll |
| **Interface** | USB Type-C | Power delivery and native USB HID data |
| **Enclosure** | Custom 3D-printed PETG/PLA | Ergonomic handheld chassis |

---

## 🔌 Hardware Pinout & Wiring

| Peripheral | Sensor / Component Pin | STM32 Pin | Function / Configuration |
| :--- | :--- | :--- | :--- |
| **MPU-6050** | VCC | **3.3V** | Power supply |
| **MPU-6050** | GND | **GND** | Ground reference |
| **MPU-6050** | SCL | **PB8** (or PB6) | I2C1_SCL |
| **MPU-6050** | SDA | **PB9** (or PB7) | I2C1_SDA |
| **Left Click (LMB)** | Pin 1 / Pin 2 | **PA0** / **GND** | GPIO Input (PULL-UP, Active LOW) |
| **Right Click (RMB)**| Pin 1 / Pin 2 | **PA1** / **GND** | GPIO Input (PULL-UP, Active LOW) |
| **Clutch / Function**| Pin 1 / Pin 2 | **PA2** / **GND** | GPIO Input (PULL-UP, Active LOW) |
| **PC Host Link** | Type-C Receptacle | **PA11 / PA12** | USB_OTG_FS (DM / DP) |

---

## 💻 Software Architecture

- **Language:** Pure C (C99 standard)
- **IDE / Toolchain:** STM32CubeIDE & GNU Arm Embedded Toolchain
- **Hardware Abstraction:** STM32Cube HAL / CMSIS
- **USB Stack:** STM32 USB Device Middleware (Class: Human Interface Device / HID Mouse)

---

## 📅 Milestones & Roadmap

- [x] Project scope definition, competitor benchmark & SMART requirements.
- [ ] Milestone 1: Hardware setup & I2C communication with MPU-6050 in C.
- [ ] Milestone 2: Configuration of native USB HID Stack
- [ ] Milestone 3: Programming main functionalities (Click, Scroll, Clutch, etc.).
- [ ] Milestone 4: Implementation of Anti-Jitter / Deadzone algorithms.
- [ ] Milestone 5: Breadboard validation of full mouse functionality.
- [ ] Milestone 6: CAD modeling & 3D printing of the handheld enclosure.
- [ ] Milestone 7: Preparing data and documentation of project.
