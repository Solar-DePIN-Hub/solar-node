# ☀️ Solar DePIN Hub — Solar-Native Decentralized Infrastructure

Solar DePIN Hub is developing renewable-energy-aware infrastructure that connects **solar generation, decentralized compute, real-world telemetry, AI workloads, and DePIN networks**.

Our goal is to build distributed computing infrastructure capable of understanding the energy available to it and eventually adapting compute workloads to renewable-energy conditions.

The project is being developed around a real solar and compute testbed in Ukraine.

---

## 🌍 Vision

Traditional computing infrastructure treats energy and compute as largely separate systems.

Solar DePIN Hub is exploring a different architecture:

**Renewable Energy → Telemetry → Intelligent Orchestration → Distributed Compute**

The long-term goal is infrastructure capable of coordinating:

- Solar generation
- Battery energy storage
- Compute resources
- Environmental telemetry
- Decentralized cloud workloads
- AI workloads
- Network availability
- Distributed energy resources

This creates the foundation for energy-aware and eventually **follow-the-sun computing infrastructure**.

---

## ⚡ Current Testbed

The Solar DePIN Hub testbed currently includes real renewable-energy and compute infrastructure.

### Solar

- 104 monocrystalline solar panels
- 2 solar platforms
- 52 panels per platform
- Risen Energy RSM120-8-585M modules
- 585 W per panel
- Approximately **60.84 kWp DC nameplate capacity**

### Inverter

- Huawei SUN2000-30KTL-M3
- 30 kW rated AC output
- Huawei FusionSolar monitoring
- Current array connected through one inverter
- Second inverter planned as the infrastructure expands

### Compute

The project is experimenting with local compute infrastructure including GPU-capable systems and containerized workloads.

Current test infrastructure includes an NVIDIA RTX 3090-class GPU system.

### Connectivity

- Fiber-optic internet
- Vega ISP
- Up to 1 Gbps service

### Environmental Data

Weather and environmental telemetry are being incorporated into the architecture, including WeatherXM infrastructure.

---

## 🖥️ Solar DePIN Node Architecture

Solar DePIN Hub is developing two primary node classes.

### 🌱 Light Node

Light Nodes are intended to provide an accessible, energy-efficient way to participate in the network.

Potential responsibilities include:

- Telemetry collection
- Environmental data
- Data validation
- Network monitoring
- Lightweight AI inference
- DePIN services
- Infrastructure agents
- Availability verification

**Final Light Node specifications are currently under development.**

### ⚡ Heavy Node

Heavy Nodes are designed for compute-intensive infrastructure.

Potential responsibilities include:

- GPU compute
- AI inference
- Decentralized cloud workloads
- Akash workloads
- Containerized applications
- DePIN infrastructure
- Larger distributed workloads

Heavy Nodes may eventually integrate directly with larger renewable-energy systems and battery storage.

**Final Heavy Node specifications are currently under development.**

---

## 🧠 Energy-Aware Compute

A core Solar DePIN Hub research area is connecting renewable-energy telemetry directly with compute orchestration.

```text
                 SOLAR ENERGY
                      │
                      ▼
                 PV INVERTER
                      │
             ┌────────┴────────┐
             │                 │
             ▼                 ▼
      ENERGY TELEMETRY    BATTERY STORAGE
             │              (planned)
             └────────┬────────┘
                      ▼
            ENERGY-AWARE CONTROL
                      │
             ┌────────┴────────┐
             ▼                 ▼
        LIGHT NODES        HEAVY NODES
                               │
                               ▼
                     DECENTRALIZED COMPUTE

