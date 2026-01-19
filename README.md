# 🤖 RPi5 & ESP32 Robot Web Controller

This project implements a robust, low-latency web interface hosted on a **Raspberry Pi 5** to control an **ESP32-based robot**. The system acts as a bridge, allowing users to drive the robot and manipulate servos via a responsive web dashboard while the ESP32 handles real-time motor control.

## 🌟 Key Features

### 🎮 Zero-Lag Command Loop
We replaced standard timer-based loops with a custom **Async/Await JavaScript architecture**.
* **No Command Buffering:** The browser waits for a "ready" signal from the robot before sending the next command, preventing command pile-up during network lag.
* **Instant Halt:** The robot stops immediately when controls are released, eliminating "runaway robot" scenarios common in standard WiFi controllers.

### 🛑 Advanced Safety Protocols
* **Redundant Stop System:** Uses a "Double-Stop" protocol (sending the stop signal multiple times) to guarantee the robot halts even if a UDP/TCP packet is lost.
* **Touch Safety Guard:** Actively listens for `touchcancel` and `mouseleave` events. If a user's finger slips off the button or an alert interrupts the screen, the motors cut power instantly.

### 📱 Mobile-First Interface
* **3-Axis Manipulation:** Dedicated sliders for controlling 3 independent servo motors (e.g., Base, Arm, Claw).
* **Touch Optimization:** CSS rules (`touch-action: manipulation`) prevent accidental zooming or text selection during rapid driving.
* **Real-Time Telemetry:** AJAX fetch calls provide live feedback from wheel encoders and onboard sensors.

---

## 🛠️ Hardware Setup

### Step 1: ESP32 Wiring
Before uploading the firmware, wire your ESP32 to the motors and drivers (L298N) as shown below. The ESP32 acts as the low-level hardware controller.

**Upload Target:** `ros2_bridge_esp32` (or your specific firmware file)

<img width="1026" height="620" alt="ESP32 Wiring Diagram" src="https://github.com/user-attachments/assets/6e16b48b-c210-473b-b5a7-f2717535e943" />

### Step 2: System Architecture (RPi5 Host)
The Raspberry Pi 5 functions as the central web server and command hub. It hosts the user interface and relays commands to the ESP32 over WiFi or Serial.

<img width="1889" height="859" alt="RPi5 System Architecture" src="https://github.com/user-attachments/assets/42a3c3e1-1f7a-4693-abb5-d2c181710319" />

---

## 🚀 Getting Started

1.  **Flash ESP32:** Upload the motor control code to your ESP32 using the Arduino IDE or PlatformIO.
2.  **Setup RPi5:** Run the web server script on your Raspberry Pi.
3.  **Connect:** Open the RPi5's IP address in your browser to access the control dashboard.
