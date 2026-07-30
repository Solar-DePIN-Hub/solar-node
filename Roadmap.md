# 🗺️ Solar DePIN Hub — Development Roadmap

Solar DePIN Hub is developing renewable-energy-aware decentralized infrastructure that connects **solar generation, real-world telemetry, distributed compute, AI workloads, and DePIN networks**.

This roadmap separates infrastructure that exists today from systems that are currently being engineered or researched.

---

## Development Status

We use four status categories:

- ✅ **Operational** — deployed and verified
- 🟢 **Planned** — confirmed development direction
- 🔵 **Proposed** — architecture under research or design
- 🟡 **TBD** — engineering decision has not yet been finalized

---

# Phase 0 — Physical Testbed & Infrastructure

**Status: ✅ Operational / Active**

Establish the physical renewable-energy and compute environment used to develop and validate Solar DePIN Hub.

## Solar Infrastructure

Current infrastructure includes:

- 104 Risen Energy RSM120-8-585M monocrystalline PV modules
- 585 W rated output per module
- Approximately 60.84 kWp DC nameplate capacity
- Two physical solar platforms
- 52 panels per platform
- Huawei SUN2000-30KTL-M3 inverter
- Huawei FusionSolar monitoring

All 104 panels currently operate through the existing inverter architecture.

### Planned Expansion

🟢 Addition of a second inverter when funding permits.

🟡 Final second-inverter model and PV redistribution remain to be determined.

---

## Compute Infrastructure

Current test infrastructure provides a foundation for experimenting with decentralized workloads and telemetry.

Existing equipment includes GPU-capable compute infrastructure, including an NVIDIA RTX 3090-class system.

Development priorities include:

- Containerized workloads
- Compute monitoring
- GPU telemetry
- Remote management
- DePIN workload experimentation

---

## Connectivity

Current connectivity includes:

- Vega fiber-optic internet
- Up to 1 Gbps service

Future improvements may include:

- Secondary WAN connection
- Network redundancy
- Infrastructure VLANs
- Dedicated management network
- Improved remote-management architecture

---

# Phase 1 — Unified Telemetry

**Status: 🟢 In Development**

Create a common telemetry layer capable of observing the physical and digital infrastructure.

## Energy Telemetry

Target metrics include:

- PV generation
- Inverter output
- Voltage
- Current
- Frequency
- Energy production
- Inverter status
- Fault conditions

Potential interfaces include:

- Modbus RTU
- Modbus TCP
- Huawei local interfaces
- FusionSolar APIs

The final production telemetry transport remains under engineering evaluation.

---

## Environmental Telemetry

Integrate weather and environmental information, including WeatherXM infrastructure.

Target metrics include:

- Temperature
- Humidity
- Wind speed
- Wind direction
- Precipitation
- Future solar irradiance and forecasting data

Environmental information may eventually help predict renewable-energy availability.

---

## Compute Telemetry

Monitor infrastructure metrics including:

- CPU utilization
- GPU utilization
- GPU memory
- GPU temperature
- GPU power consumption
- RAM utilization
- Storage
- Network throughput
- Node availability

Candidate technologies include:

- Prometheus
- Grafana
- NVIDIA telemetry
- Akash DePIN telemetry

### Phase 1 Objective

Create a unified model:

Energy + Weather + Compute + Network → **Solar DePIN Telemetry**

---

# Phase 2 — Light Node & Heavy Node Architecture

**Status: 🔵 Architecture Design**

Develop standardized Solar DePIN node classes.

## 🌱 Light Node

Light Nodes are intended to allow broader participation using energy-efficient hardware.

Potential responsibilities include:

- Solar telemetry
- Environmental telemetry
- Network monitoring
- Data validation
- Availability verification
- Lightweight AI inference
- Embeddings
- Classification
- Infrastructure agents
- Lightweight DePIN services

### Engineering Work Required

🟡 Define:

- Minimum CPU
- Minimum RAM
- Storage requirements
- Network requirements
- Power-consumption targets
- Operating system
- Container runtime
- Supported AI models
- Node software
- Security requirements

The final Light Node specification has **not yet been selected**.

---

## ⚡ Heavy Node

Heavy Nodes are intended for significantly more compute-intensive infrastructure.

Potential responsibilities include:

- GPU compute
- AI inference
- Larger AI models
- Akash workloads
- Containerized applications
- Decentralized cloud workloads
- Rendering
- Simulation
- DePIN infrastructure services

### Engineering Work Required

🟡 Define:

- CPU requirements
- GPU classes
- VRAM requirements
- System RAM
- Storage
- Networking
- Power requirements
- Cooling
- Renewable-energy requirements
- Battery integration
- Security requirements

The final Heavy Node specification has **not yet been selected**.

---

# Phase 3 — Akash Network Integration

**Status: 🟢 Planned / Engineering**

Integrate Solar DePIN compute infrastructure with Akash Network.

Development areas include:

- Akash provider deployment
- GPU workload support
- Containerized workloads
- Provider telemetry
- Node monitoring
- Renewable-energy metadata
- Workload availability
- Persistent-data strategy
- Failure recovery

A major engineering objective is determining how renewable-energy-aware compute can coexist with workload availability requirements.

---

## Energy-Aware Akash Research

🔵 Research potential mechanisms for:

- Dynamic GPU power management
- Scheduling workloads according to available solar energy
- Battery-aware compute
- Workload migration
- Geographic workload redistribution
- Renewable-energy metadata
- Provider selection based on energy availability

Any workload migration mechanism must preserve application reliability and respect decentralized-cloud workload requirements.

---

# Phase 4 — Battery Energy Storage

**Status: 🟢 Planned**

Introduce Battery Energy Storage System (BESS) infrastructure.

Battery storage could allow the Solar DePIN architecture to separate the timing of renewable-energy generation from compute consumption.

Potential capabilities include:

- Store excess solar production
- Support compute after sunset
- Smooth renewable-energy variability
- Provide temporary backup power
- Support intelligent workload scheduling
- Reduce instantaneous dependence on grid electricity

### Engineering Selection Pending

🟡 Determine:

- Battery chemistry
- Storage capacity
- Charge/discharge power
- Manufacturer
- Battery management system
- Inverter compatibility
- Telemetry interfaces
- Safety architecture

---

# Phase 5 — Energy-Aware Orchestration

**Status: 🔵 Proposed Architecture**

Develop an intelligent control plane capable of coordinating energy availability with computing demand.

Potential inputs include:

- Solar generation
- Battery State of Charge
- Weather forecasts
- Expected solar production
- GPU utilization
- Compute demand
- Electricity availability
- Node availability
- Network conditions

Potential outputs include:

- Workload placement
- Node selection
- GPU power limits
- Workload migration
- Battery utilization decisions
- Compute throttling
- Failover

The objective is to move from simply **monitoring renewable infrastructure** toward infrastructure capable of **responding to renewable-energy conditions**.

---

# Phase 6 — Multi-Site Solar DePIN Network

**Status: 🔵 Long-Term Architecture**

Expand Solar DePIN Hub beyond a single physical testbed.

Future sites could include:

- Residential solar installations
- Commercial solar
- Community solar
- Microgrids
- Renewable-powered data centers
- Distributed GPU clusters
- Community Light Nodes
- Larger Heavy Nodes

Each location could contribute different combinations of:

- Energy
- Compute
- Telemetry
- Environmental data
- Network capacity

---

# Phase 7 — Follow-the-Sun Compute

**Status: 🔵 Research Vision**

Investigate geographic workload orchestration based on renewable-energy availability.

Example:

```text
Solar Site A
   │
   │ Solar production declines
   ▼
Energy-Aware Orchestrator
   │
   │ Identify renewable capacity elsewhere
   ▼
Solar Site B
   │
   ▼
Available Compute Capacity
