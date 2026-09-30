# Cloud Computing and Virtualization Laboratory (CC) — Experiment 01

[![GitHub repo](https://img.shields.io/badge/Repository-Parth--Karpe%2FCC__LAB__EXPERIMENT__01-181717?style=for-the-badge&logo=github)](https://github.com/Parth-Karpe/CC_LAB_EXPERIMENT_01)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04%20LTS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](#)
[![Proxmox VE](https://img.shields.io/badge/Proxmox%20VE-Type--1%20Hypervisor-E57000?style=for-the-badge&logo=proxmox&logoColor=white)](#)
[![VMware](https://img.shields.io/badge/VMware-Type--2%20Workstation-607078?style=for-the-badge&logo=vmware&logoColor=white)](#)
[![Sysbench](https://img.shields.io/badge/Benchmark-Sysbench-yellow?style=for-the-badge)](#)

---

## 🏛️ Repository Architecture & Overview

This repository contains the complete experimental implementation, benchmark results, high-resolution evidence screenshots, and performance reports for **CC Lab Experiment 01: Hypervisor Analysis — Type-1 (Proxmox VE) vs Type-2 (VMware Workstation)**.

```
CC_LAB_EXPERIMENT_01/
├── CC-Experiment-01-Hypervisor-Analysis/     # Type-1 (Proxmox VE) vs Type-2 (VMware) Benchmark
│   ├── screenshots/                         # Authentic experiment evidence screenshots
│   │   ├── type1-proxmox/                   # 01 to 08 Proxmox VE screenshots
│   │   └── type2-vmware/                    # 01 to 04 VMware Workstation screenshots
│   ├── results/                             # Detailed analysis markdown & metrics
│   └── README.md                            # Experiment documentation & commands
│
├── Type-1-Proxmox-Experimental-Record.docx  # Proxmox VE Experimental Record Document
├── Type-2-VMware-Experimental-Record.docx   # VMware Workstation Experimental Record Document
└── README.md                                # Repository documentation
```

---

## 📊 Summary of Benchmark Results

### Hypervisor Analysis: Type-1 (Proxmox VE) vs. Type-2 (VMware Workstation)

* **Guest OS:** Ubuntu 22.04 LTS (Identical configuration: 2 vCPUs, 2048 MB RAM, 20 GB Disk)
* **Workload:** Sysbench Multi-Threaded Prime Search (`--cpu-max-prime=20000 --threads=2`)

| Benchmark Metric | Type-1 Proxmox VE (Bare-Metal) | Type-2 VMware Workstation (Hosted) | Advantage |
| :--- | :--- | :--- | :--- |
| **CPU Throughput (Sysbench)** | **1,548.22 events/sec** | **1,382.45 events/sec** | **+12.0% Faster (Proxmox)** |
| **Average Latency** | **1.29 ms** | **1.44 ms** | **10.4% Lower Latency** |
| **P95 Latency** | **1.35 ms** | **1.52 ms** | **11.2% Lower Latency** |
| **Jitter / Max Latency** | **2.85 ms** | **4.12 ms** | **30.8% Lower Spikes** |

---

## ⚡ Quickstart Commands Cheat Sheet

### Run Sysbench CPU Benchmark
```bash
# Verify system specs
lscpu
free -h

# Run Sysbench CPU Prime Test
sysbench cpu --cpu-max-prime=20000 --threads=2 run
```

---

## 🚀 Git Synchronization Guide

To push and synchronize this repository to GitHub:

```bash
# 1. Initialize git repository (if not already initialized)
git init

# 2. Add remote origin
git remote add origin git@github.com:Parth-Karpe/CC_LAB_EXPERIMENT_01.git

# 3. Stage all experiments and documentation
git add .

# 4. Commit changes
git commit -m "feat: CC Lab Experiment 01 - Hypervisor Analysis benchmarks and evidence screenshots"

# 5. Push to main branch
git branch -M main
git push -u origin main
```

---

## 👨‍💻 Author & Course Information

* **Course:** Cloud Computing and Virtualization Laboratory (CC)
* **Repository:** [Parth-Karpe/CC_LAB_EXPERIMENT_01](https://github.com/Parth-Karpe/CC_LAB_EXPERIMENT_01)
* **Status:** Experiment 01 — verified results and mandatory screenshot structures complete.
