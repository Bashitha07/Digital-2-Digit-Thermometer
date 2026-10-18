# 2-Digit Digital Thermometer

A low-cost, analog **2-digit digital thermometer** designed to measure temperatures from **0 °C to 99 °C**. This project was developed for the **IE2044 – System Modelling and Prototyping** module using an LM35 temperature sensor, a TC7107 ADC/display driver, and dual seven-segment displays.

## 📌 Project Overview

The thermometer converts the LM35 sensor output directly into a temperature reading without using a microcontroller or firmware. Since the LM35 produces **10 mV/°C**, the circuit is calibrated so that each degree Celsius corresponds to one displayed count.

The design combines:

- An **LM35 precision temperature sensor**
- A **TC7107 / ICL7107 analog-to-digital converter and display driver**
- Two **common-cathode seven-segment displays**
- A calibrated **100 mV reference voltage**
- Analog star-point grounding to reduce display jitter and noise
- Visual indication for temperature overflow and underflow conditions

## ✨ Key Features

- **Measurement range:** 0 °C to 99 ��C
- **Direct voltage scaling:** 10 mV from the LM35 represents 1 °C
- **Reference calibration:** 100 mV using a 1 kΩ trimmer potentiometer
- **No microcontroller required:** Fully analog measurement and display chain
- **Overflow indication:** Red LED for temperatures above 99 °C
- **Underflow indication:** Green LED for temperatures below 0 °C
- **Noise reduction:** Analog star-point grounding using `ADND*`
- **Dual-supply operation:** +5 V and −5 V rails
- **PCB design:** Single-layer routing with SMD 0805 components

## 🧠 Operating Principle

The LM35 generates an output voltage proportional to the measured temperature:

```text
VLM35 = 10 mV × Temperature (°C)
```

For example:

```text
25 °C → 250 mV
75 °C → 750 mV
```

The TC7107 measures this analog voltage and drives the two seven-segment displays. With the reference voltage calibrated to **100 mV**, the displayed value corresponds directly to the temperature in degrees Celsius.

## 🛠️ Component Summary

| Reference | Component | Package / Type | Purpose |
|:--:|---|---|---|
| U1 | TC7107 / ICL7107 | DIP-40 | Analog-to-digital conversion and display driving |
| U2 | LM35 | TO-92, through-hole | Precision Celsius temperature sensing |
| DIS1, DIS2 | Seven-segment displays | Common cathode | Tens and units temperature display |
| RV1 | Trimmer potentiometer, 1 kΩ | Through-hole | Reference voltage adjustment |
| R1–R6 | Resistors | SMD 0805 | Input conditioning, scaling, integration, oscillator, and LED current limiting |
| C1–C4 | Capacitors | SMD 0805 | Integrator, auto-zero, reference, and oscillator timing |

## 📁 Repository Contents

```text
Digital-2-Digit-Thermometer-/
├── Diagrams/               # System block diagrams and architecture diagrams
├── Report/                 # Final project report
├── Schematics/             # Proteus simulation files and EasyEDA PCB sources
├── SMP final project.pdf   # Official module project brief and specifications
└── README.md               # Project documentation
```

## 🧪 Simulation and PCB Implementation

### Phase I — Simulation

The circuit was tested in **Proteus Design Suite 8.06** across the complete 0 °C to 99 °C operating range. The simulation also validates:

- Normal temperature measurements
- Overflow conditions above 99 °C
- Underflow conditions below 0 °C
- Seven-segment display operation
- LED error indication
- Reference-voltage calibration

### Phase II — PCB Design

The PCB was developed using **EasyEDA Pro** with the following design requirements:

- Single-layer routing
- SMD 0805 resistor and capacitor footprints
- Analog star-point grounding
- Reduced digital switching noise
- Horizontally aligned seven-segment displays
- Layout suitable for practical assembly and testing

## 🔌 Power Requirements

The design uses a dual-supply configuration:

| Supply Rail | Main Purpose |
|---|---|
| `+5 V` | Logic, display-driving, and indicator circuitry |
| `−5 V` | Analog signal processing and internal integrator operation |

> **Safety note:** Verify the power-supply polarity and voltage levels before connecting the circuit. Incorrect supply connections may damage the TC7107, LM35, displays, or other components.

## 👥 Project Team

**Module:** IE2044 – System Modelling and Prototyping  
**Academic Year:** Year 2, Semester 2  
**Institution:** Sri Lanka Institute of Information Technology (SLIIT)  
**Group:** 05

| Student | Student ID |
|---|---|
| Sellapperuma B.A. | IT24103485 |
| Jayasinghe L.P. | IT24100888 |

## 📚 Technologies and Tools

- **Proteus Design Suite 8.06** — Circuit simulation
- **EasyEDA Pro** — Schematic capture and PCB design
- **LM35** — Analog temperature sensing
- **TC7107 / ICL7107** — ADC and seven-segment display driving

## 📄 License

This project was created for academic and educational purposes as part of the IE2044 module.
