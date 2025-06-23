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

## 🔄 Key Operational Phases

1. **Signal Acquisition**:
   - Piezoresistive sensor (`Rx = 323Ω–330Ω`) detects breath-induced strain
   - Non-inverting amplifier boosts signal  
     _Gain = 1 + R2 / Rx_

2. **Integration & Timing**:

   - **Ton Phase (V1 = HIGH)**:
     - Integrator charges capacitor `C1 (100nF)`
     - Output:  
       `Vi(Ton) = (Vo / RC) · T1 + Vi(0)`

   - **Toff Phase (V1 = LOW)**:
     - Integrator discharges through reference voltage
     - Output:  
       `Vi(Ton + Toff) = (-Vr / RC) · T2 + Vi(0)`

3. **Digital Conversion**:
   - Relationship:  
     `T2 / T1 = 1 + R2 / R1 → R1 = R2 · (T1 / (T2 − T1))`
   - NE555 timer generates digital output pulses proportional to resistance

---

## 🔧 Circuit Design

| **Component** | **Value/Range**          | **Quantity** |
|---------------|--------------------------|--------------|
| OP07 (Op-amp) | ±5V                      | 3            |
| Resistor Rx   | 323Ω–330Ω (1Ω steps)     | 1            |
| Resistor R1   | 330Ω                     | 1            |
| Capacitor C1  | 100nF                    | 1            |
| Reference V   | 1.2V                     | 1            |

---

## 📊 Simulation Results

### ✅ Ideal Conditions (LTspice)

![image](https://github.com/user-attachments/assets/b9953fc5-631b-4133-ad85-65ad2e1dab66)



- Maximum nonlinearity: **0.09%**

```python
# Resistance Measurement Correlation
ideal_R = [323, 324, 325, 326, 327, 328, 329, 330]
measured_R = [322.8, 323.9, 325.1, 326.0, 327.2, 328.1, 329.0, 330.0]
```
## ✅ Conclusion

This project demonstrates a **functional digital measurement system** that:

- ✅ Provides accurate respiratory monitoring (**≤2.1% error**)
- 💡 Reduces cost through **single-reference-voltage** design
- 🩺 Enables **non-invasive point-of-care diagnostics**
- ⚡ Processes data in **real-time for immediate intervention**

> The system outperforms traditional methods in **comfort**, **accessibility**, and **affordability**, while maintaining **clinical-grade precision**.

---

## 🚀 Future Work

### 🔌 Microcontroller Integration
- Add Arduino for direct digital measurements

### 📏 Miniaturization
- Develop a custom ASIC consolidating all components

### 📡 Wireless Connectivity
- Bluetooth / LoRaWAN for remote monitoring

### 🧪 Clinical Validation
- Large-scale trials across diverse patient groups

### 🌡️ Multi-Sensor Expansion
- Integrate temperature and humidity sensors

---

## 📚 References

1. Elangovan K. et al. — _Digital Signal-Conditioner for Resistive Sensors_, IEEE SAS 2020  
2. Priya P. et al. — _Noninvasive Piezoresistive Breath Sensor_, IEEE Sensors Journal 2023  
3. Ferrari V. et al. — _Oscillator-based Signal Conditioning_, IMTC Proceedings 1997  

---

> 🏫 Developed at Kerala University of Digital Sciences  
> © 2024 P K Adithya Das| Project Repository
---

