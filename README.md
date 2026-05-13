# Secure-FL-for-UAV
Secure Federated Learning Framework for Unmanned Aerial Vehicles (UAVs) is a privacy-preserving and attack-resilient distributed learning framework designed for collaborative intelligence in UAV networks. The framework enables multiple UAVs to train shared machine learning models without exchanging raw data.

## Overview

Secure-FL-for-UAV is a resource-constrained secure Federated Learning (FL) framework designed for Unmanned Aerial Vehicle (UAV) networks operating under limited energy, computation, memory, and communication bandwidth. The framework integrates SCAFFOLD-based drift correction, Top-K gradient sparsification, lightweight Differential Privacy (DP), and secure aggregation to enable efficient and privacy-preserving collaborative learning in dynamic UAV environments.

The proposed framework is evaluated using UAV object detection datasets under non-IID data settings and demonstrates improvements in communication efficiency, energy consumption, convergence stability, and privacy preservation.

This repository corresponds to the experiments reported in the manuscript:

“Resource-Constrained Secure Federated Learning Framework for Unmanned Aerial Vehicles”

Experiments correspond to GitHub release `v1.0`.

## Features

* Federated Learning for UAV networks
* SCAFFOLD-based client drift mitigation
* Differential Privacy with Gaussian noise
* Gradient sparsification using Top-K updates
* Secure aggregation for privacy-preserving model fusion
* Non-IID data partitioning using Dirichlet distribution
* Lightweight CNN architecture for UAV deployment
* Energy and communication overhead evaluation
* Privacy attack evaluation:

  * Gradient inversion attack
  * Membership inference attack
* Scalable evaluation with 50–100 UAV clients


## Repository Structure

Secure-FL-for-UAV/
│
├── configs/                  # Experiment configuration files
├── datasets/                 # Dataset preparation scripts
├── models/                   # CNN model definitions
├── scripts/                  # Utility and execution scripts
├── results/                  # Experimental logs and outputs
├── figures/                  # Figures used in manuscript
├── checkpoints/              # Saved model checkpoints
├── train.py                  # Main FL training script
├── evaluate.py               # Evaluation script
├── requirements.txt          # Python dependencies
├── seeds.txt                 # Random seeds used
├── README.md                 # Repository documentation
├── LICENSE                   # License information
└── CITATION.cff              # Citation metadata


## Installation

### Clone Repository

git clone https://github.com/sofiyastephen1-sudo/Secure-FL-for-UAV.git
cd Secure-FL-for-UAV

### Create Virtual Environment

python -m venv venv
source venv/bin/activate

### Install Dependencies

pip install -r requirements.txt

## Dataset Preparation

### Datasets Used

1. Airborne UAV Detection Dataset
2. Drone Detection Dataset

### Download Datasets

#### Airborne UAV Detection Dataset

Download from:

[https://universe.roboflow.com/team-rbfpa/airborne-uav-detection](https://universe.roboflow.com/team-rbfpa/airborne-uav-detection)

#### Drone Detection Dataset

Download from:

[https://github.com/Maciullo/DroneDetectionDataset](https://github.com/Maciullo/DroneDetectionDataset)

### Dataset Directory Structure

datasets/
│
├── airborne_uav/
├── drone_detection/
└── processed/

### Preprocessing

Run:

python scripts/preprocess.py

## Running Experiments

### Train ResFL-UAV with Differential Privacy

python train.py \
    --dataset airborne \
    --clients 100 \
    --rounds 100 \
    --epsilon 1.2 \
    --dp True \
    --scaffold True \
    --topk 0.1 \
    --seed 42

### Train Without Differential Privacy

python train.py \
    --dataset airborne \
    --clients 100 \
    --rounds 100 \
    --dp False \
    --seed 42

### Evaluate Trained Model

python evaluate.py

## Hyperparameters

| Parameter             | Value  |
| --------------------- | ------ |
| Optimizer             | Adam   |
| Learning Rate         | 0.001  |
| Batch Size            | 16     |
| Local Epochs          | 2      |
| Communication Rounds  | 100    |
| DP Clipping Norm      | 1.0    |
| Gaussian Noise Std    | 1.1    |
| Top-K Sparsification  | 10%    |
| Dirichlet Alpha       | 0.3    |
| Number of UAV Clients | 50–100 |

## Reproducing Paper Results

### Reproducing Table 3

python train.py --config configs/dp_enabled.yaml

### Reproducing Table 4

python scripts/privacy_analysis.py

### Reproducing Table 10

python scripts/compare_baselines.py

### Reproducing Privacy Attack Evaluation

python scripts/attack_evaluation.py

All experiments were conducted using random seeds:

42
123
2025

Results are reported as mean ± standard deviation across 3 independent runs.

## Results

### Main Experimental Findings

* Accuracy with DP enabled (ε = 1.2): 89.3%
* Non-private accuracy: 94.2%
* Communication overhead reduction: 68.4%
* Energy reduction: 32.7%
* Training speedup: 2.9×

### Privacy Evaluation

The framework significantly reduces vulnerability against:

* Gradient inversion attacks
* Membership inference attacks

through Differential Privacy and secure aggregation.

## Hardware Requirements

Experiments were conducted using:

| Component | Specification         |
| --------- | --------------------- |
| CPU       | Intel i7 / equivalent |
| RAM       | 16 GB                 |
| GPU       | NVIDIA RTX 3060       |
| CUDA      | 12.1                  |
| Python    | 3.10                  |
| PyTorch   | 2.2.1                 |
| OS        | Ubuntu 22.04          |

Simulated UAV constraints:

* CPU power: < 1 W
* Memory: 4 GB
* Communication bandwidth: 50–200 Mbps

## Citation

If you use this repository, please cite:

```bibtex
@article{resfluav2026,
  title={Resource-Constrained Secure Federated Learning Framework for Unmanned Aerial Vehicles},
  author={Sophia, S, Getzi Jeba Leelipushpam, P., and T. Jemima Jebaseeli},
  journal={Array},
  year={2026}
}

## License

This project is licensed under the MIT License.

See the LICENSE file for details.
