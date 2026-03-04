# Quantum Circuit Implementation using IBM Quantum Composer

This repository contains a collection of **quantum circuits designed and simulated using IBM Quantum Composer**.

The circuits were created as part of independent exploration of **quantum computing concepts using the IBM Quantum platform**.

The implementations demonstrate several fundamental ideas in **quantum information processing and quantum algorithms**, including:

* quantum superposition
* quantum entanglement
* quantum oracle evaluation
* quantum communication protocols
* quantum measurement and interference

All circuits were designed graphically in **IBM Quantum Composer** and exported as **OpenQASM programs and SVG circuit diagrams**.

---

# Platform and Tools

The circuits in this repository were built and simulated using:

* **IBM Quantum Composer**
* **IBM Quantum Experience**
* **OpenQASM 2.0**
* **Qiskit compatible circuit format**

IBM Quantum Composer provides a graphical interface for building quantum circuits using quantum gates and executing them on simulators or real quantum devices.

---

# Repository Structure

The repository is organized into folders containing individual quantum circuits and protocols.

Each circuit exported from IBM Quantum Composer includes two file formats.

### 1. OpenQASM Files (`.qasm`)

These files contain the **text representation of the quantum circuit** written in **OpenQASM (Open Quantum Assembly Language)**.

OpenQASM defines:

* quantum registers
* classical registers
* quantum gates
* measurement operations

Example structure of a `.qasm` circuit file:

```
qreg q[2];
creg c[2];

h q[0];
cx q[0], q[1];

measure q[0] -> c[0];
measure q[1] -> c[1];
```

These circuits can be directly executed using **Qiskit** or other quantum simulators.

---

### 2. Circuit Diagram Files (`.svg`)

Each `.svg` file is a **visual representation of the quantum circuit** exported from IBM Quantum Composer.

The diagram displays:

* qubit wires
* quantum gates (H, X, Z, CNOT, etc.)
* measurement operations
* classical registers

SVG files are **vector graphics**, which means they can be used in:

* research documentation
* reports
* presentations
* GitHub READMEs

without loss of resolution.

---

# Quantum Circuits Included

The repository currently contains implementations of several foundational quantum circuits and algorithms.

### Bell State Entanglement

Creation of maximally entangled two-qubit Bell states.

The circuit prepares the Bell state

$$
|\Phi^{+}\rangle =
\frac{|00\rangle + |11\rangle}{\sqrt{2}}
$$

using a **Hadamard gate followed by a CNOT gate**.

---

### Bell State Preparation

A dedicated implementation illustrating how entanglement emerges from simple gate operations.

The circuit demonstrates how two qubits evolve from

$$
|00\rangle
$$

into an entangled Bell pair through superposition and controlled interaction.

---

### Deutsch Algorithm

An implementation of the **Deutsch Algorithm**, one of the earliest examples demonstrating **quantum advantage**.

The algorithm determines whether a function

$$
f(x) : {0,1} \rightarrow {0,1}
$$

is **constant** or **balanced** using **a single oracle evaluation**, whereas a classical algorithm requires two evaluations.

---

### Deutsch–Jozsa Algorithm

A generalization of the Deutsch algorithm that determines whether a Boolean function is **constant or balanced** for multiple inputs.

The algorithm demonstrates how **quantum parallelism and interference** allow the result to be obtained with **one oracle query**.

---

### Superdense Coding

Implementation of the **Superdense Coding protocol**, a quantum communication protocol that allows transmission of **two classical bits using a single qubit** when the sender and receiver share entanglement.

The protocol begins with a Bell state

$$
|\Phi^{+}\rangle =
\frac{|00\rangle + |11\rangle}{\sqrt{2}}
$$

Alice encodes two classical bits by applying **Pauli operators** to her qubit and sends it to Bob.

Bob then applies a **Bell-basis decoding circuit** to recover the encoded classical message.

Two equivalent circuit implementations are included to demonstrate different qubit orientations.

---

# Fundamental Quantum Concepts Demonstrated

The circuits illustrate several core ideas in quantum computing.

---

## Quantum Superposition

Superposition is created using the **Hadamard gate**

$$
H|0\rangle =
\frac{|0\rangle + |1\rangle}{\sqrt{2}}
$$

This allows a qubit to represent multiple states simultaneously.

---

## Quantum Entanglement

Entanglement is generated using **Hadamard and CNOT gates**.

Example Bell state:

$$
|\Phi^{+}\rangle =
\frac{|00\rangle + |11\rangle}{\sqrt{2}}
$$

Entangled states are fundamental to many quantum protocols including:

* quantum teleportation
* superdense coding
* quantum communication
* quantum cryptography

---

## Quantum Interference

Quantum algorithms rely on **constructive and destructive interference** of probability amplitudes.

Interference allows certain computational paths to cancel while amplifying the correct result.

---

## Quantum Measurement

Measurement collapses a quantum state into classical outcomes.

In OpenQASM, measurement is written as:

```
measure q[i] -> c[i];
```

which maps a quantum bit to a classical register.

---

# Running the Circuits in Qiskit

The `.qasm` circuits can be executed using **Qiskit**.

Example Python code:

```python
from qiskit import QuantumCircuit
from qiskit import Aer, execute

qc = QuantumCircuit.from_qasm_file("circuit.qasm")

backend = Aer.get_backend("qasm_simulator")
job = execute(qc, backend=backend, shots=1024)

result = job.result()
print(result.get_counts())
```

This allows the circuits to be simulated locally or executed on **IBM Quantum hardware**.

---

# Purpose of this Repository

The goal of this repository is to:

* explore **quantum circuit design**
* understand **quantum gate operations**
* study **foundational quantum algorithms**
* experiment with **quantum communication protocols**
* practice using **IBM Quantum Composer and OpenQASM**

The circuits serve as practical demonstrations of the **core building blocks of quantum computing**.

---

# Conclusion

This repository presents a collection of quantum circuits designed using **IBM Quantum Composer** and exported to **OpenQASM**.

The included circuits illustrate key principles of **quantum computation, entanglement, and quantum algorithms** through both **visual circuit diagrams and executable quantum programs**.

Together, these implementations provide a practical introduction to designing and understanding **quantum circuits and quantum information protocols**.
