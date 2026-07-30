# Solar DePIN Hub — Physical Infrastructure

## 1. Purpose

This document describes the physical infrastructure used by the current Solar DePIN Hub testbed.

It focuses on equipment that is installed, observed, or confirmed.

Future infrastructure is clearly identified as planned or TBD so that proposed hardware is not confused with deployed equipment.

---

# 2. Infrastructure Status

Solar DePIN Hub uses the following classifications:

- ✅ **Operational** — installed and currently operating
- 🟢 **Planned** — confirmed future development
- 🔵 **Proposed** — being considered or designed
- 🟡 **TBD** — exact specification or implementation has not yet been determined

---

# 3. Testbed Overview

The current testbed combines:

- Solar photovoltaic generation
- Huawei inverter infrastructure
- Fiber-optic connectivity
- Local compute infrastructure
- GPU compute
- Server power protection
- Environmental telemetry
- Decentralized compute experimentation

High-level physical architecture:

```text
                    SOLAR ARRAY
                 104 PV MODULES
                      │
                      ▼
               HUAWEI INVERTER
                      │
                      ▼
              SITE ELECTRICAL
                      │
             ┌────────┴────────┐
             ▼                 ▼
        SITE LOADS          COMPUTE
                               │
                               ▼
                         SERVER / GPU
                               │
                               ▼
                           INTERNET
                               │
                               ▼
                     DECENTRALIZED
                         NETWORKS
```

A future Battery Energy Storage System (BESS) would add energy buffering between renewable generation and compute demand.

---

# 4. Solar PV Infrastructure

**Status: ✅ Operational**

The Solar DePIN Hub testbed contains **104 monocrystalline photovoltaic modules**.

## Current Configuration

| Parameter | Current Configuration |
|---|---|
| Manufacturer | Risen Energy |
| Model | RSM120-8-585M |
| Module Type | Monocrystalline |
| Number of Modules | 104 |
| Rated Power per Module | 585 W |
| Total DC Nameplate Capacity | ~60.84 kWp |
| Physical Platforms | 2 |
| Modules per Platform | 52 |

Total theoretical DC nameplate capacity:

```text
104 × 585 W = 60,840 W

60,840 W = 60.84 kWp
```

---

# 5. Solar Module Specifications

Confirmed module information:

| Specification | Value |
|---|---:|
| Manufacturer | Risen Energy Co., Ltd. |
| Model | RSM120-8-585M |
| Rated Maximum Power | 585 W |
| Voltage at Maximum Power (Vmp) | 34.12 V |
| Current at Maximum Power (Imp) | 17.15 A |
| Open-Circuit Voltage (Voc) | 41.00 V |
| Short-Circuit Current (Isc) | 18.16 A |
| Maximum System Voltage | 1500 V DC |
| Dimensions | 2172 × 1303 × 35 mm |
| Weight | 32 kg |

Exact PV string configuration and MPPT allocation should be documented separately once verified.

**Status: 🟡 TBD**

---

# 6. Physical Array Layout

The installation is divided into two physical solar platforms.

```text
          PLATFORM A
          52 MODULES
              │
              │
              ├──────────┐
              │          │
                         ▼
                     INVERTER
                         ▲
              │          │
              ├──────────┘
              │
          52 MODULES
          PLATFORM B
```

Both platforms currently feed the existing inverter architecture.

The exact electrical string topology is still to be documented.

---

# 7. Inverter Infrastructure

**Status: ✅ Operational**

Current inverter:

**Huawei SUN2000-30KTL-M3**

| Parameter | Value |
|---|---|
| Manufacturer | Huawei |
| Model | SUN2000-30KTL-M3 |
| Rated AC Output | 30 kW |
| Monitoring | Huawei FusionSolar |
| Current Quantity | 1 |

All 104 PV modules are currently connected through the existing single-inverter architecture.

The PV array has approximately:

```text
60.84 kWp DC solar capacity
           │
           ▼
30 kW AC inverter
```

The relationship between DC array capacity and inverter capacity should be considered when analyzing clipping, generation curves, and future expansion.

---

# 8. Second Inverter

**Status: 🟢 Planned**

A second inverter is planned when project funding allows.

The additional inverter may allow the solar infrastructure to be redistributed between the two physical arrays and provide additional electrical capacity.

The following remain undecided:

- Manufacturer/model
- Rated output
- String redistribution
- MPPT allocation
- Electrical topology
- Installation schedule

These should remain **TBD** until engineering selection is complete.

---

# 9. Solar Monitoring

**Status: ✅ Operational**

The existing Huawei installation uses **FusionSolar** for solar monitoring.

Available information may include:

- Current generation
- Historical energy production
- Inverter status
- Electrical measurements
- System alarms
- Operational state

Solar DePIN Hub intends to make selected energy information available to its own telemetry layer.

Potential interfaces under evaluation include:

- FusionSolar API
- Modbus RTU
- Modbus TCP
- Huawei local interfaces

The final production interface has not yet been selected.

---

# 10. Compute Infrastructure

**Status: ✅ Experimental Infrastructure Operational**

The site includes compute hardware used for decentralized compute experimentation.

Confirmed current GPU infrastructure includes:

- NVIDIA RTX 3090-class GPU
- Approximately 24 GB GPU VRAM
- AMD Ryzen 7-class CPU

The system has been used for server and decentralized-compute workloads.

Additional hardware specifications should be documented as they are verified.

## Still Required

🟡 Confirm:

- Exact CPU model
- Motherboard
- System RAM
- Storage type
- Storage capacity
- Power supply
- Cooling configuration
- Operating system configuration
- Network interface speed

No unverified specification should be presented as final.

---

# 11. Server Power Protection

**Status: ✅ Present**

A dedicated uninterruptible power supply (UPS) is connected to the server infrastructure.

Its purpose is to provide short-duration power protection and help protect compute equipment from:

- Power interruptions
- Voltage instability
- Unexpected shutdown
- Short-duration electrical events

The exact UPS specifications still need to be documented.

## Required Information

🟡 Confirm:

- Manufacturer
- Model
- Rated power (W)
- Rated apparent power (VA)
- Battery capacity
- Runtime under server load
- Input voltage
- Output voltage
- Communication interface, if available

The server UPS should not be confused with the future site-scale BESS.

---

# 12. Battery Energy Storage System

**Status: 🟢 Planned — Not Currently Installed**

Solar DePIN Hub plans to integrate a site-scale Battery Energy Storage System.

The BESS would serve a different purpose from the server UPS.

```text
SERVER UPS
    │
    └── Short-duration equipment protection

SITE BESS
    │
    └── Energy storage and infrastructure operation
```

Potential BESS functions include:

- Store solar generation
- Supply compute during lower solar production
- Smooth renewable variability
- Support energy-aware scheduling
- Provide site resilience
- Reduce instantaneous grid dependence

## Engineering Selection Required

🟡 Determine:

- Battery manufacturer
- Chemistry
- Usable capacity (kWh)
- Charge/discharge power (kW)
- Battery Management System
- Inverter compatibility
- Telemetry interface
- Thermal-management requirements
- Safety architecture

---

# 13. Internet Connectivity

**Status: ✅ Operational**

The site uses a fiber-optic internet connection.

| Parameter | Current Information |
|---|---|
| ISP | Vega |
| Connection | Fiber optic |
| Service Speed | Up to 1 Gbps |

Observed server throughput during an active workload has been approximately:

- **806 Mbps upload**
- **768 Mbps download**

These measurements represent observed performance and should not be interpreted as guaranteed bandwidth.

Network performance should be measured periodically as the infrastructure evolves.

---

# 14. Network Redundancy

**Status: 🔵 Future Expansion**

The current architecture can potentially be expanded with a second internet connection.

Possible future architecture:

```text
             ISP A
               │
               ▼
        ┌──────────────┐
        │              │
        │ WAN FAILOVER │
        │              │
        └──────────────┘
               ▲
               │
             ISP B
               │
               ▼
        SITE NETWORK
```

Potential benefits include:

- Internet failover
- Improved remote-management reliability
- Increased infrastructure availability
- Reduced dependence on a single ISP

Implementation remains TBD.

---

# 15. Local Network Architecture

**Status: 🟡 Detailed Topology TBD**

The production network should eventually separate infrastructure functions.

Target architecture:

```text
                    INTERNET
                       │
                       ▼
                ROUTER / FIREWALL
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
      MANAGEMENT     COMPUTE     TELEMETRY
        NETWORK      NETWORK       NETWORK
```

Future requirements include:

- VLAN segmentation
- Firewall rules
- Secure remote administration
- Infrastructure VPN
- Access control
- Monitoring
- Restricted management interfaces

Exact router, firewall, and switch specifications should be documented once verified.

---

# 16. Weather & Environmental Infrastructure

**Status: ✅ Hardware Present / 🟢 Integration Development**

WeatherXM infrastructure is used for environmental observations associated with the site.

Relevant environmental measurements include:

- Temperature
- Relative humidity
- Wind speed
- Wind direction
- Precipitation

Environmental telemetry can eventually become an input to energy forecasting and compute scheduling.

Additional data sources may later provide:

- Solar irradiance
- Cloud cover
- Forecast generation
- Atmospheric conditions

Exact WeatherXM hardware model and integration interface should be documented separately when confirmed.

---

# 17. Physical Infrastructure Relationships

The current physical system can be represented as:

```text
              SUNLIGHT
                 │
                 ▼
        104 SOLAR MODULES
                 │
                 ▼
        HUAWEI SUN2000
                 │
                 ▼
          SITE ELECTRICAL
                 │
                 ▼
         COMPUTE HARDWARE
                 │
                 ▼
             SERVER UPS
                 │
                 ▼
          SERVER / RTX 3090
                 │
                 ▼
          FIBER INTERNET
                 │
                 ▼
       DECENTRALIZED COMPUTE
```

Environmental telemetry operates alongside this system:

```text
          WEATHERXM
              │
              ▼
     ENVIRONMENTAL DATA
              │
              ▼
       TELEMETRY LAYER
```

---

# 18. Target Physical Architecture

The longer-term architecture adds battery storage, additional compute capacity, and network resilience.

```text
                       SOLAR
                         │
                         ▼
                   PV INVERTERS
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
            BESS               SITE / GRID
              │
              ▼
        POWER DISTRIBUTION
              │
       ┌──────┴──────┐
       ▼             ▼
  LIGHT NODES    HEAVY NODES
                     │
                     ▼
                GPU COMPUTE
                     │
                     ▼
                NETWORKING
                     │
              ┌──────┴──────┐
              ▼             ▼
             ISP A         ISP B
```

This is a target architecture rather than a description of the currently deployed system.

---

# 19. Infrastructure Data Still Required

The following information should be collected as engineering documentation becomes available.

## Solar

- PV string topology
- Number of strings
- Modules per string
- MPPT allocation
- DC protection equipment
- AC protection equipment

## Compute

- Exact CPU model
- Motherboard
- RAM
- Storage
- PSU
- Cooling
- Network interface

## UPS

- Manufacturer
- Model
- VA rating
- Watt rating
- Battery capacity
- Runtime

## Networking

- Router/firewall model
- Switch model
- Network topology
- VLAN architecture
- Static/public IP availability

## Environmental

- Exact WeatherXM hardware model
- Telemetry interface
- Update frequency

## Future BESS

- Manufacturer
- Chemistry
- Capacity
- Power
- BMS
- Inverter architecture
- Telemetry interface

---

# 20. Documentation Principle

Physical infrastructure documentation must distinguish between:

**What exists**

and

**What Solar DePIN Hub intends to build.**

Unverified specifications should remain marked **TBD** until confirmed from equipment labels, configuration interfaces, manufacturer documentation, or direct measurements.

This allows developers and infrastructure partners to rely on the repository as an accurate engineering reference.

---

## Related Documentation

- [`../README.md`](../README.md) — Project overview
- [`../ROADMAP.md`](../ROADMAP.md) — Development roadmap
- [`ARCHITECTURE.md`](ARCHITECTURE.md) — System architecture
- [`NODES.md`](NODES.md) — Light and Heavy Node architecture
- [`TELEMETRY.md`](TELEMETRY.md) — Telemetry architecture
- [`AKASH.md`](AKASH.md) — Akash integration
- [`SECURITY.md`](SECURITY.md) — Security architecture
