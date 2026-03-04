# Superdense Coding

This folder contains an implementation of the **Superdense Coding** protocol created with **IBM Quantum Composer** and exported as OpenQASM / SVG.

Superdense coding is a quantum communication protocol that uses an entangled pair to transmit **two classical bits** using **one qubit** (plus a pre-shared entangled qubit between sender and receiver).

---

## Files in this folder
- `superdense_coding.qasm` — OpenQASM representation of the circuit exported from IBM Quantum Composer.  
- `superdense_coding.svg` — Vector diagram of the circuit (displayed below).

---

## Circuit diagram

![Superdense Coding Circuit](superdense_coding.svg)

---

## Short description (what the circuit does)

1. **Bell-state preparation**: apply `H` on one qubit and `CNOT` to entangle the pair, producing the Bell state
$|\Phi^{+}\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}$
2. **Encoding** (performed by the sender on their qubit): depending on the two classical bits to send, apply one of the Pauli operations:
   - `00` → Identity `I`
   - `01` → `X`
   - `10` → `Z`
   - `11` → `XZ` (or `Y` up to a global phase)
3. **Decoding** (performed by the receiver): apply `CNOT` then `H` (Bell-basis measurement circuit) to convert the entangled state into the computational basis.
4. **Measurement**: measure both qubits to recover the two classical bits.

---

## Encoding ↔ Expected measurement mapping

| Classical bits (sender) | Encoding on sender's qubit | Expected measurement outcome (after decoding) |
|-------------------------|----------------------------|-----------------------------------------------|
| `00`                   | `I`                        | `00`                                          |
| `01`                   | `X`                        | `01`                                          |
| `10`                   | `Z`                        | `10`                                          |
| `11`                   | `XZ`                       | `11`                                          |

> **Note:** The **displayed bitstring order** returned by simulators (e.g., `result.get_counts()`) can depend on measurement/register ordering in the OpenQASM file. If you see reversed bit order (e.g. `10` printed when you expected `01`), check the `measure` lines in the `.qasm` file to see which qubit maps to which classical bit and map appropriately.

---

## How to run the `.qasm` file with Qiskit (example)

```python
# example_run.py
from qiskit import QuantumCircuit, Aer, execute

# Load the QASM file in the same folder
qc = QuantumCircuit.from_qasm_file("superdense_coding.qasm")

# Draw (optional) and simulate
print(qc.draw(output='text'))

backend = Aer.get_backend('qasm_simulator')
job = execute(qc, backend=backend, shots=1024)
result = job.result()
counts = result.get_counts()
print("Counts:", counts)
