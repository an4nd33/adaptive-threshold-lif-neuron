# Adaptive Threshold Leaky Integrate-and-Fire (LIF) Neuron

## Overview
This project focuses on the design and transient verification of an
adaptive-threshold Leaky Integrate-and-Fire (LIF) neuron implemented using
CMOS analog circuits for neuromorphic computing applications. The work is
part of an M.Tech VLSI Design Project and targets energy-efficient spiking
neural hardware.

Conventional LIF neurons employ a fixed firing threshold, which can lead to
sustained high firing rates under prolonged input stimulation. This behavior
results in unnecessary dynamic power consumption and reduced robustness in
large-scale spiking neural networks.

To address this limitation, this project introduces a simple circuit-level
mechanism to enable spike-activity–dependent threshold adaptation.

---

## Motivation
Biological neurons exhibit adaptive excitability: their firing threshold
increases after frequent spiking and gradually recovers during inactivity.
This mechanism, known as spike-frequency adaptation, improves energy
efficiency and stabilizes network activity.

The motivation of this work is to replicate this behavior in a compact CMOS
LIF neuron without introducing complex control logic or digital circuitry.

---

## Key Idea and Innovation
The adaptive threshold behavior is achieved by modifying the membrane node
of a standard LIF neuron:

- An **adaptation capacitor (Cadapt)** is connected to the membrane potential
  node (Vm)
- Cadapt is discharged through a **pseudo-resistor**, implemented using a MOS
  device operating in the subthreshold region

During sustained input activity, Cadapt accumulates charge and introduces an
additional discharge effect at Vm. This suppresses the membrane potential
rise for subsequent inputs, effectively increasing the firing threshold and
reducing spike frequency. When input activity decreases, Cadapt slowly
discharges, allowing the neuron to recover its baseline excitability.

This approach provides adaptive behavior using minimal additional circuitry
and operates entirely in the analog domain.

---

## Implementation
- Adaptive-threshold LIF neuron designed at the transistor level
- Circuit implemented and simulated using Cadence Virtuoso
- CMOS technology used for analog neuromorphic design
- Transient simulations performed to verify:
  - Membrane integration
  - Spike generation and reset behavior
  - Adaptive suppression of firing under sustained input

A baseline fixed-threshold LIF neuron is used as a reference for comparison.


