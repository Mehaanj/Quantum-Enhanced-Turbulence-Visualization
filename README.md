# 🌀 Quantum-Enhanced Turbulence Visualization

This project simulates 3D turbulence evolution using quantum circuits to inject complexity and variability into a synthetic fluid simulation. It integrates **Qiskit** for quantum processing and **Plotly** for interactive 3D visualization.

---

## 📦 Dependencies

```bash
pip install qiskit plotly matplotlib
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

