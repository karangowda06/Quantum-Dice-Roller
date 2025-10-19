#!/usr/bin/env python3
"""
quantum_dice.py

Simulates a "quantum" dice roll by preparing an equal superposition
over 2^k basis states (k = ceil(log2(num_sides))),
measuring (uniform draw), and using rejection sampling to map
the measurement to 1..num_sides fairly.

Dependencies: numpy; matplotlib (optional, for the histogram).
"""

import argparse
import numpy as np
from collections import Counter

def quantum_dice_roll(num_sides=6):
    """
    Simulate one quantum dice roll for a die with `num_sides` sides (>=2).
    Returns an integer in 1..num_sides.
    """
    if num_sides < 2:
        raise ValueError("num_sides must be >= 2")
    k = int(np.ceil(np.log2(num_sides)))   # number of qubits
    dim = 1 << k                           # 2**k
    while True:
        measured = np.random.randint(0, dim)
        if measured < num_sides:
            return int(measured + 1)
        # otherwise reject and try again

def quantum_dice_roll_batch(num_sides, n):
    """
    Generate n rolls efficiently using vectorized draws with rejections.
    Returns a NumPy array of length n with values in 1..num_sides.
    """
    if n <= 0:
        return np.array([], dtype=int)
    k = int(np.ceil(np.log2(num_sides)))
    dim = 1 << k
    results = []
    while len(results) < n:
        remaining = n - len(results)
        chunk = max(64, remaining * 2)  # heuristic chunk size
        candidates = np.random.randint(0, dim, size=chunk)
        valid = candidates[candidates < num_sides] + 1
        results.extend(valid.tolist())
    return np.array(results[:n], dtype=int)

def demo(num_sides=6, trials=10000, show_hist=True):
    """
    Run `trials` simulated quantum dice rolls and print counts/frequencies.
    Optionally display a histogram if matplotlib is available.
    """
    rolls = quantum_dice_roll_batch(num_sides, trials)
    counts = Counter(rolls)
    print(f"Quantum dice simulation — {trials} trials, {num_sides}-sided die")
    for face in range(1, num_sides + 1):
        c = counts.get(face, 0)
        print(f"Face {face:2d}: {c:6d}  freq={c/trials:.6f}")

    if show_hist:
        try:
            import matplotlib.pyplot as plt
            faces = list(range(1, num_sides + 1))
            freqs = [counts.get(f, 0) / trials for f in faces]
            plt.figure(figsize=(8,4))
            plt.bar(faces, freqs)
            plt.xlabel("Face")
            plt.ylabel("Frequency")
            plt.title(f"{num_sides}-sided Quantum Dice — {trials} trials")
            plt.xticks(faces)
            plt.tight_layout()
            plt.show()
        except Exception:
            print("(matplotlib not available — skipping histogram)")

def parse_args():
    p = argparse.ArgumentParser(description="Quantum-style dice roller simulator")
    p.add_argument("-s", "--sides", type=int, default=6, help="Number of sides (>=2)")
    p.add_argument("-n", "--trials", type=int, default=1, help="How many rolls to perform")
    p.add_argument("--demo", action="store_true", help="Run demo (prints distribution after many trials)")
    p.add_argument("--no-hist", action="store_true", help="Do not show histogram (even if matplotlib exists)")
    return p.parse_args()

if __name__ == "__main__":
    args = parse_args()
    if args.demo:
        demo(num_sides=args.sides, trials=args.trials if args.trials>0 else 10000, show_hist=not args.no_hist)
    else:
        # single-run / batch-run mode: print results of the requested number of rolls
        if args.trials == 1:
            print(quantum_dice_roll(num_sides=args.sides))
        else:
            rolls = quantum_dice_roll_batch(args.sides, args.trials)
            print(" ".join(map(str, rolls)))
