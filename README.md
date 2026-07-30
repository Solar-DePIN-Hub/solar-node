# ☀️ Solar DePIN Hub — Solar-Native Decentralized Compute Infrastructure

Solar DePIN Hub is building renewable-energy-aware infrastructure that connects **solar generation, distributed compute, real-world telemetry, AI workloads, and decentralized networks**.

The goal is to create a scalable architecture where computing workloads can respond to renewable energy availability instead of treating energy supply and compute demand as completely separate systems.

Our current testbed is based on a real solar installation in Ukraine and is being used to develop the software, telemetry, orchestration, and node architecture needed for a larger Solar DePIN network.

---

## 🌍 Vision

Solar DePIN Hub is exploring a future where distributed computing infrastructure can:

- Run directly alongside renewable energy generation
- Monitor real-time solar production
- Monitor environmental and weather conditions
- Route workloads according to available renewable energy
- Participate in decentralized compute networks
- Support AI inference and other compute workloads
- Use batteries to shift renewable energy into periods of lower generation
- Scale from lightweight community nodes to larger GPU-powered infrastructure
- Eventually coordinate energy, compute, storage, and network resources through intelligent orchestration

Instead of simply deploying servers and connecting them to the grid, Solar DePIN Hub is designed around the relationship between **energy production and computing demand**.

---

# ⚡ Current Solar Infrastructure

## Solar Array

The current Solar DePIN Hub testbed uses:

- **104 × Risen Energy RSM120-8-585M photovoltaic modules**
- **585 W rated output per panel**
- **60.84 kWp total DC nameplate capacity**
- **2 physical solar platforms**
- **52 panels per platform**
- Monocrystalline photovoltaic technology

### Panel Electrical Specifications

| Specification | Value |
|---|---:|
| Manufacturer | Risen Energy Co., Ltd. |
| Model | RSM120-8-585M |
| Rated Power | 585 W |
| Vmp | 34.12 V |
| Imp | 17.15 A |
| Voc | 41.00 V |
| Isc | 18.16 A |
| Maximum System Voltage | 1500 V DC |
| Module Dimensions | 2172 × 1303 × 35 mm |
| Module Weight | 32 kg |

The exact PV string and MPPT configuration is still being documented.

---

# 🔌 Inverter

The current installation uses:

**Huawei SUN2000-30KTL-M3**

- Rated AC output: **30 kW**
- Communications include RS485 / MBUS / WLAN
- Integrated with Huawei FusionSolar monitoring
- All 104 solar panels are currently connected through the existing inverter architecture

The current solar array therefore has approximately:

**60.84 kWp DC solar capacity → 30 kW AC inverter capacity**

A second inverter is planned when additional funding becomes available.

The exact future inverter model and final array redistribution have not yet been selected.

---

# 🔋 Battery Energy Storage

A site-scale Battery Energy Storage System (**BESS**) is planned but is **not currently installed**.

Battery storage is expected to become an important part of the Solar DePIN architecture because it can allow:

- Solar energy generated during peak production to be used later
- Compute workloads to continue during periods of reduced solar generation
- Better matching between renewable generation and compute demand
- Reduced dependence on instantaneous solar output
- Future participation in energy-management and microgrid systems

Battery manufacturer, chemistry, capacity, power rating, and system topology remain under engineering evaluation.

---

# 🖥️ Compute Infrastructure

Solar DePIN Hub is developing a two-tier compute model:

## Light Nodes

Light Nodes are intended to make participation possible without requiring a large GPU server.

Potential Light Node workloads include:

- Solar telemetry collection
- Environmental telemetry collection
- Network monitoring
- Data validation
- Lightweight AI inference
- Embeddings
- Classification
- Small distributed workloads
- DePIN services
- Availability verification
- Local infrastructure agents

The final Light Node hardware specification is still being designed.

Candidate hardware classes include low-power mini PCs and other energy-efficient x86 systems.

**Status: Engineering Selection Pending**

---

## Heavy Nodes

Heavy Nodes are designed for compute-intensive workloads and larger renewable-energy sites.

Potential workloads include:

- GPU compute
- AI inference
- Decentralized cloud workloads
- Akash deployments
- Containerized applications
- Larger AI models
- Rendering or simulation workloads
- DePIN infrastructure services
- Future confidential-compute workloads

Current experimental compute infrastructure includes:

- **NVIDIA RTX 3090 GPU**
- Approximately **24 GB VRAM**
- AMD Ryzen 7-class CPU
- Docker-based workloads
- Existing participation in decentralized compute infrastructure

Exact production Heavy Node hardware standards are still being developed.

---

# 🧠 Energy-Aware Compute

One of the core research areas of Solar DePIN Hub is **energy-aware workload orchestration**.

The long-term architecture is intended to combine:

```text
Solar Generation
       │
       ▼
Solar Inverter
       │
       ├──► Energy Telemetry
       │
       ▼
Battery Storage
       │
       ▼
Energy-Aware Orchestrator
       │
       ├──► Light Nodes
       │
       ├──► Heavy GPU Nodes
       │
       └──► Decentralized Compute Networks

