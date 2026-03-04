# Deutsch Algorithm

This folder contains an implementation of the **Deutsch Algorithm** created using **IBM Quantum Composer** and exported as **OpenQASM** and **SVG circuit diagrams**.

The Deutsch algorithm is one of the earliest quantum algorithms demonstrating a **quantum advantage** over classical computation.

---

# Problem Statement

Given a function

`f(x) : {0,1} → {0,1}`

the function is guaranteed to be either:

**Constant**

* `f(0) = f(1)`

**Balanced**

* `f(0) ≠ f(1)`

The goal is to determine whether the function is **constant or balanced**.

---

# Classical vs Quantum Approach

### Classical

To determine whether the function is constant or balanced, we must evaluate:

* `f(0)`
* `f(1)`

This requires **two function evaluations**.

### Quantum

The Deutsch algorithm determines the answer using **only one evaluation of the oracle**.

---

# Circuit Overview

The circuit uses **two qubits**:

* One **input qubit**
* One **ancilla qubit**

Steps performed by the circuit:

### 1. Initialization

The qubits start in the state

`|00⟩`

---

### 2. Prepare the Ancilla

An **X gate** followed by a **Hadamard gate** is applied to the second qubit, preparing it in the state

`|1⟩ → (|0⟩ - |1⟩) / √2`

---

### 3. Superposition of Input

A **Hadamard gate** is applied to the input qubit, creating the superposition

`(|0⟩ + |1⟩) / √2`

---

### 4. Oracle Application

The oracle implements the function `f(x)`.

In IBM Quantum Composer this is typically represented using **CNOT gates or controlled operations** that encode the behavior of the function.

---

### 5. Interference

Another **Hadamard gate** is applied to the input qubit, causing **quantum interference** between computational paths.

---

### 6. Measurement

The input qubit is measured.

---

# Interpreting the Result

| Measurement Result | Function Type |
| ------------------ | ------------- |
| `0`                | Constant      |
| `1`                | Balanced      |

---

# Files in this Folder

* `deutsch_algorithm.qasm` — OpenQASM representation of the quantum circuit
* `deutsch_algorithm.svg` — visual diagram of the circuit exported from IBM Quantum Composer

---

# Platform Used

This circuit was created using:

* IBM Quantum Composer
* IBM Quantum Experience
* OpenQASM 2.0
