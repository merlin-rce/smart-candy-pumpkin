<div align="center">

# 🎃 The Smart Candy Pumpkin

**An ESP32-powered, motion-activated Halloween candy dispenser**

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![Platform: ESP32](https://img.shields.io/badge/Platform-ESP32--S3-blue.svg)](https://www.espressif.com/en/products/socs/esp32-s3)
[![Made with Arduino](https://img.shields.io/badge/Made%20with-Arduino-teal?logo=arduino)](https://www.arduino.cc/)
[![Buy Me A Coffee](https://img.shields.io/badge/Support-Buy%20Me%20A%20Coffee-yellow?logo=buymeacoffee)](https://buymeacoffee.com/uztiota)

<img src="media/rendu%20affiche%20final.png" alt="Smart Candy Pumpkin" width="600">

*A living, interactive pumpkin that surprises trick-or-treaters by automatically dispensing candy!*

[Features](#-features) • [Quick Start](#-quick-start) • [Build Guide](docs/BUILD_GUIDE.md) • [Parts List](#-bill-of-materials) • [3D Files](#-3d-printed-parts)

</div>

---

## 📖 About This Project

Halloween is that magical time of year when creativity meets fright — and candy flows like never before.

The **Smart Candy Pumpkin** is a motion-activated, ESP32-powered pumpkin that automatically dispenses candy when you place your hand inside its mouth. Inside, a hidden servo and ultrasonic sensor detect movement and trigger a rotating wheel that drops a handful of sweets.

> 🎓 **Made by students:** We're two 17-year-old students from Switzerland, passionate about electronics, 3D printing, and creative projects. This is our first full project!

| Difficulty | Build Time | Cost |
|:----------:|:----------:|:----:|
| ★★★☆☆ Intermediate | 4–6 hours | ~25–40 € |

---

## ✨ Features

- 🖐️ **Motion Detection** — Ultrasonic sensor triggers when a hand enters
- ⚙️ **Automatic Dispensing** — Servo-driven wheel releases candy portions
- 🔋 **Rechargeable** — USB-C charging with 10000mAh Li-Po battery
- 🎨 **Fully 3D Printed** — Complete enclosure with modular design
- 📱 **ESP32-S3 Powered** — Modern microcontroller with plenty of room for expansion
- 🔧 **Easy to Build** — Designed for makers of all levels

---

## 🔧 How It Works

```
┌─────────────────────────────────────────────────────────────┐
│                    SMART CANDY PUMPKIN                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   ┌───────────┐    ┌──────────┐    ┌──────────┐             │
│   │ Ultrasonic│──▶│   ESP32  │───▶│  Servo   │             │
│   │  Sensor   │    │   S3     │    │  Motor   │             │
│   └───────────┘    └──────────┘    └──────────┘             │
│        │                │              │                    │
│   Detects hand    Processes      Rotates candy              │
│   < threshold      signal          wheel                    │
│                                                             │
│   ┌────────────────────────────────────────────┐            │
│   │     Power System (3.7V → 5V)               │            │
│   │  Li-Po ──▶ TP4056 ──▶ DC Booster ──▶ 5V  │            │
│   └────────────────────────────────────────────┘            │
└─────────────────────────────────────────────────────────────┘
```

1. **Detection** — The HC-SR04 ultrasonic sensor continuously monitors the inside of the pumpkin
2. **Processing** — When distance drops below threshold, ESP32 triggers the dispensing sequence
3. **Dispensing** — The servo rotates the 3D-printed wheel, releasing candy through the mouth
4. **Reset** — System returns to monitoring mode, ready for the next trick-or-treater

---

## 🚀 Quick Start

### Prerequisites

- Arduino IDE or PlatformIO
- ESP32 board support installed
- Required libraries: `ESP32Servo`, `Ultrasonic`

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/smart-candy-pumpkin.git
cd smart-candy-pumpkin

# Open in Arduino IDE or PlatformIO
# Select board: ESP32S3 Dev Module
# Upload the code
```

### Pin Configuration

| Component | Pin | Wire Color |
|-----------|-----|------------|
| Servo Signal | GPIO 14 | White/Yellow |
| Ultrasonic TRIG | GPIO 16 | Blue |
| Ultrasonic ECHO | GPIO 15 | Yellow |
| Servo VCC | 5V (from booster) | Red |
| Servo GND | GND | Black |
| Sensor VCC | 5V (from booster) | Red |
| Sensor GND | GND | Black |

---

## 📦 Bill of Materials

### ⚡ Power & Charging

| Component | Qty | Link |
|-----------|:---:|------|
| Type-C Li-Po Charging Module (TP4056 HW-373) | 1 | [AliExpress](https://shorturl.at/nKeuP) |
| 3.7V Li-Po Battery (10000mAh) | 1 | [AliExpress](https://shorturl.at/S42xR) |
| DC-DC Step-Up Converter MT3608 (5V output) | 1 | [AliExpress](https://shorturl.at/hy9fU) |
| Mini Toggle Switch | 1 | — |
| USB Type-C Cable | 1 | — |

### 🧠 Control & Sensors

| Component | Qty | Link |
|-----------|:---:|------|
| ESP32-S3 Dev Board (N16R8 solderless) | 1 | [AliExpress](https://shorturl.at/64Qph) |
| HC-SR04 Ultrasonic Sensor | 1 | [AliExpress](https://shorturl.at/7jW49) |
| Servo Motor (SG90 or MG90S) | 1 | [AliExpress](https://shorturl.at/Mjuy7) |

### 🖨️ 3D Printing & Hardware

| Component | Qty | Link |
|-----------|:---:|------|
| PLA Filament Orange (~800g) | 1 | [BambuLab PLA Matte](https://shorturl.at/Oiv1V) |
| PLA Filament Green (small amount) | 1 | — |
| PLA Filament Black (small amount) | 1 | — |
| Round Magnets D6x2mm | 6-8 | [BambuLab Magnets](https://eu.store.bambulab.com/) |

### 🔧 Tools

- Soldering station + solder wire
- Wire cutter / stripper
- Heat-shrink tubing assortment
- Hot glue gun
- Multimeter (recommended)
- 3D Printer access

---

## 🖨️ 3D Printed Parts

All STL files are located in the [`3d-models/`](3d-models/) folder:

| Part | File | Quantity | Color |
|------|------|:--------:|-------|
| Bottom Base | [`Bottom Base.stl`](3d-models/Bottom%20Base.stl) | 1 | Orange |
| Inner Cover | [`Inner Cover.stl`](3d-models/Inner%20Cover.stl) | 1 | Orange |
| Mid-Mouth Section | [`Mid-Mouth Section.stl`](3d-models/Mid-Mouth%20Section.stl) | 1 | Orange |
| Upper Mouth Section | [`Upper Mouth Section.stl`](3d-models/Upper%20Mouth%20Section.stl) | 1 | Orange |
| Candy Funnel Top | [`Candy Funnel Top.stl`](3d-models/Candy%20Funnel%20Top.stl) | 1 | Orange |
| Stem Cap | [`Stem Cap.stl`](3d-models/Stem%20Cap.stl) | 1 | Green |
| Servo Wheel | [`Servo Wheel.stl`](3d-models/Servo%20Wheel.stl) | 1 | Black |
| Alignment Connector | [`Alignement Connector.stl`](3d-models/Alignement%20Connector.stl) | 6 | Orange |

### Print Settings

| Setting | Value |
|---------|-------|
| Layer Height | 0.16 mm |
| Infill | 15–20% |
| Supports | Yes (except cable channels) |
| Total Time | ~22 hours |
| Total Filament | ~800g |

> 📥 **Ready-to-print profiles available on [MakerWorld](https://makerworld.com/fr/models/1973808-the-smart-candy-pumpkin)**

---

## 💻 Code

The Arduino sketch is located in the `code/` folder. See the full code in [`code/Smart_Candy_Pumpkin.ino`](code/Smart_Candy_Pumpkin.ino).

### Key Configuration

```cpp
#define SERVO_PIN       14    // Servo signal pin
#define TRIG_PIN        16    // Ultrasonic trigger
#define ECHO_PIN        15    // Ultrasonic echo
#define DIST_THRESHOLD  15    // Detection distance (cm)
```

### Required Libraries

Install via Arduino Library Manager:
- **ESP32Servo** by Kevin Harrington & John K. Bennett
- **Ultrasonic** by Erick Simões

### Upload Instructions

1. Open Arduino IDE
2. Go to **File → Preferences** and add ESP32 board URL:
   ```
   https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
   ```
3. Install ESP32 board package via **Tools → Board → Boards Manager**
4. Select **ESP32S3 Dev Module**
5. Connect via USB and select the correct port
6. Click **Upload** (hold BOOT button if needed)

---

## ⚠️ Safety Notes

> **This project involves electronics, soldering, and Li-Po batteries. Please read carefully.**

| ⚡ Electrical | 🔋 Battery | 🔥 Soldering |
|--------------|-----------|-------------|
| Always unplug before wiring | Never puncture or bend | Wear safety glasses |
| Double-check polarity (+/–) | Don't charge unattended | Work in ventilated area |
| Use multimeter to verify | Keep away from heat | Use proper iron stand |

---

## 🗂️ Repository Structure

```
smart-candy-pumpkin/
├── 📄 README.md                    # This file
├── 📄 LICENSE                      # CC BY-NC-SA 4.0
├── 📁 code/                        # Arduino source code
│   └── Smart_Candy_Pumpkin.ino
├── 📁 docs/                        # Documentation
│   └── BUILD_GUIDE.md              # Step-by-step build guide
├── 📁 3d-models/                   # All 3D printable STL files
│   ├── Bottom Base.stl
│   ├── Inner Cover.stl
│   ├── Mid-Mouth Section.stl
│   ├── Upper Mouth Section.stl
│   ├── Candy Funnel Top.stl
│   ├── Stem Cap.stl
│   ├── Servo Wheel.stl
│   └── Alignement Connector.stl
├── 📁 media/                       # Renders & videos
│   ├── rendu *.png                 # 3D renders
│   └── animation *.mp4             # Demo video
└── 📁 .github/
    └── FUNDING.yml                 # Sponsorship info
```

---

## 🔮 Future Improvements

- [ ] Adjustable candy portion size
- [ ] LED eyes with spooky effects
- [ ] Sound effects (screams, laughs)
- [ ] Power-saving deep sleep mode
- [ ] Wi-Fi configuration portal
- [ ] Candy count tracker

---

## 🙏 Acknowledgments

- **3D Renders:** Kwama Muhoto Tevin — for the amazing visuals
- **Workshop Support:** CPNE – ELN Department — for tools and materials
- **Build Assistance:** Alessio Castorina — for the help and fast deliveries

---

## 📚 Resources

| Resource | Description |
|----------|-------------|
| 📖 [Build Guide](docs/BUILD_GUIDE.md) | Detailed step-by-step instructions |
| 🌐 [Instructables](https://www.instructables.com/The-Smart-Candy-Pumpkin/) | Original tutorial with time-lapse videos |
| 🔌 [Circuit Diagram](https://app.cirkitdesigner.com/project/bdcf653b-0cb5-4596-8416-652c75baebec) | Interactive wiring schematic |
| 🖨️ [MakerWorld](https://makerworld.com/fr/models/1973808-the-smart-candy-pumpkin) | Ready-to-print slicer profiles |

---

## 📜 License

This project is licensed under **[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)** — see the [LICENSE](LICENSE) file for details.

You are free to share and adapt this project for **non-commercial purposes**, as long as you give appropriate credit and share your modifications under the same license.

---

<div align="center">

**Made with ❤️ in Switzerland**

If you enjoyed this project, consider supporting us!

[![Buy Me A Coffee](https://img.shields.io/badge/☕-Buy%20Me%20A%20Coffee-orange?style=for-the-badge)](https://buymeacoffee.com/uztiota)

⭐ **Star this repo** if you found it helpful!

</div>
