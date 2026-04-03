# DEV Server Configuration

<br>

Suggest an exact Dell server configuration with RAM and Storage to support the following:

- Between 20-50 developers
- Using VsCode dev containers to develop and build C++ code
- Using rootless podman
- Occasional use of GUI desktops via RDP to test 3D graphics applications in these sessions
- Need at least 4 CPU cores per developer

<br>

* * *

<br>

<br>

# 🧾 Dell Premier Cart — Dell PowerEdge R7625 (16× NVMe Build Node)

## 🖥️ Base System

- **Qty:** 1
- **SKU:** `210-BFRR`
- **Description:** PowerEdge R7625, 2U chassis

* * *

## 🧱 Chassis / Backplane (CRITICAL)

- **Qty:** 1
- **SKU:** `379-BB16NVME` _(Dell will map)_
- **Description:** **16 × 2.5" NVMe (U.2/U.3) backplane, direct-attached**

**Notes to rep (important):**

```
Must be full 16× NVMe backplane (no tri-mode / RAID bottlenecks).
All drives must be CPU direct-attached PCIe lanes.
```

* * *

## ⚙️ Processors

- **Qty:** 2
- **SKU:** `338-EPYC9654`
- **Description:** AMD EPYC 9654, 96 cores, 192 threads each

👉 **Total:** 192 cores per node

* * *

## 🧠 Memory (balanced across channels)

- **Qty:** 16
- **SKU:** `370-AF64`
- **Description:** 64GB DDR5 RDIMM

👉 **Total:** 1 TB

**Notes:**

```
Populate evenly across both CPUs (8 DIMMs per CPU minimum).
```

* * *

## 💾 NVMe Storage (PRIMARY REQUIREMENT)

### High-performance NVMe pool

- **Qty:** 16
- **SKU:** `400-BQ3T84` _(or equivalent)_
- **Description:** **3.84TB U.2/U.3 NVMe SSD (PCIe Gen4 or Gen5)**

👉 **Raw capacity:** 61.4 TB

**Notes to rep (VERY IMPORTANT):**

```
- Must be enterprise NVMe (mixed-use or read-intensive OK)
- Prefer PCIe Gen4/Gen5 highest IOPS SKU
- No RAID controller involvement
- Confirm full PCIe bandwidth (no oversubscription)
```

* * *

## 💽 Boot Optimization (BOSS)

- **Qty:** 1
- **SKU:** `403-BCRX`
- **Description:** BOSS-N1 controller
- **Qty:** 2
- **SKU:** `400-M2-960`
- **Description:** 960GB M.2 SSD

* * *

## 🌐 Networking

### Option A — Standard

- **Qty:** 1
- **SKU:** `540-BE25G`
- **Description:** Dual 25GbE SFP28 (OCP 3.0)

### Option B — Recommended (for shared cache)

- **Qty:** 1
- **SKU:** `540-BE100G`
- **Description:** Dual 100GbE QSFP28

* * *

## 🔌 Power & Cooling (REQUIRED for NVMe density)

- **Qty:** 2
- **SKU:** `450-AK2400`
- **Description:** 2400W Titanium PSU
- **Qty:** 1
- **SKU:** `412-AAHP`
- **Description:** High-performance fan kit

* * *

## 🛠️ RAID / Controllers

- **Qty:** 1
- **SKU:** `405-AAZT`
- **Description:** PERC H355 (for optional SATA tier only)

👉 **Do NOT attach NVMe drives to this controller**

* * *

## 🧩 Riser / PCIe Configuration

- **Qty:** 1
- **SKU:** `330-BRISER-HPC`
- **Description:** Riser config optimized for full NVMe population

* * *

## 🛠️ Management

- **Qty:** 1
- **SKU:** `528-CTDRAC`
- **Description:** iDRAC9 Enterprise

* * *

## 💿 OS

- **Qty:** 1
- **SKU:** `634-BLANK`
- **Description:** No OS

* * *

# 📝 Critical “Notes to Sales Rep” (paste this exactly)

```
Workload: 50+ developers using VSCode Remote SSH + rootless Podman dev containers, heavy parallel C++ builds.

Key requirements:
- 16× NVMe must be direct CPU-attached (no RAID or tri-mode controller)
- Full PCIe bandwidth per NVMe drive (no oversubscription)
- Balanced memory population across CPUs
- High-performance cooling required for sustained NVMe + CPU load
- Confirm lane mapping supports all 16 NVMe at full speed

Quote both:
- PCIe Gen4 NVMe option (cost optimized)
- PCIe Gen5 NVMe option (performance optimized)

Include lead times for CPUs and NVMe drives.
No substitutions without approval.
```

* * *

# 💰 Expected Pricing (per node)

| Component | Cost Range |
| --- | --- |
| CPUs (2× EPYC 9654) | $20K – $30K |
| RAM (1 TB) | $8K – $15K |
| NVMe (16× 3.84TB) | $6K – $12K |
| Chassis + misc | $10K – $18K |

👉 **Total per node:**

# 💵 **$50K – $75K**

* * *

# 🧠 Practical Notes (from experience)

### 1\. NVMe layout matters more than size

- 16 drives = high parallel I/O → critical for C++ builds

### 2\. Avoid “tri-mode” traps

Dell often defaults to:

- RAID-capable controllers👉 These **reduce NVMe performance**

* * *

### 3\. Ask for lane diagram

Seriously—ask Dell:

```
Provide PCIe lane mapping diagram for this config
```

* * *

# 🚀 Cluster Scaling

## Start with:

- 2 × this node → ~120 TB NVMe total

## Scale to:

- 3 nodes → clean support for 80+ developers

<br>


---

# UE Server Configuration

<br>

Suggest an exact Dell server configuration with RAM and generous disk storage to support the following:

- Server will mainly be used for running unreal engine simulations
- Used simultaneously by as many developers as practical
- Using rootless podman
- Consider splitting into 2 nodes if a single node is cost prohibitive

<br>

* * *

<br>

<br>

## Build this:

### Node A (GPU)

- R760xa
- 2–4 × L40S
- 512GB–1TB RAM
- 16 × NVMe (~60TB)

### Node B (CPU)

- R7625
- 192 cores
- 1TB RAM
- 16 × NVMe (~60TB)

<br>

* * *

<br>

<br>

Below is a **precise Dell Premier–ready BOM for Node A (GPU Unreal Engine node)** using the Dell PowerEdge R760xa platform—fully aligned with your requirements:

- GPU-heavy Unreal workloads
- ≥50 TB NVMe
- Multi-user (RDP + containers)
- Rootless Podman compatible

* * *

# 🧾 Dell Premier Cart — R760xa (Unreal Engine GPU Node)

## 🖥️ Base System

- **Qty:** 1
- **SKU:** `210-BFTR` _(R760xa base – Dell will map)_
- **Description:** PowerEdge R760xa, 2U GPU-optimized platform

👉 Supports up to **4 double-width GPUs**

* * *

# 🧱 Chassis / NVMe Backplane (CRITICAL)

- **Qty:** 1
- **SKU:** `379-BB16NVME`
- **Description:** **16 × 2.5" NVMe (U.2/U.3) backplane**

### Notes to rep:

```
Must support 16× NVMe drives simultaneously.
No RAID controller for NVMe (direct attach only).
Confirm PCIe Gen4/Gen5 full bandwidth per drive.
```

* * *

# ⚙️ CPU (Balanced for GPU workloads)

- **Qty:** 2
- **SKU:** `338-XEON-6454S`
- **Description:** Intel Xeon Gold 6454S (32 cores each)

👉 **Total: 64 cores**

💡 Why not more?

- Unreal is GPU-bound
- Extra CPU cores give diminishing returns

* * *

# 🧠 Memory (critical for Unreal scenes)

## Recommended

- **Qty:** 16
- **SKU:** `370-AF64`
- **Description:** 64GB DDR5 RDIMM

👉 **Total: 1 TB RAM**

### Notes:

```
Populate evenly across CPUs (8 DIMMs per CPU minimum).
```

* * *

# 🎮 GPU (MOST IMPORTANT COMPONENT)

## Recommended configuration

- **Qty:** 2–4
- **SKU:** `490-BL40S`
- **Description:** NVIDIA L40S 48GB PCIe

Example market reference:

- NVIDIA L40S 48GB PCIe GPU (~$8K–$10K each)

* * *

## GPU guidance

| GPUs | Users |
| --- | --- |
| 2 × L40S | ~10–15 devs |
| 4 × L40S | ~20–30 devs |

👉 Each GPU supports multiple Unreal sessions, but don’t oversubscribe heavily.

* * *

# 💾 NVMe Storage (≥50TB requirement)

## Primary NVMe pool

- **Qty:** 16
- **SKU:** `400-BQ3T84`
- **Description:** 3.84TB NVMe SSD

👉 **Raw capacity:** 61.4 TB

* * *

## Notes (VERY IMPORTANT)

```
- Must be enterprise NVMe (mixed-use or read-intensive OK)
- Prefer highest IOPS SKU available
- No PERC / RAID controller in path
- Confirm full PCIe lane mapping (no oversubscription)
```

* * *

# 💽 Boot (BOSS)

- **Qty:** 1
- **SKU:** `403-BCRX`
- **Description:** BOSS-N1
- **Qty:** 2
- **SKU:** `400-M2-960`
- **Description:** 960GB M.2

* * *

# 🌐 Networking

## Recommended (strongly)

- **Qty:** 1
- **SKU:** `540-BE100G`
- **Description:** Dual 100GbE QSFP28

👉 Needed if:

- shared DDC (Unreal)
- multi-node cluster
- remote asset streaming

* * *

# 🔌 Power & Cooling (REQUIRED for GPUs)

- **Qty:** 2
- **SKU:** `450-AK2400`
- **Description:** 2400W Titanium PSU
- **Qty:** 1
- **SKU:** `412-AAHP`
- **Description:** High-performance fan kit

* * *

# 🧩 GPU Enablement Kit (CRITICAL)

- **Qty:** 1
- **SKU:** `490-BGPUKIT`
- **Description:** GPU enablement kit (cables, airflow shrouds)

* * *

# 🛠️ Management

- **Qty:** 1
- **SKU:** `528-CTDRAC`
- **Description:** iDRAC9 Enterprise

* * *

# 💿 OS

- **Qty:** 1
- **SKU:** `634-BLANK`
- **Description:** No OS

* * *

# 📝 MUST INCLUDE (paste into Dell Premier notes)

```
Workload: Unreal Engine simulations + multi-user GPU sessions via RDP + rootless Podman containers.

Key requirements:
- 16× NVMe direct-attached (no RAID / no tri-mode controller)
- Full PCIe bandwidth per NVMe drive
- Support for 2–4 NVIDIA L40S GPUs
- High-performance cooling required for sustained GPU + NVMe load
- Balanced memory population across CPUs

Quote two options:
1) 2× L40S (cost optimized)
2) 4× L40S (performance optimized)

Provide PCIe lane mapping diagram.

No substitutions without approval.
```

* * *

# 💰 Expected Cost (realistic)

| Component | Cost |
| --- | --- |
| Base system | $20K–$35K |
| CPUs | $8K–$15K |
| RAM (1TB) | $8K–$15K |
| NVMe (16×) | $6K–$12K |
| GPUs (2–4× L40S) | $16K–$40K |

* * *

## 👉 Total:

| Config | Price |
| --- | --- |
| 2× GPU | **$70K–$110K** |
| 4× GPU | **$100K–$160K** |

* * *

# 🧠 Final Practical Advice

## 1\. Don’t underbuy GPU

If budget forces a choice:  
👉 **More GPU > more CPU**

* * *

## 2\. 50TB NVMe is excellent for Unreal

- Derived Data Cache (DDC)
- Assets
- container layers
