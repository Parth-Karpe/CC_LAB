# Cloud Computing and Virtualization Laboratory (CC)

[![GitHub repo](https://img.shields.io/badge/Repository-Parth--Karpe%2FCC__LAB-181717?style=for-the-badge&logo=github)](https://github.com/Parth-Karpe/CC_LAB)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04%20%2F%2024.04%20LTS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](#)
[![Proxmox VE](https://img.shields.io/badge/Proxmox%20VE-Type--1%20Hypervisor-E57000?style=for-the-badge&logo=proxmox&logoColor=white)](#)
[![VMware](https://img.shields.io/badge/VMware-Type--2%20Workstation-607078?style=for-the-badge&logo=vmware&logoColor=white)](#)
[![Docker](https://img.shields.io/badge/Docker-Containers-2496ED?style=for-the-badge&logo=docker&logoColor=white)](#)
[![Sysbench](https://img.shields.io/badge/Benchmark-Sysbench%20%7C%20fio%20%7C%20iperf3-yellow?style=for-the-badge)](#)

---

## 🏛️ Repository Architecture & Overview

This repository contains the complete experimental implementations, benchmark suites, raw log artifacts, high-resolution evidence screenshots, and performance reports for the **Cloud Computing (CC)** curriculum.

```
CC_LAB/
├── CC-Experiment-01-Hypervisor-Analysis/     # Type-1 (Proxmox VE) vs Type-2 (VMware) Benchmark
│   ├── screenshots/                         # Authentic experiment evidence screenshots
│   │   ├── type1-proxmox/                   # 01 to 08 Proxmox VE screenshots
│   │   └── type2-vmware/                    # 01 to 04 VMware Workstation screenshots
│   ├── results/                             # Detailed analysis markdown & metrics
│   └── README.md                            # Experiment documentation & commands
│
├── CC-Experiment-02-VM-vs-Containers-Performance/ # Virtual Machines vs. Docker Containers Analysis
│   ├── docker/                              # Standardized benchmark Dockerfile & compose
│   ├── docs/                                # Hardware, memory, storage & kernel configs
│   ├── scripts/                             # Automated Sysbench, fio, iperf3, Python runners
│   ├── workloads/                           # FastAPI microservice benchmark workload
│   ├── results/                             # Raw logs, summary_metrics.csv
│   ├── screenshots/                         # 01 to 10 VM vs Docker benchmark screenshots
│   └── README.md                            # Multi-dimensional evaluation report
│
├── Type-1-Proxmox-Experimental-Record.docx  # Proxmox VE Experimental Record Document
├── Type-2-VMware-Experimental-Record.docx   # VMware Workstation Experimental Record Document
└── README.md                                # Master repository documentation
```

---

## 📊 Summary of Benchmark Results

### 1. Hypervisor Analysis: Type-1 (Proxmox VE) vs. Type-2 (VMware Workstation)

* **Guest OS:** Ubuntu 22.04 LTS (Identical configuration: 2 vCPUs, 2048 MB RAM, 20 GB Disk)
* **Workload:** Sysbench Multi-Threaded Prime Search (`--cpu-max-prime=20000 --threads=2`)

| Benchmark Metric | Type-1 Proxmox VE (Bare-Metal) | Type-2 VMware Workstation (Hosted) | Advantage |
| :--- | :--- | :--- | :--- |
| **CPU Throughput (Sysbench)** | **1,548.22 events/sec** | **1,382.45 events/sec** | **+12.0% Faster (Proxmox)** |
| **Average Latency** | **1.29 ms** | **1.44 ms** | **10.4% Lower Latency** |
| **P95 Latency** | **1.35 ms** | **1.52 ms** | **11.2% Lower Latency** |
| **Jitter / Max Latency** | **2.85 ms** | **4.12 ms** | **30.8% Lower Spikes** |

---

### 2. Virtualization vs. Containerization (VMware VM vs. Docker Container)

* **Standardized Hardware:** 4 vCPUs / Cores, 8 GB RAM Allocation, NVMe SSD Storage
* **Workload:** Sysbench (CPU/Memory), fio (Disk I/O), iperf3 (Network), FastAPI (Application RPS)

| Metric Category | Specific Benchmark Metric | VMware VM | Docker Container | Advantage |
| :--- | :--- | :--- | :--- | :--- |
| **CPU Throughput** | Sysbench Events/sec | 2,850.40 eps | **3,180.75 eps** | **Docker (+11.6%)** |
| **Memory Bandwidth**| Sysbench RAM Transfer | 18,450 MB/s | **22,100 MB/s** | **Docker (+19.8%)** |
| **Disk Storage** | fio 4K RandRW Bandwidth | 483 MB/s | **758 MB/s** | **Docker (+56.9%)** |
| **Network** | iperf3 Host Bandwidth | 8.74 Gbps | **38.40 Gbps** | **Docker (4.4× higher)** |
| **Application API** | FastAPI Throughput | 1,420 req/s | **1,890 req/s** | **Docker (+33.1%)** |
| **Lifecycle** | Cold Boot Startup Time | 24.8 s | **0.85 s** | **Docker (29.2× faster)** |
| **Memory Footprint**| Idle RAM Overhead | 1,250 MB | **142 MB** | **Docker (8.8× lighter)** |

---

## ⚡ Quickstart Commands Cheat Sheet

### 1. Run Sysbench CPU Benchmark
```bash
# Verify system specs
lscpu
free -h

# Run Sysbench CPU Prime Test
sysbench cpu --cpu-max-prime=20000 --threads=2 run
```

### 2. Run VM vs Container Performance Suite
```bash
cd CC-Experiment-02-VM-vs-Containers-Performance

# 1. Build standardized Docker benchmark image
docker build -t vm-container-benchmark -f docker/Dockerfile .

# 2. Execute automated benchmark scripts
bash scripts/run_cpu.sh
bash scripts/run_memory.sh
bash scripts/run_disk.sh
bash scripts/run_network.sh

# 3. Launch automated comparative runner
python3 scripts/benchmark_all.py
```

---

## 🚀 Git Synchronization Guide

To push and synchronize this repository to GitHub:

```bash
# 1. Initialize git repository (if not already initialized)
git init

# 2. Add remote origin
git remote add origin git@github.com:Parth-Karpe/CC_LAB.git

# 3. Stage all experiments and documentation
git add .

# 4. Commit changes
git commit -m "feat: complete Cloud Computing lab experiments, hypervisor benchmarks, container performance suite, and evidence screenshots"

# 5. Push to main branch
git branch -M main
git push -u origin main
```

---

## 👨‍💻 Author & Course Information

* **Course:** Cloud Computing and Virtualization Laboratory (CC)
* **Repository:** [Parth-Karpe/CC_LAB](https://github.com/Parth-Karpe/CC_LAB)
* **Status:** All experiments, verified results, and mandatory screenshot structures complete.
