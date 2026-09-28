# Experiment 1: Type-1 (Proxmox VE) vs. Type-2 (VMware Workstation) Hypervisor Performance Analysis

[![Hypervisor](https://img.shields.io/badge/Hypervisor-Proxmox%20VE%20vs%20VMware-orange?style=flat-square)](#)
[![Benchmark](https://img.shields.io/badge/Benchmark-Sysbench%20CPU-blue?style=flat-square)](#)
[![Guest OS](https://img.shields.io/badge/Guest%20OS-Ubuntu%2022.04%20LTS-green?style=flat-square)](#)

---

## 1. Project Objective & Aim

To experimentally analyze and quantitatively compare the performance, scheduling latency, and resource overhead between:
1. **Type-1 Hypervisor (Bare-Metal):** Proxmox Virtual Environment (KVM Kernel Module)
2. **Type-2 Hypervisor (Hosted):** VMware Workstation Pro running on Windows Host OS

Both hypervisors host identical Ubuntu 22.04 LTS virtual machines configured with identical resource limits.

```
                    HYPERVISOR COMPARISON TOPOLOGY
                                  |
            +---------------------+---------------------+
            |                                           |
      TYPE-1 BARE METAL                           TYPE-2 HOSTED
      (Proxmox VE 8.2)                         (VMware Workstation)
            |                                           |
    +---------------+                           +---------------+
    | Ubuntu 22.04  |                           | Ubuntu 22.04  |
    | 2 vCPU / 2GB  |                           | 2 vCPU / 2GB  |
    +---------------+                           +---------------+
            |                                           |
            +---------------------+---------------------+
                                  |
                     STANDARDIZED SYSBENCH CPU
               sysbench cpu --cpu-max-prime=20000 run
```

---

## 2. Standard Virtual Machine Sizing

| Resource Parameter | Sized Value | Configuration Purpose |
| :--- | :--- | :--- |
| **Guest OS** | Ubuntu 22.04.4 LTS (Jammy) | Standardized 64-bit Linux kernel |
| **vCPU Allocation** | **2 vCPUs** | Fixed compute capability |
| **Memory Allocation** | **2048 MB (2.0 GB)** | Fixed RAM footprint |
| **Virtual Disk** | **20.0 GB** | Fixed storage capacity |
| **Benchmark Workload** | `sysbench cpu --cpu-max-prime=20000 --threads=2 run` | Fixed prime-number computation |

---

## 3. Mandatory Implementation Evidence & Screenshots

### Part 1: Type-1 Hypervisor — Proxmox VE (Bare-Metal)

#### 1. Proxmox VE Web Management Dashboard & VM Inventory
* **Evidence:** Proxmox VE web interface displaying active node status, cluster inventory, and running Ubuntu VM.

![01 Proxmox Dashboard](screenshots/type1-proxmox/01-proxmox-dashboard.png)

#### 2. Proxmox Virtual Machine Hardware Configuration
* **Evidence:** Create Virtual Machine confirmation confirming 2 cores (2 vCPUs), 2048 MiB RAM, and 20 GB disk.

![02 Proxmox VM Configuration](screenshots/type1-proxmox/02-proxmox-vm-configuration.png)

#### 3. Proxmox Virtual Machine Running State
* **Evidence:** Running Ubuntu VM visible through the Proxmox environment.

![03 Proxmox VM Running](screenshots/type1-proxmox/03-proxmox-vm-running.png)

#### 4. Ubuntu Guest Console inside Proxmox
* **Evidence:** Interactive Ubuntu console session running inside the Proxmox VM.

![04 Proxmox Ubuntu Console](screenshots/type1-proxmox/04-proxmox-ubuntu-console.png)

#### 5. CPU & Memory Topology Verification
* **Evidence:** Terminal snapshot showing CPU/cache/virtualization details and `free -h` memory allocation.

![05 Proxmox System Configuration](screenshots/type1-proxmox/05-proxmox-system-configuration.png)

#### 6. Proxmox VM Summary & Live Resource Monitoring
* **Evidence:** Summary view showing real-time CPU usage, memory utilization (1.82 GiB / 2.00 GiB), and 20 GiB boot disk.

![06 Proxmox Resource Monitoring](screenshots/type1-proxmox/06-proxmox-resource-monitoring.png)

#### 7. Proxmox Task and History Log
* **Evidence:** Proxmox task execution and history view captured during the experiment lifecycle.

![07 Proxmox Task History](screenshots/type1-proxmox/07-proxmox-task-history.png)

#### 8. Network Connectivity Verification
* **Evidence:** ICMP ping connectivity test demonstrating successful network replies with 0% packet loss.

![08 Proxmox Network Test](screenshots/type1-proxmox/08-proxmox-network-test.png)

---

### Part 2: Type-2 Hypervisor — VMware Workstation Pro (Hosted)

#### 1. VMware Virtual Machine Configuration
* **Evidence:** Hardware settings confirming processor cores, memory allocation, and virtual disk configuration.

![01 VMware VM Configuration](screenshots/type2-vmware/01-vmware-vm-configuration.png)

#### 2. VMware Virtual Machine Running with CPU Stress Test
* **Evidence:** Ubuntu VM actively executing inside VMware Workstation with a 2-CPU `stress-ng` test running.

![02 VMware VM Running](screenshots/type2-vmware/02-vmware-vm-running.png)

#### 3. Ubuntu Terminal SSH Service Status
* **Evidence:** Guest terminal confirming `ssh.service` enablement and configuration.

![03 VMware SSH Service](screenshots/type2-vmware/03-vmware-ssh-service.png)

#### 4. Network Connectivity Verification
* **Evidence:** ICMP ping test confirming active network connectivity with 0% packet loss.

![04 VMware Network Test](screenshots/type2-vmware/04-vmware-network-test.png)

---

## 4. Performance Summary Table

| Metric | Type-1 Proxmox VE (Bare-Metal) | Type-2 VMware Workstation (Hosted) | Quantitative Advantage |
| :--- | :--- | :--- | :--- |
| **Throughput (Events/sec)** | **1,548.22 eps** | **1,382.45 eps** | **+12.0% Faster (Proxmox)** |
| **Total Events (10s)** | **15,485** | **13,827** | **+1,658 extra computations** |
| **Average Latency** | **1.29 ms** | **1.44 ms** | **10.4% lower latency** |
| **P95 Latency** | **1.35 ms** | **1.52 ms** | **11.2% lower latency** |
| **Max Spike Latency** | **2.85 ms** | **4.12 ms** | **30.8% lower jitter** |

---

## 5. Key Observations & Conclusion

1. **Type-1 Superiority:** Proxmox VE delivers **12.0% higher CPU throughput** and **10.4% lower latency** because it bypasses host operating system layers and directly interfaces with CPU virtualization rings.
2. **Context-Switch Tax in Type-2:** VMware Workstation incurs unavoidable scheduling overhead because vCPU execution threads must compete with host Windows background services.
3. **Reproducibility:** All raw logs and methodology are archived in [performance-analysis.md](results/performance-analysis.md).
