# TMCD-Amplifier-Tripolar-MOSFET-Class-D-Amplifier
# 🔊 12V IRF540N MOSFET CLASS-D AMPLIFIER (H-BRIDGE CONFIGURATION)

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-orange.svg)](https://creativecommons.org/licenses/by-nc-nd/4.0/)
![Project Poster](tmcd.png)

---

## ⚙️ Project Overview

This project is a **12V High-Efficiency Class-D Audio Amplifier** designed using **IRF540N MOSFETs** in a **full H-bridge configuration**, driven by **LM393**, **NE555**, and **transistor driver stages**.  
It efficiently converts low-power analog input signals into high-power digital PWM signals, delivering amplified output to the speaker with **minimal power loss** and **excellent sound clarity**.

Unlike traditional two-MOSFET Class-D amplifiers, this design uses an **H-bridge configuration**—similar to motor driver ICs like **L298N or IR2111**—which **doubles output power**, eliminates DC blocking capacitors, and provides **symmetrical drive voltage across the load**.

---

## 🖼️ Circuit Diagram 

![TMCD Amplifier](tmcd.jpg)

---

## 🏷️ Labels

`#TMCD Amplifier` `#H-bridge amplifier`
`#efficient amplifier`
`#ClassD` `#Amplifier` `#ElectronicsProject` `#AudioAmplifier` `#PWM`  
`#HBridge` `#MOSFET` `#NE555` `#LM393` `#AnalogToPWM` `#DIYProject`  

---

## 📘 Table of Contents
1. [Features and Advantages](#-features-and-advantages)
2. [Working Principle](#-working-principle)
3. [Circuit Description](#-circuit-description)
4. [Stage-wise Working](#-stage-wise-working)
5. [Why H-Bridge Is More Efficient](#-why-h-bridge-is-more-efficient)
6. [Component List](#-component-list)
7. [Applications](#-applications)
8. [Author Info](#-author-info)

---

## 🌟 Features and Advantages

- Operates at **12V DC**, ideal for automotive or battery-powered audio systems.  
- Uses **H-Bridge MOSFET configuration** → true push-pull operation.  
- **High efficiency (≈90%)** due to Class-D switching principle.  
- **No output capacitor required**, direct symmetrical output to the speaker.  
- Compact, low-heat design with excellent power delivery.  
- Can drive **4Ω–8Ω speakers** easily at high power.  
- Uses **LM393 comparator** for precise signal modulation.  
- **NE555** generates stable triangle wave for PWM carrier.  
- **BD139/BD140** transistors form intermediate driver stages for current boosting.  
- Optional upgrade to **IR2111 MOSFET driver IC** for even higher performance.  

---

## ⚡ Working Principle

The circuit works on the **Pulse Width Modulation (PWM)** principle.  
The **audio input signal** is compared with a **triangle waveform** to generate a **PWM signal**, which switches the MOSFETs at high frequency to reproduce the amplified version of the input sound at the output.

---

## 🔩 Circuit Description

This Class-D amplifier circuit consists of four main stages:

1. **Triangle Wave Generator (NE555)**  
2. **Comparator / Modulator (LM393)**  
3. **Driver Stage (BD139–BD140 or IR2111)**  
4. **H-Bridge Output Stage (IRF540N MOSFETs)**  
5. **LC Low-Pass Filter** to recover the analog output from PWM.

---

## 🔍 Stage-wise Working

### 1️⃣ Triangle Wave Generator (NE555)
- **IC Used**: NE555 configured as an **astable multivibrator**.  
- **Pins 2 & 6** are connected together and determine the frequency.  
- **Typical Frequency**: ≈ 50 kHz to 100 kHz (as seen at Pin 2/6).  
- Output is a **triangle (or sawtooth-like)** waveform which acts as the **carrier signal**.

### 2️⃣ Pre-Amplifier Stage
- **LM386** or **LM358** (as seen in your circuit) amplifies the small audio input signal to suitable level.  
- Provides DC isolation and improves SNR before feeding into comparator.

### 3️⃣ Comparator / Modulator (LM393)
- The **LM393** compares:
  - **Input Audio Signal** (from preamp)
  - **Triangle Wave** (from NE555)
- The output becomes a **PWM signal**, whose **duty cycle** changes according to the amplitude of the input audio.
- This modulation process converts the analog input into a **digital pulse stream** that contains the same audio information.

### 4️⃣ Driver Stage (BD139–BD140 Pair)
- Two complementary transistors (BD139 NPN, BD140 PNP) boost the current capability of LM393’s output.
- They provide strong gate drive to the MOSFETs, ensuring fast and clean switching transitions.

> Alternative: You can use **IR2111 IC** as a powerful MOSFET driver for higher efficiency and lower switching delay.

### 5️⃣ H-Bridge MOSFET Output Stage
- Four **IRF540N** MOSFETs are arranged in a **full-bridge (H-bridge)** configuration.
- Each pair of MOSFETs operates in complementary mode:
  - One half-bridge drives the speaker positive terminal.
  - The other half drives the negative terminal.
- The output load (speaker) thus receives **alternating polarity PWM**, doubling the effective voltage swing.

### 6️⃣ Output LC Low-Pass Filter
- A combination of **inductor (30µH)** and **capacitor (1uF,450v)** filters the high-frequency PWM into a **smooth analog waveform**.
- The result is a **clean, amplified audio output**.

---

## 💡 Why H-Bridge Is More Efficient

| Parameter | Simple 2-MOSFET Class-D | H-Bridge Class-D (This Circuit) |
|------------|--------------------------|--------------------------------|
| Output Swing | Half of supply (Vcc/2) | Full of supply (±Vcc) |
| Power Delivery | Limited | 2× More Output Power |
| Efficiency | ~75–80% | 90–95% |
| DC Blocking Capacitor | Required | Not Required |
| Speaker Connection | One end to ground | Floating (balanced output) |
| Symmetry | Single-ended | Full-bridge differential drive |
| Thermal Loss | Higher | Lower due to balanced load sharing |

**In short:**  
This amplifier delivers **double the power**, **less heat**, and **better sound clarity**, all while running on just 12V.

---

## 🧰 Component List

| Component | Description |
|------------|-------------|
| NE555 | Triangle wave generator |
| LM393 | Comparator for PWM modulation |
| LM386 / LM358 | Audio preamplifier |
| BD139 / BD140 | Driver transistors |
| IRF540N | Power MOSFETs for H-bridge |
| L1 (30µH) | Output filter inductor |
| C1 (1uF ,450v) | Output filter capacitor |
| D1-D4 | Flyback protection diodes |
| 12V Regulator | LM7812 or LM2940 |
| Audio Input | Line-level or Aux input |
| Speaker | 4–8Ω, 10–50W |

---

## 🎶 Applications

- DIY Bluetooth speaker amplifier  
- Car and bike audio systems  
- Portable battery-powered sound systems  
- Educational project for electronics students  
- Class-D PWM-based switching amplifier study  

---

## 🔧 Improvements

This Class-D amplifier circuit can be further optimized and upgraded to achieve higher output power and overall performance. Below are some practical improvement options:

**1. Dual Power Supply Configuration:**
Use two separate power supplies — one 12 V supply for the preamplifier, modulator, and driver stages, and another 25 V supply exclusively for the power stage (IRF540N MOSFETs).
→ This separation reduces noise coupling and increases clean output power.


**2. Higher Voltage MOSFET Upgrade (IRF640):**
Replace IRF540N with IRF640 MOSFETs and power the stage with up to 80 V.
→ This modification increases the amplifier’s power (wattage) output due to the MOSFET’s higher voltage handling capability.


**3. High Power MOSFET Upgrade (IRFP260):**
For extreme power applications, replace IRF540N with IRFP260 MOSFETs.
→ This enhances both voltage and current handling, resulting in a drastic and almost exponential power increase.

⚠️ However, ensure all MOSFETs have matching β (gain), R<sub>DS(on)</sub>, and threshold voltages to maintain control and prevent saturation or imbalance.


**4. Parallel MOSFET Configuration:**
More output power can be achieved by paralleling multiple MOSFETs.
→ Always verify that all parallel MOSFETs have identical β values, R<sub>DS(on)</sub>, and V<sub>th</sub> ratings, as even slight mismatches can cause uneven current distribution or thermal runaway.

**⚠️ use snubber circuit to protect mosfet against reverse peak voltage because our load is inductive when it's charge once and mosfet off conducting, inductor of speaker gives reverse voltage at mosfet's drain/source pin which connected to speaker**

---
## 👨‍🔬 Author Info

**Project Creator:** *Mikey-7x / Yogesh R. Chauhan*  
**GitHub:** [github.com/mikey-7x](https://github.com/mikey-7x?tab=repositories)  
**License:** [![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-orange.svg)](https://creativecommons.org/licenses/by-nc-nd/4.0/)
**Date:** 2 November 2025
---

☕ Credits

Developed with  ❤️ by **[mikey-7x](https://github.com/mikey-7x)** 🚀🔥  


[other repository](https://github.com/mikey-7x?tab=repositories)

---

## 🧡 Support

If you like this project, give it a ⭐ on GitHub and share it with your friends in electronics and embedded systems communities!

---
