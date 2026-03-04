# Deutsch–Jozsa Algorithm

This folder contains an implementation of the **Deutsch–Jozsa quantum algorithm** created using **IBM Quantum Composer** and exported as **OpenQASM** and **SVG circuit diagrams**.

The Deutsch–Jozsa algorithm is one of the earliest examples demonstrating how **quantum computers can solve certain problems exponentially faster than classical computers**.

---

# Problem Statement

Given a function

$$
f(x): \{0,1\}^n \rightarrow \{0,1\}
$$

the function is promised to be either:

- **Constant** → the output is the same for all inputs  
- **Balanced** → the output is $0$ for half the inputs and $1$ for the other half  

The goal is to determine whether the function is **constant or balanced**.

---

# Classical vs Quantum Computation

### Classical computation

A classical computer may require up to

$$
2^{n-1} + 1
$$

function evaluations to determine whether the function is constant or balanced.

### Quantum computation

The **Deutsch–Jozsa algorithm** can determine this with **only one evaluation of the oracle**, demonstrating a clear advantage of quantum computation.

---

# Circuit Overview

The circuit implemented here uses:

- **4 input qubits**
- **1 ancilla qubit**

---

# Step 1 — Initialization

The ancilla qubit is prepared in the state

$$
|-\rangle = \frac{|0\rangle - |1\rangle}{\sqrt{2}}
$$

This state is obtained by applying:

- an **X gate**
- followed by a **Hadamard gate**

to the ancilla qubit.

---

# Step 2 — Superposition

Hadamard gates are applied to all input qubits:

$$
H^{\otimes n}|0\rangle
$$

This creates a superposition of all possible input states.

---

# Step 3 — Oracle

The oracle encodes the function $f(x)$.

In this implementation the oracle is constructed using **CNOT gates**:

```
cx q[0], q[4]
cx q[1], q[4]
cx q[2], q[4]
cx q[3], q[4]
```

This corresponds to a **balanced function**, since the output depends on multiple input qubits.

---

# Step 4 — Quantum Interference

Another layer of **Hadamard gates** is applied to the input qubits.

Quantum interference ensures that measurement outcomes reveal whether the function is constant or balanced.

---

# Step 5 — Measurement

The input qubits are measured.

- If the result is **0000**, the function is **constant**
- If **any bit is 1**, the function is **balanced**

---

# Circuit Diagram

The file `deutsch_jozsa.svg` contains the **visual diagram of the quantum circuit** exported from IBM Quantum Composer.

It shows:

- qubit wires
- Hadamard gates
- CNOT gates
- measurement operations

---

# Files in this Folder

- `deutsch_jozsa.qasm` — OpenQASM description of the quantum circuit  
- `deutsch_jozsa.svg` — circuit diagram exported from IBM Quantum Composer  

---

# Running the Circuit with Qiskit

Example Python script to simulate the circuit:

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

- IBM Quantum Composer  
- IBM Quantum Experience  
- OpenQASM 2.0  
- Qiskit compatible circuit format  

---

# Conclusion

This implementation demonstrates the **Deutsch–Jozsa algorithm**, which shows how quantum computers can determine whether a function is **constant or balanced** using **only a single oracle query**.

It highlights the role of **quantum superposition, interference, and entanglement** in achieving computational advantages over classical algorithms.
