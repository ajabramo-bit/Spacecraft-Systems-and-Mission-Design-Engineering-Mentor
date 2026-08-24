# Mechanical Subsystem

**Course:** ASTE-331a — Spacecraft Systems Engineering  
**Lecture:** 07 — Mechanical Subsystem  
**Instructors:** Jim Chase, Danielle Marsh   
**Source:** `331_07_Mechanical_20251114.pdf`

---

## Lecture Overview

This lecture introduces spacecraft mechanical systems, including primary, secondary, and tertiary structure; mechanisms and deployables; spacecraft configuration; materials selection; launch and on-orbit mechanical environments; mass estimation; structural trade studies; structural analysis and test; and the mechanical subsystem design process.

The lecture uses an asteroid sample-return spacecraft as a running configuration example and concludes with the Beagle 2 deployment failure as a case study in mechanisms, redundancy, testing, and system-level dependencies.

---

## Table of Contents

- [1. Mechanical Subsystem Overview](#1-mechanical-subsystem-overview)
- [2. Asteroid Sample Return Mission Example](#2-asteroid-sample-return-mission-example)
- [3. Mechanical Constraints and Drivers](#3-mechanical-constraints-and-drivers)
- [4. Requirements Flowdown](#4-requirements-flowdown)
- [5. Common Mechanical and Structural Requirements](#5-common-mechanical-and-structural-requirements)
- [6. Mechanical Subsystem Design](#6-mechanical-subsystem-design)
- [7. Common Spacecraft Structures](#7-common-spacecraft-structures)
- [8. Materials Selection](#8-materials-selection)
- [9. Composite Materials](#9-composite-materials)
- [10. Mechanisms and Deployables](#10-mechanisms-and-deployables)
- [11. Configuration Considerations](#11-configuration-considerations)
- [12. Loads and Environments](#12-loads-and-environments)
- [13. Launch Accelerations](#13-launch-accelerations)
- [14. Launch Vibrations](#14-launch-vibrations)
- [15. Launch Acoustics and Shock](#15-launch-acoustics-and-shock)
- [16. Preliminary Mass Estimation](#16-preliminary-mass-estimation)
- [17. Trade Studies](#17-trade-studies)
- [18. Structural Analysis and Testing](#18-structural-analysis-and-testing)
- [19. Statics and Stress Analysis](#19-statics-and-stress-analysis)
- [20. Dynamics and Modal Analysis](#20-dynamics-and-modal-analysis)
- [21. Thermal Analysis and Testing](#21-thermal-analysis-and-testing)
- [22. Fatigue Analysis and Testing](#22-fatigue-analysis-and-testing)
- [23. Other Mechanical Testing](#23-other-mechanical-testing)
- [24. Mechanical Subsystem Design Process](#24-mechanical-subsystem-design-process)
- [25. Beagle 2 Case Study](#25-beagle-2-case-study)
- [26. Lecture Summary](#26-lecture-summary)

---

# 1. Mechanical Subsystem Overview

> **Source: Slide 2**

## Function

The mechanical subsystem:

- Provides structure to support the spacecraft and payload
- Enables deployment mechanisms and separation systems
- Protects against launch and on-orbit stresses
- Protects against radiation and micrometeoroids

Primary drivers include:

- Spacecraft type
  - Orbiter
  - Lander
  - Rover
- Payload type
  - Camera
  - Sampling system
  - Other mission-specific hardware
- Overall dry and wet mass
- Articulated:
  - Solar arrays
  - Antennas
  - Instruments

The subsystem is also commonly called **Structures and Mechanisms** and often includes spacecraft harnessing.

## GRAIL Example

Mechanical hardware includes:

- Four side panels
- Propulsion and payload panels
- Tank supports
- Fittings
- Solar-array deployment mechanisms
- Launch-vehicle separation system

Total mechanical mass:

```text
~35 kg
```

## Common Components

### Primary Structure

- Core structure
- Structural panels

### Secondary Structure

- Tank supports
- Fittings
- Payload supports
- Booms

### Mechanisms

- Gimbals
- Deployables
- Release systems

### Payload Elements

Examples:

- Wheels
- Sample-return canisters

Depending on the project, these can instead be owned by the payload subsystem.

### Adapters

- Launch vehicle to spacecraft
- Spacecraft to probe
- Spacecraft to spacecraft

## Key Trades and Analyses

- Configuration
- CAD
- Field-of-view design
- Loads analysis
- Stiffness analysis
- Master Equipment List
- Mechanism design
- Torque analysis

## Key Parameters

- Mass
- Power
- Cost

## Relationship with Other Subsystems

Mechanical design:

- Houses and supports all spacecraft subsystems
- Provides environmental protection
- Distributes ACS and propulsion loads
- Supports grounding and harness routing for power
- Provides heat-transfer and heat-dissipation paths for thermal design

---

# 2. Asteroid Sample Return Mission Example

> **Source: Slides 3–11**

The lecture uses a conceptual asteroid sample-return spacecraft similar to OSIRIS-REx.

Mission characteristics include:

- Deep-space mission to a near-Earth asteroid
- Touch-And-Go sample collection
- Sample Return Canister
- Electric propulsion using Hall thrusters
- High-voltage power at approximately 110 V

Major externally visible elements include:

- Hall thrusters
- High-gain antenna
- RCS thrusters
- Approximately 15 m² solar arrays
- Star trackers
- Science cameras
- Radar

---

## Primary Structure

> **Source: Slide 4**

The primary structure consists of:

- Core structure
- Four main panels:
  - -X
  - +X
  - -Y
  - +Y

**Figure description:** The exploded CAD view shows the spacecraft built around a central cylindrical/core load-carrying structure. Large equipment panels attach around the core, allowing subsystem hardware to be integrated onto panels before final spacecraft assembly.

---

## Secondary Structure

> **Source: Slide 5**

Examples include:

- Hall-thruster support
- Solar-array truss/substrate
- Component mounts
- Equipment-support structures

The lecture notes that much of the secondary structure is not normally visible in a high-level spacecraft configuration drawing.

---

## Mechanisms and Additional Hardware

> **Source: Slide 6**

### Solar Arrays

Use:

- Hinges
- Latches

### Sample Collection System

Includes:

- Arm assembly
- Shoulder joint
- Elbow joint
- Wrist joint
- Tube structures
- Launch restraints
- End effector
- Sample pad

### Sample Return Capsule

Includes:

- Thermal Protection System
- Primary structure
- Sample canister
- Latches
- Pins

---

## Spacecraft Adapter

> **Source: Slide 7**

Interfaces include:

### Spacecraft to Sample Return Capsule

- Spin-eject mechanism
- Hinge-latch mechanism

### Spacecraft to Launch Vehicle

The spacecraft-side launch-vehicle adapter is shown beneath the spacecraft.

The launch-vehicle side is not shown in the configuration view.

---

## Telecom and Avionics Panel

> **Source: Slide 8**

The +Y panel demonstrates how mechanical configuration must accommodate hardware from multiple subsystems.

Hardware includes:

- -X LGA
- +X LGA
- Waveguide switches
- Diplexer
- TWTAs
- SDSTs
- Solar Array Drive Assembly
- SADA electronics box
- Payload electronics boxes
- Avionics / flight-computer boxes
- High Voltage Electronics Assembly
- Power electronics box

**Figure description:** The panel layout shows RF hardware near the upper portion of the panel, the SADA near the center, and power/avionics/payload electronics grouped in the lower region. Mechanical layout therefore becomes a system-level packaging problem rather than simply a structural problem.

---

## Other Panels

> **Source: Slide 9**

Additional spacecraft panels accommodate:

- SADA
- SADA electronics
- Power Processing Units
- High-voltage to low-voltage converters
- 22-Ah battery
  - 11 cells
- Coarse Sun Sensor
- IMUs
- Sample Collection System electronics

---

## Launch Configuration

> **Source: Slides 10–11**

Launch configuration is critical for:

- Volume constraints
- Dynamic constraints

The spacecraft must fit inside the launch-vehicle fairing with sufficient clearance to prevent contact during launch.

### Dynamic Envelope

The spacecraft is not perfectly stationary during launch. Structural motion and vibration require a clearance envelope around the stowed spacecraft.

### Transportation

Mechanical design must also account for transportation loads.

The spacecraft may be transported in orientations that differ from its launch or operational orientation—for example, on its side.

Therefore, mechanical design must consider loads from:

- Ground transportation
- Handling
- Integration
- Launch
- On-orbit operation

---

# 3. Mechanical Constraints and Drivers

> **Source: Slides 12–13**

## Constraints

### Cost and Budget

Mechanical architecture, materials, manufacturing methods, and testing are constrained by available budget.

### Schedule

Development and integration schedules constrain:

- Design maturity
- Manufacturing
- Analysis
- Test
- Rework

### Launch Vehicle

The selected launch vehicle defines:

- Launch environment
- Maximum spacecraft mass
- Adapter interface
- Fairing volume
- Dynamic environment

### Manufacturability

The structure must be practical to:

- Fabricate
- Assemble
- Inspect
- Integrate

### Testability

Design must account for:

- Hardware access
- Earth-gravity loads
- Mechanical ground-support equipment

---

## Drivers

### Mission Performance

Includes:

- Mission duration
- Trajectory
- Orbiter vs. lander/rover

### Deployments and Mechanisms

Examples:

- Solar arrays
- Antennas
- Booms

### Payload Accommodations

Includes:

- Pointing
- Fields of view
- Alignment

### Subsystem Accommodations

Includes:

- ACS sensor FOVs
- Thruster FOVs
- Sensor/thruster alignment
- Harness routing
- Thermal pathways
- Keep-out zones

### Space Environment

Includes:

- Thermal environment
- Radiation
- Vacuum
- Outgassing

**Outgassing** occurs when trapped materials are released in vacuum.

### Mass and Mass Properties

Mechanical configuration directly determines:

- Total mass
- Center of gravity
- Moments of inertia
- Products of inertia

---

# 4. Requirements Flowdown

> **Source: Slide 14**

System requirements begin with mission objectives but are strongly influenced by:

- Cost
- Schedule
- System architecture

Requirements flow to the mechanical subsystem so that the spacecraft and payload can perform functions such as:

- Trajectory execution
- Pointing
- Science observation

The general process is:

```text
Science / Mission Requirements
↓
Spacecraft System Requirements
↓
Mechanical Subsystem Requirements
↓
Spacecraft Conceptual Design
↓
Structural / Thermal Analysis
↓
Revisit Requirements
↓
Spacecraft Detailed Design
↓
Iterate Analysis and Design
```

The lecture emphasizes iteration: mechanical requirements, configuration, and analysis are repeatedly revisited until the design is satisfactory.

---

# 5. Common Mechanical and Structural Requirements

> **Source: Slide 15**

| Requirement | Definition | Typical Driver |
|---|---|---|
| Strength | Load required to break, buckle, or unacceptably deform structure | Maximum expected launch/landing loads |
| Structural Response | Magnitude and duration of vibration | Maximum expected dynamic loads |
| Structural Life | Number of load cycles before fatigue, creep, stress-corrosion cracking, or failure | Repetitive events and articulations |
| Natural Frequency | Frequency at which a structure vibrates when excited | Launch vehicle and ACS frequencies |
| Mass Properties | Mass, CG, moments and products of inertia | Launch vehicle and ACS stability |
| Damping | Ability of structure to dissipate vibration energy | Payload stability |
| Stiffness | Load required to produce a unit deflection | Strength, frequency, deflection requirements |
| Dynamic Envelope | Volume that vibrating spacecraft must not violate inside fairing | Launch-vehicle fairing |
| Positional Stability | Ability to maintain location or direction | Payload and ACS sensor needs |
| Mechanical Interface | Bolt patterns/features controlling how components are joined | Subsystem and testability needs |

The goal is not simply to prevent structural failure. Mechanical requirements also ensure:

- Dynamic compatibility with the launch vehicle
- ACS stability
- Payload pointing
- Adequate clearances
- Repeatable interfaces
- Mission lifetime

---

# 6. Mechanical Subsystem Design

> **Source: Slides 16–17**

## Primary Structure

The primary structure:

- Houses the majority of spacecraft components
- Transmits loads through the spacecraft to the launch-vehicle interface
- Provides payload/component attachment points
- Commonly uses a core structure with subsystem-specific panels

Subsystem panels can often be:

- Integrated individually
- Tested individually
- Installed during final assembly

The structure is sized to accommodate:

- Propulsion hardware
- Electronics boxes
- Payload hardware

---

## Secondary Structure

Secondary structure bridges primary structure to mounted hardware.

Examples:

- Solar-array truss
- Solar-array substrate
- Equipment benches
- Component supports

---

## Tertiary Structure

Additional support and attachment hardware.

Examples:

- Brackets
- Local supports

---

## Mechanisms

Devices that:

- Move
- Rotate
- Slide
- Separate

Examples:

- Release devices
- Hinges
- Booms
- Motors
- Gimbals

---

## Additional Hardware

May include:

- Ballast mass
- Payload attachments
- Telescope barrels
- Sample Return Capsules

---

## Launch Vehicle and Spacecraft Adapters

Provide interfaces between:

- Launch vehicle and spacecraft
- Multiple spacecraft
- Probes
- Other separated elements

---

## Harness

Includes cables and wires required for:

- Electrical power
- Data

Mechanical design must provide:

- Routing
- Support
- Bend radius
- Attachment points
- Clearance

---

# 7. Common Spacecraft Structures

> **Source: Slide 18**

Several common structural approaches can overlap within a spacecraft.

## Skin-Frame Structures

Common throughout aerospace.

- Stringers carry axial load.
- Skin carries shear and axial loads.

Aircraft wings are a representative example.

---

## Sandwich Structures

Use:

- Metal or composite face sheets
- Foam or honeycomb core

Increasing panel thickness provides large stiffness improvements with relatively small mass increases.

Useful for:

- Bending
- Buckling resistance
- Vibration performance

Additional failure modes can occur, particularly at adhesive interfaces.

---

## Isogrids

Mass-efficient structures with material cutouts.

Advantages:

- High structural efficiency
- Low mass

Disadvantages:

- Costly
- Complex
- Difficult to machine

Can be:

- Metallic
- Composite

Composite isogrids require intricate molds.

---

## Cylinder Structures

Can be:

### Monocoque

Load carried primarily by cylindrical skin.

### Semi-Monocoque / Stiffened Cylinder

Uses skin and stringers.

Common for fuselage-like structures.

Useful when interior access is important.

---

# 8. Materials Selection

> **Source: Slide 19**

Material selection must provide sufficient robustness against:

- Mechanical loads
- Launch loads
- Thermal environment
- Radiation environment

## Important Properties

- Density
- Yield strength
- Ultimate strength
- Strength-to-weight ratio
- Elastic modulus / stiffness
- Coefficient of thermal expansion
- Thermal conductivity
- Radiation resistance

---

## Material Comparison

| Material | Density | Strength | Temperature Tolerance | Applications | Benefits | Issues |
|---|---|---|---|---|---|---|
| Aluminum | Low | High | Medium | Panels, framework | Ease of manufacture | — |
| Steel | High | High | High | Bolts, fasteners | — | High mass |
| Titanium | Medium-high | High | Medium | Brackets, tanks, joints | Corrosion resistance | Higher mass |
| Polymers | Low | Low | Low | Insulation, seals | Ductility | Glass-transition temperature |
| Ceramics | Medium | Medium | High | Coatings, TPS | Thermal performance | Brittle |
| Composites | Low | High | Medium-high | Panels, booms, trusses | Optimizable properties | Expensive and complex |

### Aluminum

Most common due to favorable:

- Stiffness-to-weight ratio
- Strength-to-weight ratio
- Manufacturability

### Steel

- High strength
- High-temperature capability
- Heavy

### Titanium

- High strength
- Corrosion resistance
- Useful against atomic oxygen and other environmental effects
- Heavier than aluminum

### Polymers

Examples:

- Kapton
- Epoxy

Advantages:

- Lightweight

Disadvantages:

- Much weaker
- Glass-transition-temperature concerns

### Ceramics

- High-temperature capability
- Brittle
- Used in some thermal-protection applications

### Composites

- Strong
- Lightweight
- Expensive
- Complex to manufacture/test
- Difficult to join

---

# 9. Composite Materials

> **Source: Slide 20**

Composites contain:

- Fibers
- Matrix

They commonly use multiple layers with different fiber orientations.

The combination creates properties stronger or more useful than either constituent alone.

## Orthotropic Behavior

Composites are **orthotropic**.

Mechanical properties differ depending on direction.

Therefore, unlike many metals, material response cannot be assumed identical in every axis.

## Common Fibers

- Carbon fiber
- Glass fiber
- Aramid fiber

## Common Polymer Matrices

- Epoxy
- Cyanate ester

## Design Parameters

Major laminate design parameters include:

- Fiber selection
- Matrix selection
- Ply angle
- Layer stacking sequence

## Failure

Composite failure is direction-dependent.

Multiple failure modes must be considered.

Manufacturing variation drives extensive:

- Process control
- Material testing
- Structural testing

---

# 10. Mechanisms and Deployables

> **Source: Slide 21**

## Mechanisms

### Actuators

Enable movement.

Examples:

- Motors
- Servos

Especially common in robotics.

### Gimbals

Control orientation of:

- Instruments
- Antennas
- Solar arrays

### Hinges

Provide rotational motion between spacecraft elements.

Example:

- Solar-array deployment

### Restraints and Locks

Secure deployable hardware during:

- Launch
- Operation

---

## Deployables

### Solar Arrays

- Stowed during launch
- Usually deployed immediately after launch-vehicle separation
- Deployment is typically autonomous

### Antennas

An HGA may be stowed during launch and deployed after communication is established using an LGA.

### Radiators

Large radiators may be stowed for launch and deployed during commissioning.

### Booms

Sensitive instruments such as magnetometers can be mounted on booms to reduce spacecraft-generated noise.

### Instruments

Large or sensitive instruments may be stowed and may include deployable covers.

---

## Deployment Actuation

### Pyrotechnics

Advantages:

- Simple
- Fast

Disadvantages:

- Misfire/early-fire risk
- Shock
- Debris
- Irreversible

### Springs

Advantages:

- Simple
- Reliable
- Can be reversible

Disadvantages:

- Limited force
- Environmental sensitivity
- Wear
- Slow

### Motors

Advantages:

- Controlled
- Reusable
- Low shock
- Scalable

Disadvantages:

- Complex
- Heavy
- Higher electrical power

---

## Design Challenges

- Reliability in vacuum
- Temperature variation
- Deployment shock
- Deployment failure
- Redundancy

Europa Clipper is shown as an example with:

- Deployable solar arrays
- Instrument boom
- Antennas
- Camera covers
- Gimbaled solar array

---

# 11. Configuration Considerations

> **Source: Slides 22–23**

Spacecraft configuration is driven by requirements from nearly every subsystem.

## Payload Accommodation

### Pointing, Stability, and Alignment

Drive structural stiffness to minimize:

- Vibration response
- Mechanical deflection
- Thermal deflection

### Fields of View and Keep-Out Zones

Drive hardware placement and spacecraft geometry.

### EMI

Can require physical separation between systems.

### Special Hardware

Examples:

- Masts
- Sample-collection systems

---

## Mass Properties

Driven by:

- Launch vehicle
- ACS

### Center of Gravity

The CG is the effective location where spacecraft mass/weight is concentrated.

It affects stability and force/torque response.

### Moment of Inertia

MOI describes resistance to changes in rotational motion.

It affects response to applied torque.

### Products of Inertia

POI describe cross-axis mass distribution and affect dynamic coupling/stability.

Symmetry is therefore important.

Typical configuration practices include:

- Solar arrays in symmetric 2- or 4-panel layouts
- Fuel tanks near CG
- Reaction wheels near CG
- Thrusters divided into symmetric clusters
- Main engine near the CG axis

Ballast can be used to adjust mass properties.

---

## Testability

Subsystem-specific panels can simplify:

- Integration
- De-integration
- Repair
- Testing

---

## Propulsion Requirements

Thrusters have:

- FOV requirements for thrust
- KOZ requirements for plume impingement

Main engine should generally be close to CG.

## ACS Requirements

Sensors require:

- Pointing
- Stability
- Alignment
- FOV
- KOZ

Actuators should generally be near CG.

## Avionics Requirements

Electronics require heat-dissipation accommodation.

## Telecom Requirements

- Antenna FOV
- Antenna KOZ
- Electronics heat dissipation

## Power Requirements

Electronics and RTGs require heat-dissipation accommodation.

## Thermal Requirements

- Radiator FOV
- Radiator KOZ
- Heat-transfer pathways

## Harness Requirements

Harness design requires:

- Mounting area
- Bend radius
- Routing space

---

# 12. Loads and Environments

> **Source: Slide 24**

The mechanical subsystem must survive loads encountered during:

- Launch
- Separation
- Deployment
- On-orbit operation

## Mechanical Loads

### Launch

- Accelerations
- Shock
- Vibration
- Acoustics

Launch requirements are specified in the launch-vehicle user's guide.

### Deployments

Deployments such as:

- Solar arrays
- Booms

can generate shock loads.

### Onboard Equipment

Sources of vibration include:

- Reaction wheels
- Pumps

Micro-vibrations can affect sensitive instruments.

---

## Thermal Environment

Temperature changes cause:

- Expansion
- Contraction
- Thermal stress

The coefficient of thermal expansion is:

```math
\alpha =
\frac{\Delta L}{L_0 \Delta T}
```

where:

- `ΔL` = change in length
- `L0` = original length
- `ΔT` = temperature change

CTE mismatch between joined materials can generate thermal stress.

Repeated thermal cycling can also cause fatigue.

---

## Radiation

Mechanical considerations include:

- Material longevity
- Radiation hardening
- Radiation degradation of polymers
- Radiation degradation of composites

## MMOD

Micrometeoroid and orbital-debris design includes:

- Shielding
- Material selection
- Impact analysis
- Impact testing

---

# 13. Launch Accelerations

> **Source: Slide 25**

Launch accelerations are commonly divided into axial and lateral components.

## Axial

Acts along the spacecraft main axis.

Caused by rocket thrust.

The spacecraft is compressed against the payload adapter.

Peak axial acceleration commonly occurs during:

- Early liftoff
- Maximum-thrust portions of ascent

## Lateral

Acts perpendicular to the spacecraft main axis.

Caused by:

- Vibration
- Wind
- Structural bending

Lateral loads can peak around **Max Q**, the maximum dynamic-pressure condition.

The slide includes a Falcon 9/Falcon Heavy payload load-factor envelope and an example of STEREO spacecraft structural load testing.

---

# 14. Launch Vibrations

> **Source: Slide 26**

Launch vibration comes from:

- Rocket-engine operation
- Atmospheric turbulence

Frequency and amplitude vary throughout launch and can peak around:

- Ignition
- Liftoff

Two major vibration descriptions are used:

- Sine
- Random

## Sine Vibration

Used to understand behavior at specific frequencies and identify resonances.

Specified as acceleration at a given frequency.

## Random Vibration

Represents simultaneous broad-spectrum, non-deterministic launch vibration.

Specified using:

```text
Power Spectral Density (PSD)
```

with units:

```math
\frac{g^2}{Hz}
```

Overall acceleration can be represented as:

```text
Grms
```

which is related to the square root of the area under the PSD curve.

---

## Sine vs. Random Vibration

| Aspect | Sine Vibration | Random Vibration |
|---|---|---|
| Frequency | Single controlled frequencies | Wide simultaneous spectrum |
| Pattern | Repeating sine waves | Non-repeating random variations |
| Causes | Combustion, bending modes, harmonics | Acoustic energy, turbulence, external vibration |
| Primary Use | Low-frequency periodic oscillations and resonances | High-frequency complex loads |
| Purpose | Identify resonances/weaknesses | Evaluate durability under broadband vibration |
| Test Process | Sweep single-frequency sinusoidal excitation | Apply broad spectrum simultaneously |

---

# 15. Launch Acoustics and Shock

> **Source: Slide 27**

## Launch Acoustics

High sound-pressure levels from engines reverberate through the launch vehicle.

They can cause random vibration that affects:

- Structures
- Electronics
- Instruments

Acoustic loading commonly peaks during liftoff.

It is specified using:

```text
Sound Pressure Level (SPL)
```

in dB as a function of frequency.

---

## Launch Shock

Shock is a transient load associated with rapid events such as:

- Stage separation
- Engine shutdown
- Booster separation
- Fairing deployment

Shock is commonly represented using a:

```text
Shock Response Spectrum (SRS)
```

in units of acceleration.

The Falcon 9 example on the slide shows separation-plane SRS values that rise sharply with frequency, illustrating how high-frequency shock can be severe even though it is brief.

---

# 16. Preliminary Mass Estimation

> **Source: Slide 28**

Early conceptual design can estimate mechanical mass using allocation rules.

## Primary Structure

- 5% of internal high-density components
  - Electronics boxes
  - Batteries
- 15% of external high-density components
  - Blankets
  - Instruments
  - Telecom
- 20% of distributed components
  - Dry tanks
  - Feed system
  - Thrusters

## Secondary Structure

- 15% of primary structure
  - Junctions
  - Stiffeners
  - Brackets
- 6% of externally supported systems
  - Arrays
  - Antennas
  - Thrusters
- 4% of propellant mass for strengtheners

## Additional Items

- 1.5 kg/m² for deployed panels
  - Solar arrays
  - Radiators
- 1.0 kg per latch/release system
- 10% of primary-structure mass for integration/interface hardware
  - Shims
  - Fasteners
- Ballast:
  - ~1% total dry mass for 3-axis spacecraft
  - ~2.5% for spin-launched spacecraft
- Launch-vehicle interface:
  - ~5% of total wet-system mass
  - 75% allocated to launcher
  - 25% allocated to spacecraft

## Notes

Primary/secondary estimates assume composites.

If aluminum is used:

```text
Add ~12%
```

Optimized designs and advanced materials may reduce estimates by:

```text
~15–20%
```

Early estimates should carry approximately:

```text
20–30% contingency
```

until higher-fidelity CAD and structural estimates are available.

---

# 17. Trade Studies

> **Source: Slides 29–30**

Multiple mechanical configurations can satisfy mission requirements while producing different impacts on:

- Other subsystems
- Cost
- Mass
- Performance
- Margin
- Risk

Trade studies quantitatively compare alternatives using criteria with different weights.

The lecture emphasizes:

> Always compare what you exchange in a trade study.

For example, optimizing mass properties may sacrifice:

- Configuration benefits
- Structural margin
- Packaging flexibility

---

## Example Weighted Trade Study

The lecture uses a car-selection example to illustrate weighted scoring.

| Criterion | Importance |
|---|---:|
| Purchase Cost | 4 |
| Annual Maintenance Cost | 2 |
| Horsepower | 2 |
| Fuel Economy | 3 |
| Aesthetic | 3 |

The example produces:

| Option | Total Score |
|---|---:|
| Lexus IS 300 | 90 |
| BMW 330i | 83.5 |
| Mercedes C300 | 85 |

The highest-scoring option is the Lexus IS 300 under the stated assumptions and weighting.

The lesson is the **method**, not the automobile selection: trade results depend on requirements, weighting, assumptions, and scoring rules.

---

## Common Mechanical Trade Studies

> **Source: Slide 30**

### Launch Vehicle

Evaluate:

- Lift capability
- Fairing size
- Launch environment
- Payload adapter

### Spacecraft Configuration

Evaluate:

- Stowed layout
- Deployed layout
- Primary/secondary load paths
- Deployable layout
- Mass properties
- Fairing fit

### Primary Structure

Evaluate:

- Design loads
- Materials
- Payload shape
- Attachment methods
- Member sizing
- Stiffness
- Strength

### Subsystem Support

Ensure:

- Antenna FOV
- Instrument FOV
- Solar-array FOV
- Pointing
- Stability
- Mechanism requirements

Also determine whether active/passive load-response control is needed.

### Mass Properties

Ensure structures and mechanisms meet:

- Mass allocation
- Mass-property requirements

Include uncertainty for new designs.

---

# 18. Structural Analysis and Testing

> **Source: Slides 31–33**

Structural analysis and testing determine whether the spacecraft can:

- Survive the mission
- Perform required functions

The process is iterative.

If testing or analysis requires increased structural mass:

1. Update the design.
2. Update the configuration.
3. Re-run analysis.
4. Re-test as necessary.

This ultimately supports verification and validation.

## Analysis Challenges

- Model accuracy
- Model validation
- Transient-load modeling
- Thermo-mechanical coupling

## Testing Challenges

- Handling large complex systems without damage
- Reproducing launch environments on Earth
- Mission-specific testing
  - Deep space
  - Planetary landing

Testing feeds analytical-model validation.

---

## Qualification, Protoflight, and Acceptance Testing

> **Source: Slide 33**

| | Qualification | Protoflight | Acceptance |
|---|---|---|---|
| Purpose | Demonstrate robust design margin | Verify flight design with sufficient margin when units are limited | Verify each flight unit |
| Conducted On... | Prototype, not flown | Actual flight hardware | Every flight unit |
| Conditions | ~1.5–2× expected operational limits | Slightly above operational, below full qualification | At or slightly below operational limits |
| Outcome | Demonstrates design robustness | Demonstrates flight hardware survives mission without overstress | Demonstrates functionality/manufacturing quality |
| Examples | High-level loads, vibe, shock, TVAC | Moderate-level loads, vibe, shock, TVAC | Standard-level loads, vibe, shock, TVAC |

---

# 19. Statics and Stress Analysis

> **Source: Slides 34–36**

## Stress Analysis

Purpose:

- Determine structural stresses
- Determine component stresses
- Verify load capability
- Determine deflections
- Verify stiffness

### Coupled Loads Analysis

CLA combines loads from multiple:

- Sources
- Directions

during launch.

### Finite Element Analysis

FEA simulates:

- Stress
- Deformation
- Vibration

Example tools:

- ANSYS
- NASTRAN
- Abaqus

---

## Static Load Testing

Evaluates spacecraft ability to withstand launch-like static loads.

Loads are applied in a controlled manner at or above expected levels.

Quasi-static testing applies loads gradually and holds them steady.

---

## Basic Equations Used for Stress Calculations

> **Source: Slides 35–36**

The following equations are used for basic spacecraft structural stress and deformation calculations.

| Concept | Equation | Variables | Application |
|---|---|---|---|
| **Normal Stress** | $\sigma = \frac{F}{A}$ | **σ** = normal stress<br>**F** = axial force<br>**A** = cross-sectional area | Stress perpendicular to a cross-sectional area due to axial loads. **Important for launch-load analysis.** |
| **Shear Stress** | $\tau = \frac{V}{A}$ | **τ** = shear stress<br>**V** = shear force<br>**A** = cross-sectional area | Stress parallel to a cross-sectional area. **Important for joints and fasteners subjected to shear during launch.** |
| **Strain** | $\epsilon = \frac{\Delta L}{L_0}$<br>$\gamma = \frac{\Delta x}{L}$ | **ε** = normal strain<br>**γ** = shear strain<br>**ΔL** = change in length<br>**L₀** = original length<br>**Δx** = lateral displacement<br>**L** = length over which shear occurs | Deformation per unit length. **Important for assessing structural elongation or angular distortion under load.** |
| **Hooke's Law** | $\sigma = E\epsilon$<br>$\tau = G\gamma$ | **E** = Young's modulus<br>**G** = shear modulus | Linear relationship between stress and strain in the elastic region. **Important for deformation calculations.** |
| **Bending Stress** | $\sigma = \frac{My}{I}$ | **σ** = bending stress<br>**M** = bending moment<br>**y** = distance from neutral axis<br>**I** = moment of inertia | Stress from bending moments in beams. **Important for analyzing spacecraft booms, panels, and supports.** |
| **Torsional Shear Stress** | $\tau = \frac{Tr}{J}$ | **τ** = shear stress<br>**T** = applied torque<br>**r** = radius<br>**J** = polar moment of inertia | Stress in rotating parts, **like antennas or reaction wheels.** |
| **Thermal Stress** | $\sigma_{\text{thermal}} = E\alpha\Delta T$ | **σthermal** = thermal stress<br>**E** = Young's modulus<br>**α** = coefficient of thermal expansion<br>**ΔT** = temperature change | Stress induced by temperature changes. **Important for spacecraft facing thermal cycles.** |
| **von Mises Stress** | $\sigma_v = \sqrt{\sigma_x^2-\sigma_x\sigma_y+\sigma_y^2+3\tau_{xy}^2}$ | **σv** = von Mises stress<br>**σx, σy** = normal stresses<br>**τxy** = shear stress | Stress due to combined normal and shear stresses. **Important for failure prediction under combined loading.** |
| **Safety Factor** | $SF = \frac{\text{Material Strength}}{\text{Applied Stress}}$ | **SF** = safety factor<br>**Material Strength** = yield/ultimate strength<br>**Applied Stress** = calculated stress | Ensures design stress remains within safe limits. **Important for reliability under uncertain conditions.**<br><br>**Yield:** typically 1.1–1.25<br>**Ultimate:** typically 1.4–2 |
| **Axial Deformation** | $\Delta L = \frac{FL_0}{AE}$ | **ΔL** = change in length<br>**F** = axial force<br>**L₀** = original length<br>**A** = cross-sectional area<br>**E** = Young's modulus | Elongation or compression due to axial load. **Important for assessing structural changes during launch acceleration.** |

---

# 20. Dynamics and Modal Analysis

> **Source: Slide 37**

## Dynamics and Modal Analysis

**Purpose:** Determines natural frequencies, mode shapes, and damping; determines vibration loads.

### Strategies

- **Dynamic analysis** assesses spacecraft under transient and time-dependent loads such as vibrations and shock.
  - **Examples:** LS-DYNA, MSC ADAMS

- **Modal analysis** assesses spacecraft natural frequencies to ensure resonance does not compromise structural integrity under launch and operational loads.
  - **Examples:** HyperMesh, MSC NASTRAN

---

## Dynamics and Modal Testing

### Vibration Testing

**Purpose:** Tests spacecraft's tolerance to vibrational environment of launch and separation events.

**Strategy:** Shaker table subjects spacecraft to varying frequencies and amplitudes.

- **Sinusoidal vibe testing** concentrates energy on single frequency at a time to excite resonance, stressing the structure.
- **Random vibe testing** covers many frequencies, closer to launch environment.

### Shock Testing

**Purpose:** Tests spacecraft's tolerance to shock events like stage separation or pyro firings.

**Strategy:** Impact device or explosive actuator generates sudden, high-energy shocks.

### Acoustic Testing

**Purpose:** Tests spacecraft's tolerance to the noise environment of launch.

**Strategy:** Acoustic chamber exposes the spacecraft to high-decibel sound waves.

### Modal Testing

**Purpose:** Identifies the natural frequencies and vibration modes of the spacecraft structure.

**Strategy:** Shaker table applies small oscillatory forces at different points to determine resonant frequencies.

---

# 21. Thermal Analysis and Testing

> **Source: Slide 38**

## Thermal Analysis

**Purpose:** Determines robustness of spacecraft to operational and survival temperatures; determines stresses, strains, and deflections caused by temperature changes.

**Strategy:** Thermal analysis software analyzes temperature distributions and thermal stresses to predict thermal loads on spacecraft due to space environment.

**Examples:**

- Thermal Desktop
- Sinda

## Thermal Testing

### Thermal Vacuum Testing (TVAC)

**Purpose:** Ensures the spacecraft can withstand the extreme temperatures and vacuum conditions of space.

**Strategy:** Places spacecraft in a thermal vacuum chamber, temperatures cycle and hold through extremes of mission profile.

**Types:**

- **Thermal balance:** Steady-state conditions to validate thermal models.
- **Thermal cycle:** Cycling conditions to test resilience to repeated temperature changes — e.g., due to repeated eclipses (can cause expansion, contraction, fatigue).
- **Thermal soak:** Prolonged exposure to a single hot and cold temperature to test resilience to extremes.
- **Thermal shock:** Quick transitions between hot and cold temperatures to test resilience to rapid temperature change — e.g., due to eclipse exit.

**Figure description:** The slide shows an example spacecraft thermal analysis model and Europa Clipper in a TVAC chamber.

---

# 22. Fatigue Analysis and Testing

> **Source: Slide 39**

Fatigue cycling occurs for repetitive loads often lower than **yield or ultimate strength** — cracks form and propagate through system until sudden fracture.

### Examples

- Spacecraft tanks that undergo multiple pressurization cycles.
- Mechanisms that are repeated frequently (e.g., solar array gimbals, robotics motors).

### Endurance Limit

**Endurance Limit:** Stress amplitude under which fatigue will not occur.

### Fatigue Life

**Fatigue Life:** Number of cycles of a load a structure can sustain without fatigue.

- Defined in S-N (Stress vs # of cycles) curves.

FEA can support fatigue analysis, but typically needs to be validated with testing.

## Fatigue and Durability Testing

**Purpose:** Assesses long-term material performance under repeated or cyclic loads.

**Strategy:** Applies repeated loading cycles to components to test for fatigue.

**Figure description:** The slide shows an S-N curve plotting stress against number of cycles, including representative curves for steel and aluminum and an endurance-limit region.

---

# 23. Other Testing

> **Source: Slide 40**

## Mass Properties Testing

**Purpose:** Ensure total mass, CG, MOI, POI are within specifications.

**Strategies:**

- **Mass:** Uses precision scale or load cell.
- **CG:** Spacecraft is mounted on a fixture that allows it to pivot until it balances (minimal torque); location where it balances is used to determine the CG.
- **MOI and POI:** Spacecraft is placed on a spin table and rotated around each principal axis; angular response (frequency and acceleration) are measured and used to calculate MOI and POI for each axis.

## Life Testing

**Purpose:** Assesses durability of spacecraft components for expected operational environment and mission duration.

**Strategy:** Components are subjected to mission-like conditions (loads, vibrations, temperatures) over an extended period, typically ~1.5 to 2× life for margin.

- Can do accelerated testing at higher loads, but requires careful assessment to ensure this is representative.

## Bakeout

**Purpose:** Reduces outgassing, prevents contamination of spacecraft to itself (contamination control) and other planetary bodies (planetary protection).

**Strategy:** Spacecraft is elevated to high temperature (~100 to 125 °C) in vacuum (typically part of TVAC testing); post bakeout inspection ensures cleanliness is met.

**Figure description:** The slide shows a spacecraft mounted on equipment used for spacecraft mass-properties testing.

---

# 24. Mechanical Subsystem Design Process

> **Source: Slides 41–48**

Slide 41 introduces the **Mechanical Subsystem Design Process**.

## Design Process Overview

> **Source: Slide 42**

The overall mechanical subsystem design process is:

```text
Define mech subsystem requirements
        ↓
Define mech subsystem architecture
        ↓
Select mech subsystem hardware
        ↓
Build, integrate, and test mech subsystem
        ↓
Deliver mech subsystem to Spacecraft ATLO
        ↓
Operate Spacecraft with mech subsystem
```

FSW development occurs alongside mechanical hardware development:

```text
Develop FSW code to operate mech subsystem
```

The process is divided into:

| Phase | Mechanical Development |
|---|---|
| **Phase A** | Define mech subsystem requirements |
| **Phase B/C** | Define mech subsystem architecture; select mech subsystem hardware; develop FSW code to operate mech subsystem; design mech subsystem |
| **Phase D** | Build, integrate, and test mech subsystem; deliver mech subsystem to Spacecraft ATLO |
| **Phase E** | Operate Spacecraft with mech subsystem |

**Figure description:** The slide presents the mechanical development process as a connected flowchart. Circular arrows around the requirements, architecture, design, and build/test portions emphasize that the process is iterative.

---

## Requirements

> **Source: Slide 43**

### Mechanical Subsystem Requirements Development

Develop L4 mechanical subsystem requirements in response to L3 flight system requirements, such as:

- **The mechanical subsystem shall have a mass less than 1,500 kg** → drives sizing, materials.
- **The mechanical subsystem shall have a resonant frequency greater than 25 Hz** → drives sizing, materials, layout, launch restraints.
- **The mechanical subsystem shall survive a static launch load of 6g axial and 2g lateral** → drives sizing, materials, layout.
- **The mechanical subsystem shall ensure a 65 deg FOV for the Camera** → drives configuration.

**Figure description:** The process diagram highlights the requirements-development portion of Phase A while the later architecture, hardware, FSW, I&T, delivery, and operations stages remain visible in the background.

---

## Architecture

> **Source: Slide 44**

### Mechanical Subsystem Architecture Development

Perform key mechanical architecture trades and sizing analyses, such as:

- Primary and secondary structure sizing for driving loads.
- Mechanism needs.
- Configuration layout.
- Materials selection.
- Mass and mass properties.

**Figure description:** The process diagram highlights the mechanical architecture stage in Phase B/C.

---

## Design

> **Source: Slide 45**

### Mechanical Subsystem Design

- Select materials, design structure.
- Layout configuration (CAD), create drawings.
- Create MEL.
- Perform structural analysis, iterate design accordingly.
- Design relevant FSW code:
  - Deployments.
  - Solar array and HGA gimbal articulations.
  - Robotic motor articulations.

**Figure description:** The process diagram highlights hardware selection and FSW development as the mechanical subsystem moves through Phase B/C design.

---

## Build and Test

> **Source: Slide 46**

### Mechanical Subsystem Build and I&T

- Integrate structure and mechanisms.
- Perform subsystem-level qualification, protoflight, and/or acceptance testing, including:
  - Vibration.
  - Shock.
  - Acoustics.
  - Thermal.

**Figure description:** The process diagram highlights the "Build, integrate, and test mech subsystem" block in Phase D.

---

## Deliver

> **Source: Slide 47**

### Mechanical Subsystem Delivery

- Deliver mechanical subsystem into ATLO for integration with rest of flight hardware.
- Execute system-level environmental testing, including:
  - Vibration.
  - Shock.
  - Acoustics.
  - Thermal.
- Execute deployment tests for:
  - Solar arrays.
  - Booms.
  - Etc.

**Figure description:** The process diagram highlights delivery of the mechanical subsystem to Spacecraft ATLO during Phase D.

---

## Operate

> **Source: Slide 48**

### Mechanical Subsystem Operation

- Release deployables, typically in early operations (solar array, booms, etc).
- Perform trending on actuators (solar array gimbal, HGA gimbal, robotics motors, etc).
- Update FSW if needed in order to accommodate mechanism operation (e.g., changes to speed, fault limits).

**Figure description:** The final process diagram highlights spacecraft operation with the mechanical subsystem during Phase E.

---

# 25. Case Studies

> **Source: Slide 49**

Slide 49 introduces the **Case Studies** section.

---

# 26. Case Study: Beagle 2

> **Source: Slide 50**

Beagle 2 was an ESA Mars probe launched in 2003 as part of Mars Express.

- Successfully separated from Mars Express, but failed to establish communication after landing.

## Key Failure

One or more solar panels did not fully deploy, likely obstructing the antenna.

## Causes

### No Communication Redundancy

Relied on a single communication path, which became unusable due to the deployment issue.

### Landing Challenges

The EDL sequence had unexpected atmospheric conditions, potentially damaging solar array deployment hardware.

### Deployment Complexity

The success of communications depended on complete solar array deployment.

### Limited Testing

Tight budget constraints limited extensive testing at realistic conditions, particularly of critical deployments after relevant environments.

## Lessons Learned

### Redundant Comm Paths

Multiple communication paths should be included to prevent a single point of failure.

### Robust Deployment Systems

Minimize dependencies in deployment sequences.

### Enhanced Testing for Critical Systems

Allocate budget and schedule resources to enable comprehensive testing at realistic conditions, especially for high-risk operations like EDL and deployments.

### Improved Environmental Modeling

Ensure accurate and adaptive atmospheric models for Martian conditions.

**Figure description:** The upper image shows the intended Beagle 2 deployment with the solar panels completely opened around the lander. The lower Mars-orbit image shows the assumed actual deployment, with the interpreted panel arrangement indicating that the complete deployment sequence likely did not occur.