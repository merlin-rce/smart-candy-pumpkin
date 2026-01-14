# The Smart Candy Pumpkin  
*ESP32-powered interactive Halloween candy dispenser*

---

## Overview

The Smart Candy Pumpkin is an interactive Halloween decoration that automatically dispenses candy when a hand is detected inside the pumpkin.

The project is built around an ESP32 microcontroller, an ultrasonic distance sensor, and a servo-driven 3D-printed candy wheel. When someone reaches into the pumpkin’s mouth, the sensor detects the movement and triggers the mechanism, releasing a portion of candy.

This project combines Arduino programming, basic electronics, and 3D printing into a single build. It was designed to be fully reproducible, well-documented, and suitable for students, makers, and Halloween enthusiasts.

> **Beginner-friendly version available:**  
> A more detailed, step-by-step version of this project is available on Instructables:  
> https://www.instructables.com/The-Smart-Candy-Pumpkin-/


---

## How It Works

1. The ultrasonic sensor continuously measures the distance inside the pumpkin  
2. When a hand is detected below a defined threshold  
3. The ESP32 processes the signal  
4. A servo motor rotates a 3D-printed wheel  
5. Candy is released through the mouth opening  

The system is powered by a rechargeable 3.7 V Li-Po battery and includes USB-C charging for convenience.

---

## Features

- Interactive Halloween decoration  
- ESP32-based control system  
- Ultrasonic hand detection  
- Servo-driven candy dispensing mechanism  
- Fully 3D-printed enclosure  
- Rechargeable battery with USB-C charging  
- Modular and reproducible design  

---

## Technologies Used

- **Microcontroller:** ESP32-S3  
- **Programming language:** Arduino (C++)  
- **Sensor:** HC-SR04 ultrasonic distance sensor  
- **Actuator:** SG90 / MG90S servo motor  
- **Power system:**  
  - 3.7 V Li-Po battery  
  - TP4056 Type-C charging module  
  - DC-DC step-up converter (5 V output)  
- **Fabrication:** FDM 3D printing (PLA)

---

### Folder Overview

- **README.md**  
  Project documentation and build overview

- **code/**  
  Arduino source code for the ESP32  
  - `Smart_Candy_Pumpkin.ino`

- **3d-print/**  
  3D printable files and slicer project  
  - `STL/` – Exported STL files  
  - `BambuStudio/` – Ready-to-print `.3mf` project

- **electronics/**  
  Wiring diagrams and electronic documentation

- **media/**  
  Visual content for documentation  
  - `images/` – Build and final photos  
  - `videos.md` – Demo and time-lapse links

- **LICENSE**  
  Project license
  
---

## Safety Notes

This project involves electronics, soldering, and Li-Po batteries.

- Always double-check battery polarity before powering the circuit  
- Never short-circuit, puncture, or bend Li-Po batteries  
- Do not charge the battery unattended  
- Keep heat sources (soldering iron, hot glue) away from the battery  
- Wear safety glasses when soldering  

---

## 3D Printing Information

- **Material:** PLA  
- **Layer height:** 0.16 mm  
- **Infill:** 15–20 %  
- **Total print time:** approximately 22 hours  
- **Filament usage:** approximately 800 g  

The model is split into multiple parts to simplify printing and assembly.

---

## Code

The Arduino sketch manages:

- Distance measurement using the ultrasonic sensor  
- Detection logic and trigger threshold  
- Servo control for the candy wheel  
- Timing and basic debounce logic  

All pin assignments and key parameters are clearly commented and can be easily modified.

**Source file:**
/code/Smart_Candy_Pumpkin.ino

---
## Possible Improvements

- Adjustable candy portion size  
- LED or sound effects  
- Power-saving sleep mode  
- Different candy sizes or wheel designs  
- External configuration via buttons or Wi-Fi  

---

## Credits

- **3D renders:** Kwama Muhoto Tevin  
- **Workshop support:** CPNE – ELN Department  
- **Build assistance:** Alessio Castorina  

---

## License

This project is shared for educational and personal use.  
You are free to build, modify, and improve it. Attribution is needed.

---

## Conclusion

The Smart Candy Pumpkin is a compact and well-documented project that demonstrates how electronics, programming, and 3D printing can be combined into a functional and interactive Halloween decoration.

If you build your own version, feedback and improvements are always welcome.
