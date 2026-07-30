# Solar DePIN Hub — Node Architecture

## 1. Purpose

Solar DePIN Hub is developing a multi-tier node architecture designed to connect renewable energy, telemetry, decentralized infrastructure, and distributed compute.

The initial architecture defines two primary node classes:

- 🌱 Light Node
- ⚡ Heavy Node

These node classes serve different purposes.

Light Nodes prioritize accessibility, low power consumption, telemetry, and lightweight workloads.

Heavy Nodes prioritize compute capacity, GPU workloads, decentralized cloud infrastructure, and deeper integration with renewable-energy systems.

Final hardware specifications are still under engineering evaluation.

---

# 2. Design Goals

The node architecture should allow Solar DePIN Hub to scale beyond a single physical solar installation.

The network should eventually support:

- Low-power community participation
- Renewable-energy telemetry
- Environmental telemetry
- Distributed compute
- AI workloads
- DePIN services
- Akash workloads
- Geographic distribution
- Energy-aware scheduling
- Infrastructure monitoring

The architecture should avoid requiring every participant to operate expensive GPU hardware.

---

# 3. Node Hierarchy

```text
                   SOLAR DEPIN NETWORK
                           │
              ┌────────────┴────────────┐
              │                         │
              ▼                         ▼
         🌱 LIGHT NODE             ⚡ HEAVY NODE
              │                         │
        Low Power                   High Compute
        Telemetry                   GPU Workloads
        Validation                  Akash Provider
        Monitoring                  AI Inference
        Light AI                    DePIN Services
              │                         │
              └────────────┬────────────┘
                           ▼
                  SOLAR DEPIN LAYER
                           │
                           ▼
                  UNIFIED TELEMETRY
                           │
                           ▼
                 FUTURE CONTROL PLANE
```

---

# 4. 🌱 Light Node

**Status: 🔵 Architecture Design**

A Light Node is intended to be an accessible Solar DePIN participant that does not require data-center-class or high-end GPU hardware.

The concept is inspired by lightweight DePIN participation models where users can contribute useful infrastructure using ordinary computing hardware.

A Solar DePIN Light Node should provide useful network services while maintaining relatively low:

- Hardware cost
- Power consumption
- Heat generation
- Bandwidth requirements
- Maintenance requirements

---

# 5. Potential Light Node Responsibilities

Light Nodes may support one or more of the following functions.

## Telemetry

- Solar-generation telemetry
- Inverter telemetry
- Environmental telemetry
- Network telemetry
- Local device health
- Energy-consumption telemetry

## Verification

- Node availability verification
- Data validation
- Telemetry validation
- Network-health checks

## Lightweight Compute

- Small AI models
- Embeddings
- Classification
- Data preprocessing
- Lightweight inference
- Infrastructure agents
- Automation tasks

## DePIN Services

Light Nodes may eventually participate in compatible decentralized infrastructure networks where hardware requirements permit.

---

# 6. Light Node Hardware Philosophy

Light Nodes should favor:

- Energy efficiency
- Low idle power
- Commodity hardware
- Simple deployment
- Long-term reliability
- Remote management
- Linux compatibility
- Container support

Possible hardware classes include:

- Mini PCs
- Small x86 systems
- Existing desktop computers
- Energy-efficient home servers
- Other supported edge devices

The project should avoid selecting a single mandatory hardware platform until real workloads have been benchmarked.

---

# 7. Preliminary Light Node Specification

**Status: 🟡 TBD / Benchmarking Required**

The following represents a preliminary design range rather than a final requirement.

| Component | Preliminary Direction |
|---|---|
| CPU | Modern 64-bit multi-core processor |
| Architecture | x86-64 initially |
| RAM | 8 GB minimum candidate / 16 GB preferred candidate |
| Storage | SSD preferred |
| Storage Capacity | 128 GB+ candidate |
| GPU | Not required for basic Light Node |
| Network | Stable broadband connection |
| Operating System | Linux |
| Container Runtime | Docker-compatible |
| Power | Low-power target |
| Remote Management | Required for managed deployments |

These specifications must be validated against actual Solar DePIN workloads before becoming minimum requirements.

---

# 8. Light Node Software

A future Light Node software stack may include:

```text
LINUX
  │
  ▼
CONTAINER RUNTIME
  │
  ▼
SOLAR DEPIN NODE AGENT
  │
  ├── Telemetry Collector
  ├── Health Monitor
  ├── Network Client
  ├── Workload Runtime
  └── Security / Identity
```

The Solar DePIN Node Agent would provide the common software layer connecting heterogeneous hardware to the network.

---

# 9. Light Node Deployment Modes

Not every Light Node needs access to solar hardware.

Potential deployment modes include:

### Solar Light Node

Connected directly to renewable-energy infrastructure.

Potential capabilities:

- Inverter telemetry
- Energy telemetry
- Environmental telemetry
- Local compute

### Community Light Node

Operated by a network participant without direct solar integration.

Potential capabilities:

- Network services
- Validation
- Lightweight compute
- Availability monitoring

### Environmental Light Node

Located alongside environmental sensors.

Potential capabilities:

- Weather telemetry
- Environmental data
- Data validation

### Edge AI Light Node

Optimized for low-power AI workloads.

Potential capabilities:

- Local inference
- Classification
- Embeddings
- Infrastructure agents

---

# 10. ⚡ Heavy Node

**Status: 🔵 Architecture Design**

Heavy Nodes provide substantially greater compute capacity.

They are intended for workloads that cannot reasonably operate on Light Nodes.

Heavy Nodes may be located at:

- Solar installations
- Commercial renewable-energy sites
- Data centers
- Microgrids
- Distributed compute facilities
- Other energy-capable infrastructure sites

---

# 11. Potential Heavy Node Responsibilities

Heavy Nodes may provide:

## Decentralized Compute

- Akash provider workloads
- Containerized applications
- GPU workloads
- General-purpose compute

## AI

- AI inference
- Larger models
- GPU inference
- AI agents
- Embedding workloads
- Future training or fine-tuning where practical

## DePIN Infrastructure

- Network services
- Infrastructure APIs
- Distributed services
- Telemetry processing

## Energy Integration

- Solar-aware workload operation
- Battery-aware compute
- GPU power management
- Energy-aware scheduling
- Future workload migration

---

# 12. Preliminary Heavy Node Specification

**Status: 🟡 TBD / Benchmarking Required**

No final Heavy Node standard has been selected.

A production Heavy Node will likely require substantially greater resources than a Light Node.

| Component | Preliminary Direction |
|---|---|
| CPU | High-performance multi-core x86-64 |
| RAM | Workload dependent |
| Storage | NVMe SSD preferred |
| GPU | Optional or required depending on Heavy Node class |
| GPU VRAM | Workload dependent |
| Network | High-speed stable broadband/fiber preferred |
| Operating System | Linux |
| Container Runtime | Docker / OCI-compatible |
| Power | Site dependent |
| Cooling | Required according to compute density |
| Monitoring | Required |
| Remote Management | Required |

Final minimum specifications must be determined through benchmarking.

---

# 13. Current Heavy Node Test Infrastructure

**Status: ✅ Experimental**

Current Solar DePIN Hub compute infrastructure includes a system with:

- NVIDIA RTX 3090-class GPU
- Approximately 24 GB VRAM
- AMD Ryzen 7-class CPU

This system provides a useful development environment for testing:

- GPU telemetry
- Container workloads
- AI inference
- Decentralized compute
- Akash-related infrastructure

The current machine should not automatically be interpreted as the final Heavy Node hardware standard.

---

# 14. Heavy Node Classes

As the project develops, Heavy Nodes may eventually be divided into additional profiles.

Possible examples:

### Heavy Compute Node

Optimized for:

- CPU workloads
- Containers
- General decentralized compute

### Heavy GPU Node

Optimized for:

- GPU workloads
- AI inference
- Rendering
- Accelerated compute

### Renewable Heavy Node

Integrated directly with:

- Solar generation
- Energy telemetry
- BESS
- Energy-aware orchestration

### Confidential Heavy Node

Equipped with hardware capable of supporting:

- Trusted Execution Environments
- Attestation
- Confidential workloads
- Confidential AI

These classifications remain proposed.

---

# 15. Light Node vs. Heavy Node

| Capability | 🌱 Light Node | ⚡ Heavy Node |
|---|---|---|
| Low Power | Primary Goal | Secondary |
| Consumer Hardware | Yes | Possible |
| Telemetry | Yes | Yes |
| Environmental Data | Yes | Yes |
| Basic Validation | Yes | Yes |
| Lightweight AI | Yes | Yes |
| Large AI Models | Limited | Yes |
| GPU Required | No | Depends on class |
| Akash Provider | Generally No | Potentially Yes |
| Large Containers | Limited | Yes |
| Renewable Integration | Optional | Strongly Supported |
| BESS Integration | Unlikely | Potential |
| Energy-Aware Scheduling | Participant | Major Participant |
| High-Speed Networking | Helpful | Preferred |
| Advanced Cooling | No | Potentially Required |

---

# 16. Node Discovery

**Status: 🔵 Proposed**

Nodes should eventually be able to advertise their capabilities to the Solar DePIN network.

Example capability information:

```text
Node ID
Node Class
CPU
RAM
Storage
GPU
GPU VRAM
Network Capacity
Energy Source
Solar Availability
Battery Availability
Geographic Region
Supported Workloads
Current Utilization
Health Status
```

This information could allow the control plane to understand what resources are available across the network.

---

# 17. Node Identity

**Status: 🔵 Proposed**

Each node should eventually possess a unique cryptographic identity.

The identity layer may support:

- Node authentication
- Signed telemetry
- Workload authorization
- Reputation
- Attestation
- Auditability

Private credentials should remain locally protected and should never be exposed through public telemetry.

---

# 18. Node Registration

A future registration process may resemble:

```text
NEW NODE
   │
   ▼
INSTALL NODE AGENT
   │
   ▼
GENERATE / REGISTER IDENTITY
   │
   ▼
HARDWARE DISCOVERY
   │
   ▼
CAPABILITY VALIDATION
   │
   ▼
NETWORK REGISTRATION
   │
   ▼
HEALTH CHECK
   │
   ▼
ACTIVE NODE
```

The exact registration mechanism remains under design.

---

# 19. Node Telemetry

Every participating node should eventually expose a standardized health and capability model.

Potential metrics include:

- CPU utilization
- RAM utilization
- Storage utilization
- GPU utilization
- GPU temperature
- GPU power
- Network throughput
- Node uptime
- Workload status
- Energy availability
- Renewable-energy percentage where measurable

Telemetry requirements may differ between Light and Heavy Nodes.

---

# 20. Energy Metadata

One feature that differentiates Solar DePIN nodes from ordinary compute nodes is the potential inclusion of energy information.

A node may eventually advertise information such as:

```text
Energy Source:
Solar / Grid / Battery / Mixed

Current Solar Production:
X kW

Battery State of Charge:
X %

Compute Power:
X W

Renewable Availability:
Available / Limited / Unavailable
```

The exact data model remains under development.

---

# 21. Energy-Aware Workloads

Future workloads may specify whether they can respond to energy conditions.

Potential workload categories:

### Always-On

Requires continuous availability.

### Flexible

Can tolerate scheduling changes.

### Interruptible

Can pause when renewable energy becomes unavailable.

### Migratable

Can move between compatible nodes.

### Renewable-Priority

Attempts to operate primarily when renewable energy is available.

These workload classes remain conceptual and require substantial engineering work.

---

# 22. Geographic Distribution

The Light/Heavy architecture is designed to support multiple locations.

```text
                 SOLAR DEPIN NETWORK
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
       REGION A      REGION B      REGION C
          │             │             │
     Light Nodes    Light Nodes    Light Nodes
     Heavy Nodes    Heavy Nodes    Heavy Nodes
          │             │             │
          └─────────────┼─────────────┘
                        ▼
                DISTRIBUTED COMPUTE
```

Geographic distribution may eventually improve:

- Resilience
- Renewable-energy utilization
- Network coverage
- Compute availability

---

# 23. Node Security

Every node should follow basic security requirements.

These include:

- Least-privilege access
- Secure authentication
- Encrypted communication
- Signed software
- Secure update mechanisms
- Container isolation
- Secrets protection
- Audit logging
- Restricted management interfaces

Heavy Nodes may require additional protections because they can host third-party workloads.

Detailed requirements belong in [`SECURITY.md`](SECURITY.md).

---

# 24. Node Software Updates

The future node agent should support controlled software updates.

Potential process:

```text
SIGNED RELEASE
      │
      ▼
VERIFY SIGNATURE
      │
      ▼
STAGED UPDATE
      │
      ▼
HEALTH CHECK
      │
   ┌──┴──┐
   ▼     ▼
SUCCESS FAILURE
   │     │
   ▼     ▼
KEEP   ROLLBACK
```

Automatic updates should include rollback mechanisms wherever practical.

---

# 25. Development Strategy

The Light Node and Heavy Node standards should not be finalized based solely on theoretical hardware requirements.

The recommended process is:

```text
DEFINE WORKLOADS
      │
      ▼
BUILD PROTOTYPES
      │
      ▼
BENCHMARK HARDWARE
      │
      ▼
MEASURE POWER
      │
      ▼
MEASURE PERFORMANCE
      │
      ▼
TEST RELIABILITY
      │
      ▼
DEFINE MINIMUM SPECS
```

This allows hardware requirements to emerge from actual workload performance.

---

# 26. Immediate Engineering Questions

Before Solar DePIN Hub publishes final node requirements, the following questions need answers.

## Light Node

- What services must every Light Node provide?
- Should Light Nodes earn rewards?
- What useful work does a community Light Node perform?
- Is 8 GB RAM sufficient?
- Should ARM devices eventually be supported?
- How much storage is required?
- What is the maximum desired power consumption?
- Which AI models should be supported?
- What bandwidth is required?

## Heavy Node

- Is a GPU mandatory?
- What minimum GPU VRAM is required?
- Should CPU-only Heavy Nodes exist?
- What storage is required for Akash?
- How should persistent storage work?
- What minimum network bandwidth is required?
- How should renewable-energy data be verified?
- How should BESS availability affect workloads?
- What cooling standards are necessary?

These questions should be answered through prototypes and testing.

---

# 27. Long-Term Objective

The Light/Heavy Node architecture allows Solar DePIN Hub to combine two different strengths.

Light Nodes provide:

**Scale + Accessibility + Telemetry + Distribution**

Heavy Nodes provide:

**Compute + GPU Capacity + AI + Decentralized Cloud Infrastructure**

Together:

```text
       MANY LIGHT NODES
              +
       HEAVY COMPUTE NODES
              +
      RENEWABLE ENERGY DATA
              +
      UNIFIED TELEMETRY
              │
              ▼
        SOLAR DEPIN NETWORK
```

The objective is not simply to create another class of compute server.

The objective is to create a distributed infrastructure network where nodes can communicate both their **computational capabilities and their relationship with energy**.

---

## Related Documentation

- [`../README.md`](../README.md) — Project overview
- [`../ROADMAP.md`](../ROADMAP.md) — Development roadmap
- [`ARCHITECTURE.md`](ARCHITECTURE.md) — System architecture
- [`INFRASTRUCTURE.md`](INFRASTRUCTURE.md) — Physical infrastructure
- [`TELEMETRY.md`](TELEMETRY.md) — Telemetry architecture
- [`AKASH.md`](AKASH.md) — Akash integration
- [`SECURITY.md`](SECURITY.md) — Security architecture