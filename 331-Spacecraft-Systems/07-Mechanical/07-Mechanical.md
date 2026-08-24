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

## Basic Stress and Strain Equations

> **Source: Slide 35**

### Normal Stress

```math
\sigma = \frac{F}{A}
```

where:

- `σ` = normal stress
- `F` = axial force
- `A` = cross-sectional area

Used for axial launch-load analysis.

### Shear Stress

```math
\tau = \frac{V}{A}
```

where:

- `τ` = shear stress
- `V` = shear force
- `A` = cross-sectional area

Important for joints and fasteners.

### Normal Strain

```math
\epsilon = \frac{\Delta L}{L_0}
```

### Shear Strain

```math
\gamma = \frac{\Delta x}{L}
```

### Hooke's Law

```math
\sigma = E\epsilon
```

```math
\tau = G\gamma
```

where:

- `E` = Young's modulus
- `G` = shear modulus

### Bending Stress

```math
\sigma = \frac{My}{I}
```

where:

- `M` = bending moment
- `y` = distance from neutral axis
- `I` = area moment of inertia

Important for:

- Booms
- Panels
- Supports

### Torsional Shear Stress

```math
\tau = \frac{Tr}{J}
```

where:

- `T` = applied torque
- `r` = radius
- `J` = polar moment of inertia

---

## Additional Stress Equations

> **Source: Slide 36**

### Thermal Stress

```math
\sigma_{\text{thermal}} = E\alpha\Delta T
```

where:

- `E` = Young's modulus
- `α` = coefficient of thermal expansion
- `ΔT` = temperature change

### von Mises Stress

```math
\sigma_v
=
\sqrt{
\sigma_x^2
-
\sigma_x\sigma_y
+
\sigma_y^2
+
3\tau_{xy}^2
}
```

Used to evaluate combined normal and shear stress.

### Safety Factor

```math
SF
=
\frac{\text{Material Strength}}
{\text{Applied Stress}}
```

Representative values from the lecture:

- Yield: ~1.1–1.25
- Ultimate: ~1.4–2

### Axial Deformation

```math
\Delta L
=
\frac{F L_0}{AE}
```

---

# 20. Dynamics and Modal Analysis

> **Source: Slide 37**

## Dynamics Analysis

Determines spacecraft behavior under:

- Transient loads
- Time-dependent loads
- Vibration
- Shock

Example tools:

- LS-DYNA
- MSC ADAMS

## Modal Analysis

Determines:

- Natural frequencies
- Mode shapes
- Damping

The purpose is to ensure resonance does not compromise structural integrity during:

- Launch
- Spacecraft operation

Example tools:

- HyperMesh
- MSC NASTRAN

---

## Vibration Testing

Tests tolerance to launch/separation vibration.

A shaker table applies varying:

- Frequency
- Amplitude

### Sine Vibration

Concentrates energy at one frequency at a time and can strongly excite resonances.

### Random Vibration

Applies many frequencies and more closely approximates launch.

---

## Shock Testing

Tests tolerance to events such as:

- Stage separation
- Pyrotechnic firing

An impact device or explosive actuator creates sudden high-energy shocks.

---

## Acoustic Testing

An acoustic chamber exposes the spacecraft to high sound-pressure levels representative of launch.

---

## Modal Testing

Small oscillatory forces are applied at different points to identify:

- Resonant frequencies
- Structural modes

---

# 21. Thermal Analysis and Testing

> **Source: Slide 38**

## Thermal Analysis

Determines:

- Operational-temperature robustness
- Survival-temperature robustness
- Thermal stresses
- Thermal strains
- Thermally induced deflections

Thermal software predicts:

- Temperature distributions
- Thermal loads
- Thermal stresses

Example tools:

- Thermal Desktop
- SINDA

---

## Thermal Vacuum Testing

TVAC verifies spacecraft performance under:

- Vacuum
- Hot temperatures
- Cold temperatures

### Thermal Balance

Steady-state conditions used to validate thermal models.

### Thermal Cycle

Repeated hot/cold cycling.

Used to evaluate effects such as:

- Expansion
- Contraction
- Fatigue
- Repeated eclipses

### Thermal Soak

Prolonged exposure to a hot or cold extreme.

### Thermal Shock

Rapid transition between temperature extremes.

Example:

- Eclipse exit

---

# 22. Fatigue Analysis and Testing

> **Source: Slide 39**

Fatigue can occur under repetitive loads that are below yield or ultimate strength.

Cracks can:

1. Form.
2. Propagate.
3. Eventually cause sudden fracture.

Examples:

- Repeated tank pressurization
- Solar-array gimbals
- Robotics motors
- Frequently cycled mechanisms

## Endurance Limit

Stress amplitude below which fatigue is not expected to occur.

## Fatigue Life

Number of load cycles a structure can withstand without fatigue failure.

Represented using:

```text
S-N curves
```

which plot stress against number of cycles.

FEA can support fatigue analysis but generally requires test validation.

## Fatigue Testing

Repeated loading is applied to components to assess long-term durability.

---

# 23. Other Mechanical Testing

> **Source: Slide 40**

## Mass Properties Testing

Verifies:

- Total mass
- CG
- MOI
- POI

### Mass

Measured using:

- Precision scale
- Load cell

### Center of Gravity

The spacecraft is mounted on a fixture that allows it to pivot until balanced.

The balance location is used to determine CG.

### MOI and POI

The spacecraft is placed on a spin table and rotated about principal axes.

Measured angular response is used to determine inertia properties.

---

## Life Testing

Assesses durability for:

- Mission duration
- Expected operational environment

Components are subjected to mission-like:

- Loads
- Vibrations
- Temperatures

Typical test life:

```text
~1.5–2× mission life
```

Accelerated testing can use higher loads but must be evaluated carefully to ensure it remains representative.

---

## Bakeout

Purpose:

- Reduce outgassing
- Prevent self-contamination
- Support planetary protection

Strategy:

- Heat spacecraft in vacuum
- Typical temperature:
  - ~100–125 °C
- Often performed as part of TVAC

A post-bakeout inspection verifies cleanliness.

---

# 24. Mechanical Subsystem Design Process

> **Source: Slides 41–48**

The lecture presents the mechanical subsystem lifecycle as:

```text
Define Mechanical Requirements
↓
Define Mechanical Architecture
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

> **Source: Slide 43**

Develop Level-4 mechanical requirements from Level-3 flight-system requirements.

Examples:

### Mass

```text
Mechanical subsystem mass < 1,500 kg
```

Drives:

- Sizing
- Materials

### Resonant Frequency

```text
Resonant frequency > 25 Hz
```

Drives:

- Sizing
- Materials
- Layout
- Launch restraints

### Static Launch Load

```text
6 g axial
2 g lateral
```

Drives:

- Sizing
- Materials
- Layout

### Camera Field of View

```text
65° FOV
```

Drives configuration.

---

## Phase B/C — Architecture

> **Source: Slide 44**

Perform mechanical architecture trades and sizing analyses for:

- Primary structure
- Secondary structure
- Driving loads
- Mechanism needs
- Configuration layout
- Material selection
- Mass
- Mass properties

---

## Phase B/C — Design

> **Source: Slide 45**

Mechanical design includes:

- Select materials
- Design structure
- Create CAD configuration
- Create drawings
- Create MEL
- Perform structural analysis
- Iterate design

Relevant FSW may control:

- Deployments
- Solar-array gimbals
- HGA gimbals
- Robotic motors

---

## Phase D — Build and Test

> **Source: Slide 46**

- Integrate structure and mechanisms
- Perform subsystem-level:
  - Qualification testing
  - Protoflight testing
  - Acceptance testing

Test environments include:

- Vibration
- Shock
- Acoustics
- Thermal

---

## Phase D — Delivery to ATLO

> **Source: Slide 47**

Deliver the mechanical subsystem for integration with the rest of the spacecraft.

System-level environmental testing includes:

- Vibration
- Shock
- Acoustics
- Thermal

Execute deployment testing for:

- Solar arrays
- Booms
- Other deployables

---

## Phase E — Operations

> **Source: Slide 48**

During flight:

- Release deployables, usually during early operations
- Trend actuator performance
  - Solar-array gimbal
  - HGA gimbal
  - Robotics motors
- Update FSW when needed

Possible FSW changes include:

- Actuation speed
- Fault limits
- Mechanism operating parameters

---

# 25. Beagle 2 Case Study

> **Source: Slides 49–50**

Beagle 2 was an ESA Mars probe launched in 2003 as part of Mars Express.

It successfully separated from Mars Express but did not establish communication after landing.

## Key Failure

One or more solar panels apparently did not fully deploy.

The incomplete deployment likely obstructed the communications antenna.

**Figure description:** The intended configuration shows all petal-like solar panels fully open. The inferred actual configuration from later imagery shows only a subset apparently deployed, preventing the final configuration required for communications.

---

## Contributing Causes

### No Communication Redundancy

The spacecraft relied on a single communication path.

The deployment failure made that path unusable.

### Landing Challenges

Unexpected atmospheric conditions during EDL may have damaged or affected solar-array deployment hardware.

### Deployment Complexity

Communications success depended on complete solar-array deployment.

A mechanical deployment therefore became a prerequisite for telecom functionality.

### Limited Testing

Budget constraints limited testing under realistic conditions, particularly deployment testing after representative environments.

---

## Lessons Learned

### Redundant Communication Paths

Multiple paths reduce single-point failure risk.

### Robust Deployment Systems

Minimize dependencies in deployment sequences.

### Enhanced Testing

Allocate sufficient:

- Budget
- Schedule
- Test resources

to high-risk operations such as:

- EDL
- Deployments

### Improved Environmental Modeling

Use accurate and adaptive atmospheric models for Martian conditions.

The case illustrates a central systems-engineering lesson:

**A mechanical deployment failure can propagate into a complete mission-level communications failure when subsystem dependencies are not sufficiently fault tolerant.**

---

# 26. Lecture Summary

> **Source: Slides 1–50**

The mechanical subsystem provides the spacecraft's physical structure, interfaces, mechanisms, packaging, and mechanical-environment protection.

Its responsibilities include:

- Primary structure
- Secondary structure
- Tertiary structure
- Mechanisms
- Deployables
- Launch-vehicle interfaces
- Payload interfaces
- Harness accommodation
- Configuration
- Mass properties

Mechanical design is strongly coupled to every spacecraft subsystem.

Configuration must simultaneously satisfy:

- Payload FOVs
- Telecom FOVs
- Thruster plume KOZs
- ACS sensor alignment
- Thermal radiator geometry
- Harness routing
- Launch fairing
- Mass properties
- Testability

Mechanical requirements include more than simple strength.

Important requirements include:

- Strength
- Structural response
- Structural life
- Natural frequency
- Mass properties
- Damping
- Stiffness
- Dynamic envelope
- Positional stability
- Mechanical interfaces

Materials are selected based on:

- Density
- Strength
- Stiffness
- Temperature tolerance
- CTE
- Thermal conductivity
- Radiation resistance
- Manufacturability
- Cost

Common structural approaches include:

- Skin-frame
- Sandwich panels
- Isogrids
- Cylindrical structures

Mechanisms include:

- Actuators
- Gimbals
- Hinges
- Restraints
- Locks
- Pyrotechnic releases
- Springs
- Motors

The mechanical subsystem must survive:

- Axial acceleration
- Lateral acceleration
- Sine vibration
- Random vibration
- Acoustics
- Shock
- Thermal cycling
- Radiation
- MMOD
- Repetitive fatigue loads

Key structural equations include:

```math
\sigma = \frac{F}{A}
```

```math
\tau = \frac{V}{A}
```

```math
\epsilon = \frac{\Delta L}{L_0}
```

```math
\sigma = E\epsilon
```

```math
\sigma = \frac{My}{I}
```

```math
\tau = \frac{Tr}{J}
```

```math
\sigma_{\text{thermal}} = E\alpha\Delta T
```

and:

```math
SF
=
\frac{\text{Material Strength}}
{\text{Applied Stress}}
```

Analysis and test are tightly coupled.

Major analysis areas include:

- Static/stress
- Coupled loads
- Finite-element analysis
- Dynamics
- Modal response
- Thermal response
- Fatigue

Major test areas include:

- Static loads
- Sine vibration
- Random vibration
- Shock
- Acoustics
- Modal testing
- TVAC
- Fatigue
- Mass properties
- Life testing
- Bakeout

The design process is iterative:

```text
Requirements
↓
Architecture
↓
Materials / Structure / Mechanisms / Configuration
↓
Analysis
↓
Hardware and FSW Design
↓
Build and Test
↓
ATLO and System-Level Test
↓
Flight Operations
```

The Beagle 2 case study demonstrates why mechanical design must be treated as a spacecraft-level systems problem. A solar-array deployment issue likely prevented antenna operation, turning a mechanism failure into loss of communications and therefore loss of mission.
