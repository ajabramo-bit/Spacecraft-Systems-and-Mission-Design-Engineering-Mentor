# Electrical Power Subsystem

**Course:** ASTE-331a — Spacecraft Systems Engineering  
**Lecture:** 06 — Electrical Power Subsystem  
**Instructors:** Jim Chase, Danielle Marsh  
**Source:** `331_06_Power_20251107.pdf`

---

## Lecture Overview

This lecture introduces the spacecraft Electrical Power Subsystem (EPS), including power generation, energy storage, power control, electrical isolation and grounding, EMI/EMC, and the power-subsystem design process. It also uses Solar Probe, Psyche, and Europa Clipper to show how mission requirements, environment, heritage, operations, and hardware architecture drive EPS design.

---

## Table of Contents

- [1. Electrical Power System Overview](#1-electrical-power-system-overview)
- [2. Electrical Terminology](#2-electrical-terminology)
- [3. Mission Design Examples](#3-mission-design-examples)
- [4. Power Generation Overview](#4-power-generation-overview)
- [5. Solar Arrays](#5-solar-arrays)
- [6. Solar Array Performance and Sizing](#6-solar-array-performance-and-sizing)
- [7. Radioisotope Thermoelectric Generators](#7-radioisotope-thermoelectric-generators)
- [8. Energy Storage Overview](#8-energy-storage-overview)
- [9. Batteries](#9-batteries)
- [10. Battery Sizing and Energy Equations](#10-battery-sizing-and-energy-equations)
- [11. Other Energy Storage Options](#11-other-energy-storage-options)
- [12. Power Control Overview](#12-power-control-overview)
- [13. Power Regulation](#13-power-regulation)
- [14. Solar Array Power Control](#14-solar-array-power-control)
- [15. Power Distribution](#15-power-distribution)
- [16. Energy Management](#16-energy-management)
- [17. Electrical Isolation](#17-electrical-isolation)
- [18. Grounding](#18-grounding)
- [19. EMI and EMC](#19-emi-and-emc)
- [20. Power Subsystem Design Process](#20-power-subsystem-design-process)
- [21. Europa Clipper Case Study](#21-europa-clipper-case-study)
- [22. Lecture Summary](#22-lecture-summary)

---

# 1. Electrical Power System Overview

> **Source: Slides 2**

## Function

The Electrical Power System provides electrical power and power distribution throughout the spacecraft.

Primary drivers typically include:

- Sun-spacecraft distance
- Power profiles during science and telecom operations
- Launch and eclipse periods for battery sizing
- Safe-mode operation
  - Spacecraft attitude
  - Power draw
- Hardware redundancy

## GRAIL Example

The GRAIL power system included:

- Power electronics
  - Interface cards
  - Converters
- One 30 A-hr battery
- Two solar arrays
- Total mass of approximately 30 kg

## Common EPS Functions

### Power Generation

- Solar arrays
- Radioisotope thermoelectric generators (RTGs)

### Energy Storage

- Batteries
- Fuel cells
- Flywheels
- Supercapacitors

### Power Control

- Power regulation
- Power distribution
- Energy management
- Array and battery voltage regulation
- Current distribution
- Battery charging and discharging

### Electrical Isolation and Grounding

- Isolation
- Grounding
- EMI/EMC considerations

## Key Trades and Analyses

- Solar arrays vs. RTGs
- Battery type
  - Primary
  - Secondary
- Solar-array sizing
- Battery sizing
- Power Equipment List (PEL)
- Power analysis
- Heritage from prior systems

## Key Parameters

- System power loads
- Power profiles
- Power margins
- Worst-case depth of discharge

---

## Typical EPS Architecture

> **Source: Slide 3-4**

### Power generation
- solar power nuclear power

### Energy storage
- batteries
- fuel cells
- flywheels
- supercapacitors

### Power control
- power regulation
- power distribution
- energy management

## Typical components include:

### Solar Array

Provides power generation.

### Battery

Provides energy storage.

### Power Conditioning Unit

The **PCU** regulates power from the solar array and battery.

Typical functions include:

- Battery charge regulation
- Solar-array regulation
- Maximum-power-point control
- Bus-voltage control

### Power Distribution Unit

The **PDU** provides:

- Power conversion
- Switching
- Distribution
- Protection

A representative architecture is:

```text
Solar Array
     ↓
Power Conditioning Unit
     ↕
   Battery
     ↓
Power Bus
     ↓
Power Distribution Unit
     ↓
Spacecraft Loads
```

The slide's block diagram shows solar panels feeding a PCU with battery-charge regulation and MPPT-based control, a battery connected to the bus, and a PDU containing EMI filters, DC/DC converters, distribution/protection circuits, and switches.

---

# 2. Electrical Terminology

> **Source: Slide 5**

## Voltage

Voltage is the electrical potential that pushes electric charge through a circuit.

The lecture compares it to **water pressure in a hose**.

Units:

```text
Volts (V)
```

## Current

Current measures the flow of electric charge.

The lecture compares it to the **amount of water flowing through a hose**.

Units:

```text
Amperes (A)
```

## Resistance

Resistance measures opposition to electrical current.

The lecture compares it to **sand obstructing a hose**.

Units:

```text
Ohms
```

The slide reminds students of the voltage-current-resistance relationship:

```math
V = IR
```

---

# 3. Mission Design Examples

> **Source: Slides 6–7**

## Solar Probe

Key EPS design drivers include:

- Flagship mission
  - Drives system-wide redundancy
- Extremely close distance to the Sun
  - Requires precise autonomous solar-array control
  - Requires active solar-array cooling
- Severe thermal and radiation environment
  - Drives degradation analysis
  - Drives environmental testing of solar arrays and batteries

The system block diagram shows EPS interacting with essentially every spacecraft subsystem, including avionics, G&C, instruments, propulsion, cooling, telecom, thermal hardware, and separation hardware.

---

## Psyche

Key EPS design drivers include:

- Class B mission
  - Drives overall redundancy
- Approximately 3.3 AU from the Sun
  - Drives solar-array sizing
- Multi-hour eclipse periods in orbit around Psyche
  - Drive battery sizing
- Electric propulsion
  - Drives a high-voltage power bus
- Split EPS design between JPL and Maxar with different heritage architectures
  - Drives multiple power converters
  - Drives power-switching electronics

The Psyche power block diagram shows the solar array and battery feeding a PCU, with regulated high-voltage and low-voltage paths supplying the propulsion system and spacecraft loads.

---

# 4. Power Generation Overview

> **Source: Slides 8–9**

Power generation produces electrical energy to:

- Power spacecraft subsystems and components
- Charge spacecraft batteries

Two common forms are:

## Solar Power

Solar panels convert sunlight into electrical energy.

## Nuclear Power

A nuclear source such as an RTG converts heat from radioactive decay into electrical energy.

---

## Power-Generation Trade Considerations

### Conversion Efficiency

Representative values from the lecture:

- Solar arrays: approximately 20–30%
- RTGs: approximately 5–10%

### Degradation

Solar arrays degrade due to:

- Radiation
- Temperature effects

RTGs generally provide greater longevity.

### Environmental Dependence

Solar arrays require sunlight and are affected by:

- Dust
- Shadowing

RTGs are generally much less dependent on the external illumination environment.

### Total Power Capability

Solar arrays generally have much higher total wattage capability than RTGs.

### Regulation

RTGs are subject to nuclear regulations.

---

# 5. Solar Arrays

> **Source: Slides 10–12**

Solar arrays consist of many interconnected photovoltaic cells that convert sunlight into electricity.

When sunlight reaches a cell:

1. Photons excite electrons.
2. Electric charge is generated.
3. The charge produces current when connected to a circuit.
4. Current can power spacecraft devices.

---

## Solar-Array Configurations

### Body-Mounted Arrays

Generally used for spinning spacecraft.

### Deployable Arrays

Generally used for:

- Three-axis-stabilized spacecraft
- Landers

Deployable arrays can be:

- Fixed
- Gimbaled

Gimbals allow arrays to point toward the Sun while reducing the need to rotate the spacecraft.

## Design Drivers

- Sun distance
- Radiation environment
- Thermal environment
- Micrometeoroids

---

## Solar-Cell Semiconductor Physics

Solar cells are made from semiconductor materials such as silicon.

They use doped layers with different electrical properties.

### P-Type

Contains positive charge carriers represented as excess **holes**.

### N-Type

Contains additional electrons.

When photons strike the cell:

- Electrons are excited.
- Electron-hole pairs form.
- Charge separation produces current when the circuit is connected.

---

## Multi-Junction Solar Cells

Multi-junction cells use multiple semiconductor layers to absorb different wavelength regions.

Advantages:

- Uses more of the solar spectrum
- Higher efficiency

Considerations:

- Heat sensitivity
- Greater complexity
- Higher cost

---

## Solar-Array Current-Voltage Curve

The solar-array I/V curve describes output current as a function of output voltage.

### Short-Circuit Current

`Isc` is the maximum current produced when the output is shorted.

At this condition:

```math
V = 0
```

### Open-Circuit Voltage

`Voc` is the maximum voltage when no load is connected.

At this condition:

```math
I = 0
```

### Maximum Power Point

The **MPP**, also called `Pmax`, is the point where output power is maximized.

```math
P = IV
```

The MPP is the most efficient operating condition for the solar array.

### Environmental Effects

More sunlight shifts the I/V curve upward.

Lower temperature shifts the curve toward higher voltage.

The lecture summarizes this as:

> Solar panels like cold and sunny conditions.

---

# 6. Solar Array Performance and Sizing

> **Source: Slide 13**

Solar-array output depends on several factors.

## Solar Irradiance

Representative solar flux:

```math
S_0 \approx 1370\ \frac{W}{m^2}
```

Solar flux scales with distance from the Sun according to the inverse-square relationship:

```math
S(R) = S_0\frac{1}{R^2}
```

where `R` is measured in AU.

---

## Solar-Cell Efficiency

Representative efficiency:

```text
~30%
```

depending on cell manufacturer and design.

---

## Cosine Loss

Solar-array output decreases when sunlight is not normal to the panel.

The cosine factor accounts for solar-incidence angle.

---

## Packing Factor

Packing factor is:

```math
\text{Packing Factor}
=
\frac{\text{Total Cell Area}}{\text{Total Panel Area}}
```

Representative value:

```text
~88%
```

---

## Beginning-of-Life Effects

Representative factors:

- Workmanship: ~98%
- Wiring losses: ~96%

## End-of-Life Effects

Representative factors:

- Radiation: ~94%
- UV: ~98.5%
- Micrometeoroids: ~99.5%

## Array Size

Array area is determined from:

```text
Number of panels × area per panel
```

---

## Solar-Array Power Equation

The lecture combines these effects into:

```math
P_{\text{array}}
=
S_0
\left(\frac{1}{R^2}\right)
\eta_{\text{cell}}
L_{\cos}
PF
F_{\text{BOL}}
F_{\text{EOL}}
A_{\text{array}}
```

where:

- `S0` = reference solar flux
- `R` = Sun-spacecraft distance in AU
- `ηcell` = cell efficiency
- `Lcos` = cosine-loss factor
- `PF` = packing factor
- `FBOL` = beginning-of-life factor
- `FEOL` = end-of-life factor
- `Aarray` = solar-array area

---

# 7. Radioisotope Thermoelectric Generators

> **Source: Slide 14**

RTGs generate electrical power from radioactive decay.

A representative fuel is:

```text
Plutonium-238
```

The decay produces heat, and thermoelectric materials convert a temperature difference into electrical voltage and power.

## Typical Applications

RTGs are commonly used for:

- Deep-space missions
- Landers with long eclipses
- Missions with long winter seasons

Representative power:

```text
~200–300 W
```

RTG output is relatively steady-state, so batteries may be required for power surges.

## Example Missions

- Cassini
- New Horizons
- Mars Science Laboratory
- Mars 2020

## Design Drivers

- Nuclear regulations
- Ground handling
- Contamination risk in failure scenarios
- Thermoelectric degradation
  - Approximately 1–2% per year
- Thermal management

Waste heat can sometimes be used by the spacecraft thermal system.

---

## GPHS-RTG Example

The lecture gives:

- Used on Cassini, Galileo, and Ulysses
- Mass: 56 kg
- Length: 113 cm
- Diameter: 43 cm
- Plutonium load: 10.9 kg
- Thermal power: 4394 W
- Electrical power at launch: 296 W
- Electrical power at end of mission: 209 W

This example illustrates the relatively low electrical conversion efficiency of RTGs compared with their thermal output.

---

# 8. Energy Storage Overview

> **Source: Slides 15–16**

Energy storage supplies spacecraft loads when the primary generation source cannot provide enough power.

Examples:

### Solar-Powered Spacecraft

Storage is needed during:

- Orbital eclipses
- Nighttime for surface missions

### RTG-Powered Spacecraft

The battery can supplement the RTG during loads that exceed its steady power capability.

---

## Energy-Storage Technologies

### Batteries

Most common.

Convert chemical energy to electrical energy.

Can be:

- One-time use
- Rechargeable

### Fuel Cells

Convert chemical energy continuously while fuel and oxidizer are supplied.

### Flywheels

Store energy mechanically in a rotating mass.

Can support short-duration applications.

### Supercapacitors

Store energy electrostatically.

Useful for:

- Rapid charge/discharge
- High peak loads

## Design Considerations

- Energy density
- Number of charge/discharge cycles
- Eclipse/off-Sun duration
- Thermal environment

---

# 9. Batteries

> **Source: Slide 17**

The lecture presents a historical progression of spacecraft battery technologies.

## Lead-Acid

- Low cost
- Reliable
- Heavy
- Low energy density
- Used in early spacecraft

## Nickel-Cadmium

- Improved energy density
- Improved thermal properties
- Used in early crewed missions

## Nickel-Hydrogen

- Improved energy density
- Long cycle life
- Better thermal stability
- Used in long-duration missions

## Lithium-Ion

- Significantly higher energy density
- Lower mass
- Common in modern spacecraft

## Lithium-Polymer

- Lightweight alternative to Li-ion
- Used in small satellites and CubeSats

## Nickel-Metal Hydride

- Improved performance over NiCd
- High discharge rates
- Intermediate cost/performance option

## Solid-State Batteries

- Potential for higher energy density
- Improved safety
- Still experimental according to the lecture

---

# 10. Battery Sizing and Energy Equations

> **Source: Slide 18**

## Battery Capacity

Battery capacity in ampere-hours describes current delivery over time.

```math
C_{\text{battery}}(Ah)
=
I(A)t(hr)
```

Example:

```math
40\ A \times 2\ hr = 80\ Ah
```

---

## Stored Battery Energy

Stored energy depends on capacity and voltage.

```math
E_{\text{battery}}(Wh)
=
C_{\text{battery}}(Ah)V(V)
```

Example:

```math
80\ Ah \times 12\ V = 960\ Wh
```

---

## Load Energy

```math
E_{\text{load}}(Wh)
=
P_{\text{load}}(W)t(hr)
```

---

## Depth of Discharge

Depth of discharge is the percentage of battery capacity removed during discharge.

```math
DoD(\%)
=
\frac{E_{\text{load}}}{E_{\text{battery}}}
\times 100
```

Equivalently:

```math
DoD(\%)
=
\frac{C_{\text{used}}}{C_{\text{battery}}}
\times 100
```

Example:

```text
75% DoD → 25% capacity remaining
```

---

## Battery Drain for Recharge

The lecture defines the required recharge power as:

```math
P_{\text{recharge}}
=
\frac{E_{\text{load}}}
{\eta_{\text{discharge}}
\eta_{\text{recharge}}
t_{\text{recharge}}}
```

Representative efficiencies:

- Discharge efficiency: ~90%
- Recharge efficiency: ~80%

The available recharge time depends on how long the solar array is producing sufficient power.

---

# 11. Other Energy Storage Options

> **Source: Slide 19**

## Fuel Cells

Convert chemical energy to electrical energy through electrochemical reactions.

Typical reactants:

- Hydrogen
- Oxygen

Water is produced as the byproduct.

### Advantages

- High efficiency
- Low emissions
- Reliable power over extended periods

### Disadvantages

- Continuous fuel/oxidizer supply required
- Storage and management complexity

### Applications

- Apollo
- ISS

---

## Flywheels

Store kinetic energy in a high-speed rotating mass.

### Advantages

- High efficiency
- Long life

### Disadvantages

- Mechanical wear
- Thermal dissipation

The lecture notes that spacecraft flywheel energy storage has largely remained in studies.

---

## Supercapacitors

Store energy electrostatically rather than chemically.

### Advantages

- High power density
- Rapid charging
- Rapid discharging
- Long cycle life

### Disadvantages

- Low energy density
- High cost

### Applications

- BepiColombo
- Mars Exploration Rovers

---

# 12. Power Control Overview

> **Source: Slides 20–21**

Power control:

- Converts generated power into usable spacecraft power
- Provides switching to spacecraft components
- Controls battery charge/discharge

Three major functions are:

1. Power regulation
2. Power distribution
3. Energy management

---

## Power Regulation

- Regulates the spacecraft power bus
- Provides stable and deterministic operation
- Converts voltage to levels required by spacecraft devices
- Protects against overload conditions

## Power Distribution

- Provides switching to spacecraft loads
- Isolates loads so a fault cannot damage the rest of the bus

## Energy Management

- Provides closed-loop battery charging/discharging
- Uses hardware and FSW
- Protects against battery overcharge

---

# 13. Power Regulation

> **Source: Slides 22–23**

Most spacecraft operate using **DC power**.

## Regulated Bus

Output voltage is maintained approximately constant.

### Advantages

- Stable
- Deterministic
- Better for sensitive electronics

### Disadvantages

- More complex
- Requires regulators
- Conversion introduces efficiency losses

---

## Unregulated Bus

Voltage changes with:

- Source conditions
- Solar-array output
- Battery voltage
- Spacecraft load

### Advantages

- Simpler
- Highly efficient

### Disadvantages

- Non-deterministic
- More difficult to monitor
- Potentially harmful to sensitive devices

---

## Typical Bus Voltages

Representative spacecraft bus:

```text
28–32 V
```

Some systems use:

```text
up to ~100 V
```

particularly electric-propulsion systems.

Individual instruments may require lower voltages such as:

```text
5 V
12 V
```

Power converters may be:

- Standalone boxes
- Embedded in devices

---

## Array Power Regulator

Monitors:

- Voltage
- Current

Functions:

- Controls solar-array output
- Protects against overloads
- Sized for maximum expected array power

## Battery Charge/Discharge Regulator

Monitors battery voltage/current and:

- Controls output
- Keeps charge/discharge current safe
- Protects against overload
- Is sized by voltage and output-power rating

## Error Amplifier

Compares:

- Reference voltage
- Feedback voltage

The difference is amplified as the error signal.

These regulation functions are commonly incorporated into the **PCU**.

---

# 14. Solar Array Power Control

> **Source: Slide 24**

Solar-array power can be controlled using:

- Direct Energy Transfer
- Peak Power Tracking

## Direct Energy Transfer

DET transfers power directly from the solar array to the load without intermediate conversion.

Unused power must be dissipated, for example through shunts that connect/disconnect array sections.

### Advantages

- Simple
- Highly efficient

### Disadvantages

- Less optimal
- Variable output

### Applications

Best suited to missions with relatively continuous power demand.

Examples:

- Lunar Reconnaissance Orbiter
- Mars Exploration Rovers

For MER, DET is used during daylight and batteries at night.

---

## Peak Power Tracking

PPT uses converters to dynamically change the electrical load on the solar array so that it operates near the MPP.

### Advantages

- Maximizes captured solar power

### Disadvantages

- More complex
- Conversion introduces efficiency losses

### Applications

Useful when power availability or demand changes significantly.

Examples:

- Dawn
- Juno
- Solar Probe

The lecture's analogy compares DET to riding a bicycle in one fixed gear and PPT to using gears to remain near the most efficient operating point.

---

# 15. Power Distribution

> **Source: Slide 25**

The **Power Distribution Unit** typically distributes electrical power across the spacecraft.

The PDU:

- Accepts power from solar array or battery
- Converts voltage when required
- Provides switched power outputs to devices
- Provides protection

Power switches can be implemented using:

- Relays
- Field-effect transistors (FETs)

---

## Relays

An electromagnet mechanically opens or closes the circuit.

### Advantages

- Simple
- Robust

### Disadvantages

- Slow switching
- Higher mass
- Mechanical position can be affected by shock/vibration

---

## FETs

A semiconductor controls current flow using an electric field.

Voltage on the gate controls current between source and drain.

### Advantages

- Fast switching
- Lightweight
- Durable
- No moving parts

### Disadvantages

- More complex
- Can be susceptible to failures such as radiation events

---

## Protection

Power distribution hardware can provide:

- Overvoltage protection
- Overcurrent protection
- Fusing

The PDU and PCU are often combined into a:

```text
PCDU
```

Power Conditioning and Distribution Unit.

---

# 16. Energy Management

> **Source: Slide 26**

Solar-array energy is conditioned by the PCU before charging the battery.

PCU electronics and FSW regulate charging by:

- Monitoring battery voltage
- Monitoring state of charge
- Determining when charging starts/stops
- Monitoring current
- Adjusting charge rate
- Monitoring battery temperature

---

## Battery-Charging Phases

### Bulk Charge

Battery is charged at constant current until a set voltage is reached.

### Absorption Charge

Battery voltage is held constant while current gradually decreases as the battery approaches full charge.

### Trickle Charge

Battery is charged using a low constant current to maintain charge without overcharging.

---

## Safety Considerations

### Overcharge Protection

Prevents the battery from exceeding safe voltage.

### Thermal Management

Prevents:

- Overheating
- Thermal runaway

The battery is generally maintained below its absolute maximum voltage to improve lifetime.

The lecture also notes that battery voltage and state of charge are not identical measures. Voltage depends on temperature, load, internal resistance, and other factors.

For LEO spacecraft, the battery repeatedly charges in sunlight and discharges during eclipse.

---

# 17. Electrical Isolation

> **Source: Slides 27–28**

Electrical isolation prevents unwanted electrical connections and interference.

It is a critical reliability function because it:

- Protects against high voltage
- Prevents ground loops
- Reduces noise
- Reduces interference between circuits

## Isolation Methods

### Physical Separation

Keep high-voltage and low-voltage systems physically separated.

### Isolation Barriers

Use:

- Coatings
- Enclosures
- Other physical barriers

### Transformers

Transfer energy through electromagnetic induction while electrically isolating circuits.

### Optocouplers

Transfer information/energy across an isolation boundary using light.

---

# 18. Grounding

> **Source: Slide 29**

Grounding establishes:

- A common electrical reference
- A path for current/fault energy to dissipate

It supports:

- Electrical safety
- EMI reduction
- Fault-current dissipation

## Single Point Ground

An SPG establishes one common ground reference, typically at spacecraft structure.

The purpose is to:

- Prevent ground loops
- Minimize potential differences

---

## Hard Ground

Uses a low-resistance connection to the SPG.

### Advantages

- Stable reference
- Reliable
- Good fault-current dissipation

### Disadvantages

- Inflexible
- More susceptible to noise/ground-loop interference

### Applications

- Power distribution
- Safety systems

---

## Soft Ground

Uses a high-resistance connection to the SPG.

### Advantages

- Flexible
- Reduces noise and interference

### Disadvantages

- Poorer fault-current dissipation

### Applications

- Sensitive circuits
- Circuits requiring isolation from high voltage

---

## Floating Ground

Completely isolated from the SPG.

Isolation can use:

- Transformers
- Optocouplers

### Advantages

- Strong noise/interference isolation

### Disadvantages

- Reference can vary significantly
- Poor fault-current dissipation

### Applications

Sensitive circuits requiring high-voltage isolation.

---

# 19. EMI and EMC

> **Source: Slide 30**

## Electromagnetic Interference

EMI is disturbance to electronics caused by electromagnetic energy.

### Conducted EMI

Travels through conductive paths/direct electrical connections.

### Radiated EMI

Propagates through space without a direct conductive connection.

### Internal Sources

Examples:

- Motors
- Power supplies
- Digital circuits
- Devices switching on/off

### External Sources

Examples:

- Solar flares
- Cosmic radiation
- Other spacecraft

---

## Electromagnetic Compatibility

EMC is the ability of a device to function without:

- Causing unacceptable interference
- Being unacceptably affected by interference

### Emissions

Limits the EMI produced by the device.

The device is the **source**.

### Susceptibility

Ensures the device can tolerate EMI.

The device is the **victim**.

---

## EMI/EMC Design Methods

- Physical separation
- Shielding
- Separate wiring
- Filtering
- Grounding

The lecture summarizes an EMI problem as three elements:

```text
Noise Source
     ↓
Coupling Mechanism
     ↓
Victim Circuit
```

Examples of coupling mechanisms include:

- Shared power lines
- Close proximity
- Ground noise

Poor shielding, missing filters, and poor grounding increase susceptibility.

---

# 20. Power Subsystem Design Process

> **Source: Slides 31–38**

The lecture presents the EPS lifecycle from requirements through spacecraft operation.

```text
Define Requirements
↓
Define Architecture
↓
Select Hardware + Develop FSW
↓
Build, Integrate, and Test
↓
Deliver to Spacecraft ATLO
↓
Operate Spacecraft
```

---

## Phase A — Requirements

Develop Level-4 EPS requirements from Level-3 flight-system requirements.

Examples:

**Single-fault tolerance**
- Drives redundancy
- Drives protective features

**Produce 600 W at 5 AU**
- Drives solar-array sizing

**Accommodate a 1-hour eclipse**
- Drives battery sizing

**Provide a 31-V regulated bus**
- Drives PCU design

**Provide switching to 10 science instruments**
- Drives PDU design

---

## Phase B/C — Architecture

Perform key architecture trades and sizing analyses:

- Redundancy
- Solar-array sizing for maximum operational power at EOL
- Battery sizing for:
  - Launch
  - Eclipse
  - Safe mode
- Harness sizing for peak load
- Power-switch type
- Electrical isolation
- Grounding

---

## Phase B/C — Detailed Design

Select hardware such as:

- Solar array
- Battery
- PCU
- PDU

Develop FSW for:

- Battery-charging logic
- Fault monitoring

The lecture emphasizes iteration between requirements, architecture, hardware selection, and software design.

---

## Phase D — Build and Test

Power-subsystem build and integration includes:

- Fabricate/procure PCU and PDU electronics
- Procure solar array
- Procure battery
- Assemble electronics
- Perform functional testing with solar-array and battery test equipment
- Perform qualification testing
  - Mechanical
  - Thermal

---

## Phase D — Delivery and ATLO

Deliver engineering models into testbeds for system-level verification and validation.

This includes testing with:

- Avionics
- Flight software

Flight hardware—including solar array and battery—is delivered to spacecraft ATLO.

Activities include:

- Integration
- Functional testing
- Environmental testing
- Hardware/software troubleshooting
- Rework as needed

A test battery is often used during ATLO to reduce risk to the flight battery.

---

## Phase E — Operations

Operate the EPS during:

- Launch
- Cruise
- Science operations

Trend hardware data including:

- Solar-array temperature
- Solar-array voltage/current
- Battery temperature
- Battery voltage/current
- Device power/current
- Power-switch state

Perform FSW updates as required.

---

# 21. Europa Clipper Case Study

> **Source: Slides 39–40**

Europa Clipper uses two battery-inhibit mechanisms.

## Battery Arm Plugs

When installed, they complete the circuit and allow the batteries onto the power bus.

## Battery Discharge Interrupt Switches

These switches can be held **OPEN** when continuously driven by ground-support equipment, keeping the spacecraft powered off.

They also autonomously open during extreme bus undervoltage.

---

## Operational Consequence

Previous missions such as Mars 2020 and MSL used latching relays that could be pulsed open or closed without continuous electrical power.

For Europa Clipper:

1. Battery Arm Plugs had to be installed before encapsulation and stacking on Falcon Heavy.
2. After fairing encapsulation, the plugs could no longer be accessed.
3. Once installed, the spacecraft required continuous ground support to maintain the desired battery-disconnect state.
4. The ATLO team therefore required 24/7 monitoring for days before launch.
5. During Hurricane Milton, team members had to monitor the GSE so the Battery Discharge Interrupt Switches remained open and Europa Clipper stayed powered off.

The lecture notes that latching relays could instead have been pulsed open, allowing the team to evacuate safely until the hurricane passed.

This case demonstrates how a seemingly small power-switching architecture decision can create major consequences for:

- Ground operations
- Safety
- Staffing
- Launch-site procedures
- Fault management

---

# 22. Lecture Summary

> **Source: Slides 1–40**

The Electrical Power Subsystem provides generation, storage, conditioning, regulation, distribution, protection, and management of spacecraft electrical power.

A representative architecture is:

```text
Power Generation
      ↓
Power Conditioning
      ↕
Energy Storage
      ↓
Power Bus
      ↓
Power Distribution
      ↓
Spacecraft Loads
```

Power generation commonly uses:

- Solar arrays
- RTGs

Solar-array performance depends on:

- Sun distance
- Cell efficiency
- Incidence angle
- Packing factor
- BOL losses
- EOL degradation
- Array area

The lecture's solar-array sizing relationship is:

```math
P_{\text{array}}
=
S_0
\left(\frac{1}{R^2}\right)
\eta_{\text{cell}}
L_{\cos}
PF
F_{\text{BOL}}
F_{\text{EOL}}
A_{\text{array}}
```

Energy storage is most commonly provided by batteries, although fuel cells, flywheels, and supercapacitors have specialized applications.

Battery sizing requires understanding:

- Ampere-hour capacity
- Stored watt-hours
- Load energy
- Depth of discharge
- Charge/discharge efficiency
- Recharge time

Key relationships include:

```math
C = It
```

```math
E_{\text{battery}} = CV
```

```math
E_{\text{load}} = Pt
```

```math
DoD
=
\frac{E_{\text{load}}}{E_{\text{battery}}}
```

Power control consists of:

- Regulation
- Distribution
- Energy management

The PCU manages source and battery power. The PDU switches and protects spacecraft loads. These may be combined into a PCDU.

Solar-array regulation can use:

- Direct Energy Transfer
- Peak Power Tracking

DET is simpler and highly efficient but less optimal. PPT is more complex but keeps the array near maximum power under changing conditions.

Battery energy management requires:

- Controlled charging
- State-of-charge monitoring
- Voltage/current monitoring
- Temperature monitoring
- Overcharge protection
- Thermal-runaway protection

Electrical isolation, grounding, and EMI/EMC are reliability functions—not secondary details. They prevent faults and noise from propagating through the spacecraft.

The EPS design process progresses through:

```text
Requirements
↓
Architecture
↓
Hardware + FSW Design
↓
Build and Qualification
↓
Spacecraft Integration / ATLO
↓
Flight Operations
```

Mission requirements drive concrete design choices. Sun distance drives array sizing, eclipses drive battery sizing, bus-voltage requirements drive PCU design, load counts drive PDU design, and fault-tolerance requirements drive redundancy and protection.

The Europa Clipper case study reinforces the systems-engineering lesson: power architecture affects not only electrical performance but also ground operations, safety, test procedures, and launch-site staffing.
