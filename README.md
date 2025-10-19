🎲 Quantum Dice Roller — A Quantum Randomness Simulator
The Quantum Dice Roller is a Python-based simulation that demonstrates how quantum superposition and measurement can be used to generate perfectly random outcomes — just like rolling a die, but with quantum principles.
Instead of relying on classical pseudo-random algorithms, this project mimics how a quantum computer would prepare qubits in an equal superposition of states, measure them, and collapse the wavefunction to yield a random number. The result is a quantum-accurate dice roll simulated on classical hardware.

🧠 Concept Overview
In quantum mechanics, a qubit can exist in a superposition of |0⟩ and |1⟩ until it is measured, at which point it collapses to one of the states with a certain probability.
This simulator extends that principle to multiple qubits to emulate a die with any number of sides:

Determine the minimum number of qubits required: k = ceil(log₂(N))
Create a uniform superposition over all 2^k possible states
Simulate measurement to obtain a random basis state
Map that measurement outcome to a die face (1 to N) using rejection sampling to ensure fairness
The process models what would happen if an actual quantum computer were used to generate a random outcome from a fair superposition.

⚙️ Features
🎯 True quantum-style randomness (simulated using uniform probability over quantum states)
🧩 Supports any N-sided die (2-sided coin up to large N)
🧮 Efficient batch simulation using NumPy

📊 Visual output with histogram analysis (optional Matplotlib visualization)

💡 Lightweight & educational — ideal for learning basic quantum concepts without needing a real quantum processor
