# Bell State Entanglement Circuit

This folder contains an implementation of a **Bell state preparation circuit** created using **IBM Quantum Composer** and exported as **OpenQASM** and **SVG circuit diagrams**.

Bell states are maximally entangled two-qubit quantum states and are fundamental building blocks in many quantum information protocols such as:

* Quantum teleportation
* Superdense coding
* Quantum cryptography
* Quantum error correction

---

# Circuit Overview

This circuit prepares an entangled pair of qubits using a **Hadamard gate** followed by a **CNOT gate**.

Steps performed by the circuit:

### 1. Initialization

Both qubits start in the computational basis state:

$$
|00\rangle
$$

---

### 2. Superposition

A **Hadamard gate** is applied to the first qubit.

This creates a superposition state:

$$
\frac{|0\rangle + |1\rangle}{\sqrt{2}}
$$

---

### 3. Entanglement

A **CNOT gate** is applied with:

* **control** → first qubit
* **target** → second qubit

This entangles the qubits and produces a **Bell state**.

---

# Resulting Quantum State

After the entangling operation, the system is in the **Phi-plus Bell state**:

$$
|\Phi^{+}\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}
$$

This state means:

* both qubits are perfectly correlated
* measuring one qubit instantly determines the state of the other

---

# Measurement Outcomes

When the qubits are measured, the possible results are:

| Result | Probability |
| ------ | ----------- |
| 00     | 50%         |
| 11     | 50%         |

The outcomes **01** and **10** do not occur due to the entanglement between the qubits.

---

# Files in this Folder

* `bell_entanglement.qasm` — OpenQASM representation of the quantum circuit
* `bell_entanglement.svg` — visual diagram of the circuit exported from IBM Quantum Composer

---

# Platform Used

This circuit was designed and simulated using:

* IBM Quantum Composer
* IBM Quantum Experience
* OpenQASM 2.0
