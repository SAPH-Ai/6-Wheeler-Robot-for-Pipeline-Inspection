# 🚜 6-Wheeler Robot for Pipeline Inspection

![Status](https://img.shields.io/badge/Status-Prototype-orange)
![Hardware](https://img.shields.io/badge/Hardware-Arduino_Mega%20%7C%20Uno-teal)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📖 Overview

The **6-Wheeler Pipeline Inspection Robot** is a specialized subsystem of the *AI-Assisted Drainage & Sewage Maintenance* project. Designed to tackle the dangerous and inaccessible conditions of underground sewage lines, this robot replaces manual labor in hazardous environments.

Leveraging **Artificial Intelligence** and a rugged **6-wheel drive system**, it autonomously navigates pipelines to identify blockages, detect explosive gases like Methane ($CH_4$), and perform targeted cleaning operations.

---

## ✨ Key Features

### 🧠 AI-Powered Detection
* **Computer Vision:** Utilizes **OpenCV** and **YOLOv8** trained on a custom dataset to identify debris, cracks, and obstacles in real-time.
* **Autonomous Navigation:** The bot processes visual data to make navigation decisions without human intervention.


### 🛡️ Safety & Environmental Sensing
* **Gas Detection:** Integrated **MQ-135 sensor** monitors air quality.
    * *Good:* < 20%
    * *Bad:* > 20%
    * *Danger:* > 50% (Triggers Methane mitigation protocols).
* **Live Monitoring:** Streams real-time HD video and environmental data (Temperature/Humidity via DHT11) to the host PC.

### 🦾 Active Maintenance
* **Robotic Arm:** A mechanical arm assembly capable of gripping and removing solid debris.
* **Chemical Mitigation:** Automatically sprays neutralizing solutions (e.g., NaOH) when hazardous gas levels are detected.
* **Sanitization:** Onboard UV LEDs and sanitizer nozzles disinfect contaminated zones.

---

## ⚙️ System Architecture

The robot's logic is distributed between two microcontrollers for efficient processing:

1.  **Arduino Mega (Main Controller):** Handles the locomotion (6-wheel drive), robotic arm manipulation, and communication.
2.  **Arduino Uno (Sensor Node):** Manages the sensor array (Gas, LDR, Sonar) and sanitization peripherals.

### 🔌 Connection Diagram


[Image of Arduino Mega circuit diagram]


---

## 🛠️ Hardware Specifications

| Component | Function |
| :--- | :--- |
| **Microcontrollers** | Arduino Mega 2560, Arduino Uno |
| **Drive System** | 6x High-Torque Gear Motors (L298N Driver) |
| **Vision** | USB HD Camera, IR Camera for dark zones |
| **Sensors** | MQ-135 (Gas), LDR (Light), HC-SR04 (Sonar), DHT11 |
| **Actuators** | 7x Servo Motors (Arm), Water/Chemical Pumps |
| **Power** | 3S LiPo Battery with LM2596 Buck Converter |

---

## 🧩 How It Works

1.  **Inspection:** The robot enters the pipeline, using its **6-wheel traction** to traverse sludge and rugged terrain.
2.  **Detection:**
    * **Sonar** checks for physical blockages (< 30cm trigger distance).
    * **AI Camera** scans for specific trash types or structural damage.
    * **Gas Sensors** sniff for Methane.
3.  **Action:**
    * If **Debris** is found -> **Robotic Arm** engages to remove it.
    * If **Methane** is high -> **Chemical Nozzle** sprays oxidizers.
    * If **Bacteria** risk is high -> **UV Lights** activate.

---

## 🚀 Installation & Usage

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/YourRepo/6-Wheeler-Pipeline-Bot.git](https://github.com/YourRepo/6-Wheeler-Pipeline-Bot.git)
    ```
2.  **Upload Firmware:**
    * Flash `Drainage_System.ino` to the Arduino Mega.
    * Flash `Sensor_Node.ino` to the Arduino Uno.
3.  **Run AI Controller:**
    * Connect the robot to the Host PC via USB/Bluetooth (HC-05).
    * Run the Python script:
        ```bash
        python ai_detection_main.py
        ```
4.  **Deploy:** Place the robot in the inspection zone and monitor the dashboard.

---

## 📉 Impact
* **Cost Reduction:** Significantly lowers maintenance costs compared to manual cleaning.
* **Safety:** Removes human workers from "inhuman" and explosive sewage environments.



---
