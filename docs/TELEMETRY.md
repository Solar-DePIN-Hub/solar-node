# Solar DePIN Hub — Telemetry Architecture

## 1. Purpose

Solar DePIN Hub requires telemetry from both physical energy infrastructure and digital compute infrastructure.

The telemetry architecture is intended to combine:

- Solar generation
- Inverter operation
- Environmental conditions
- Compute utilization
- GPU utilization
- Network performance
- Node health
- Decentralized compute status
- Future battery state

into a common infrastructure data layer.

The long-term objective is to provide reliable data for monitoring, analytics, automation, and future energy-aware workload orchestration.

---

# 2. Telemetry Architecture

```text
                  PHYSICAL INFRASTRUCTURE
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
       SOLAR           ENVIRONMENT        FUTURE BESS
      INVERTER          WEATHER              │
          │                │                 │
          └────────────────┼─────────────────┘
                           ▼
                    ENERGY TELEMETRY
                           │
                           │
                           ▼
                   UNIFIED DATA LAYER
                           ▲
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
       COMPUTE           NETWORK          DePIN
      TELEMETRY         TELEMETRY       TELEMETRY
          │                │                │
          └────────────────┼────────────────┘
                           ▼
                     OBSERVABILITY
                           │
                           ▼
                FUTURE CONTROL PLANE
```

Not every component shown above is currently deployed.

---

# 3. Telemetry Status

Solar DePIN Hub uses the following classifications:

- ✅ **Operational** — telemetry source exists and is currently usable
- 🟢 **In Development** — integration work is underway or planned
- 🔵 **Proposed** — future architecture or research
- 🟡 **TBD** — implementation has not yet been selected

---

# 4. Solar Telemetry

**Status: ✅ Monitoring Available / 🟢 Direct Integration in Development**

The current solar installation uses a Huawei SUN2000-30KTL-M3 inverter and Huawei FusionSolar monitoring.

Solar telemetry is one of the primary physical data sources for Solar DePIN Hub.

Target metrics include:

- Current PV generation
- Daily energy production
- Historical energy production
- AC output power
- DC input information
- Voltage
- Current
- Frequency
- Inverter state
- Fault conditions
- Alarm state

The exact available metrics depend on the selected Huawei telemetry interface.

---

# 5. Huawei Telemetry Interfaces

Several methods may be evaluated for obtaining inverter information.

## FusionSolar

Huawei FusionSolar currently provides monitoring of the solar installation.

Potential advantages:

- Existing deployment
- Remote accessibility
- Historical information
- Existing Huawei ecosystem integration

Potential limitations include:

- Cloud dependency
- API availability
- API rate limits
- Authentication requirements
- Possible telemetry delay

---

## Modbus RTU

**Status: 🔵 Under Evaluation**

A local Modbus RTU connection could provide direct communication with supported Huawei equipment.

Potential architecture:

```text
HUAWEI INVERTER
       │
       │ RS485
       ▼
USB / RS485 INTERFACE
       │
       ▼
TELEMETRY COLLECTOR
       │
       ▼
SOLAR DEPIN DATA LAYER
```

Potential advantages:

- Local telemetry
- Reduced cloud dependency
- Potentially lower latency
- Infrastructure can continue monitoring during some internet outages

---

## Modbus TCP

**Status: 🔵 Under Evaluation**

Where supported by the final network and Huawei configuration, Modbus TCP may provide another local telemetry path.

```text
HUAWEI INFRASTRUCTURE
         │
         ▼
     LOCAL NETWORK
         │
         ▼
   MODBUS TCP CLIENT
         │
         ▼
 TELEMETRY COLLECTOR
```

The exact production telemetry interface should be selected after compatibility and reliability testing.

---

# 6. Telemetry Collector

**Status: 🔵 Architecture Design**

Solar DePIN Hub should eventually use a dedicated telemetry collector rather than coupling infrastructure logic directly to a vendor API.

Conceptual architecture:

```text
FUSIONSOLAR ───────┐
                   │
MODBUS RTU ────────┤
                   │
MODBUS TCP ────────┼──► TELEMETRY COLLECTOR
                   │
WEATHERXM ─────────┤
                   │
COMPUTE METRICS ───┤
                   │
NETWORK METRICS ───┘
```

The collector would normalize data before passing it to the wider Solar DePIN platform.

Potential implementation languages include:

- Python
- Go

The final implementation remains TBD.

---

# 7. Environmental Telemetry

**Status: ✅ Data Source Present / 🟢 Integration Development**

WeatherXM infrastructure provides environmental information relevant to the Solar DePIN site.

Relevant measurements include:

- Temperature
- Relative humidity
- Wind speed
- Wind direction
- Precipitation

Additional future sources may provide:

- Solar irradiance
- Cloud cover
- Atmospheric pressure
- Solar forecast information
- Expected PV generation

---

# 8. Why Weather Data Matters

Environmental information is useful beyond displaying current weather.

Future energy forecasting may use:

```text
CURRENT WEATHER
       +
WEATHER FORECAST
       +
HISTORICAL SOLAR DATA
       +
TIME OF DAY
       +
SEASON
       │
       ▼
EXPECTED SOLAR GENERATION
```

Expected solar generation could eventually become an input to compute scheduling.

---

# 9. Compute Telemetry

**Status: 🟢 In Development**

Compute telemetry provides visibility into the machines performing Solar DePIN workloads.

Target CPU/system metrics include:

- CPU utilization
- CPU temperature
- System load
- RAM utilization
- Disk utilization
- Disk health
- Container state
- Operating-system health
- Uptime

These metrics help determine whether a node is healthy and capable of accepting additional workloads.

---

# 10. GPU Telemetry

GPU telemetry is especially important for Heavy Nodes.

Target metrics include:

- GPU utilization
- VRAM utilization
- GPU temperature
- GPU power consumption
- Clock speed
- Fan state where available
- Active processes
- GPU health

For NVIDIA systems, telemetry may be collected using supported NVIDIA interfaces and monitoring tools.

Current experimental infrastructure includes an RTX 3090-class GPU system.

---

# 11. Energy per Compute Workload

**Status: 🔵 Research**

A long-term objective is to understand the relationship between compute activity and electricity consumption.

Example:

```text
WORKLOAD
   │
   ▼
GPU UTILIZATION
   │
   ▼
GPU POWER
   │
   ▼
ENERGY CONSUMPTION
   │
   ▼
WORKLOAD ENERGY PROFILE
```

This could eventually allow Solar DePIN Hub to estimate:

- Energy consumed by a workload
- Renewable energy used
- Compute efficiency
- Energy cost
- Carbon intensity where appropriate data is available

These measurements require validation before being used for accounting or verification.

---

# 12. Network Telemetry

**Status: 🟢 Basic Measurements Available**

Network telemetry is required because decentralized workloads depend on reliable connectivity.

Target metrics include:

- Download throughput
- Upload throughput
- Latency
- Packet loss
- Interface utilization
- Connection state
- WAN availability

The current site uses Vega fiber connectivity with service up to 1 Gbps.

Previously observed server throughput during an active workload was approximately:

- 806 Mbps upload
- 768 Mbps download

These are observed measurements rather than guaranteed service levels.

---

# 13. Node Health

Every Light Node and Heavy Node should eventually expose a standardized health state.

Example:

```text
NODE
 │
 ├── CPU Health
 ├── Memory Health
 ├── Storage Health
 ├── GPU Health
 ├── Network Health
 ├── Telemetry Health
 └── Workload Health
          │
          ▼
     NODE STATUS
```

Possible node states may include:

- Healthy
- Degraded
- Unavailable
- Maintenance
- Unknown

The final state model remains under development.

---

# 14. Light Node Telemetry

Light Nodes should expose enough information for network operation without creating excessive monitoring overhead.

Potential metrics include:

- Node uptime
- CPU utilization
- RAM utilization
- Storage availability
- Network status
- Node-agent status
- Workload status
- Local energy information where available
- Environmental telemetry where available

Light Nodes should not be required to expose private user information.

---

# 15. Heavy Node Telemetry

Heavy Nodes require deeper observability because they may host significant workloads.

Potential metrics include:

- CPU
- RAM
- Storage
- GPU
- GPU power
- GPU temperature
- Network throughput
- Container state
- Workload state
- Energy availability
- Battery information
- Solar production
- Akash provider status

Heavy Node telemetry may become a major input to future orchestration.

---

# 16. Akash DePIN Telemetry

**Status: 🟢 Integration Research**

Solar DePIN Hub is exploring integration with Akash-focused DePIN telemetry tooling.

The objective is to connect decentralized compute state with physical energy state.

Conceptually:

```text
AKASH WORKLOAD
      │
      ▼
COMPUTE TELEMETRY
      │
      │
      ├─────────────┐
      │             │
      ▼             ▼
GPU METRICS    WORKLOAD STATE
      │             │
      └──────┬──────┘
             ▼
       SOLAR DEPIN
       DATA LAYER
             ▲
             │
       SOLAR TELEMETRY
```

This allows infrastructure monitoring to understand both the workload and the energy environment supporting it.

---

# 17. Future Battery Telemetry

**Status: 🟢 Planned**

When a BESS is installed, target metrics should include:

- State of Charge
- State of Health
- Charge power
- Discharge power
- Battery temperature
- Available energy
- Fault state
- Battery Management System status

Battery State of Charge may eventually become one of the most important inputs to energy-aware scheduling.

---

# 18. Unified Telemetry Model

**Status: 🔵 Architecture Design**

The long-term objective is to normalize telemetry into a common infrastructure model.

Example:

```text
SITE
 │
 ├── ENERGY
 │    ├── Solar Production
 │    ├── Grid State
 │    └── Battery State
 │
 ├── ENVIRONMENT
 │    ├── Temperature
 │    ├── Wind
 │    └── Precipitation
 │
 ├── COMPUTE
 │    ├── CPU
 │    ├── GPU
 │    ├── RAM
 │    └── Storage
 │
 ├── NETWORK
 │    ├── Throughput
 │    ├── Latency
 │    └── Availability
 │
 └── WORKLOADS
      ├── Containers
      ├── Akash
      └── DePIN
```

A normalized model reduces dependence on individual hardware vendors and networks.

---

# 19. Observability Stack

**Status: 🔵 Planned Architecture**

Candidate technologies include:

- Prometheus
- Grafana
- Vendor telemetry collectors
- Custom Solar DePIN collectors
- Akash telemetry services

Conceptual flow:

```text
DATA SOURCES
     │
     ▼
COLLECTORS
     │
     ▼
PROMETHEUS
     │
     ▼
GRAFANA
     │
     ├── Dashboards
     ├── Alerts
     └── Historical Analysis
```

The final observability stack should be selected through implementation testing.

---

# 20. Telemetry Update Frequency

Different data does not necessarily require the same polling interval.

Example categories:

### High Frequency

Potential examples:

- GPU utilization
- GPU power
- CPU utilization
- Active workload state

### Medium Frequency

Potential examples:

- Solar generation
- Inverter state
- Battery power
- Network throughput

### Lower Frequency

Potential examples:

- Weather conditions
- Hardware inventory
- Long-term energy statistics

Exact intervals should be determined through testing rather than hard-coded prematurely.

---

# 21. Telemetry Storage

**Status: 🟡 TBD**

Solar DePIN Hub will require storage for historical telemetry.

Requirements include:

- Time-series data
- Retention policies
- Query performance
- Backup
- Data integrity
- Storage efficiency

Potential architectures may use a dedicated time-series database or monitoring platform.

No production telemetry database has yet been selected.

---

# 22. Telemetry API

**Status: 🔵 Proposed**

A common API could allow other Solar DePIN components to consume normalized infrastructure state.

Conceptual example:

```text
PHYSICAL SYSTEMS
       │
       ▼
TELEMETRY COLLECTORS
       │
       ▼
NORMALIZED DATA
       │
       ▼
SOLAR DEPIN API
       │
   ┌───┼───────────┐
   ▼   ▼           ▼
 UI   AI        ORCHESTRATOR
```

This prevents every application from needing direct access to physical equipment.

---

# 23. Telemetry Security

Telemetry systems should follow least-privilege principles.

Important requirements include:

- Do not expose inverter management interfaces publicly
- Do not expose server management interfaces publicly
- Protect API credentials
- Encrypt remote telemetry where practical
- Authenticate nodes
- Validate telemetry sources
- Separate monitoring access from control access
- Avoid placing secrets inside public repositories

Read-only telemetry access should be preferred wherever control access is unnecessary.

---

# 24. Monitoring vs. Control

Solar DePIN Hub should maintain a clear separation between:

**Observing infrastructure**

and

**Controlling infrastructure**

Example:

```text
TELEMETRY
   │
   ▼
READ-ONLY DATA
   │
   ▼
MONITORING

----------------

AUTHORIZED CONTROL
   │
   ▼
POLICY ENGINE
   │
   ▼
INFRASTRUCTURE ACTION
```

A monitoring compromise should not automatically provide the ability to control an inverter, battery, server, or workload.

---

# 25. Data Validation

**Status: 🔵 Research**

Telemetry used for automated infrastructure decisions should be validated.

Possible techniques include:

- Range validation
- Timestamp validation
- Cross-sensor comparison
- Historical anomaly detection
- Cryptographic node identity
- Signed telemetry
- Multiple independent data sources

For example, solar-production information could potentially be compared against weather conditions and historical production patterns to detect abnormal readings.

---

# 26. Telemetry and AI

**Status: 🔵 Long-Term Research**

AI systems may eventually analyze telemetry for:

- Anomaly detection
- Energy forecasting
- Hardware failure prediction
- Capacity forecasting
- Workload-placement recommendations
- Incident analysis

Conceptually:

```text
TELEMETRY
    │
    ▼
HISTORICAL DATA
    │
    ▼
AI ANALYSIS
    │
    ├── Anomaly Detection
    ├── Energy Forecast
    ├── Failure Prediction
    └── Capacity Forecast
```

AI output should initially be advisory rather than automatically receiving unrestricted control over physical infrastructure.

---

# 27. Telemetry and Energy-Aware Scheduling

The ultimate purpose of the unified telemetry layer is to provide trustworthy infrastructure state to the future control plane.

```text
SOLAR
  +
BATTERY
  +
WEATHER
  +
COMPUTE
  +
NETWORK
  +
WORKLOAD
   │
   ▼
CURRENT INFRASTRUCTURE STATE
   │
   ▼
ENERGY-AWARE ORCHESTRATOR
```

Possible future decisions include:

- Accept workload
- Delay flexible workload
- Reduce compute power
- Use stored battery energy
- Select another node
- Migrate compatible workload
- Trigger failover

These capabilities remain under research.

---

# 28. Immediate Engineering Priorities

The telemetry work should initially focus on a small number of reliable metrics.

## Priority 1 — Solar

Confirm a reliable method to obtain:

- Current generation
- Inverter state
- Energy production

## Priority 2 — Compute

Collect:

- CPU utilization
- RAM
- GPU utilization
- GPU VRAM
- GPU temperature
- GPU power

## Priority 3 — Network

Collect:

- WAN availability
- Throughput
- Latency

## Priority 4 — Environment

Integrate:

- WeatherXM data

## Priority 5 — Unified Dashboard

Display the information through a common monitoring system.

Only after these measurements are reliable should they become inputs to automated workload decisions.

---

# 29. Development Principle

Telemetry is the sensory layer of Solar DePIN Hub.

Without reliable telemetry, an energy-aware control plane cannot know:

- How much renewable energy is available
- Whether a node is healthy
- Whether a GPU has spare capacity
- Whether a network connection is reliable
- Whether a battery has sufficient stored energy
- Whether a workload should remain where it is

The progression should therefore be:

```text
MEASURE
   │
   ▼
VALIDATE
   │
   ▼
STORE
   │
   ▼
VISUALIZE
   │
   ▼
ANALYZE
   │
   ▼
AUTOMATE
```

Solar DePIN Hub should not automate infrastructure decisions until the underlying telemetry has been demonstrated to be reliable.

---

## Related Documentation

- [`../README.md`](../README.md) — Project overview
- [`../ROADMAP.md`](../ROADMAP.md) — Development roadmap
- [`ARCHITECTURE.md`](ARCHITECTURE.md) — System architecture
- [`INFRASTRUCTURE.md`](INFRASTRUCTURE.md) — Physical infrastructure
- [`NODES.md`](NODES.md) — Light and Heavy Node architecture
- [`AKASH.md`](AKASH.md) — Akash integration
- [`SECURITY.md`](SECURITY.md) — Security architecture
