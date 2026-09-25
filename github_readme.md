# Automatic Waste Sorter & Disposal System ♻️🤖

An IoT-based automated waste segregation and disposal system built to automatically classify waste into **Metallic**, **Wet**, and **Dry/Plastic** categories using multi-sensor fusion and a rotating bin turntable mechanism.

---

## 📸 System Overview

This project uses an embedded controller paired with an array of sensors to detect, classify, and sort waste items into designated bins without human intervention.

```
                  +-----------------------+
                  |  Waste Object Inserted|
                  +-----------+-----------+
                              |
                              v
                      [ IR Sensor ] ---> Detects Object Presence & Triggers Buzzer
                              |
              +---------------+---------------+
              |                               |
              v                               v
    [ Inductive Sensor ]             [ Rain/Moisture Sensor ]
    Detects Metal Waste              Detects Wet/Organic Waste
              |                               |
              +---------------+---------------+
                              |
                              v
                     [ Decision Logic ]
                              |
                              v
                 [ ULN Driver + Stepper ]
             Rotates Base to Target Bin Location
                              |
                              v
                  [ Drop Flap Opens ]
              Item Disposed into Correct Bin
```

---

## 📦 Features

- **Multi-Sensor Classification:**
  - **IR Sensor:** Detects presence of waste inserted into the chute.
  - **Inductive Proximity Sensor:** Detects ferrous and conductive metals.
  - **Rain / Moisture Sensor Module:** Detects wet, organic, or liquid-bearing waste.
- **Automated Sorting:** Stepper motor driven by a ULN2003 driver rotates a turntable mechanism to align the matching bin.
- **Audio & Visual Feedback:** Piezo buzzer and indicator LEDs alert users upon successful object detection.
- **Gravity-Fed Disposal:** Mechanized trap door opens to release sorted waste into its respective collection bin.

---

## 🛠️ Hardware Components

| Component | Model / Type | Quantity | Function |
| :--- | :--- | :---: | :--- |
| **Microcontroller** | Arduino Uno / Nano / ESP32 | 1 | Main Controller |
| **Stepper Motor** | 28BYJ-48 (5V DC) | 1 | Turntable Rotation |
| **Motor Driver** | ULN2003 Driver Board | 1 | Stepper Motor Drive |
| **Metal Sensor** | LJ12A3-4-Z/BX Inductive Sensor | 1 | Metal Detection |
| **Moisture Sensor** | FC-37 / YL-83 Rain Sensor | 1 | Wet Waste Detection |
| **Presence Sensor** | TCRT5000 / Standard IR Module | 1 | Entry Detection |
| **Audio Alert** | 5V Active Piezo Buzzer | 1 | Audio Notification |
| **Frame & Structure** | PVC Pipe, Plastic Jars, Acrylic Base | 1 Set | System Frame & Bins |

---

## ⚙️ Pin Mapping & Connections

| Component Pin | Microcontroller Pin | Description |
| :--- | :--- | :--- |
| **IR Sensor Out** | Digital Pin `D2` | Input (Presence Detection) |
| **Inductive Sensor Out** | Digital Pin `D3` | Input (Metal Detection) |
| **Rain Sensor AO/DO** | Digital / Analog Pin `A0` | Input (Moisture Detection) |
| **Piezo Buzzer** | Digital Pin `D4` | Output (Audio Alert) |
| **ULN2003 IN1** | Digital Pin `D8` | Stepper Motor Driver Pin 1 |
| **ULN2003 IN2** | Digital Pin `D9` | Stepper Motor Driver Pin 2 |
| **ULN2003 IN3** | Digital Pin `D10` | Stepper Motor Driver Pin 3 |
| **ULN2003 IN4** | Digital Pin `D11` | Stepper Motor Driver Pin 4 |

---

## 🚦 Logic Matrix

| IR Sensor | Inductive Sensor | Rain Sensor | Category | Target Action |
| :---: | :---: | :---: | :---: | :--- |
| **HIGH** | **HIGH** | *Don't Care* | 🪙 **Metal** | Rotate Turntable to Bin 1 (Metal) |
| **HIGH** | **LOW** | **HIGH** | 🍎 **Wet** | Rotate Turntable to Bin 2 (Wet) |
| **HIGH** | **LOW** | **LOW** | 🥤 **Dry / Plastic** | Rotate Turntable to Bin 3 (Plastic) |
| **LOW** | **LOW** | **LOW** | **Idle** | Return to Home Position |

---

## 💻 Getting Started

### Prerequisites
1. [Arduino IDE](https://www.arduino.cc/en/software) installed on your computer.
2. Required Libraries (e.g., `<Stepper.h>` or `<AccelStepper.h>`).

### Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/automatic-waste-sorter.code.git
   ```
2. Open the main sketch file (`automatic_waste_sorter.ino`) in Arduino IDE.
3. Select your microcontroller board and COM port.
4. Upload the code to your board.

---

## 🔮 Future Improvements

- Integrate load cell weight sensors to monitor bin capacity.
- Add ESP32/Wi-Fi capabilities for IoT-based remote bin level monitoring.
- Implement camera-based computer vision for multi-class recyclable sorting (paper, cardboard, clear plastic).

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.