# 📖 Smart Candy Pumpkin — Complete Build Guide

This guide contains detailed step-by-step instructions for building the Smart Candy Pumpkin from start to finish.

> 🎥 **Video tutorials available:** Check out our [Instructables page](https://www.instructables.com/The-Smart-Candy-Pumpkin-/) for time-lapse videos of each step.

---

## Table of Contents

1. [Safety & Preparation](#1-safety--preparation)
2. [Wiring Overview](#2-wiring-overview)
3. [Adding the Power Switch](#3-adding-the-power-switch)
4. [Connecting Charger to DC Booster](#4-connecting-the-charger-to-the-dc-booster)
5. [Connecting Battery to Charger](#5-connecting-the-battery-to-the-charging-module)
6. [Wiring the Ultrasonic Sensor](#6-wiring-the-ultrasonic-sensor)
7. [Preparing the Servo Connection](#7-preparing-the-servo-connection)
8. [Power Wiring to Booster](#8-power-wiring-servo--sensor-to-the-booster)
9. [Wiring to ESP32](#9-wiring-everything-to-the-esp32)
10. [Uploading the Code](#10-uploading-the-code-to-the-esp32)
11. [3D Printing](#11-3d-printing-the-pumpkin)
12. [Gluing Stem & Placing Magnets](#12-gluing-the-pumpkin-stem-and-placing-magnets)
13. [Assembling Candy Funnel](#13-assembling-the-candy-funnel-with-upper-mouth-section)
14. [Routing Wires](#14-routing-the-wires-to-the-bottom-base)
15. [Mounting Electronics](#15-mounting-the-electronics-in-the-bottom-base)
16. [Final Assembly](#16-final-pumpkin-assembly)
17. [Testing & Completion](#17-the-pumpkin-comes-to-life)

---

## 1. Safety & Preparation

Before bringing your pumpkin to life, let's make sure everything stays safe — both for you and your workspace.

### ⚠️ Safety Guidelines

| Category | Precautions |
|----------|-------------|
| **Electrical** | Always unplug power before wiring or soldering. Double-check all battery polarities (+/–). |
| **Li-Po Battery** | Handle with care — never bend, puncture, or charge unattended. Place on non-flammable surface while charging. |
| **Soldering** | Wear protective glasses, work in ventilated area, use proper stand for your iron. |
| **3D Printing** | Let parts cool completely before assembly. Trim off sharp edges or support marks. |

### 💡 Pro Tips

- A multimeter is your best friend — always check voltage before powering your ESP32
- Hot glue and Li-Po cells don't mix! Keep glue away from batteries and wires

---

## 2. Wiring Overview

Before starting the build, here's how every component connects together.

### 📐 Full Circuit Diagram

👉 **Interactive circuit:** [View on Cirkit Designer](https://app.cirkitdesigner.com/project/bdcf653b-0cb5-4596-8416-652c75baebec)

### Pin Connections

#### Servo Motor
| Wire | Connection |
|------|------------|
| White (Signal) | GPIO 14 on ESP32 |
| Red (VCC) | 5V output from booster |
| Black (GND) | GND output from booster |

#### Ultrasonic Sensor (HC-SR04)
| Pin | Connection |
|-----|------------|
| VCC | 5V output from booster |
| GND | GND output from booster |
| TRIG | GPIO 16 (blue wire) |
| ECHO | GPIO 15 (yellow wire) |

#### Power System
```
Battery (3.7V) → HW-373 Type-C Charger
├── Red (+) → B+
└── Black (–) → B-

HW-373 Output → MT3608 Booster Input
├── OUT+ → VIN+ (red)
└── OUT– → VIN– (black)
```

> 🧠 **Tip:** Always double-check the polarity (+/–) before powering on. A wrong connection can damage the ESP32 or booster.

---

## 3. Adding the Power Switch

We're adding a small toggle switch to control power between the battery and the circuit.

### Steps

1. **Trim the switch** — It's a 3-pin toggle. Cut off the third pin (unused)
2. **Cut the battery's red wire** in half. You now have two ends: one from the battery, one going to the circuit
3. **Strip & tin** both ends with a bit of solder
4. **Slide heat-shrink tube** on the battery side before soldering
5. **Solder connections:**
   - Battery wire → left lug
   - Circuit wire → right lug
6. **Shrink the tubing** with a lighter — quick passes, no flames near the Li-Po!

✅ You now have a clean power switch inline with the battery.

---

## 4. Connecting the Charger to the DC Booster

Linking the Type-C charging module to the DC-DC booster for 5V output.

### Steps

1. **Prepare two short wires** — just long enough from charger to booster
2. **Strip and tin** both ends of each wire
3. **Solder to charging module** — use the output pads (NOT BAT+/BAT–)
4. **Solder to DC booster** — VIN+ and VIN– pads
5. **Verify polarity:** + → +, – → –
6. **Adjust output voltage:**
   - Plug USB-C cable into charger
   - Use small screwdriver to turn the adjustment screw
   - Adjust until output reads **5.0V** (check with multimeter)
7. **Add heat-shrink tubing** for insulation

✅ Charger and booster now deliver clean 5V output!

---

## 5. Connecting the Battery to the Charging Module

Soldering the Li-Po battery directly to the Type-C charging board.

### Steps

1. Take the battery leads:
   - **Red = +**
   - **Black = –**
2. **Tin both ends**
3. **Solder:**
   - Red → B+
   - Black → B–
4. **Add heat-shrink** before soldering, then slide over joints
5. **Shrink carefully** with lighter — short passes, keep flame away from Li-Po!

✅ Battery is now safely connected to the charger.

---

## 6. Wiring the Ultrasonic Sensor

Preparing clean, removable connections for the HC-SR04 sensor.

### Steps

1. **Prepare 4-wire ribbon cable** (red, black, yellow, blue) with female connector end
2. **Tin all four wires** on the open side
3. **Remove default header** from sensor by adding solder to pins
4. **Solder wires directly to sensor:**
   | Pin | Wire Color |
   |-----|------------|
   | VCC | Red 🔴 |
   | GND | Black ⚫ |
   | Echo | Yellow 🟡 |
   | Trig | Blue 🔵 |
5. **Prepare male pins:** Take 4 male-to-male pins, tin shorter side
6. **Solder each color wire** to matching pin
7. **Add heat-shrink** over every joint

✅ You now have a plug-and-play ultrasonic sensor cable!

---

## 7. Preparing the Servo Connection

Creating a detachable connector for the servo motor.

### Steps

1. **Cut three short wires:** black, red, yellow
2. **Strip and tin** both ends of each wire
3. **Take three male-to-male pins** and solder wires to short side
4. **Add heat-shrink tubing** and shrink with lighter
5. **Match colors on servo side:**
   | Servo Wire | Your Wire |
   |------------|-----------|
   | Black | Black ⚫ |
   | Red | Red 🔴 |
   | White | Yellow 🟡 |

✅ You have a detachable 3-pin servo connector!

---

## 8. Power Wiring: Servo + Sensor to the Booster

Connecting 5V and GND for servo and sensor to the DC booster output.

### Steps

**For 5V (Red wires):**
1. Take red wire from servo + red wire from sensor + extra red wire (for ESP32)
2. Strip and tin loose ends
3. Twist all three red wires together
4. Slide small heat-shrink behind them
5. Solder bundle to **V-OUT+** pad on DC booster
6. Add larger heat-shrink over the group

**For GND (Black wires):**
1. Repeat same process with black wires
2. Twist together, tin, solder to **V-OUT–**
3. Finish with heat-shrink tubing

✅ Servo, sensor, and ESP32 now share 5V and ground from booster!

---

## 9. Wiring Everything to the ESP32

Final soldering connections to the ESP32 board.

### Signal Connections

| Wire | ESP32 Pin |
|------|-----------|
| Trigger (blue) | GPIO 16 |
| Echo (yellow) | GPIO 15 |
| Servo signal (yellow) | GPIO 14 |

### Power Connections

| Wire | ESP32 Pin |
|------|-----------|
| Red (from booster V-OUT+) | 5V |
| Black (from booster V-OUT–) | GND |

### Steps

1. **Tin each wire**
2. **Insert through corresponding hole** on ESP32
3. **Solder from back side**
4. **Trim wire ends** so they don't stick out

> ⚠️ **Tip:** Keep all connections on the same side of the board for clean, flat assembly.

✅ ESP32 is fully wired and ready!

---

## 10. Uploading the Code to the ESP32

Time to give your pumpkin a brain! 🧠🎃

### Step 1: Install Arduino IDE

Download from [arduino.cc](https://www.arduino.cc/en/software)

### Step 2: Add ESP32 Board Support

1. Open Arduino IDE → **File → Preferences**
2. In "Additional Boards Manager URLs", paste:
   ```
   https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
   ```
3. Click OK

### Step 3: Install ESP32 Package

1. Go to **Tools → Board → Boards Manager**
2. Search for "esp32"
3. Install package by **Espressif Systems**
4. Select **Tools → Board → ESP32 Arduino → ESP32S3 Dev Module**

### Step 4: Install Required Libraries

Go to **Sketch → Include Library → Manage Libraries** and install:
- **ESP32Servo** by Kevin Harrington & John K. Bennett
- **Ultrasonic** by Erick Simões

### Step 5: Configure the Code

Open `code/Smart_Candy_Pumpkin.ino` and verify pins match your build:
```cpp
#define SERVO_PIN       14
#define TRIG_PIN        16
#define ECHO_PIN        15
#define DIST_THRESHOLD  15  // cm
```

### Step 6: Upload

1. Connect ESP32 via USB (use the USB port, not UART)
2. Select correct port under **Tools → Port**
3. Click **Upload (▶)**
4. If upload doesn't start, hold **BOOT** button until flashing begins

### Testing

1. Open **Serial Monitor** (115200 baud)
2. Move hand inside pumpkin area
3. Servo should spin and "drop candy"

✅ ESP32 is programmed!

---

## 11. 3D Printing the Pumpkin

The model is split into 8 printable parts for easy assembly.

### Parts List

| Part | Color | Qty |
|------|-------|:---:|
| Bottom Base | Orange 🟠 | 1 |
| Inner Cover | Orange 🟠 | 1 |
| Mid-Mouth Section | Orange 🟠 | 1 |
| Upper Mouth Section | Orange 🟠 | 1 |
| Candy Funnel Top | Orange 🟠 | 1 |
| Stem Cap | Green 🟢 | 1 |
| Servo Wheel | Black ⚫ | 1 |
| Alignment Connector | Orange 🟠 | 6 |

### Print Settings

| Setting | Value |
|---------|-------|
| Layer Height | 0.16 mm |
| Infill | 15–20% |
| Plate | Textured build plate |
| Supports | Normal (see note below) |

> ⚠️ **Important:** Disable supports inside the cable management area of the Bottom Base — otherwise wires won't fit through!

### Stats

- ⏱️ Total print time: ~22 hours (Bambu Lab P1S)
- 🧵 Filament used: ~800g PLA

### Download Files

- STL files included in repository root
- Ready-to-print profiles: [MakerWorld](https://makerworld.com/fr/models/1973808-the-smart-candy-pumpkin)

✅ Print all parts before continuing!

---

## 12. Gluing the Pumpkin Stem and Placing Magnets

### Attaching the Stem

1. Take the small **green stem**
2. Apply small drop of **super glue** to center of top cap
3. Press firmly for a few seconds
4. Let dry

### Placing the Magnets

The underside of the top cap has small round holes for magnets.

> ⚠️ **Critical:** Check magnet polarity before inserting!

1. Take two magnets and stick them together (shows attracting faces)
2. Slide one magnet into hole (should fit snugly)
3. For matching part, use second magnet (still attached) to find correct orientation
4. Separate gently and insert second magnet

> ✨ No glue needed — friction fit holds them in place!

---

## 13. Assembling the Candy Funnel with Upper Mouth Section

### Steps

1. **Place servo motor** into dedicated slot in Mid-Mouth Section
2. **Insert black Servo Wheel** from other side
3. **Secure with screw** from servo kit
   - ⚠️ Don't overtighten — servo needs to rotate freely!
4. **Insert ultrasonic sensor** into its opening
5. **Pass wires** through cable hole behind it
6. **Add double-sided tape** under sensor to secure (no tape under servo!)
7. **Align Candy Funnel Top** with Upper Mouth Section
8. **Insert plastic connection cylinders** into large holes
9. **Apply glue** on cylinders
10. **Press parts together** firmly until glue sets

> ⚠️ Don't attach this assembly to rest of pumpkin yet!

✅ Servo and sensor installed, funnel attached!

---

## 14. Routing the Wires to the Bottom Base

Passing all wires through the built-in cable tunnel.

### Steps

1. Take a piece of **fishing line** (or thin strong wire)
2. **Tie servo and sensor wires** together at one end of fishing line
3. From Bottom Base, **feed fishing line up** through cable passage
4. **Pull fishing line back down**, bringing wires with it
   - Go slowly — passage is tight!
5. **Tape or glue wires** along top edge inside pumpkin

✅ Wires routed cleanly from top to bottom!

---

## 15. Mounting the Electronics in the Bottom Base

### Placement

1. **Battery** — Stick in center with double-sided tape. Route cables behind it.
2. **ESP32** — Place at bottom, secure with tape
3. **Power switch** — Insert into side hole
4. **Charging module** — Mount in slot, align USB-C port with external hole
5. **DC booster** — Stick next to charger with tape
6. **Flatten wires** along walls for clean finish

✅ All electronics securely placed!

---

## 16. Final Pumpkin Assembly

### Steps

1. Place **Inner Cover** — rests on inner ledge in Bottom Base
   - ⚠️ Don't glue! Keeps it removable for maintenance
2. Take **Bottom Base** and **Mid-Mouth Section**
3. Insert **plastic connection cylinders** into large holes
4. Apply **small drop of glue** on each cylinder
5. **Press parts together** carefully until aligned
6. Hold a few seconds for glue to set

✅ Pumpkin body fully assembled!

---

## 17. The Pumpkin Comes to Life!

🎉 **Congratulations!** Your Smart Candy Pumpkin is complete!

### Final Steps

1. Fill the funnel with M&M's or your favorite candies 🍬
2. Flip the power switch
3. Watch the magic happen!

### Troubleshooting

| Issue | Solution |
|-------|----------|
| Servo doesn't move | Check wiring, verify 5V from booster |
| No detection | Adjust `DIST_THRESHOLD` in code |
| Servo moves wrong direction | Swap open/close angles in code |
| ESP32 won't upload | Hold BOOT button during upload |

---

## 🎃 Enjoy Your Creation!

You've built a full Halloween robot — great job! 👏

### Share Your Build

- 💬 Leave a comment on our [Instructables page](https://www.instructables.com/The-Smart-Candy-Pumpkin/)
- ☕ [Support us on Buy Me a Coffee](https://buymeacoffee.com/uztiota)
- ⭐ Star this repository!

---

*Made with 🎃 in Switzerland*
