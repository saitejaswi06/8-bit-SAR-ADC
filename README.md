# 🔍 8-bit SAR ADC | Digital Logic & Analog Interface Design

An 8-bit Successive Approximation Register (SAR) Analog-to-Digital Converter designed and simulated to convert analog input signals into 8-bit digital outputs efficiently. The design balances speed and accuracy for moderate-speed data acquisition systems.

---

## 🎯 Objective
To implement and simulate an **8-bit SAR ADC** that:
- Accurately converts analog voltages (0–5V) into 8-bit digital values.
- Minimizes conversion time using a binary search algorithm.
- Achieves <2 LSB Integral Non-Linearity (INL) in simulation.

---

## ⚙️ Design Architecture

### ➤ Core Components:
| Block                      | Function                                           |
|----------------------------|----------------------------------------------------|
| SAR Logic (Digital)        | Performs binary search for bit-by-bit conversion.  |
| Comparator (Analog)        | Compares DAC output with the analog input.         |
| DAC (Digital-Analog)       | Generates reference voltage from SAR bits.         |
| Control Unit               | Synchronizes sampling, hold, and bit trial cycles. |

### ➤ Operating Principle:
1. **Sampling Phase:** Analog input is sampled onto the comparator.
2. **Successive Approximation:**
   - Start with MSB = 1, others = 0.
   - DAC outputs voltage corresponding to trial digital code.
   - Comparator compares DAC output and input voltage.
   - SAR logic sets/clears the bit based on comparator output.
   - Process repeats for next bit until all bits resolved.
3. **Final Output:** After 8 clock cycles, a stable 8-bit digital word is obtained.

---

## 🛠️ Implementation Details

- **Logic Design:** SAR register, FSM controller for managing trial cycles, and comparator enable logic.
- **DAC:** Modeled as an ideal resistor-ladder or capacitor-based DAC in simulations.
- **Comparator:** Modeled as an ideal voltage comparator with zero offset in LTspice or Verilog testbench.
- **Clock Control:** One conversion completed in 8 clock cycles (1 per bit).

---

## 🔬 Simulation Results
- Simulated in **LTspice** / Verilog testbench.
- Verified INL < 2 LSB across full voltage range (0–5V).
- Step-by-step bit convergence observed in waveform analysis.
- Accurate 8-bit conversion within 8 clock cycles.

---

## ✅ Key Features
- Efficient binary search reduces conversion time.
- Scalable design adaptable for higher bit resolutions (10-bit, 12-bit).
- Demonstrated stable performance under varying input conditions.

---

## 🔧 Future Enhancements
- Replace ideal blocks with transistor-level comparator and DAC.
- Add sample-and-hold circuitry for continuous analog inputs.
- Optimize for low-power embedded applications.

---

## 🔍 Summary
This 8-bit SAR ADC project showcases the digital-analog interaction in embedded systems and forms the basis of moderate-speed data acquisition systems in microcontrollers, sensor nodes, and mixed-signal ICs.
