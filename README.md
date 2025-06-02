# QuBound Dataset for Quantum Circuit Performance Prediction

This repository contains the processed dataset used in the paper:

**"Computational Performance Bounds Prediction in Quantum Computing with Unstable Noise"**
Submitted to *IEEE TCAD*, 2024.

---

## Dataset Overview

This dataset includes circuit-specific performance traces and noise parameters collected from IBM Quantum cloud backends. It supports two types of performance metrics used in our experiments:

* **Observable-based Performance** → The performance is defined using the Observable, such as ZZZ observables.
* **Probability-based Performance** → The performance is defined using the Probability of quantum state, such as the probability of state |0000>.

The performance trace will be used to create the label/ground truth in the experiments, while the noise parameters, along with the circuit structures, will be used to 
create the input features. Notice that for the Observable-based dataset, it requires preprocessing to handle and calculate the observables, otherwise, it will only contain
the probability of all possible quantum states. On the other hand, for the Probability-based dataset, since we did a reverse circuit operation, the user should only care
about the first quantum state |0X>, as the reverse operation will theoretically undo the circuit and result it back to the original state.


---

## Folder Structure

```
Datasets-for-QuBound/
│
├── d1/    ← Data for Table IV (Observable-based)
│   ├── GHZ3_ibmq_kolkata.csv
│   ├── ...
│
├── d2/    ← Data for Table II (Probability-based)
│   ├── GHZ3_reverse_ibmq_mumbai.csv
│   ├── ...
```

Each `.csv` file corresponds to one circuit on one backend.
Each row represents one execution instance, including:

* Gate-level encoding
* Noise parameters (T1, T2, gate error, readout error)
* Measured performance value

---

##  Circuit Benchmarks

* GHZ3 / GHZ4
* VQE4
* QAOA4
* HS4
* RB3

---

##  Usage

Each file contains execution traces for a specific quantum circuit under real device noise.
They are used to train and evaluate the QuBound model for circuit-specific performance bound prediction.
Input features are constructed as described in the paper, and can be directly used for sequence learning.

---

<!-- ##  Citation

Please cite the following if you use this dataset:

> \[Your paper’s citation entry once accepted]

--- -->

##  Contact

For questions, please contact:
**Jinyang Li** – jli56@gmu.edu

