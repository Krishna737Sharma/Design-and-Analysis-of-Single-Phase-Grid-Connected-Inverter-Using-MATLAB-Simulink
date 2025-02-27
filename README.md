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

## Inverter Model

### Single-Phase Grid Connected Inverter
The output of a PV model is not constant and is relatively small. To boost the voltage and maintain consistency, a **boost converter** is used. The boosted voltage is then converted into AC by the inverter, and the developed power is injected into the grid.

#### MATLAB Simulink Models and Outputs

![5 1](https://github.com/user-attachments/assets/40c69aa5-07c7-4026-9ad2-e1e4a12a308f)
- **Fig.5.1**: Single-Phase Grid Connected Inverter Model
- 
![5 2](https://github.com/user-attachments/assets/f8815b46-7977-4a70-b0aa-25968e6c98f7)
- **Fig.5.2**: MATLAB simulink modal by using matlab function control

![5 2](https://github.com/user-attachments/assets/cd93aba8-402d-477e-b9ce-6bea09ab6888)
- **Fig.5.3**: Gating Pulses of the Inverter Switching Module

![5 2](https://github.com/user-attachments/assets/ec71c0c2-de93-4bf5-bb8a-6abe90172f49)
- **Fig.5.4**: Hysteresis Controller Simulink Model

![5 2](https://github.com/user-attachments/assets/b3dea571-68be-4241-bd88-13517e2908b2)
- Fig.5.6.Grid current and voltage in-phase waveform

![5 2](https://github.com/user-attachments/assets/98b0a26c-d3c6-4657-acfc-a83d5fbb830b)
- Fig.5.7.Grid current and voltage out of phase waveform

### Inverter Parameters and Specifications

| **Parameter**                | **Specification**       |
|-------------------------------|--------------------------|
| Solar Insolation              | 1000 W/m²               |
| Nominal Solar Array Voltage   | 120 V                   |
| Grid Voltage                  | 230 V                   |
| Grid Frequency                | 60 Hz                   |
| Inverter Current              | 10 A                    |
| DC Link Capacitor             | 1000 µF                 |
| Filter Inductor               | 5 mH                    |
| Transformer                   | 1:1                     |
| Inverter Switching Frequency  | 20 kHz                  |
| Load Resistor                 | 100 Ω                   |

---

### Hysteresis Controller and MATLAB Function Control
The **Hysteresis Controller** generates PWM pulses for the inverter. Below are the related models and waveforms:

![5 2](https://github.com/user-attachments/assets/3bb494ad-9a04-43a5-afcf-dd4516d35f99)

- **Fig.5.4**: Hysteresis Controller Output


![5 2](https://github.com/user-attachments/assets/9104af76-f831-4feb-837e-07fa139b8eb1)

- **Fig.5.5**: Error Output Waveform

#### MATLAB Function Code
```matlab
function a = fcn(x, ma, shift)
    shift_k = shift * pi / 180;       % Convert degrees to radians
    a = ma * sin(x + shift_k);       % Reference voltage
end
