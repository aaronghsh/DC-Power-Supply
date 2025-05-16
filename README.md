# AC to DC Power Supply ⚡

Welcome to the AC–DC Power Supply project! This project involves designing a DC power supply capable of delivering **3V ± 0.1V at 10mA** from a **120V AC input at 1 kHz**. The design uses a combination of rectifier, filter, and optional regulator stages. It was simulated in **LTspice** and physically implemented using lab components and a function generator.

---

## Technologies & Tools Used

- **LTspice**: Used to simulate the AC–DC conversion process.
- **Analog Discovery 3 (AD3)**: Used as a signal generator and oscilloscope.
- **1N4148 Diodes**: For full-wave rectification.
- **RC Filter Circuit**: To smooth the rectified output.
- **Zener Diode (Optional)**: For voltage regulation (not used in final build).
- **Resistors, Capacitor (100μF)**: From 2EI4 lab kit for load and filtering.

---

## Features

- **Full-Wave Center-Tapped Rectifier (FWCT)**:
  - Converts both half-cycles of AC into DC.
  - More efficient and simpler than a full-bridge in this context.
- **RC Filter**:
  - Reduces ripple in the rectified output.
  - Designed for smooth low-voltage outputs.
- **Zener Regulation (Optional)**:
  - Considered but not required due to sufficient voltage stability from the RC filter.
- **Transformer Design (Simulated)**:
  - Simulated coil ratio of **23:1** for stepping down 120V RMS to the desired voltage.
- **LTspice Simulations**:
  - Verified the output voltage and current within desired specifications.

---

## Circuit Design

1. **Load Resistor**:
   - Calculated using Ohm’s Law:  
     ```
     R = V / I = 3V / 10mA = 300Ω
     ```
   - Physically implemented using two 150Ω resistors in series.

2. **Capacitor Calculation**:
   - Designed using ripple voltage formula:
     ```
     C = I / (f × V_ripple) = 10mA / (2000Hz × 0.2V) = 25μF
     ```
   - A 100μF capacitor was used for added stability in real-world conditions.

3. **Rectification**:
   - Two 1N4148 diodes arranged in FWCT configuration.
   - Forward voltage drop considered (0.7V per diode at 10mA).

4. **Transformer Design**:
   - Simulated step-down ratio:
     ```
     Turns ratio = 120V / 5.26V ≈ 23:1
     ```

---

## Results

- **Measured Output Voltage**: 2.94V – 3.06V → Ripple = 0.12V (Tolerance ±0.06V)
- **Load Current**: 9.8mA – 10.2mA
- **LTspice Simulation**:
  - Output Voltage: 2.98V – 3.03V
  - Load Current: 9.97mA – 10.1mA
- **Efficiency Comparison**:
  - Simulated vs Physical results showed minor variation due to component tolerances.

---

## Project Files

- `LTspice/Project1.asc`: Schematic for transient simulation.
- `AD3 Waveform Capture`: Used to confirm Vo and IL.
- `Project Report.pdf`: Full design write-up including theory, simulation, results, and analysis.

---

## Future Improvements

- Add voltage regulation for tighter ripple control.
- Use a real transformer for full AC-to-DC implementation (instead of function generator).
- Improve tolerance by using precision resistors and capacitors.
- Explore PCB layout and fabrication for a compact, stable design.

