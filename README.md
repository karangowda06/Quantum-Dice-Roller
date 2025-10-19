# Quantum-Dice-Roller
🎲 Quantum Dice Roller — A Quantum Randomness Simulator  The Quantum Dice Roller is a Python-based simulation that demonstrates how quantum superposition and measurement can be used to generate perfectly random outcomes — just like rolling a die, but with quantum principles.  Instead of relying on classical pseudo-random algorithms.
# 🎲 Quantum Dice Roller — Quantum Randomness Simulator

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Quantum](https://img.shields.io/badge/Quantum-Simulation-purple)
![Made with NumPy](https://img.shields.io/badge/Made%20with-NumPy-orange)
### 🧠 Overview

The **Quantum Dice Roller** is a Python-based simulator that demonstrates how **quantum superposition** and **measurement** can generate perfectly random outcomes — similar to rolling a die, but modeled on quantum principles.

Instead of using a classical pseudo-random number generator, this project emulates how a **quantum computer** would prepare qubits in an equal superposition, measure them, and collapse the wavefunction to produce a truly random result.  
The result is a **quantum-accurate dice roll**, simulated on classical hardware.

### ⚙️ How It Works

1. Compute the number of qubits needed for an N-sided die:  
   `k = ceil(log₂(N))`
2. Prepare an **equal superposition** of all `2^k` states.  
3. Simulate a **quantum measurement** (uniform random draw).  
4. Use **rejection sampling** to ensure fair mapping of outcomes to the die faces (1..N).  
5. Return a random, unbiased result that mimics a real quantum measurement.

This process mirrors what would happen on a quantum device using gates and measurement operators — but here, it’s simulated efficiently using NumPy.
### ✨ Features

- 🎯 Simulates **quantum-style randomness** using uniform superposition  
- 🧩 Supports **any N-sided die** (from 2-sided coin to large N)  
- ⚡ **Fast & efficient** batch simulation via NumPy  
- 📊 **Visualizes** results with histogram plots (optional)  
- 🧮 **Educational tool** to understand basic quantum concepts  
- 💡 Runs entirely on classical hardware — no quantum computer needed 
