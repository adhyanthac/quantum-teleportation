# Single-Body Quantum Teleportation using Bell State Measurement

This repository contains a Python implementation and simulation of **single-body quantum teleportation** using Bell state measurements. It demonstrates how an arbitrary single-qubit state $|\psi\rangle$ can be transferred from Alice to Bob using a shared entangled pair (EPR pair) and classical communication.

## Notebook Overview

The notebook [`quantum_teleportation_bell_state_measurement.ipynb`](./quantum_teleportation_bell_state_measurement.ipynb) walks through the quantum teleportation protocol step-by-step:

1. **State Preparation**:
   - Alice's initial state is prepared as an arbitrary normalized qubit state:
     $$|\psi\rangle = \alpha|0\rangle + \beta|1\rangle \quad \text{where} \quad |\alpha|^2 + |\beta|^2 = 1$$
   - A shared EPR pair (Bell state) is created:
     $$|\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$$
   - The combined 3-qubit initial state $|\Psi\rangle$ is formed by the tensor product:
     $$|\Psi\rangle = |\psi\rangle \otimes |\Phi^+\rangle$$

2. **Alice's Measurement Basis**:
   - Alice performs a joint Bell state measurement on her two qubits (qubit 0 and qubit 1).
   - The measurement is projected onto the four orthonormal Bell states:
     - $|I\rangle = |\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$
     - $|X\rangle = |\Psi^+\rangle = \frac{1}{\sqrt{2}}(|01\rangle + |10\rangle)$
     - $|Y\rangle = |\Psi^-\rangle = \frac{1}{\sqrt{2}}(|01\rangle - |10\rangle)$
     - $|Z\rangle = |\Phi^-\rangle = \frac{1}{\sqrt{2}}(|00\rangle - |11\rangle)$

3. **Bob's State Extraction & Correction**:
   - Alice's measurement projects the system into one of the four outcomes, each with a uniform probability of $P = 0.25$.
   - Bob's qubit collapses to a Pauli-rotated version of Alice's original state.
   - Upon receiving Alice's measurement result (2 classical bits), Bob applies the corresponding Pauli correction gate ($I, X, Y$, or $Z$) to reconstruct the original state:
     - Outcome $|I\rangle \rightarrow$ Apply Identity ($I$)
     - Outcome $|X\rangle \rightarrow$ Apply $X$
     - Outcome $|Y\rangle \rightarrow$ Apply $Y$
     - Outcome $|Z\rangle \rightarrow$ Apply $Z$

---

## Accomplished Results

The simulation validates the teleportation protocol using `numpy` and `scipy`:
* **Orthonormality Check**: Verified that the four Bell measurement states form an exact orthonormal basis by computing the Gram-Schmidt matrix (confirming it is the Identity matrix).
* **Probability Verification**: Proved that all four measurement outcomes have a probability of exactly $25\%$ ($P = 0.25$).
* **Fidelity Testing**: Successfully extracted Bob's state after projection and applied the matching Pauli correction gate. The state fidelity $F = |\langle\psi|\phi_{\text{corrected}}\rangle|^2$ for all four outcomes is **exactly $1.00000000$**, demonstrating perfect quantum state reconstruction.

---

## Future Work

* **Many-Body Simulation**: The next phase of this research is to extend this single-body simulation framework to **many-body quantum teleportation** to investigate state transfer in multi-particle and many-body systems.
