# 🌀 Quantum-Enhanced Turbulence Visualization

This project simulates 3D turbulence evolution using quantum circuits to inject complexity and variability into a synthetic fluid simulation. It integrates **Qiskit** for quantum processing and **Plotly** for interactive 3D visualization.

---

## 📦 Dependencies

```bash
!pip install qiskit==0.46.3 qiskit-aer qiskit-terra qiskit-ibmq-provider qiskit-machine-learning qiskit-algorithms qiskit-optimization
```

##ALSO ADD
```bash
!pip list | grep qiskit
```
### Import Numpy
```bash
!pip install numpy==1.24
```

```bash
!pip install qiskit-aer

```
### Delete the unwanted files
```bash
!pip cache purge
```

### Import AER
```bash
from qiskit import Aer
print(Aer.backends())

```

### Load the account 
```bash

from qiskit import IBMQ

# Save your IBM Quantum token (replace 'YOUR_API_TOKEN' with your actual token)
IBMQ.save_account('YOUR_API_TOKEN')

```

```bash
# Load the IBM Quantum account
IBMQ.load_account()

```
```bash
# Get the provider
provider = IBMQ.get_provider()

# List all available backends
backends = provider.backends()
print(backends)
```
```bash
from qiskit import QuantumCircuit, Aer, transpile, assemble, execute

# Create a quantum circuit with 2 qubits
qc = QuantumCircuit(2, 2)  # Add 2 classical bits for measurement

# Create a Bell state
qc.h(0)  # Apply Hadamard gate to the first qubit
qc.cx(0, 1)  # Apply CNOT gate from qubit 0 to qubit 1

# Measure the qubits
qc.measure([0, 1], [0, 1])  # Measure qubit 0 into classical bit 0 and qubit 1 into classical bit 1

# Draw the circuit
qc.draw('text')  # This will render the circuit as text instead of using Matplotlib.
```
```bash
!pip cache purge# Use the Aer simulator
simulator = Aer.get_backend('aer_simulator')

# Transpile the circuit for the simulator
transpiled_circuit = transpile(qc, simulator)

# Assemble the circuit into a Qobj
qobj = assemble(transpiled_circuit)

# Execute the circuit
job = simulator.run(qobj)

# Get the results
result = job.result()

# Get the counts (measurement results)
counts = result.get_counts(qc)
print(counts)
```

### Sample
```bash
# Import necessary libraries
from qiskit import QuantumCircuit, Aer, transpile, assemble, execute
from qiskit.visualization import plot_histogram

# Create a quantum circuit with 2 qubits and 2 classical bits
qc = QuantumCircuit(2, 2)  # 2 qubits, 2 classical bits for measurement

# Create a Bell state
qc.h(0)  # Apply Hadamard gate to the first qubit
qc.cx(0, 1)  # Apply CNOT gate from qubit 0 to qubit 1

# Measure the qubits
qc.measure([0, 1], [0, 1])  # Measure qubit 0 into classical bit 0 and qubit 1 into classical bit 1

# Draw the circuit
print("Quantum Circuit:")
print(qc.draw())

# Use the Aer simulator
simulator = Aer.get_backend('aer_simulator')

# Transpile the circuit for the simulator
transpiled_circuit = transpile(qc, simulator)

# Assemble the circuit into a Qobj
qobj = assemble(transpiled_circuit)

# Execute the circuit
job = simulator.run(qobj)

# Get the results
result = job.result()

# Get the counts (measurement results)
counts = result.get_counts(qc)
print("Counts:", counts)

# Plot the histogram of the results
plot_histogram(counts)
```
---
## 🧠 Overview
- Uses a parameterized quantum circuit to generate dynamic behavior.

- Visualizes a 3D synthetic turbulence field influenced by virtual pressure points.

- Evolves turbulence over time using quantum results.

- Includes interactive sliders and animation with Plotly.

---
## 🧮 Code Breakdown
1. turbulence_circuit(num_qubits, time_step)
- Builds a parameterized quantum circuit:

- Applies Hadamard gates to place qubits in superposition.

- Creates entanglement using CNOT gates.

- Introduces rotation (RY, RZ) and controlled-RZ gates to add complexity.

- Binds θ = π/4 to control quantum gate rotation.

- Returns the final quantum circuit.

2. run_quantum_circuit(qc)
- Runs the quantum circuit on the AerSimulator.

- Retrieves and returns measurement counts (bitstring probabilities).

3. generate_turbulence_field(size, pressure_points, time_step)
- Initializes a 3D cube of random values as a turbulence field.

- Adds pressure disturbances at specified (x, y, z) coordinates.

- Intensity scaled by time step.

- Returns the updated turbulence array.

4. create_interactive_visualization(...)
- Builds 3D Scatter plots using Plotly for each time step:

- Uses color and opacity to reflect turbulence intensity.

- Marks pressure points as red dots.

- Adds time animation with go.Frame() and a play/pause slider.

- Displays the animated visualization in the browser.

---

## 📊 Parameters
- num_qubits = 7: Number of qubits for quantum simulation (affects circuit complexity).

- time_steps: 10 evenly spaced values from 0.1 to 2.0.

- pressure_points: List of [x, y, z, intensity] for where and how turbulence is injected.

- turbulence_data: Stores the turbulence field per time step.

- quantum_circuits: Stores each quantum circuit for reuse/analysis.

- quantum_counts: Stores the measurement result of each quantum circuit.

