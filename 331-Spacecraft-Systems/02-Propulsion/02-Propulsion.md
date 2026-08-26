# Propulsion System

**Course:** ASTE-331a — Spacecraft Systems Engineering  
**Lecture:** 02 — Propulsion System (aka Propulsion or simply Prop)  
**Instructors:** Jim Chase, Danielle Marsh   
**Source:** `331_02_Propulsion_20250905.pdf`

------------------------------------------------------------------------

## Lecture Overview

This lecture develops the spacecraft propulsion subsystem from basic
physical principles through architecture selection, requirements,
schematic design, sizing, hardware selection, and integrated-system
trades.

The lecture begins with the function of propulsion and examples of
cold-gas, solid, liquid, and electric propulsion. It then introduces the
rocket equation and ideal gas law, followed by a lunar sample-return
example showing how mission operations drive propulsion architecture.

The main design workflow is:

1.  Understand the mission concept of operations and propulsion
    requirements.
2.  Select a candidate propulsion architecture.
3.  Create a propulsion schematic.
4.  Calculate required propellant from the $\Delta V$ budget.
5.  Size propellant tanks.
6.  Size pressurant and pressurant tanks.
7.  Estimate wet and dry propulsion-system mass.
8.  Select and place thrusters.
9.  Build the Master Equipment List (MEL) and propellant budget.
10. Iterate the design while considering redundancy, reliability, cost,
    contamination, testability, and mission risk.

The lecture uses multiple real spacecraft examples, including
OSIRIS-REx, Cassini, GPM, EO-1, Magellan, and MESSENGER.

------------------------------------------------------------------------

## Table of Contents

- [1. Propulsion Introduction](#1-propulsion-introduction)
- [2. Propulsion Background and
  Theory](#2-propulsion-background-and-theory)
- [3. Architecture Selection](#3-architecture-selection)
- [4. Requirements and Propellant
  Budgets](#4-requirements-and-propellant-budgets)
- [5. Propulsion Schematics](#5-propulsion-schematics)
- [6. Propulsion Schematic Examples](#6-propulsion-schematic-examples)
- [7. Propulsion Subsystem Sizing](#7-propulsion-subsystem-sizing)
- [8. ACS / RCS Thruster Design and
  Placement](#8-acs--rcs-thruster-design-and-placement)
- [9. Propulsion Hardware](#9-propulsion-hardware)
- [10. Primary Propulsion Design
  Artifacts](#10-primary-propulsion-design-artifacts)
- [11. Integrated-System Requirements and Schematic
  Interpretation](#11-integrated-system-requirements-and-schematic-interpretation)
- [12. Propulsion System Trades](#12-propulsion-system-trades)
- [13. Mars Observer Case Study](#13-mars-observer-case-study)
- [14. Lecure Summary](#14-lecture-summary)


------------------------------------------------------------------------

# 1. Propulsion Introduction

## Propulsion Overview

> **Source: Slide 2**

### Function

The propulsion subsystem:

- Provides thrust for trajectory-design maneuvers and often attitude
  control.
- Is typically driven primarily by the trajectory and corresponding
  $\Delta V$ budget.
- Uses components selected to meet minimum requirements while minimizing
  mass, power, and cost.

### Small Solar Orbiter Example

Example propulsion hardware:

- 12 × 0.7-N orbit and attitude-control thrusters
- 8 × 0.04-N warm-gas thrusters
- Warm-gas generator
- Propellant tank
- Miscellaneous hardware
- Total mass: ~13 kg

### Common Components

**Chemical propulsion**

- Monopropellant
- Bipropellant
- Fuel/propellant tanks
- Thrusters
- Integration hardware

**Other propulsion**

- Solid Rocket Motors (SRMs)
- Electric propulsion systems

### Key Trades and Analyses

- Propulsion type: solid, monopropellant, bipropellant, electric
- Thruster sizing
- Fuel-tank sizing
- Heritage from prior systems

### Key Parameters

- Subsystem mass
- Power
- Cost
- Thruster specific impulse, $I_{sp}$
- Thruster locations
- Cant angles
- Propellant load
- Propellant margins

**Figure description:** The slide includes a propulsion schematic for
the Small Solar Orbiter. A gas-generator/accumulator arrangement
supplies twelve 0.7-N monopropellant thrusters and two groups of eight
0.04-N warm-gas thrusters.

------------------------------------------------------------------------

## Basic Mechanics of Propulsion

> **Source: Slide 3**

A propulsion system is built around several major functions:

- Architecture
- Propellant and pressurant tanks
- Thrusters / engines / motors
- Manifold
- Redundancy
- Sizing
- Iteration

### Manifold Design

The manifold can contain:

- Lines
- Filters
- Regulators
- Flow-control devices
- Valves
  - Solenoid/latch valves
  - Check valves
  - Pyrotechnic valves
- Pressure transducers
- Temperature sensors

**Figure description:** The conceptual diagram begins with tanks for
gas, propellant, and pressurant. These feed a large manifold-design
region, which then distributes fluid to thrusters, engines, or motors. A
separate pressurant manifold may feed the propellant tank. Photographs
show representative tanks, thrusters, and valves.

The design is iterative: architecture, tanks, manifold, thrusters,
redundancy, and sizing must be repeatedly reconciled.

------------------------------------------------------------------------

## Common Propulsion Systems

> **Source: Slide 4**

### Cold-Gas Thruster Systems

- Generate thrust by expansion of a pressurized gas.
- Typically used for orbit maintenance and/or attitude control.
- Simpler system.
- Lower mass and cost.
- Lower specific impulse:

$$
I_{sp}\approx45\text{–}73\text{ s}
$$

### Solid Rocket Motors

- Generate thrust by combustion of a solid propellant.
- Typically used for ascent and orbit insertion.
- Simple design with no moving parts.
- High specific impulse:

$$
I_{sp}\approx290\text{–}304\text{ s}
$$

### Liquid Propulsion Systems

- Use liquid propellant(s) to generate thrust.
- Used for orbit insertion, orbit maintenance, and attitude control.

Typical specific impulse:

| System         | Typical $I_{sp}$ |
|----------------|-----------------:|
| Monopropellant |        200–235 s |
| Bipropellant   |        274–467 s |
| Dual-mode      |        200–467 s |

Complexity and cost vary and are traded against efficiency and mass.

### Electric Propulsion

- Uses electrical power to accelerate propellant through an electric or
  magnetic field.
- Typically used for:
  - Interplanetary trajectories
  - Orbit maintenance
  - Attitude control
- Increased complexity and cost.
- Very high specific impulse:

$$
I_{sp}\approx500\text{–}3000\text{ s}
$$

------------------------------------------------------------------------

## OSIRIS-REx Example

> **Source: Slide 5**

OSIRIS-REx uses a monopropellant system with **28 engines**:

- 4 high-thrust main engines
- 6 medium-thrust engines
- 16 attitude-control thrusters
  - 2 per corner
- 2 specialized low-thrust engines for Touch-and-Go sample collection

**Figure description:** The spacecraft configuration identifies the
helium tank and 200-N thrusters. A propulsion schematic shows gaseous
helium pressurization feeding an $N_2H_4$ hydrazine system and
distributing propellant to main engines, trajectory-correction engines,
attitude-control thrusters, and low-thrust engines.

------------------------------------------------------------------------

## Cassini Example

> **Source: Slide 6**

Cassini demonstrates the complexity that can appear in a mature
spacecraft propulsion schematic.

**Figure description:** The slide shows Cassini near Saturn, a
photograph of the spacecraft during integration, and a detailed
propulsion-system schematic containing tanks, pressure-control
assemblies, propellant isolation assemblies, main engines, and multiple
thruster-cluster assemblies.

The point of the slide is that although a complete flight schematic
initially appears complicated, it can be understood by recognizing the
individual components and their functions.

------------------------------------------------------------------------

# 2. Propulsion Background and Theory

## Rocket Equation

> **Source: Slide 7**

The **rocket equation** is used to calculate the propellant required to
generate a change in velocity, $\Delta V$.

It applies to vehicles that generate thrust by expelling mass and is
based on conservation of momentum.

Momentum is:

$$
P=mv
$$

The Tsiolkovsky / classical / ideal rocket equation can be written:

$$
m_0=m_f e^{\Delta V/v_e}
$$

or equivalently:

$$
m_f=m_0e^{-\Delta V/v_e}
$$

where:

- $m_0$ = initial mass
- $m_f$ = final mass
- $\Delta V$ = change in velocity
- $v_e$ = exhaust velocity

Specific impulse relates to exhaust velocity by:

$$
v_e=g_0I_{sp}
$$

For spacecraft:

- Initial mass $m_0$ = spacecraft wet mass
- Final mass $m_f$ = spacecraft dry mass
- Propellant mass:

$$
m_p=m_0-m_f
$$

The equation can be applied to total mission $\Delta V$ or sequentially
to individual burns. Sequential application is required when dry mass
changes during the mission, such as when a probe is released.

### Common $\Delta V$ Uses

- Launch and landing
- Inclination changes
- Orbit maintenance
- Attitude control
- Momentum dumps

**Figure description:** A momentum-conservation graphic illustrates a
rocket before and after expelling a small mass. A MESSENGER trajectory
diagram shows that real missions may contain many separate $\Delta V$
events.

------------------------------------------------------------------------

## Ideal Gas Law

> **Source: Slide 8**

Gases are used in propulsion systems:

- Directly as propellant, such as in cold-gas systems.
- Indirectly as pressurant for liquid propellants.

To function within specifications, thrusters require
gas/liquid propellant to enter the thruster at a
specified pressure.

The ideal gas law is used to estimate required pressurant mass and
volume:

$$
PV=nRT
$$

where:

- $P$ = pressure, Pa
- $V$ = volume, m³
- $T$ = temperature, K
- $n$ = gas mass, kg
- $R_s$ = specific gas constant, J/(kg·K)

When pressure is expressed in bar and volume in liters, the slide gives:

$$
PV=\frac{nRT}{100}
$$

The ideal-gas relationship is a useful approximation for many propulsion
gases.

For some gases, including hydrogen and high-pressure helium, other
equations or correction factors may be required.

**Figure description:** One diagram shows a cold-gas system with storage
tank, regulator, valve, and nozzle. Another shows a pressure-fed liquid
system where high-pressure gas acts through a regulator on a
liquid-propellant tank, forcing propellant through a flow-control valve
into the rocket.

------------------------------------------------------------------------

# 3. Architecture Selection

## Lunar Sample Return Architecture

> **Source: Slides 9–10**

### Review the Concept of Operations

Determine where and how much thrust is needed:

- Trajectory maneuvers and orbit insertion
- Orbit maintenance
- Attitude control
  - Propulsion versus GN&C
- Special considerations such as lunar ascent

Then determine what type of propulsion system accommodates each use.

Important considerations:

- Mass efficiency
- Cost
- Consolidation of different propulsion-system types
- $\Delta V$
- Dry mass
- Redundancy
- Sample contamination
- Optical-instrument constraints

### Perform Analysis and Iterate

- Consider design at system and subsystem levels.
- Develop a propulsion schematic for each required propulsion system.
- Select off-the-shelf tanks and thrusters based on sizing analyses.

### Lunar Sample Return Example Architecture

**Launch**

- Atlas V-class launch vehicle
- Liquid engines + SRM boosters

**Lunar Braking and Landing System**

- Ejected SRM + monopropellant
- 12 high-thrust engines

**Ascent System**

- SRM + monopropellant
- 6 high-thrust engines
- 8 attitude-control thrusters

**Sample Return Capsule**

- No propulsion system
- Earth atmosphere provides braking
- Low mass/drag ratio reduces velocity
- Helicopter catch used for recovery

**Comsat**

- Single-string monopropellant system
- 1 mid-thrust engine
- 8 attitude-control thrusters

Total excluding launch vehicle:

$$
37 = 2\text{ SRMs}+35\text{ thrusters}
$$

**Figure description:** The mission diagram follows launch, trans-lunar
cruise, lunar orbit insertion, LL2 staging, lunar
approach/descent/landing, surface operations, ascent, trans-Earth
cruise, Earth approach/EDL, and sample recovery. A communications
satellite remains in lunar orbit and communicates through DSN.

------------------------------------------------------------------------

## Propulsion System Architecture Tree

> **Source: Slide 11**

The architecture tree separates propulsion into **Chemical** and
**Electric Propulsion (EP)**.

### Chemical

#### Gas

**Cold Gas**

- Blowdown
  - Simpler, shorter-duration missions
  - Simpler/safer integration and test
- Regulated
  - Mitigates leakage
  - Provides longer life

**Hot Gas**

- Uses a hydrazine gas generator to provide low thrust.

#### Liquid

**Monopropellant**

- Simplest and most reliable for missions requiring moderate capability.
- Typical $\Delta V$ in the hundreds of m/s.

Variants:

- Blowdown
- Regulated
- Recharge

**Bipropellant**

- Higher efficiency for larger missions.
- More complex and costly.

Variants:

- Bipropellant
- Dual Mode
- Cryogenic

#### Solid Rocket Motors

- Typical SRMs are simple, highly reliable, and low cost.
- Usually inflexible after propellant is cast.

Variants:

- Standard SRM
- SRM Hybrid
- Other SRM applications

### Electric Propulsion

- Very high efficiency for large $\Delta V$ trajectories and
  long-duration attitude control.
- Requires significant power, often kW.

Variants:

- Solar EP
- Nuclear EP
- EP Hybrid

**EP Hybrid:** EP provides long-term $\Delta V$ and/or ACS, while
chemical propulsion handles shorter maneuvers.

------------------------------------------------------------------------

# 4. Requirements and Propellant Budgets

## Example L3 and L4 Requirements

> **Source: Slide 12**

### Flight System Requirements

**L3_FS_001:** The flight system shall support spacecraft dry-mass
allocations that include propulsion-subsystem dry mass.

|                     |    S/C-A |    S/C-B |
|---------------------|---------:|---------:|
| Dry Mass Allocation | 655.8 kg | 653.2 kg |

**L3_FS_002:** The flight system shall provide fully redundant 3-axis
attitude and translational control to support science operations.

**L3_FS_003:** The flight system shall provide full redundancy to ensure
operations over a five-year lifetime. Components not required for the
full five-year mission duration do not necessarily need to be redundant.

### GN&C Subsystem Requirements

**L4_GNC_001:** The GN&C subsystem shall accommodate a Mars gravity
gradient with an average spacecraft torque of:

$$
0.00012\text{ N·m}
$$

**L4_GNC_002:** The GN&C subsystem shall provide daily momentum dumps at
Mars to desaturate the GN&C system.

A reasonable thruster burn time is:

$$
5\text{–}20\text{ s}
$$

for a momentum dump.

------------------------------------------------------------------------

## Example L4 Propulsion Requirements

> **Source: Slide 13**

**L4_Prop_001:** The propulsion subsystem shall support the specified
$\Delta V$ budget.

| Maneuver                     | S/C-A $\Delta V$ (m/s) | S/C-B $\Delta V$ (m/s) |
|------------------------------|-----------------------:|-----------------------:|
| Phasing                      |                   55.6 |                    0.0 |
| TCM-1                        |                    0.0 |                   25.0 |
| TCM-2                        |                    3.0 |                    3.0 |
| TCM-3                        |                    1.0 |                    1.0 |
| TCM-4                        |                    1.0 |                    1.0 |
| TCM-5                        |                    5.0 |                    5.0 |
| Mars Orbiter Insertion (MOI) |                  814.5 |                  813.7 |
| Gravity Loss                 |                   49.1 |                   57.5 |
| Lower Apogee – 1             |                  537.2 |                  652.2 |
| Gravity Loss                 |                    9.2 |                   18.4 |
| Lower Apogee – 2             |                  537.2 |                  652.2 |
| Gravity Loss                 |                    6.5 |                   12.2 |
| Reserves                     |                   50.0 |                   50.0 |
| **Total**                    |             **2069.3** |             **2291.0** |

A phasing event delays spacecraft A orbit insertion by five days.

**L4_Prop_002:** The propulsion subsystem shall accommodate additional
propellant masses separate from trajectory propellant.

| Item                           |   S/C-A |   S/C-B |
|--------------------------------|--------:|--------:|
| Propellant residuals & hold-up | 24.0 kg | 24.0 kg |
| RCS propellant                 | 20.0 kg | 20.0 kg |

**L4_Prop_003:** The propulsion subsystem shall provide thrust-vector
control for main-engine burns using four 22-N monopropellant thrusters
to offset Mars gravity losses.

------------------------------------------------------------------------

## Detailed Propellant Budget

> **Source: Slide 14**

A detailed propellant budget applies the rocket equation sequentially
across mission maneuvers.

For each maneuver:

1.  Select propulsion system.
2.  Use its $I_{sp}$.
3.  Begin with initial spacecraft mass $M_0$.
4.  Calculate delivered mass $M_f$ from the rocket equation.
5.  Calculate propellant:

$$
M_p=M_0-M_f
$$

6.  Subtract released payload dry mass, if applicable.
7.  Use the resulting mass as the initial mass for the next maneuver.

General pattern:

$$
M_f=f(M_0,\Delta V,I_{sp})
$$

$$
M_p=M_0-M_f
$$

$$
M_{0,\text{next}}=M_{f,\text{previous}}-\Delta M_{\text{dry}}
$$

Selection of monopropellant versus bipropellant is based on:

1.  Required thrust / burn time
2.  Efficiency
3.  Timing relative to repressurization events

Engine cant can also reduce effective thrust and may need to be
included.

------------------------------------------------------------------------

# 5. Propulsion Schematics

## Schematic Diagrams

> **Source: Slide 15**

The first critical step in designing a propulsion subsystem is creating
a **draft schematic diagram**.

The schematic helps identify:

- System requirements
- System features
- Interfaces
- Redundancy
- Components

Before creating it, determine:

### Propulsion Architecture

- Cold gas
- Monopropellant
- Bipropellant
- Dual-mode
- SRM
- Electric

### Pressure Architecture

- Blowdown
- Regulated

### Hardware Quantities

- Number and size of propellant tanks
- Number and size of pressurant tanks
- Number and size of thrusters

### Redundancy

**Single-string**

- Any single fault may cause system failure.

**Selected redundancy**

- More critical or less reliable components are redundant.

**Full redundancy**

- Generally requires two faults before failure.
- Common exceptions may include tanks, main engines, some propellant
  lines, etc.

If information is unavailable, explicitly state assumptions before
continuing.

------------------------------------------------------------------------

## Schematic Design Approach

> **Source: Slide 16**

### Objectives

- Provide propellant needed by thrusters:
  - Where
  - When
  - How much
- Prevent:
  - Leaks
  - Mixing
  - Backflow
  - Contaminants
- Provide adequate:
  - Monitoring
  - Servicing
  - Testing

### Approach

1.  Place tanks and thrusters based on architecture.
2.  Add lines, filters, regulators, etc.
3.  Select and add valves based on function.
4.  Add pressure and temperature monitoring.

### Review and Iteration

- Review required redundancy.
- Iterate at system and subsystem levels.
- Minimize cost for the appropriate level of risk.

The lecture emphasizes that there is rarely a perfect answer. Designs
vary with mission constraints and acceptable risk, and selections must
be defendable.

------------------------------------------------------------------------

## Component Symbols and Descriptions

> **Source: Slide 17**

| Component                     | Function                                                                                                                                 |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Tank                          | Stores propellant; liquid systems may include internal devices separating propellant and pressurant and reducing slosh                   |
| System Filter                 | Removes unexpected particulates; typically downstream of tanks and service valves                                                        |
| Isolation / Latch Valve       | Provides controlled open/closed flow without continuous electrical power; used between tank and thruster and for isolating branches      |
| Pyrotechnic Valve             | Single-use valve that begins open or closed and changes state once after pyro activation                                                 |
| Check Valve                   | Allows flow in only one direction and can prevent unintended fuel/oxidizer mixing                                                        |
| Service Valve                 | Used to fill/drain tanks and support end-to-end functional testing                                                                       |
| Dual-Stage Pressure Regulator | Controls downstream pressure; dual stage improves pressure/flow stability                                                                |
| Cavitating Venturi            | Controls pressure drop relatively independently of downstream fluctuations; useful for mixture-ratio control and water-hammer prevention |
| Pressure Transducer           | Monitors pressure for ground and flight operations                                                                                       |
| Temperature Sensor            | Monitors temperature for ground testing and flight operations                                                                            |
| Thruster                      | Small rocket engine used for spacecraft course or attitude changes                                                                       |
| Solid Rocket Motor            | Solid motor requiring data/power interface rather than a fluid manifold connection                                                       |
| Lines & Fittings              | Typically titanium or stainless steel                                                                                                    |

Pyrotechnic valve notation:

- NO = Normally Open
- NC = Normally Closed

------------------------------------------------------------------------

## Other Symbol Variations

> **Source: Slide 18**

Different propulsion programs use different schematic symbols for
similar components.

Examples shown include alternative symbols for:

- Flexible lines
- Check valves
- Pyro valves
- Regulators
- Pressure transducers
- Filters
- Isolation valves
- Service/fill/drain valves
- Solenoid valves
- Engine valves
- Orifices
- Temperature transducers
- Thrusters

**Key point:** Do not assume a symbol has the same meaning across every
schematic. Read the legend.

------------------------------------------------------------------------

## Example Exercise

> **Source: Slide 19**

For each propulsion schematic example:

> Identify each component and understand its function.

------------------------------------------------------------------------

# 6. Propulsion Schematic Examples

## Example 1 — Microsat Cold-Gas System

> **Source: Slide 20**

Adelis-SAMSON satellite cold-gas propulsion system.

### Requirements

- Total impulse: ≥ 150 N·s
- Propulsion-system mass: ≤ 2 kg
- Non-toxic, non-flammable, non-explosive propellant
- Total thrust: 80 mN
- Propellant: **Krypton**

### Pressure Levels

High-pressure section:

$$
160\text{ bar}\approx2321\text{ psi}
$$

Low-pressure section:

$$
2\text{ bar}\approx29\text{ psi}
$$

### Components

- Propellant tank
- Filter
- High-pressure transducer
- Fill and vent valve
- Latch valve
- High-pressure regulator
- Low-pressure regulator
- Low-pressure transducer
- Four-branch manifold
- Four solenoid valves
- Four nozzles

The slide notes that a single dual-stage regulator is more common than
separate high- and low-pressure regulators.

------------------------------------------------------------------------

## Example 2 — Simple Monopropellant Blowdown

> **Source: Slide 21**

### Assumptions

- Diaphragm tank
- No external pressurant system
- One-year mission life

### Architecture

Hydrazine tank with:

- Pressure monitor
- Fill/drain valve at top
- Fill/drain valve at bottom
- Pyrotechnic valve
- Additional service valve
- Filter
- Latch valve
- Thruster branches

### Design Notes

- Pyro valve enables the system for use.
- Latch valve controls propellant flow to thrusters.
- Service valves at top and bottom of tank support ground operations.
- An additional service valve is added downstream of the pyro valve for
  testing.
- Because the pyro valve is more likely to introduce contamination than
  be damaged by it, the filter is placed **after the pyro valve** and
  before the latch valve.

------------------------------------------------------------------------

## Example 3 — GPM Monopropellant Blowdown

> **Source: Slide 22**

### Spacecraft

Global Precipitation Measurement (GPM):

- Mass: 3850 kg
- Power: 1.95 kW

RCS uses chemical propulsion for:

- Attitude control
- Reaction-wheel momentum dumps
- Low-Earth-orbit maintenance

### Thrusters

12 total:

- 8 aft
  - 4 straight
  - 4 90-degree nozzles
- 4 forward-facing

All thrusters support attitude control and reaction-wheel dumps.

Only forward thrusters support maneuvers.

Hydrazine is decomposed catalytically using heated platinum/palladium
catalyst beds.

Thrust decreases during blowdown:

- Launch:

$$
44.5\text{ N at }27.6\text{ bar}
$$

- End of life:

$$
13.3\text{ N at }6.8\text{ bar}
$$

Attitude control uses pulse mode; orbital maneuvers use steady-state
firing.

### Tank

- 545 kg hydrazine at launch
- 27.6 bar launch pressure
- Qualified to 34.5 bar
- Burst pressure: 55.2 bar
- Minimum flight pressure: 6.8 bar
- Temperature range: 2–50 °C
- Minimum hydrazine storage life: 10 years
- Pressurization: 6.2 kg $N_2$

### Schematic Features

- Redundant pressure transducers
- Filter downstream of tank
- Cavitating venturis
- Isolation valves
- Redundant valves at thrusters

------------------------------------------------------------------------

## Example 4 — EO-1 Monopropellant Blowdown

> **Source: Slide 23**

EO-1 was a low-cost technology demonstrator.

It also had:

- Magnetic torquers
- Reaction wheels
- Electric propulsion

Therefore the monopropellant system was primarily used for **orbit
raises**.

The schematic includes:

- $GN_2$ pressurant
- $N_2H_4$ hydrazine
- Pressure transducer
- Temperature sensors
- Service valves
- System filter
- Cavitating venturi
- Latch valve with back-pressure regulator
- Four dual-valve REAs

A cavitating venturi and back-pressure regulator are combined to
maintain a defined downstream pressure.

------------------------------------------------------------------------

## Example 5 — Cassini Bipropellant Main Engine Assembly

> **Source: Slides 24–28**

Cassini's Main Engine Assembly (MEA) supported Saturn orbit insertion
and more than 100 other maneuvers.

### Propellants

- Oxidizer: NTO
- Fuel: MMH

The system is fully redundant.

- REA-A = primary engine
- REA-B = redundant engine
- REA-B was never ultimately used.

### Pressure States

The slides identify representative primary-line pressures including
approximately:

- 235 psia primary oxidizer
- 237 psia primary fuel
- 216 psia primary oxidizer
- 193 psia primary fuel
- Redundant oxidizer/fuel lines vented to approximately 0 psia when
  inactive

### Main Engine Flow-Control Sequence

1.  **Pyro valve**

    - Starts open.
    - Closes when switching to backup engine.

2.  **Cavitating venturi**

    - Restricts flow.
    - Protects downstream latch-valve/BPR hardware.

3.  **Primary latch valve with back-pressure regulator**

    - Drops pressure.

4.  **Secondary pyro valve**

    - Opens if primary latch valve fails closed.

5.  **Oxidizer and fuel engine valves**

    - Control engine operation.
    - Control mixture ratio.

The oxidizer and fuel manifolds are functionally similar.

### Redundancy Logic

- Pyro valves select primary versus redundant main engine.
- Isolation with backup pyro valves minimizes potential leakage.
- Engine valves control thrust duration.

### Failed Engine-Valve Reconfiguration

If an engine valve fails:

1.  Open the required four valves.
2.  Attempt primary engine operation.
3.  If a valve is stuck closed, reconfigure the manifold.
4.  Fire the backup engine.

**Figure description:** A sequence of simplified valve diagrams shows
the nominal configuration, attempted firing, failed closed valve, and
reconfiguration to the redundant engine.

------------------------------------------------------------------------

## Pyro-Ladders

> **Source: Slide 29**

A pyro-ladder allows discrete pressurization events while minimizing
long-term leakage.

Sequence:

1.  Open `Pyro-NC-1`.
2.  Tank pressurizes.
3.  Close `Pyro-NO-1`.
4.  Repeat for the next rung.

In the example schematic, the oxidizer can be pressurized **four
times**.

Pyro ladders are useful when a long mission needs several isolated
pressurization events.

------------------------------------------------------------------------

## Propulsion Schematic Instructions

> **Source: Slide 30**

1.  **Place estimated propellant and pressurant tanks.**

2.  **Add thrusters.**

    - Group by type or redundancy string.
    - Use symbol size to indicate relative thrust.

3.  **Add lines, filters, regulators, and flow-control devices
    downstream of tanks.**

    - Filters remove contaminants.
    - Regulators, venturis, and BPRs protect downstream hardware.

4.  **Add valves appropriate to function.**

    - Isolation valves for on/off control.
    - Pyro/check valves for ground or flight safety.
    - Pyro ladders for controlled events with reduced leakage.
    - Service valves for fueling, draining, and testing.

5.  **Add pressure transducers and temperature sensors.**

    - Pressure transducers are often placed opposite service valves.
    - Temperature sensors are often omitted from simplified schematics.

6.  **Review redundancy.**

    - In a fully redundant design, no single fault should cause mission
      failure, subject to accepted exceptions.

7.  **Perform checks and labeling.**

    - Avoid back-flowing filters.
    - Ensure system-level testability after spacecraft integration.
    - Label oxidizer, fuel, pressurant, thrusters, SRMs, and notes.

8.  **Determine component sizing, complexity, and cost; iterate.**

------------------------------------------------------------------------

## Schematic Template

> **Source: Slide 31**

The blank schematic template provides symbols for:

- Tank
- Tank with pressurant
- System filter
- Isolation/latch valve
- Normally closed pyro valve
- Normally open pyro valve
- Single-string check valve
- Dual-string check valve
- Service valve
- Dual-stage pressure regulator
- Cavitating venturi
- Pressure transducer
- Temperature sensor
- Single-valve thruster
- Dual-valve thruster
- Solid rocket motor
- Lines and fittings

The lecture emphasizes that an initial design does not have a single
perfect answer. The important requirement is to understand and defend
component selections.

------------------------------------------------------------------------

# 7. Propulsion Subsystem Sizing

## Five Design Steps

> **Source: Slide 32**

1.  Create a draft schematic.
2.  Use $\Delta V$ to determine propellant quantity.
3.  Use propellant quantity to determine tank size.
4.  Use tank size to determine pressurant quantity and tank size.
5.  Estimate wet/dry system mass.

------------------------------------------------------------------------

## Step 1 — Architecture and Draft Schematic

> **Source: Slide 33**

Identify candidate architecture and create a preliminary schematic.

Consider:

- Number/type of tanks
- Number/type of thrusters
- Pressure regulator for regulated systems
- Latch valves for nominal control
- Pyro valves/ladders for isolation and redundancy
- Check valves
- Cavitating venturis
- Service valves
- Pressure sensors
- Temperature sensors

For back-of-the-envelope or exam designs, a full schematic may not be
required, but the designer should estimate quantities of regulators,
valves, sensors, etc.

------------------------------------------------------------------------

## Step 2 — Calculate Propellant

> **Source: Slides 34–36**

Required usable propellant depends on:

- Total $\Delta V$
- Spacecraft mass
- Specific impulse

Rocket equation:

$$
\Delta V=g_cI_s\ln\left(\frac{M_i}{M_f}\right)
$$

where:

- $g_c=9.8067$
- $I_s$ = average specific impulse, s
- $M_i$ = initial spacecraft mass, kg
- $M_f$ = final spacecraft burnout mass, kg

Solving for propellant mass:

$$
M_p=M_f\left[\exp\left(\frac{\Delta V}{g_cI_s}\right)-1\right]
$$

### Additional Propellant

Additional propellant may be required for:

- ACS
- Margin
- Trajectory uncertainty
- Performance variations
  - Temperature
  - $I_{sp}$
  - Bipropellant mixture ratio
  - Thruster performance

Residual / hold-up propellant is non-usable.

Typical values:
- Monopropellant: 1%
- Bipropellant: 3.5%

### Splitting Bipropellant Load

For bipropellant and dual-mode systems:

$$
M_{\text{tot prop}}=M_{ox}+M_{fu}
$$

Mixture ratio:

$$
MR=\frac{M_{ox}}{M_{fu}}
$$

Therefore:

$$
M_{ox}=M_{fu}MR
$$

Typical bipropellant:

$$
MR=1.65
$$

For $N_2O_4/MMH$, this approximately allows equal-volume fuel and
oxidizer tanks, improving commonality and reducing cost.

Typical dual-mode:

$$
MR=1.05
$$

For $N_2O_4/N_2H_4$, this can require unequal or non-optimal tanks,
causing either cost or mass penalties.

------------------------------------------------------------------------

## Step 3 — Calculate Tank Size

> **Source: Slide 37**

### Number of Tanks

The number of fuel, oxidizer, and pressurant tanks depends on:

- Required propellant quantity
- Available heritage tank sizes
- Mass
- Cost

Use identical tanks where practical.

### Tank Volume

For monopropellant and bipropellant:

1.  Use propellant density to calculate required liquid volume.
2.  Add an initial **20% tank-capacity margin**.
3.  Account for pressurant volume for simple monopropellant blowdown.
4.  Select heritage tanks satisfying volume requirements.
5.  Iterate with pressurant sizing to minimize mass.

Mass is often used as a proxy for cost when direct cost data are
unavailable.

------------------------------------------------------------------------

## Step 4 — Determine Pressurant

> **Source: Slides 38–41**

Pressurant ensures adequate propellant pressure at the thruster inlet.

Example: a cold-gas thruster may require approximately 100 psia at the
relevant point in the propulsion system.

Sizing must ensure:

- Beginning-of-mission pressure remains within tank limits.
- End-of-mission pressure remains sufficient for thruster operation.

Ideal gas law:

$$
PV=nRT
$$

For typical spacecraft calculations:

$$
T\approx300\text{ K}
$$

For gaseous nitrogen:

$$
R_{GN_2}=296.8\text{ J/(kg·K)}
$$

### Cold-Gas Propellant

At BOM:

$$
P_{BOM}V=n_{BOM}(296.8)(300)
$$

At EOM:

$$
P_{EOM}V=n_{EOM}(296.8)(300)
$$

Expended propellant:

$$
n_{BOM}-n_{EOM}=n_{\text{propellant}}
$$

Combined form:

$$
(P_{BOM}-P_{EOM})V=n_{\text{propellant}}RT
$$

Tank-capacity margin is commonly carried, e.g. 20%.

### Monopropellant Blowdown

Gas mass remains approximately constant while gas volume increases as
liquid propellant is expelled.

At BOM:

$$
P_{BOM}V_{BOM}=nRT
$$

At EOM:

$$
P_{EOM}V_{EOM}=nRT
$$

The change in gas volume equals the expended propellant volume:

$$
V_{EOM}-V_{BOM}=V_{\text{propellant}}
$$

The slide derives:

### End-of-Mission Volume Relationship

V_EOM / V_propellant = P_BOM / (P_BOM − P_EOM)

This can be used to solve tank volume and then pressurant mass.

### Other Configurations

- Multiple blowdown tanks
- Regulated tanks with separate pressurization system

Separate tanks require latch valves to control flow.

### Real-Gas Effects

When ideal-gas assumptions become inaccurate, e.g. helium:

- Use ideal-gas estimate for this class.
- More advanced analysis may use real-gas relationships such as Van der
  Waals.
- An approximate correction factor such as 1.2 may be used when
  appropriate.

------------------------------------------------------------------------

## Step 5 — Estimate Wet and Dry System Mass

> **Source: Slides 42–44**

Create a mass list from all hardware in the schematic.

Representative Current Best Estimates (CBEs):

| Component                     |            Unit Mass |
|-------------------------------|---------------------:|
| Pressure transducer           |               0.3 kg |
| Temperature sensor            |               0.1 kg |
| Latch valve                   |               0.7 kg |
| Service valve                 |              0.25 kg |
| System filter                 |               0.9 kg |
| Cavitating venturi            |               0.1 kg |
| Accumulator                   |              0.25 kg |
| Burst disk                    |               0.2 kg |
| System tubing & fittings      | 5% of hardware above |
| Mounting brackets / fasteners | 5% of hardware above |

Typical contingency / growth allowance:

- Tanks and thrusters: 10%
- Valves, regulators, etc.: 20%
- Tubing, brackets, etc.: 30%

If a component mass cannot be found, use a reasonable placeholder
estimate and label it as such.

### Solid Rocket Motor Sizing

SRMs may provide one-time $\Delta V$ burns.

Total impulse capability:

$$
I_{\text{total}}=F_{\text{SRM}}t
$$

Required impulse:

$$
I_{\text{required}}=m_{\text{wet}}\Delta V
$$

Trajectory design generally attempts to match available and required
impulse. Any difference must be accommodated by another propulsion
system.

### Example Dry-Mass Table

| Component                     | Unit Mass (kg) | Qty | Base Mass (kg) | Contingency | Total Mass (kg) |
|-------------------------------|---------------:|----:|---------------:|------------:|----------------:|
| 490-N Thruster                |           3.76 |   1 |           3.76 |          5% |            3.95 |
| 4-N Thrusters                 |           0.37 |  10 |           3.70 |          5% |            3.89 |
| Pressurant Tank               |           6.00 |   1 |           6.00 |          5% |            6.30 |
| Fuel Tank                     |          11.70 |   1 |          11.70 |          5% |           12.29 |
| Oxidizer Tank                 |          11.70 |   1 |          11.70 |          5% |           12.29 |
| Pressure Transducers          |           0.30 |  12 |           3.60 |          5% |            3.78 |
| Temperature Sensors           |           0.10 |  24 |           2.40 |          5% |            2.52 |
| Pressure Regulator            |           1.10 |   2 |           2.20 |          5% |            2.31 |
| Latch Valves                  |           0.70 |  10 |           7.00 |          5% |            7.35 |
| Service Valves                |           0.25 |  10 |           2.50 |          5% |            2.63 |
| System Filters                |           0.90 |  10 |           9.00 |          5% |            9.45 |
| Cavitating Venturi            |           0.10 |   2 |           0.20 |          5% |            0.21 |
| System Tubes / Fittings       |           3.19 |   — |              — |         30% |            4.14 |
| Mounting Brackets / Fasteners |           3.35 |   — |              — |         30% |            4.35 |
| **Total**                     |                |     |                |             |    **75.44 kg** |

### Example Propellant Mass

| Propellant |     Mass |
|------------|---------:|
| Pressurant |   2.2 kg |
| Hydrazine  | 176.4 kg |
| Oxidizer   | 139.3 kg |

------------------------------------------------------------------------

# 8. ACS / RCS Thruster Design and Placement

## ACS Thruster Design

> **Source: Slides 45–46**

When propulsion is used only for attitude control, it is often called a
**Reaction Control System (RCS)**.

RCS thrusters are typically the smallest propulsion thrusters.

They may back up reaction wheels after a wheel failure, although they do
not provide the same pointing precision.

### Characteristics

- Pointing control:

$$
0.1^\circ\text{–}5.0^\circ
$$

- Many thrust sizes available.
- Propellant-limited.
- May introduce contamination.
- Capable of high torque.
- Accuracy limited by thruster configuration and minimum impulse bit.

### Coupled Thrusters

The graphics show coupled thrusters acting through the spacecraft center
of mass.

For one translational degree of freedom:

- Two coupled thrusters can produce translation without unwanted
  rotation.

For one rotational degree of freedom:

- Two opposing thrusters produce a torque couple.

### Redundancy

Dual redundancy normally means A and B strings.

Thus one fully redundant DOF may require:

$$
4\text{ thrusters}
$$

### Placement

Thrusters are typically:

- On opposite sides of the center of mass
- Near or beyond the outer edge for longer moment arm
- Grouped in clusters of 2–4
- Oriented in different directions

------------------------------------------------------------------------

## 16-Thruster RCS Configuration

> **Source: Slides 47–50**

The notional configuration uses:

- 16 thrusters
- 4 clusters
- 6 degrees of freedom

Arrows show plume direction.

Example commands:

- For $+X$: fire thrusters **1 and 9**
- For $-Z$: fire **8 and 16**
- For rotation about $+Y$: fire **3 and 9**

Slides 48–50 highlight how different pairs produce rotations about the
spacecraft:

- $Y$ axis
- $X$ axis
- $Z$ axis

**Figure description:** Four clusters are placed around a box-shaped
spacecraft. Each cluster contains four differently oriented thrusters.
Opposing pairs provide translation or torque while limiting undesired
coupling.

------------------------------------------------------------------------

# 9. Propulsion Hardware

## Thrusters — Characteristics and Uses

> **Source: Slide 51**

### Primary Characteristics

**Thrust level**

- Example: 1 N versus 490 N
- Determines ability to provide force and $\Delta V$

**Efficiency**

- Specific impulse, $I_{sp}$
- Depends on thruster type and propellant

**Minimum Impulse Bit (MIB)**

- Smallest controllable impulse
- Determines fine-control capability

### Primary Uses

- Trajectory Correction Maneuvers (TCMs)
- Orbital maintenance
- Momentum dumps
- Attitude / reaction control
- Thrust Vector Control (TVC)

### Matching Thrusters to Spacecraft

Evaluate:

- Large $\Delta V$ requirements
- Attitude-control requirements
- Minimum burn time
- Maximum burn time
- MIB
- Maneuver duration

Orbit-insertion burns may need to remain below approximately 2–3 hours.

Typical architecture:

- RCS thrusters for attitude control and momentum dumps
- Main engine(s) for large, efficient $\Delta V$ maneuvers
- Mid-size thrusters for functions such as TVC

Thrust can also be increased by firing multiple thrusters.

------------------------------------------------------------------------

## MR-103G 1-N Thruster Example

> **Source: Slide 52**

Aerojet Rocketdyne MR-103G 1-N-class hydrazine rocket engine assembly.

### Design Characteristics

- Propellant: Hydrazine
- Catalyst: S-405
- Thrust / steady state: approximately 1.13–0.19 N
- Feed pressure: approximately 28.3–4.8 bar
- Chamber pressure: approximately 23.8–4.5 bar
- Expansion ratio: 100:1
- Flow rate: approximately 0.5–0.09 g/s
- Valve: dual seat
- Mass: approximately 0.33 kg

### Performance

- Specific impulse: approximately 224–202 s
- Total impulse: approximately 97,078 N·s
- Total pulses: approximately 835,017
- Minimum impulse bit: approximately 0.0133 N·s under the cited
  condition
- Demonstrated steady-state firing durations of hundreds to thousands of
  seconds per firing and tens of cumulative hours

**Figure description:** The slide includes a photograph, dimensioned
drawing, and manufacturer performance/specification table for the
thruster.

------------------------------------------------------------------------

## Representative Thruster Data

> **Source: Slide 53**

### Cold-Gas Thrusters

| Thruster | Thrust (N) | Mass (kg) | Nominal Pressure (bar) | MEOP (bar) | Heritage                |
|----------|-----------:|----------:|-----------------------:|-----------:|-------------------------|
| 0.01-N   |       0.01 |      0.04 |                    1.5 |         10 | CHAMP, GRACE            |
| 0.04-N   |       0.04 |      0.04 |                    1.5 |         10 | CHAMP, GRACE            |
| 0.12-N   |       0.12 |      0.14 |                    6.9 |       20.7 | SIRTF                   |
| 3.6-N    |        3.6 |      0.23 |                   15.7 |       15.7 | SAFER, SCIT, Pluto Fast |
| 1-N      |        1.0 |     0.115 |                     90 |        186 | GEO applications        |

### Monopropellant Thrusters

| Thruster | Thrust (N) | Mass (kg) | Min Pressure (bar) | Op. Pressure (bar) |
|----------|-----------:|----------:|-------------------:|-------------------:|
| MR-103G  |          1 |      0.33 |                4.8 |               28.3 |
| MR-111G  |          4 |      0.37 |                6.7 |               24.1 |
| MR-106L  |         22 |      0.59 |                5.9 |               27.6 |
| MR-107T  |        110 |      1.01 |                7.0 |               35.0 |
| MR-107U  |        300 |      1.38 |               20.6 |               52.4 |
| MR-80B   |       3100 |     168.0 |               47.2 |               47.2 |

### Bipropellant / Dual-Mode Thrusters

| Thruster | Thrust (N) | Mass (kg) | Min Pressure (bar) | Op. Pressure (bar) | Comments             |
|----------|-----------:|----------:|-------------------:|-------------------:|----------------------|
| R-6F     |         22 |      0.97 |                6.9 |              20.79 | MMH/NTO              |
| R-1E     |        110 |      2.00 |                6.9 |               27.6 | MMH/NTO              |
| R-4D-11  |        490 |      3.76 |                4.1 |               29.3 | MMH/NTO              |
| R-42DM   |        890 |       7.3 |                5.5 |               31.0 | Hydrazine, dual-mode |
| R-40B    |       4000 |      10.5 |               10.3 |               27.6 | MMH/NTO              |

------------------------------------------------------------------------

## Thruster Cant and Cosine Loss

> **Source: Slide 54**

When a thrust vector is intentionally canted or unintentionally
misaligned, there is a cosine loss.

$$
F_{\text{actual}}=F_{\text{spec}}\cos\theta
$$

Example:

$$
F_{\text{spec}}=5\text{ N}
$$

$$
\theta=10^\circ
$$

$$
F_{\text{actual}}=5\cos(10^\circ)=4.92\text{ N}
$$

When sizing a thruster from a required effective force, divide the
required force by the cosine term.

Canting coupled thrusters can provide additional lateral stability.

Sanity checks:

- $0^\circ$: actual thrust equals specified thrust.
- $90^\circ$: zero useful axial thrust.

------------------------------------------------------------------------

## Thruster Stability and Duration

> **Source: Slide 55**

A typical thruster firing contains:

- Rise time
- Steady-state region
- Tail-off

Rise time and tail-off create small inefficiencies.

The **minimum impulse bit** is the minimum-duration / minimum-impulse
controllable firing and therefore affects maneuver and attitude-control
resolution.

Thrusters may operate in:

- Steady-state mode
- Pulse mode

------------------------------------------------------------------------

## Tanks

> **Source: Slides 56–58**

### Tank Design

Propellant tanks must account for:

- Structural/stress analysis
- Dynamic analysis
- Leak-before-burst and flow-growth analysis
- Propellant behavior
- Propellant-management devices (PMDs)

Tank PMDs may include:

- Diaphragms
- Vanes
- Channel meshes
- Surface-tension devices

### Representative Cold-Gas / Pressurant Tanks

| Tank         | Volume (L) | Mass (kg) | MEOP (bar) |
|--------------|-----------:|----------:|-----------:|
| NG-80615-1   |         28 |       6.8 |      310.3 |
| NG-80412-1   |         50 |         7 |        150 |
| NG-80400-1   |       67.3 |        10 |        310 |
| NG-80446-1   |       67.3 |      10.7 |        310 |
| NG-80525-1   |       67.3 |      10.7 |        310 |
| NG-80436-1   |       81.4 |      12.7 |        331 |
| NG-80496-1   |       81.4 |      12.7 |        331 |
| NG-80475-201 |         87 |      16.8 |        310 |
| NG-80592-1   |      129.8 |      20.5 |      185.1 |
| NG-80326-1   |        3.9 |       1.5 |        248 |
| NG-80195-1   |        9.4 |       5.4 |        184 |
| NG-80558-1   |         16 |      5.99 |        175 |
| NG-80314-201 |       36.1 |        16 |        248 |
| NG-80510-1   |       36.6 |      11.9 |      335.8 |

### Representative Liquid-Propellant Tanks

| Tank         | Volume (L) | Mass (kg) | MEOP (bar) |
|--------------|-----------:|----------:|-----------:|
| NG-80568-1   |        3.8 |      1.36 |         24 |
| NG-80296-1   |       58.6 |       3.6 |       29.3 |
| NG-80599     |       94.6 |       6.6 |         22 |
| NG-80462-1   |      161.5 |        10 |         29 |
| NG-80394-1   |      229.2 |      11.7 |       20.7 |
| NG-80561-1   |        311 |     15.88 |       20.7 |
| NG-80373-1   |      337.4 |      13.8 |       20.7 |
| NG-80317-105 |      383.6 |      27.2 |       24.1 |
| NG-80340-1   |      503.8 |      17.1 |         19 |
| NG-80484-1   |      646.6 |      23.4 |       20.7 |
| NG-80432-1   |        858 |      30.7 |       20.7 |
| NG-80425-101 |        938 |      33.1 |       20.7 |
| NG-80501-1   |     1025.4 |      35.4 |         16 |
| NG-80404-5   |       1196 |     37.51 |      10.34 |
| NG-80441-1   |     1275.5 |      41.3 |       17.2 |
| NG-80528-1   |    1511.68 |     55.34 |       20.7 |
| NG-80554-1   |       1754 |      61.2 |       17.2 |

------------------------------------------------------------------------

## Solid Rocket Motors

> **Source: Slide 59**

The slide provides representative STAR solid-motor data spanning small
to large impulse classes.

Examples include:

| Motor     | Dry Mass (kg) | Propellant Mass (kg) | $I_{sp}$ (s) | Total Impulse (kN·s) |
|-----------|--------------:|---------------------:|-------------:|---------------------:|
| Star-3A   |           0.7 |                 0.12 |          241 |                  0.3 |
| Star-3    |           0.7 |                 0.48 |          266 |                  1.3 |
| Star-5A   |           2.4 |                 2.27 |        250.8 |                  5.7 |
| Star-12   |           9.4 |                18.28 |          252 |                 46.0 |
| Star-13   |           4.6 |                30.98 |          273 |                 83.6 |
| Star-17   |           9.5 |                69.63 |        286.2 |                197.9 |
| Star-24   |         18.33 |               199.90 |        282.9 |                560.5 |
| Star-37   |          62.7 |               558.40 |          260 |              1584.46 |
| Star-37FM |          81.5 |              1065.90 |        289.8 |              3051.35 |
| Star-37Y  |          80.6 |              1071.40 |          297 |               3118.2 |

**Figure description:** A STAR 48A motor data sheet shows a
spherical/rounded motor case and long nozzle along with dimensional and
performance specifications.

------------------------------------------------------------------------

## Propellant Management Devices

> **Source: Slide 60**

Diaphragms are often used to prevent propellant and pressurant from
mixing.

However, some tanks use no physical barrier. In those systems, liquid
position is controlled using:

- Vanes
- Channel meshes
- Other surface-tension-based PMDs

These devices manage liquid propellant in low gravity and help ensure
propellant remains available at tank outlets.

------------------------------------------------------------------------

# 10. Primary Propulsion Design Artifacts

> **Source: Slide 61**

Primary propulsion design artifacts:

- Schematic
- Master Equipment List (MEL)
- Propellant budget
- Power analysis
- Cost estimate

Power analysis and cost estimation are identified as later-course /
next-semester topics.

The MEL consolidates component names, unit masses, quantities,
contingency, total mass, and comments.

------------------------------------------------------------------------

# 11. Integrated-System Requirements and Schematic Interpretation

## Example Requirements

> **Source: Slides 62–63**

### Flight System

- Total flight-system mass shall be less than 500 kg.

### Orbital Mechanics

- Flight system shall provide 500 m/s of post-launch $\Delta V$.
- Flight system shall support a maximum $\Delta V$ burn of 400 m/s.
- Alternatively, the flight system may be required to support a
  trajectory $\Delta V$ budget in a specified table.

### Attitude Control

- Propulsion system shall provide 3-axis control while orbiting Mars.
- Propulsion system shall provide a +X-axis spin of 1.0 rpm.

### Propellant

- Propellant tanks shall store 100–110 kg of propellant.

### Thrusters

- Main engine shall support a maximum-duration burn of 40 minutes.

### Pressurization

- Pressurization system shall maintain 400 psia for Mars Orbit
  Insertion.

### Redundancy

- Propulsion system shall be fully redundant.

### Contamination Control

- Propulsion system shall not release hydrazine contaminants.

### Design Skills Connected to Requirements

- Rewrite rocket equation using dry or wet mass.
- Use $\Delta V$ and mass to determine propellant and pressurant.
- Determine number and placement of thrusters.
- Incorporate lower-level constraints.
- Size thrusters based on pressure and burn duration.
- Apply redundancy.
- Consider alternate architectures or propellants when constraints
  demand them.

------------------------------------------------------------------------

## Interpreting a Simple Schematic

> **Source: Slides 64–65**

Questions to ask:

- What are the components?
- What propulsion architecture is shown?
- What mission duration is implied?
- What is wrong with the design?

The example is a:

**Simple monopropellant blowdown hydrazine system**

with:

- Hydrazine tank
- $GN_2$ pressurant
- Pressure transducer
- Pyro valve
- Latch valve
- Thruster branches

Problems identified:

- No filter downstream of pyro valve.
- No service valve below monopropellant tank.
- No service valve downstream of pyro valve to test the latch valve.

------------------------------------------------------------------------

## Interpreting a Regulated Bipropellant Schematic

> **Source: Slides 66–67**

The architecture is a **regulated bipropellant system**.

Major components:

- Helium pressurant
- Regulator
- Oxidizer tank
- Fuel tank
- Check valves
- Filters
- Pyro valves
- Pressure transducers
- Latch valves
- Fill/drain service valves
- Test service valves
- Pyro ladder
- Dual-string coupled thrusters

Issues and corrections:

- No flow control beyond the regulator after first use
  - Add high-pressure latch valve.
- Insufficient control of oxidizer vapors
  - Add pyro ladder.
- Regulator cannot be adequately tested
  - Add service valves.

------------------------------------------------------------------------

## Complex Monopropellant Schematic

> **Source: Slides 68–70**

The schematic includes:

- GHe pressurant
- $N_2H_4$ hydrazine
- Multiple normally open / normally closed pyro valves
- Pressure transducers
- Latch valves
- Multiple thruster classes:
  - 0.9 N
  - 22 N
  - 445 N

Questions include:

- How many repressurization events can be performed?
- What are each thruster class's functions?
- Is the design single-string or dual-string?
- How does propellant/pressurant flow through a selected region?
- What is the minimum electrical wiring needed?
- Identify three redundant regions.

------------------------------------------------------------------------

## Magellan Venus Orbiter

> **Source: Slide 69**

Magellan used a more complex monopropellant blowdown system with an
external pressurant system.

Thrusters:

- 12 × 0.9-N for attitude control
- 4 × 22-N
- 8 × 445-N for orbit insertion and maintenance

A STAR 48 SRM was used for orbit insertion, with 22-N and 445-N
thrusters providing additional control.

The mission's \>1-year flight time and redundancy requirements led to a
series of pyro valves to minimize leaks while retaining the ability to
enable/disable individual branches.

The SRM is not fluid-connected to the manifold and therefore is not
shown as part of the manifold schematic.

------------------------------------------------------------------------

## MESSENGER Bipropellant Pressurization Trade

> **Source: Slides 71–72**

MESSENGER performed a trade study to select its pressurization
architecture.

Constraint:

- 6-year trajectory
- 6 large maneuvers
- Maneuvers distributed over the last three years of cruise

This combination required a design that minimized leakage and mixing
risk.

The options used similar components in different arrangements.

A pyro ladder provides a discrete number of on/off pressurization events
while using pyrotechnic isolation to reduce leakage.

### Design Selection

- **Option 1:** insufficient protection against propellant mixing; Mars
  Observer lessons learned were relevant.
- **Options 2 and 3:** technically good, but heavier and more expensive.
- **Option 4:** required a somewhat new tank design but was more
  efficient and safer.

------------------------------------------------------------------------

# 12. Propulsion System Trades

## Trade Summary — Part 1

> **Source: Slide 73**

### Solid Rocket Motor

**Pros**

- Simple design
- Few/no moving parts
- Minimal pre-launch preparation
- Easy on-orbit readiness
- No leakage/slosh concerns
- Low system mass for some total-impulse ranges
- Highly reliable kick-stage solution for fixed total impulse

**Cons**

- Inadvertent ignition/explosion can be catastrophic
- Inflexible to propellant-mass changes after casting/machining
- Complex/toxic exhaust may be unacceptable for some applications

### Electric Propulsion

**Pros**

- Very high efficiency for high-$\Delta V$ trajectories
- Can minimize total flight-system mass

**Cons**

- Requires significant electrical power, often kW-class

### Cold Gas

**Pros**

- Low total system mass and cost for low-impulse applications
- Simpler than liquid systems
- Non-hazardous pre-launch preparation
- Easy on-orbit preparation
- No liquid slosh / center-of-gravity issues

**Cons**

- Leakage concerns, especially for long missions
- Increased total-impulse requirements can rapidly make the architecture
  non-optimal

------------------------------------------------------------------------

## Trade Summary — Part 2

> **Source: Slide 74**

### Monopropellant

**Pros**

- Simple, reliable blowdown architecture
- Reasonably mass-efficient for small/medium $\Delta V$
- Many heritage tanks and thrusters
- Stable across wide range of impulse bits and burn durations
- Small thrusters qualified for \>1 million pulses
- Suitable for long-life missions
- Relatively simple exhaust products

**Cons**

- Blowdown tank mass inefficiency
- Regulated systems improve mass efficiency but add cost/complexity
- Hydrazine is toxic during fueling
- Not mass-efficient for very small total-impulse systems
- More expensive than cold gas

### Bipropellant

**Pros**

- High $I_{sp}$ and good mass efficiency for medium/large $\Delta V$
- Typical mixture ratio can allow equal-volume fuel/oxidizer tanks
- Many heritage tanks and thrusters
- Stable over useful pressure/temperature range
- Long burns greater than 60 minutes demonstrated

**Cons**

- No qualified low-thrust thrusters below approximately 10 N in the
  lecture's example set
- Requires regulated pressurization
- Exhaust is more complex/toxic than monopropellant
- Propellants are toxic during fueling
- More complex, costly, and potentially less reliable than
  monopropellant

### Dual-Mode — Monopropellant + Bipropellant

**Pros**

- Higher performance
- Good mass efficiency for medium/large systems
- Simpler hardware layout than completely separate mono- and
  bipropellant systems

**Cons**

- Complexity comparable to bipropellant
- Less stable operating range
- Mixture ratio can require different-sized fuel/oxidizer tanks
- More limited heritage-thruster selection

------------------------------------------------------------------------

# 13. Mars Observer Case Study

> **Source: Slide 75**

JPL launched **Mars Observer** on:

**September 25, 1992**

Mission science objectives included study of the Martian:

- Surface
- Atmosphere
- Climate
- Magnetic field

Three days before planned orbit insertion:

- Communication with the spacecraft was lost.
- Communication was never re-established.

This case study follows the lecture's discussion of long-duration
propulsion systems, isolation, pressurization, mixing protection, and
the importance of architecture and redundancy.

------------------------------------------------------------------------

# 14. Lecture Summary

> **Source: Slides 1–75**

The propulsion subsystem converts stored energy and propellant into
controlled spacecraft thrust.

The mission's trajectory and $\Delta V$ requirements are usually the
primary design drivers, but propulsion also interacts strongly with:

- GN&C / ACS
- Structures
- Thermal
- Power
- Mission operations
- Contamination control
- Reliability
- Integration and test
- Cost

The propulsion design process is iterative:

``` text
Mission Concept of Operations
          |
          v
Propulsion Requirements
          |
          v
Architecture Selection
          |
          v
Draft Schematic
          |
          v
Propellant Sizing
          |
          v
Tank Sizing
          |
          v
Pressurant Sizing
          |
          v
Thruster / Hardware Selection
          |
          v
Wet & Dry Mass Estimate
          |
          v
MEL + Propellant Budget
          |
          v
Redundancy / Risk / Cost Review
          |
          +------ Iterate ------+
```

Core equations include the rocket equation:

$$
\Delta V=g_0I_{sp}\ln\left(\frac{m_0}{m_f}\right)
$$

and the ideal gas law:

$$
PV=nRT
$$

Propellant mass is:

$$
m_p=m_0-m_f
$$

For bipropellant systems:

$$
M_{\text{tot prop}}=M_{ox}+M_{fu}
$$

$$
MR=\frac{M_{ox}}{M_{fu}}
$$

Thruster cant causes cosine loss:

$$
F_{\text{actual}}=F_{\text{spec}}\cos\theta
$$

The lecture's major propulsion architectures are:

| Architecture        | General Character                                              |
|---------------------|----------------------------------------------------------------|
| Cold Gas            | Simple, low cost, low $I_{sp}$                                 |
| Monopropellant      | Reliable and versatile for moderate capability                 |
| Bipropellant        | Higher efficiency for larger $\Delta V$, but more complex      |
| Dual-Mode           | Combines mono/biprop functions in one architecture             |
| SRM                 | Simple, reliable, high-thrust fixed-impulse solution           |
| Electric Propulsion | Very high efficiency, low thrust, high electrical-power demand |

A good propulsion design must not only meet the nominal $\Delta V$
requirement. It must also account for:

- Propellant residuals and hold-up
- ACS propellant
- Pressurant
- Tank capacity margin
- Thruster operating pressure
- Burn duration
- Minimum impulse bit
- Thruster placement
- Cant / misalignment
- Contamination
- Leakage
- Flow direction
- Redundancy
- Ground servicing
- System-level testability
- Component heritage
- Growth allowance
- Mission duration

The schematic is one of the central engineering artifacts because it
forces the designer to explicitly show how tanks, pressurant, valves,
filters, regulators, sensors, and thrusters interact.

The lecture repeatedly emphasizes that there is rarely a single perfect
propulsion design. The correct architecture depends on mission
constraints, acceptable risk, mass, cost, lifetime, redundancy, and
heritage, and the engineer must be able to defend each design decision.

