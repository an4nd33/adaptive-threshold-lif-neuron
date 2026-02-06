# Implementation Idea: Adaptive Threshold Mechanism in LIF Neuron

## Background
In a conventional Leaky Integrate-and-Fire (LIF) neuron, the firing threshold
remains fixed irrespective of the neuron’s spiking history. Under sustained
or repetitive input, this leads to continuous high-frequency spiking, which
results in increased dynamic power consumption and reduced robustness in
neuromorphic systems.

Biological neurons, however, exhibit adaptive excitability, where the firing
threshold increases after frequent spiking and gradually relaxes during
periods of inactivity. This project introduces a simple circuit-level
mechanism to replicate this behavior in a CMOS LIF neuron.

---

## Core Idea
The key innovation in this design is the introduction of a **spike-history–
dependent feedback mechanism** at the membrane node.

This is achieved by:
- Adding an **adaptation capacitor (Cadapt)** connected to the membrane
  potential node (Vm)
- Discharging Cadapt through a **pseudo-resistor**, implemented using a
  MOS device operating in the subthreshold region

This combination enables slow temporal dynamics without requiring large
physical resistors.

---

## Circuit-Level Operation

### Normal Operation (Low or Irregular Input)
- Input current integrates on the membrane capacitor
- Vm rises and falls based on input strength and leakage
- Cadapt remains weakly charged or fully discharged
- The neuron behaves similarly to a conventional fixed-threshold LIF neuron

### Sustained Input Activity
- Repeated spiking causes Cadapt to accumulate charge
- The accumulated voltage on Cadapt introduces an additional discharge
  path at the membrane node
- This effectively suppresses Vm rise for subsequent inputs
- As a result, the firing threshold is raised indirectly, and spike frequency
  reduces over time

### Recovery During Inactivity
- When input activity decreases, Cadapt slowly discharges through the
  pseudo-resistor
- Vm regains its ability to integrate input current efficiently
- The neuron gradually returns to its baseline excitability

---

## Why This Approach Is Effective
- Requires **minimal additional circuitry**
- Avoids explicit threshold control logic
- Operates purely in the analog domain
- Mimics biological spike-frequency adaptation
- Expected to reduce average power consumption by limiting unnecessary
  high-rate spiking under constant input

---

## Design Considerations
- The value of Cadapt determines the strength of adaptation
- The pseudo-resistor sets the recovery time constant
- Both parameters can be tuned to balance responsiveness and stability

---

## Current Status
- Adaptive-threshold LIF neuron schematic completed
- Transient simulations verify adaptation behavior
- Quantitative power and area analysis is ongoing

This implementation serves as a compact and scalable approach for introducing
adaptive excitability in low-power neuromorphic circuits.

