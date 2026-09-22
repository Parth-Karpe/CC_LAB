# Performance Analysis of Type-1 and Type-2 Hypervisors

## Proxmox VE vs VMware Workstation

> A practical experimental study comparing the CPU performance and resource utilization of a Type-1 and Type-2 hypervisor using identically configured Ubuntu virtual machines.

---

## 📌 Overview

This repository contains the complete implementation, experimental observations, screenshots, benchmark results, and comparison of:

- **Proxmox VE** — Type-1 Hypervisor
- **VMware Workstation** — Type-2 Hypervisor

The experiment uses identically configured Ubuntu virtual machines and the **Sysbench CPU benchmark** to analyze performance.

The primary objective is to understand how virtualization architecture affects virtual machine performance when the guest operating system and allocated resources are kept approximately identical.

---

## 🎯 Objectives

1. Create a virtual machine using **Proxmox VE**.
2. Create an equivalent virtual machine using **VMware Workstation**.
3. Configure both VMs with approximately identical hardware resources.
4. Install Ubuntu on both virtual machines.
5. Verify CPU, memory, disk, and system configuration.
6. Install and configure Sysbench.
7. Perform CPU benchmarking using Sysbench.
8. Record execution time, events, events per second, and latency.
9. Monitor VM resource utilization.
10. Compare the experimental observations of Type-1 and Type-2 hypervisors.

---

# 🖥️ Hypervisors Used

| Hypervisor | Type | Environment |
|---|---|---|
| Proxmox VE | Type-1 | Centralized physical server |
| VMware Workstation | Type-2 | Runs on top of host operating system |

---

# ⚙️ Experimental VM Configuration

| Parameter | Configuration |
|---|---|
| Guest OS | Ubuntu |
| CPU | 2 vCPU |
| Memory | 2 GB |
| Virtual Disk | 20 GB |
| CPU Configuration | 1 processor/socket × 2 cores |
| Benchmark | Sysbench CPU |
| Benchmark Prime Limit | 20,000 |

---

# 🧪 Experiment 1 — Proxmox VE

## Type-1 Hypervisor

Proxmox VE is used as the Type-1 hypervisor.

### VM Name

```text
CC-Experiment1-Type1
```

### VM Configuration

| Resource | Configuration |
|---|---|
| Hypervisor | Proxmox VE |
| Hypervisor Type | Type-1 |
| Operating System | Ubuntu |
| CPU | 2 vCPU |
| Memory | 2 GB |
| Disk | 20 GB |
| Network | vmbr0 |

### Proxmox VM Creation Workflow

```text
General
   ↓
OS
   ↓
System
   ↓
Disks
   ↓
CPU
   ↓
Memory
   ↓
Network
   ↓
Confirm
```

---

## 📸 Proxmox Screenshots

### 1. Proxmox Login

![Proxmox Login](screenshots/proxmox/01-login.png)

### 2. Proxmox Dashboard

![Proxmox Dashboard](screenshots/proxmox/02-dashboard.png)

### 3. Virtual Machine Configuration

![Proxmox VM Configuration](screenshots/proxmox/03-vm-configuration.png)

### 4. CPU Configuration

![CPU Configuration](screenshots/proxmox/04-cpu.png)

Expected configuration:

```text
Sockets : 1
Cores  : 2
Total  : 2 vCPU
```

### 5. Memory Configuration

![Memory Configuration](screenshots/proxmox/05-memory.png)

```text
Memory: 2048 MiB
```

### 6. Disk Configuration

![Disk Configuration](screenshots/proxmox/06-disk.png)

```text
Disk: 20 GB
```

### 7. Network Configuration

![Network Configuration](screenshots/proxmox/07-network.png)

```text
Bridge: vmbr0
Model : VirtIO / Default
```

---

# 🐧 Ubuntu Verification — Proxmox VM

## System Information

```bash
hostnamectl
```

Record:

- Hostname
- Operating System
- Kernel Version
- Architecture

## CPU Information

```bash
lscpu
```

Record:

- Architecture
- CPU(s)
- CPU model
- Virtualization information

## Memory Information

```bash
free -h
```

Record:

- Total memory
- Used memory
- Free memory
- Available memory

## Disk Information

```bash
df -h
```

Record:

- Filesystem
- Total capacity
- Used space
- Available space

## Resource Monitoring

```bash
top
```

Observe:

- CPU utilization
- Memory utilization
- Running processes
- Load average

Press `q` to exit.

---

# ⚡ Sysbench Installation

```bash
sudo apt update
sudo apt install sysbench -y
```

Verify installation:

```bash
sysbench --version
```

---

# 🚀 Proxmox CPU Benchmark

```bash
sysbench cpu --cpu-max-prime=20000 run
```

### Metrics Recorded

- Total execution time
- Total number of events
- Events per second
- Minimum latency
- Average latency
- Maximum latency

## 📊 Proxmox Results

| Metric | Result |
|---|---:|
| Hypervisor | Proxmox VE |
| Type | Type-1 |
| CPU | 2 vCPU |
| Memory | 2 GB |
| Disk | 20 GB |
| Total Execution Time | **TODO** |
| Total Events | **TODO** |
| Events / Second | **TODO** |
| Minimum Latency | **TODO** |
| Average Latency | **TODO** |
| Maximum Latency | **TODO** |

> Replace `TODO` with the actual values obtained from the experiment.

---

# 🖥️ Proxmox Resource Utilization

Resource utilization was observed from:

```text
Datacenter
   ↓
Proxmox Node
   ↓
Virtual Machine
   ↓
Summary
```

| Resource | Observation |
|---|---|
| CPU Usage | TODO |
| Memory Usage | TODO |
| Network Traffic | TODO |
| Disk Usage | TODO |

---

# 🧪 Experiment 2 — VMware Workstation

## Type-2 Hypervisor

VMware Workstation is used as the Type-2 hypervisor.

The VM is configured to approximately match the Proxmox VM.

### VM Name

```text
CC-Experiment1-Type2
```

### VM Configuration

| Resource | Configuration |
|---|---|
| Hypervisor | VMware Workstation |
| Hypervisor Type | Type-2 |
| Operating System | Ubuntu |
| CPU | 2 vCPU |
| Memory | 2 GB |
| Disk | 20 GB |
| Network | NAT |

### VMware Workflow

```text
Launch VMware Workstation
        ↓
Create New Virtual Machine
        ↓
Typical Configuration
        ↓
Select Ubuntu ISO
        ↓
Configure VM Name
        ↓
Configure 20 GB Disk
        ↓
Customize Hardware
        ↓
Configure 2 vCPU
        ↓
Configure 2 GB RAM
        ↓
Configure Network
        ↓
Finish VM Creation
        ↓
Install Ubuntu
        ↓
Verify Configuration
        ↓
Install Sysbench
        ↓
Run CPU Benchmark
        ↓
Record Results
        ↓
Shutdown VM
```

---

# 📸 VMware Screenshots

### 1. VMware Workstation Home

![VMware Home](screenshots/vmware/01-home.png)

### 2. Create Virtual Machine

![VM Creation](screenshots/vmware/02-vm-creation.png)

### 3. VM Hardware Configuration

![VM Settings](screenshots/vmware/03-vm-settings.png)

### 4. CPU Configuration

![CPU Configuration](screenshots/vmware/04-cpu.png)

Expected:

```text
Processors              : 1
Cores per Processor     : 2
Total vCPU              : 2
```

### 5. Memory Configuration

![Memory Configuration](screenshots/vmware/05-memory.png)

```text
Memory: 2048 MB
```

### 6. Disk Configuration

![Disk Configuration](screenshots/vmware/06-disk.png)

```text
Disk: 20 GB
```

### 7. Network Configuration

![Network Configuration](screenshots/vmware/07-network.png)

```text
Network: NAT
```

---

# 🐧 Ubuntu Verification — VMware VM

## System Information

```bash
hostnamectl
```

## CPU Information

```bash
lscpu
```

## Memory Information

```bash
free -h
```

## Disk Information

```bash
df -h
```

## Resource Monitoring

```bash
top
```

Press `q` to exit.

---

# ⚡ Sysbench Installation

```bash
sudo apt update
sudo apt install sysbench -y
```

Verify:

```bash
sysbench --version
```

---

# 🚀 VMware CPU Benchmark

```bash
sysbench cpu --cpu-max-prime=20000 run
```

### Metrics Recorded

- Total execution time
- Total number of events
- Events per second
- Minimum latency
- Average latency
- Maximum latency

## 📊 VMware Results

| Metric | Result |
|---|---:|
| Hypervisor | VMware Workstation |
| Type | Type-2 |
| CPU | 2 vCPU |
| Memory | 2 GB |
| Disk | 20 GB |
| Total Execution Time | **TODO** |
| Total Events | **TODO** |
| Events / Second | **TODO** |
| Minimum Latency | **TODO** |
| Average Latency | **TODO** |
| Maximum Latency | **TODO** |

---

# 📈 Final Comparison

| Performance Metric | Proxmox VE | VMware Workstation |
|---|---:|---:|
| Hypervisor Type | Type-1 | Type-2 |
| CPU | 2 vCPU | 2 vCPU |
| Memory | 2 GB | 2 GB |
| Disk | 20 GB | 20 GB |
| Total Execution Time | TODO | TODO |
| Total Events | TODO | TODO |
| Events / Second | TODO | TODO |
| Minimum Latency | TODO | TODO |
| Average Latency | TODO | TODO |
| Maximum Latency | TODO | TODO |

---

# 📊 Performance Analysis

## Execution Time

```text
Proxmox VE:
TODO seconds

VMware Workstation:
TODO seconds
```

Observation:

> Record the measured difference based on the actual experiment.

## Events Per Second

```text
Proxmox VE:
TODO events/sec

VMware Workstation:
TODO events/sec
```

Observation:

> Record the measured difference based on the actual experiment.

## Latency

| Latency Metric | Proxmox VE | VMware Workstation |
|---|---:|---:|
| Minimum | TODO | TODO |
| Average | TODO | TODO |
| Maximum | TODO | TODO |

Observation:

> Analyze the measured latency values from both experiments.

---

# 📷 Experimental Evidence

All screenshots collected during the experiment are stored in:

```text
screenshots/
```

Screenshots are organized according to the hypervisor:

```text
screenshots/
├── proxmox/
└── vmware/
```

Each screenshot represents an actual stage of the experimental procedure.

---

# 📝 Experiment Log

## Proxmox VE

| Step | Status | Evidence |
|---|---|---|
| Proxmox login | ⬜ | Screenshot |
| VM creation | ⬜ | Screenshot |
| CPU configuration | ⬜ | Screenshot |
| Memory configuration | ⬜ | Screenshot |
| Disk configuration | ⬜ | Screenshot |
| Network configuration | ⬜ | Screenshot |
| Ubuntu installation | ⬜ | Screenshot |
| CPU verification | ⬜ | Screenshot |
| Memory verification | ⬜ | Screenshot |
| Sysbench installation | ⬜ | Screenshot |
| CPU benchmark | ⬜ | Screenshot |
| Resource monitoring | ⬜ | Screenshot |

## VMware Workstation

| Step | Status | Evidence |
|---|---|---|
| VMware launch | ⬜ | Screenshot |
| VM creation | ⬜ | Screenshot |
| CPU configuration | ⬜ | Screenshot |
| Memory configuration | ⬜ | Screenshot |
| Disk configuration | ⬜ | Screenshot |
| Network configuration | ⬜ | Screenshot |
| Ubuntu installation | ⬜ | Screenshot |
| CPU verification | ⬜ | Screenshot |
| Memory verification | ⬜ | Screenshot |
| Sysbench installation | ⬜ | Screenshot |
| CPU benchmark | ⬜ | Screenshot |
| Resource monitoring | ⬜ | Screenshot |

---

# 💻 Commands Used

```bash
# System information
hostnamectl

# CPU information
lscpu

# Memory information
free -h

# Disk information
df -h

# Resource monitoring
top

# Update packages
sudo apt update

# Install Sysbench
sudo apt install sysbench -y

# Check Sysbench version
sysbench --version

# CPU benchmark
sysbench cpu --cpu-max-prime=20000 run

# Shutdown VM
sudo poweroff
```

---

# 📁 Repository Organization

```text
.
├── README.md
│
├── screenshots/
│   ├── proxmox/
│   └── vmware/
│
├── results/
│   ├── proxmox-results.md
│   ├── vmware-results.md
│   └── comparison.md
│
├── commands/
│   └── benchmark-commands.md
│
└── docs/
    └── lab-manual.pdf
```

---

# 🔬 Experimental Methodology

```text
Create VM
   ↓
Configure identical resources
   ↓
Install Ubuntu
   ↓
Verify CPU / Memory / Disk
   ↓
Monitor baseline resources
   ↓
Install Sysbench
   ↓
Run CPU benchmark
   ↓
Record benchmark metrics
   ↓
Record resource utilization
   ↓
Repeat for second hypervisor
   ↓
Compare observations
```

---

# 📌 Important Experimental Conditions

For a meaningful comparison:

- Keep the guest operating system consistent.
- Keep CPU allocation consistent.
- Keep memory allocation consistent.
- Keep virtual disk allocation consistent.
- Use the same Sysbench benchmark command.
- Record the complete benchmark output.
- Record the Sysbench version.
- Record system configuration using `lscpu`, `free -h`, and `df -h`.
- Preserve screenshots as experimental evidence.
- Avoid modifying VM resources between benchmark runs unless the change is explicitly documented.

---

# 👨‍💻 Experiment Record

**Student:** Parth Karpe  
**Course:** Computer Science / AI Engineering  
**Experiment:** Performance Analysis of Type-1 and Type-2 Hypervisors

### Experiment Date

```text
TODO
```

### Host System

```text
CPU:
RAM:
GPU:
Operating System:
```

### Proxmox Environment

```text
Proxmox Version:
Server CPU:
Server RAM:
VM ID:
VM Name:
```

### VMware Environment

```text
VMware Workstation Version:
Host OS:
Host CPU:
Host RAM:
VM Name:
```

---

# ✅ Final Status

| Component | Status |
|---|---|
| Proxmox VM | ⬜ |
| VMware VM | ⬜ |
| Ubuntu Installation | ⬜ |
| Configuration Verification | ⬜ |
| Sysbench Installation | ⬜ |
| Proxmox Benchmark | ⬜ |
| VMware Benchmark | ⬜ |
| Screenshots | ⬜ |
| Results Recorded | ⬜ |
| Comparison Completed | ⬜ |
| Final Analysis | ⬜ |

---

# 📚 Reference

**Performance Analysis of Type-1 and Type-2 Hypervisors — Proxmox VE (Type-1) vs VMware Workstation (Type-2).**

This repository is intended to preserve the experimental procedure, actual observations, screenshots, raw benchmark outputs, and final comparison.

---

## 📌 Conclusion

This repository documents the practical performance analysis of virtual machines running on a Type-1 hypervisor (Proxmox VE) and a Type-2 hypervisor (VMware Workstation).

The final comparison is based on experimentally measured:

- Execution time
- Total events
- Events per second
- Latency
- CPU utilization
- Memory utilization
- Other recorded resource observations

The conclusions in this repository should be based on the experimental measurements collected during the lab execution.
