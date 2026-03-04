# Deutsch–Jozsa Algorithm (Constant Function)

This folder contains an implementation of the **Deutsch–Jozsa quantum algorithm** created using **IBM Quantum Composer** and exported as **OpenQASM** and **SVG circuit diagrams**.

The Deutsch–Jozsa algorithm is one of the earliest quantum algorithms demonstrating how quantum computation can outperform classical computation for specific problems.

---

# Problem Statement

The algorithm considers a Boolean function

$$
f(x) : {0,1}^n \rightarrow {0,1}
$$

with the promise that the function is either:

* **Constant** – the output is the same for all inputs
* **Balanced** – the output is $0$ for half of the inputs and $1$ for the other half

The goal is to determine whether the function is **constant or balanced**.

---

# Classical vs Quantum Computation

### Classical approach

In the worst case, a classical computer must evaluate the function

$$
2^{n-1} + 1
$$

times to determine whether the function is constant or balanced.

### Quantum approach

The **Deutsch–Jozsa algorithm** solves the problem using **only one evaluation of the oracle**.

This illustrates an exponential improvement compared to classical algorithms.

---

# Circuit Overview

The circuit implemented here uses:

* **4 input qubits**
* **1 ancilla qubit**

---

# Step 1 — Initialization

All input qubits start in the state

$$
|0\rangle
$$

The ancilla qubit is prepared in the state

$$
|-\rangle = \frac{|0\rangle - |1\rangle}{\sqrt{2}}
$$

This is achieved by applying:

* an **X gate**
* followed by a **Hadamard gate**

to the ancilla qubit.

---

# Step 2 — Creating Superposition

Hadamard gates are applied to the input register:

$$
H^{\otimes n} |0\rangle
$$

This produces a superposition of all possible input states.

---

# Step 3 — Oracle

The oracle represents the function ( f(x) ).

In this implementation **no gates are applied between the barriers**, which corresponds to a **constant oracle** where

$$
f(x) = 0
$$

for all input values.

---

# Step 4 — Interference

A second layer of Hadamard gates is applied to the input qubits.

Quantum interference causes the amplitudes of the states to combine in a way that reveals whether the function is constant or balanced.

---

# Step 5 — Measurement

The input qubits are measured.

Expected result for a **constant function**:

$$
0000
$$

If the function were balanced, at least one measured bit would be **1**.

---

# Circuit Diagram

The file `deutsch_jozsa.svg` contains the **visual representation of the circuit** exported from IBM Quantum Composer.

It displays:

* qubit wires
* Hadamard gates
* initialization gates
* measurement operations

---

# Files in this Folder

* `deutsch_jozsa.qasm` — OpenQASM description of the quantum circuit
* `deutsch_jozsa.svg` — circuit diagram exported from IBM Quantum Composer

---

# Running the Circuit with Qiskit

Example Python script:

```python
from qiskit import QuantumCircuit, Aer, execute

qc = QuantumCircuit.from_qasm_file("deutsch_jozsa.qasm")

backend = Aer.get_backend("qasm_simulator")

job = execute(qc, backend=backend, shots=1024)

result = job.result()

print(result.get_counts())
```

---

# Platform Used

This circuit was designed and simulated using:

* IBM Quantum Composer
* IBM Quantum Experience
* OpenQASM 2.0
* Qiskit compatible format

---

# Conclusion

This implementation demonstrates the **Deutsch–Jozsa algorithm with a constant oracle**.

The algorithm exploits **quantum superposition and interference** to determine whether a function is constant or balanced using **a single oracle evaluation**, highlighting one of the earliest examples of **quantum computational advantage**.
