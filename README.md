# Design and Analysis of Single Phase Grid Connected Inverter

This repository provides the design, implementation, and analysis of a **Single Phase Grid Connected Inverter**. The project highlights the working principles of inverters, their integration with photovoltaic (PV) systems, and synchronization with the electrical grid.

---

## Introduction

Power inverters are vital components in many DC-to-AC conversion systems, such as:
- **Uninterrupted Power Supply (UPS)**
- **Induction Motor Drives**
- **Automatic Voltage Regulators (AVR)**

A key requirement of power inverters is the ability to produce and maintain a **stable and clean sinusoidal output voltage waveform**, irrespective of the connected load type. This is achieved with a robust **feedback controller**.

### Photovoltaic (PV) Systems
PV sources are projected to play a significant role in the global energy portfolio by 2040 due to their:
- Clean, emission-free energy generation
- Renewable and abundant nature
- High reliability and efficiency

However, PV arrays typically produce a low output voltage. To meet the high bus voltage requirements of grid inverters, a step-up converter is employed to boost the voltage.

### Solar Inverter Features
Solar inverters are equipped with special functions for efficient integration with PV arrays:
- **Maximum Power Point Tracking (MPPT):** Ensures optimal PV performance.
- **Anti-Islanding Protection:** Prevents back-feeding power during grid outages.
- **Grid Synchronization:** Aligns inverter output phase and frequency with the grid.

---

## Key Concepts

### I-V and P-V Characteristics of a Solar Cell
The I-V and P-V characteristics of an ideal solar cell are shown below:

**Formula for Maximum Power:**
- \( P_{\text{max}} = V_{\text{oc}} \cdot I_{\text{sc}} \)
  - \( V_{\text{oc}} \): Open Circuit Voltage
  - \( I_{\text{sc}} \): Short Circuit Current
- \( P_{\text{mpp}} = V_{\text{mp}} \cdot I_{\text{mp}} \)
  - \( V_{\text{mp}} \): Maximum Voltage
  - \( I_{\text{mp}} \): Maximum Current

---

### Current Controlled PWM Inverters
Current-controlled PWM inverters are widely used in high-performance AC drives due to their ability to eliminate stator dynamics. The main goal of the current controller is to align the load current vector with the reference current trajectory. Errors in load current are input to the PWM modulator, which generates switching signals for the inverter.

---

### Single-Phase Grid Connected Inverter

#### Ideal Circuit
The ideal circuit of a single-phase full-bridge grid-connected inverter is shown below. The PV array produces DC power, which is boosted by a step-up converter and then converted to AC by the inverter. Synchronization ensures the inverter output matches the grid's phase and frequency.

#### Schematic
The inverter consists of four power MOSFETs (IRF840) and four fast recovery diodes (FR407). For larger systems, IGBTs are recommended due to their cost-effectiveness at higher power ratings.

**Switching Characteristics:**
- Voltage-bidirectional, two-quadrant switches can block positive and negative voltages but conduct only positive current.
- Optical isolated gate driver circuits are used for driving inverter switches.

#### Circuit Description
- **High-Side Gate Drivers:**
  - Two independent power supplies (e.g., \( V_{\text{DD3}} \), \( V_{\text{DD4}} \)) drive switches \( Q3 \) and \( Q4 \).
- **Low-Side Gate Drivers:**
  - A common power supply \( V_{\text{DD5}} \) drives switches \( Q5 \) and \( Q6 \).

---

## Repository Structure

```plaintext
grid-connected-inverter/
├── README.md            # Overview of the project
├── LICENSE              # License information
├── Simulink_Model/      # MATLAB Simulink models
│   ├── single_phase_inverter.slx
│   └── supporting_files/
├── Results/             # Simulation results
│   ├── waveforms/
│   ├── I-V_and_P-V_Characteristics/
│   └── efficiency_analysis/
├── Docs/                # Documentation
│   ├── project_report.pdf
│   └── circuit_diagrams/
├── Scripts/             # MATLAB analysis scripts
│   ├── pwm_analysis.m
│   ├── mppt_simulation.m
└── .gitignore           # Files and folders to ignore in Git
