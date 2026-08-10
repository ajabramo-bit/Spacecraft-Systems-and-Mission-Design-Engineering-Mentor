# ASTE-331a: Introduction to Space Systems

**Course:** ASTE-331a: Spacecraft Systems Engineering  
**Lecture:** Introduction to Space Systems  
**Date:** August 29, 2025  
**Instructors:** Jim Chase, Danielle Marsh  
**Source:** `331_01_SpaceSystemsIntro_20250829.pdf`

---

## Lecture Overview

This lecture introduces spacecraft systems engineering, walks through the conceptual design of NASA's GRAIL mission, provides an overview of major spacecraft subsystems, and introduces mission requirements flow-down.

### Main Topics

1. **Spacecraft Systems Engineering**
2. **GRAIL Conceptual Design**
3. **Overview of Spacecraft Subsystems**
4. **Mission Requirements Flow-Down**

---

# 1. Spacecraft Systems Engineering

## What Is a System?

A system is a collection of elements that work together to perform one or more functions.

A space system can contain many interconnected elements, including spacecraft, payloads, ground systems, launch systems, and mission operations.

Systems engineering involves:

- Planning
- Developing
- Integrating
- Testing
- Launching
- Operating space systems

Because space systems involve many different technical disciplines and organizations, systems engineering requires coordination across a broad range of engineering and management activities.

## What Do Systems Engineers Do?

Systems engineers are responsible for helping create successful systems.

Their responsibilities include:

- Developing the system concept
- Defining system architecture
- Designing the system
- Analyzing complexity and risk
- Determining how to measure whether the system works as intended
- Coordinating different elements of the system

---

## System Design & Development

A system:

- Satisfies stakeholder requirements
- Is organized as a hierarchy of subsystems and lower-level elements
- May itself be part of a larger "super-system"

### Functional Decomposition

The definition of a system—including its functions, interfaces, and lower-level subsystems—is called **functional decomposition**.

System design addresses:

- Component architecture
- Interfaces
- Constraints
- End-to-end system behavior

System development includes the activities required to produce and integrate the resulting product.

---

## Typical Space Project Organization

A typical space project can include:

- Project / Science Management
- Payload System
- Flight System
- Mission System
- Launch System
- Ground Data System
- Mission Operations
- Launch Vehicle
- Launch Services
- Bus Integration & Test

### Spacecraft / Bus Elements

A spacecraft bus can include:

- Propulsion
- Guidance, Navigation & Control (GN&C)
- Telecommunications
- Command & Data Handling (C&DH)
- Power
- Mechanical
- Thermal

Systems engineering exists at each level of the project organization.

---

# 2. GRAIL Conceptual Design

## Mission Background

The **Gravity Recovery and Interior Laboratory (GRAIL)** was a lunar science mission in NASA's Discovery Program.

The mission used high-quality measurements of the Moon's gravitational field to determine its interior structure.

GRAIL consisted of two small spacecraft.

The spacecraft:

- Launched on September 10, 2011
- Used a Delta II launch vehicle
- Cruised for approximately 3–4 months
- Entered lunar orbit approximately 25 hours apart
- Conducted science operations around the Moon
- Impacted the lunar surface on December 17, 2012

---

## GRAIL Study Objectives

The initial study objectives included:

- Determine whether a lunar gravity-mapping mission was feasible
- Develop a lower-risk and lower-cost mission
- Coordinate with the scientific team

### Major Constraints

The study attempted to:

- Minimize risk
- Avoid new technologies
- Maintain robust mass and power margins
- Stay within a cost cap of approximately $425 million
- Launch no earlier than January 2012
- Complete development in approximately 4–5 years
- Conduct approximately 3–6 months of operations

---

## GRAIL Science Objectives

The mission objectives included:

1. Determine the structure of the lunar interior from crust to core.
2. Improve understanding of the thermal evolution of the Moon.
3. Apply knowledge of the Moon's internal structure and thermal evolution to other terrestrial planets.
4. Produce a detailed lunar gravity field useful for future scientific and exploration objectives.

---

## Basic Concept of Operations

The GRAIL mission concept consisted of:

1. **Launch**
2. **Cruise**
3. **Lunar Orbit Insertion**
4. **Science Operations at the Moon**
5. **Decommission / Impact**

The spacecraft operated in approximately 50 × 50 km polar lunar orbits.

The two spacecraft maintained a separation distance of approximately 50–500 km during the early concept.

Communication with Earth used the Deep Space Network (DSN).

---

## GRAIL Payload

Each spacecraft carried an enhanced **Ka-Band Ranging & Instrument Assembly** based on the GRACE KBR instrument.

The instrument used Ka-band radio frequency measurements to precisely determine the distance between the two spacecraft.

### Payload Requirements

Approximate payload characteristics:

- Mass: 15 kg
- Power: 15 W
- Pointing control: 0.25°
- Pointing knowledge: 200 arcsec
- Data rate: 10 MB/day

The two spacecraft needed to point toward one another to support the ranging measurement.

---

## Mission Design

The mission design included several major trades.

### Earth Escape vs. Staging

Two options were considered:

**Earth Escape**
- Launch vehicle insertion directly toward lunar rendezvous

**Staging**
- Launch vehicle insertion into a high Earth orbit
- Multiple chemical burns to spiral outward toward lunar rendezvous

### Direct Insertion vs. Low Energy

Two approaches were considered:

**Direct Insertion**
- Lunar orbit insertion followed by burns to reach the final lunar orbit

**Low Energy**
- Use of a low-energy trajectory involving Lagrangian points
- Eventually transition to the final lunar orbit

---

## Propulsion Trades

Questions included:

- Integrated propulsion system or separate system?
- Bipropellant or monopropellant?
- Which launch vehicle should be used?

The mission considered launch vehicles including:

- Taurus 3113
- Delta II

---

## Mission Operations

The concept included:

- Two spacecraft
- Approximately 50 × 50 km polar lunar orbits
- Approximately 113-minute orbital period
- Approximately 50 km spacecraft separation
- Approximately 3 months of operations
- Continuous tracking while on the lunar near-side
- Approximately 10 MB/day downlink
- 34-m DSN antenna

---

# 3. Overview of Spacecraft Subsystems

The lecture introduces the major spacecraft subsystems and explains their functions, drivers, trades, and important parameters.

---

## 3.1 Propulsion

### Function

Provides thrust for:

- Trajectory maneuvers
- Often, attitude control

The primary driver is typically the trajectory and corresponding **ΔV budget**.

### GRAIL Example

- 1 × 22-N thruster
- 8 × 0.8-N thrusters
- Warm gas generator
- Fuel tank
- Miscellaneous hardware
- Total mass: approximately 15 kg

### Common Components

- Chemical propulsion
  - Monopropellant
  - Bipropellant
- Fuel tanks
- Thrusters
- Solid rocket motors
- Electric propulsion systems

### Key Trades

- Propulsion type
- Thruster sizing
- Fuel tank sizing
- Heritage from previous systems

### Key Parameters

- Mass
- Power
- Cost
- Thruster specific impulse (Isp)
- Thruster locations
- Cant angles
- Propellant load
- Margins

---

# 3.2 Attitude Control System (ACS)

### Function

Provides:

- Attitude control
- Attitude knowledge
- Stability

These functions support spacecraft pointing.

Pointing requirements can be driven by:

- Science instruments
- Trajectory maneuvers
- Telecommunications
- Thermal requirements

ACS may also be called:

- GNC
- ADCS
- AOCS

### GRAIL Example

- 1 × star tracker
- 3 × reaction wheels
- 1 × inertial measurement unit (IMU)
- 1 × sun sensor
- Total mass: approximately 5 kg

### Common Components

**Sensors**
- Sun sensors
- Magnetometers
- Gyros
- GPS receivers
- Star trackers

**Control Effectors**
- Reaction wheels
- Momentum wheels
- Control moment gyros
- Magnetic torquers
- Reaction control thrusters

### Key Trades & Analyses

- 3-axis control vs. other approaches
- Reaction wheels vs. thrusters
- Control analysis
- Knowledge analysis
- Stability analysis
- Error budgets
- Heritage from prior systems

### Key Parameters

- Mass
- Power
- Cost
- Pointing control
- Pointing knowledge
- Stability / jitter

---

# 3.3 Telecommunications

### Function

Provides communication:

- To the spacecraft
- From the spacecraft

Communication is typically with Earth, but can also occur between spacecraft.

Telecommunications can occasionally support radio science.

The primary driver is typically spacecraft-to-Earth distance.

### GRAIL Example

- S-band transponder
- Diplexer
- Low-gain antenna (LGA)
- Miscellaneous hardware
- Total mass: approximately 5 kg

### Common Components

- Radio / transponder
- Amplifier
- Antennas:
  - High-gain antenna (HGA)
  - Medium-gain antenna (MGA)
  - Low-gain antenna (LGA)

### Key Trades & Analyses

- Fixed vs. articulated antennas
- Data rate and volume analysis
- Link budget
- Antenna sizing
- Radio band
- Power level
- Heritage from prior systems

### Key Parameters

- Mass
- Power
- Cost
- Transmission power
- Data rate / data volume
- Margin

---

# 3.4 Command & Data Handling (C&DH)

### Function

Provides spacecraft:

- Command and control
- Internal data handling

C&DH includes flight software (FSW), including boot and reset functionality.

The primary drivers are typically:

- Redundancy
- Interfaces
- Complexity of downstream components
- Payload requirements

C&DH may also be called the **Flight Computer**.

### GRAIL Example

- Rad750 processor
- Interface cards
- Converters
- Backplane
- Chassis assembly
- Total mass: approximately 5 kg

### Common Components

- Electronics box / chassis
- Processor
- Payload interface cards
- Data interface cards
- Memory

Depending on system complexity, these functions may be contained within one box or multiple boxes.

### Key Trades & Analyses

- Functional block diagram
- Interface types
  - 1553
  - LVDS
  - RS-422
  - etc.
- Onboard memory storage
- CPU utilization
- Radiation shielding
- Heritage from prior systems

### Key Parameters

- Mass
- Power
- Cost

---

# 3.5 Electrical Power System (EPS)

### Function

Provides electrical power and distributes it throughout the spacecraft.

### Primary Drivers

- Sun-spacecraft distance
- Power profiles during science operations
- Power profiles during telecommunications
- Launch conditions for battery sizing
- Redundancy

EPS is often grouped with C&DH under **Avionics**.

### GRAIL Example

- Power electronics
- Interface cards
- Converters
- 1 × 30 Ah battery
- 2 × solar arrays
- Total mass: approximately 30 kg

### Common Components

**Generators**
- Solar arrays
- Radioisotope thermoelectric generators (RTGs)

**Storage**
- Fuel cells
- Primary batteries
- Secondary batteries

**Power Processing**
- Voltage regulation
- Current distribution

### Key Trades & Analyses

- Solar arrays vs. RTGs
- Battery type
- Array sizing
- Battery sizing
- Power equipment list (PEL)
- Power analysis
- Heritage from prior systems

### Key Parameters

- System power loads
- Power profiles
- Power margins
- Worst-case depth of discharge

---

# 3.6 Thermal

### Function

Provides appropriate thermal control throughout the spacecraft.

The primary driver is the overall thermal model.

The thermal model considers temperatures from:

- Avionics
- Instruments
- Batteries
- Mechanisms
- Propulsion

All components must remain within their qualification temperature limits.

### GRAIL Example

- Paint and films
- Multi-layer insulation (MLI)
- Instrument thermal mass plate
- Heaters
- Thermostats
- Sensors
- Total mass: approximately 10 kg

### Common Components

**Surface coatings / treatments**
- Films
- Paints
- MLI

**Conductors and insulators**

**Heat transfer regulators**
- Heat pipes
- Louvers
- Phase-change devices
- Heat switches

### Key Trades & Analyses

- Active vs. passive thermal control
- Thermal analysis
- Radiator design
- Radiator locations
- Thermal margins

### Key Parameters

- Mass
- Power
- Cost
- Updated attitude profile

---

# 3.7 Mechanical

### Function

Provides spacecraft structure and supports:

- Spacecraft
- Payload
- Mechanisms
- Separation systems

Primary drivers include:

- Spacecraft type
- Payload
- Dry and wet mass
- Articulated arrays
- Antennas
- Instruments

Mechanical is also called **Structure & Mechanisms**.

It may also include the harness / wiring.

### GRAIL Example

- 4 side panels
- Propulsion and payload panels
- Tank support
- Fittings
- Solar array deployment mechanism
- Launch vehicle separation system
- Total mass: approximately 35 kg

### Common Components

**Primary structure**
- Core structure
- Panels

**Secondary structure**
- Tank support
- Fittings
- Payload support
- Booms

**Other**
- Payload elements
- Mechanisms
- Launch vehicle and spacecraft adapters

### Key Trades & Analyses

- Configuration
- CAD
- Field-of-view (FOV) design
- Loads analysis
- Stiffness analysis
- Master equipment list
- Mechanism analysis
- Torque analysis

### Key Parameters

- Mass
- Power
- Cost

---

# 4. Mission Requirements Flow-Down

## What Is a Requirement?

A requirement is a singular documented physical or functional need that a particular design, product, or process aims to satisfy.

In aerospace, requirements help map the system hierarchy to the functions needed to accomplish mission objectives.

Requirements are generally written using **"shall" statements**:

> The XYZ shall...

---

## Example Requirements Flow-Down

A mission objective can be progressively decomposed into lower-level requirements.

### Level 1 — Mission

**The Mission shall achieve an Earth orbit that supports the science requirements.**

↓

### Level 2 — Project

**The Project shall place an Orbiter in a 500 km, geocentric Earth orbit.**

↓

### Level 3 — Spacecraft

**The Spacecraft shall provide a total ΔV capability of 1,000 m/s.**

↓

### Level 4 — Component

**The propellant tank shall store 100 kg of propellant.**

The key idea is that higher-level requirements are progressively decomposed into more specific requirements at lower levels.

---

## Why Requirements Are Used

Requirements are used to:

- Understand the end-to-end design before hardware exists
- Communicate between customers and suppliers
- Protect system capability and margins
- Define interfaces
- Establish contractual expectations
- Ensure institutional best practices

Requirements can also establish margins between what is actually needed and what the system is designed to provide.

For example:

- Actual need: 900 m/s ΔV
- Spacecraft requirement: 1,000 m/s ΔV

The additional capability provides margin.

---

## When Are Requirements Written?

Requirements are typically written for:

- New developments
- New system capabilities
- Existing hardware, where requirements describe its operation

Requirements development generally continues until there are no additional new development items in the system description.

---

## Why Verify Requirements?

Requirements are verified to:

- Ensure the system meets its specified requirements
- Understand the degree to which the system meets those requirements

---

# 5. Requirements Hierarchy

The lecture presents a hierarchy of requirements:

```text
L1  Program / Sponsor
        ↓
L2  Project
        ↓
L3  System
        ↓
L4  Subsystem
        ↓
L5  Assembly / Software