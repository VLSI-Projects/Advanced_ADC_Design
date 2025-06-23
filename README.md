# Digital Measurement System for Non-Invasive Piezoresistive Breath Sensor




## 📌 Abstract

This project develops a digital measurement system for a **non-invasive piezoresistive breath sensor**, enabling precise respiratory monitoring in **point-of-care settings**. The system leverages the **piezoresistive effect** to detect breath-induced deformations through resistance variations.

### Key Innovations:
- Single-reference-voltage architecture reducing complexity and cost  
- Integration of signal conditioning circuits (integrator, comparator, amplifier)  
- Real-time respiratory data processing  
- Novel circuit design inspired by **dual-slope ADC principles**

Validated through **LTspice simulations** and **experimental prototyping**, the system achieves:
- 0.09% nonlinearity under ideal conditions
- 2.1% nonlinearity in practical scenarios

---

## 🧠 Introduction

Traditional respiratory monitoring often involves **invasive procedures** or **bulky equipment**. Our system addresses these challenges by integrating:

- A **non-invasive piezoresistive sensor** embedded in a breath mask
- A digital measurement system built using:
  - Integrator (OP07)
  - Comparator (OP07)
  - Non-inverting amplifier (OP07)
  - Timer (NE555 monostable multivibrator)
  - Multiplexer (CD4053 as a switch)
- A single **1.2V reference voltage**, simplifying the circuit

> The system converts resistance changes from breathing into digital outputs, enabling **continuous health monitoring** in both clinical and home settings.

---

## ⚙️ Methodology

### 📐 System Architecture

![image](https://github.com/user-attachments/assets/c1929a66-4e65-4383-baf7-337d74cc4e77)

*Fig 1: Digital measurement system circuit*

### 🔄 Operational Phases

#### ➤ Signal Acquisition:
- Sensor Rx (323Ω–330Ω) detects breath-induced strain
- Amplifier boosts signal:
  \[
  V_o = \left(1 + \frac{R_2}{R_x}\right) \cdot V_{in}
  \]

#### ➤ Integration & Timing:
- **Ton Phase (V1 = HIGH):**
  - Integrator charges C1 (100nF)
  \[
  V_i(T_{on}) = \left(\frac{V_o}{RC}\right)T_1 + V_i(0)
  \]

- **Toff Phase (V1 = LOW):**
  - Integrator discharges via Vref
  \[
  V_i(T_{on} + T_{off}) = \left(-\frac{V_r}{RC}\right)T_2 + V_i(0)
  \]

#### ➤ Digital Conversion:
\[
\frac{T_2}{T_1} = 1 + \frac{R_2}{R_1} \Rightarrow R_1 = R_2\left(\frac{T_1}{T_2 - T_1}\right)
\]

- NE555 timer generates digital pulses proportional to resistance

---

## 🔧 Circuit Design

| **Component** | **Value/Range**         | **Quantity** |
|---------------|--------------------------|--------------|
| OP07 (Op-amp) | ±5V                     | 3            |
| Resistor Rx   | 323Ω–330Ω (1Ω steps)     | 1            |
| Resistor R1   | 330Ω                    | 1            |
| Capacitor C1  | 100nF                   | 1            |
| Reference V   | 1.2V                    | 1            |

---

## 📊 Simulation Results

### ✅ Ideal Conditions (LTspice)

![LTspice Ideal](https://via.placeholder.com/400x200?text=Fig+3+%26+4+-+LTspice+Results)

- Maximum nonlinearity: **0.09%**

```python
# Resistance Measurement Correlation
ideal_R = [323, 324, 325, 326, 327, 328, 329, 330]
measured_R = [322.8, 323.9, 325.1, 326.0, 327.2, 328.1, 329.0, 330.0]

> A low-cost, non-invasive respiratory monitoring solution for point-of-care applications  
> Developed at Kerala University of Digital Sciences, Innovation and Technology  
> © P K Adithya Das

---

