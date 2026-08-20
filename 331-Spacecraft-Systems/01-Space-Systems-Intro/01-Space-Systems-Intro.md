# Introduction to Space Systems

**Course:** ASTE-331a — Spacecraft Systems Engineering  
**Lecture:** 01 — Introduction to Space Systems  
**Instructors:** Jim Chase, Danielle Marsh  
**Source:** `331_01_SpaceSystemsIntro_20250829.pdf`

------------------------------------------------------------------------

## Lecture Overview

This lecture introduces spacecraft systems engineering, using the GRAIL
mission as a conceptual-design case study before surveying the major
spacecraft subsystems and introducing mission requirements flow-down.

The lecture begins with the definition and organization of space systems
and systems engineering. It then follows the early GRAIL concept from
science objectives and program constraints through concept of
operations, payload requirements, trajectory and propulsion trades,
spacecraft-bus selection, and preliminary mission requirements. The
lecture next surveys propulsion, attitude control, telecommunications,
control and data handling, electrical power, thermal, and mechanical
subsystems. It concludes with requirements engineering: why requirements
are written, how they are organized hierarchically, and how high-level
mission objectives are flowed down into quantitative subsystem
requirements.

------------------------------------------------------------------------

## Table of Contents

- [1. Spacecraft Systems Engineering](#1-spacecraft-systems-engineering)
- [2. GRAIL Conceptual Design](#2-grail-conceptual-design)
- [3. Overview of Spacecraft Subsystems](#3-overview-of-spacecraft-subsystems)
- [4. Mission Requirements Flow-Down](#4-mission-requirements-flow-down)

------------------------------------------------------------------------

# 1. Spacecraft Systems Engineering

> **Source: Slide 3**

Slide 3 begins **Part 1: Spacecraft Systems Engineering**.

------------------------------------------------------------------------

## Introduction to Space Systems

> **Source: Slide 4**

### Space Systems

A **system** is a collection of elements that work synergistically
together to perform one or more functions.

Space systems engineering encompasses the planning, development,
integration, testing, launch, and operation of space systems. These
activities require close coordination among participants whose
scientific, engineering, and management capabilities span many
disciplines.

### Systems Engineers

Systems engineers are central to creating successful systems. Their
responsibilities include:

- System concept
- System architecture
- System design
- Analysis of complexity and risk
- Determining how system performance will be measured
- Determining whether the deployed system works as intended
- Coordinating the many interconnected facets of system creation

### Breadth and Depth

The slide includes a breadth-versus-depth graphic.

**Figure description:** The horizontal direction is labeled **Breadth**
and the vertical direction **Depth**. A green oval labeled **This Class
(331a/b)** spans broadly across the top of many technical areas,
illustrating the broad knowledge expected in systems engineering.
Individual technical areas extend downward to different depths. A
circled deep region states that **depth in relevant areas is critical to
being a systems engineer**.

The slide also shows the **International Space Station** and **SpaceX
Starship (first orbital test flight)** as examples of complex space
systems.

------------------------------------------------------------------------

## Examples of Space Systems

> **Source: Slides 5–7**

### STS-1

**STS-1 (Space Transportation System-1)** was the first orbital
spaceflight of NASA's Space Shuttle program.

- The first orbiter was **Columbia**.
- Launch: **April 12, 1981**
- Return: **April 14, 1981**
- Mission duration: approximately **54.5 hours**
- Earth orbits completed: **36**

**Figure description:** The slide shows Columbia launching vertically
from the pad with its external tank and solid rocket boosters.

### Space Interferometry Mission (SIM)

The **Space Interferometry Mission (SIM)** was a planned NASA space
telescope.

One of its principal goals was to search for **Earth-sized planets in
the habitable zones of nearby stars**.

**Figure description:** An artist's rendering shows the proposed space
observatory in orbit with its spacecraft body and deployed solar panels.

### Gravity Recovery and Climate Experiment (GRACE)

The **Gravity Recovery and Climate Experiment (GRACE)** was a joint
mission of NASA and the German Aerospace Center.

- Two satellites made detailed measurements of anomalies in Earth's
  gravity field.
- Launch: **March 2002**
- End of science mission: **October 2017**

**Figure description:** Two satellites are shown flying in formation
above Earth.

### Gravity Recovery and Interior Laboratory (GRAIL)

The **Gravity Recovery and Interior Laboratory (GRAIL)** was a lunar
science mission that used high-quality gravitational-field mapping of
the Moon to determine its interior structure.

**Figure description:** Two spacecraft are shown above the lunar surface
with inter-spacecraft links illustrated between them.

### Phoenix

**Phoenix** was a robotic Mars spacecraft.

- Landed on Mars: **May 25, 2008**
- Instruments aboard the lander were used to assess local habitability
  and investigate the history of water.

**Figure description:** Phoenix is shown descending toward the Martian
surface with its descent engines firing.

### Mars Science Laboratory (MSL)

**Mars Science Laboratory (MSL)** was a robotic mission to Mars.

- Launch: **November 26, 2011**
- Delivered the **Curiosity** rover to **Gale Crater**

Objectives included:

- Investigating Mars' habitability
- Studying Martian climate
- Studying Martian geology
- Collecting information relevant to a future human mission to Mars

**Figure description:** The slide shows the MSL entry vehicle and the
sky-crane landing system lowering Curiosity toward the surface.

------------------------------------------------------------------------

## System Design and Development

> **Source: Slide 8**

### A System

A system:

- Serves to satisfy stakeholder requirements
- Is a hierarchy of subsystems, sub-subsystems, etc.
- May have super-systems, super-super-systems, etc.

### Functional Decomposition

The definition of a system, including its functions, interfaces, and
lower-level subsystems, is **functional decomposition**.

### System Design

**System design** addresses the architecture of:

- Components
- Interfaces
- Constraints

across the end-to-end system.

### System Development

**System development** consists of all activities required to produce
and integrate the resulting product.

### Hierarchy Diagram

The slide illustrates a generic system hierarchy:

``` text
Level (n-2)                         X
                                    |
                  +-----------------+-----------------+
                  |          |             |          |
Level (n-1)      X.1        X.2           X.3        X.4
                                           |
                                  +--------+--------+
                                  |                 |
Level n                         X.3.1             X.3.2
                                  |
                           +------+------+
                           |             |
Level (n+1)             X.3.1.1       X.3.1.2
                           |
                      +----+----+
                      |         |
Level (n+2)       X.3.1.1.1  X.3.1.1.2
```

If `X.3.1` is the **system of interest**:

- `X.3.1.1` and `X.3.1.2` are its subsystems.
- `X.3.1.1.1` and `X.3.1.1.2` are sub-subsystems.
- `X.3` is its supersystem.
- `X` is its super-supersystem.

**Source noted on slide:** *System Engineering Overview, A. Ruskin.*

------------------------------------------------------------------------

## Typical Project Organization

> **Source: Slide 9**

A typical spacecraft project is organized into levels.

### Level 1

- Project and/or Science Management
- Business Office
- Mission Assurance

### Level 2

- Payload System
- Flight System
- Mission System
- Launch System

### Level 3

**Payload System**

- Instrument A
- Instrument B
- Etc.

**Flight System**

- SIT / ATLO
- Spacecraft / Bus

**Mission System**

- Ground Data System
- Mission Operations

**Launch System**

- Launch Vehicle
- Launch Services

### Level 4 — Spacecraft / Bus

- Propulsion
- GN&C
- Telecom
- C&DH
- Power
- Mechanical
- Thermal
- Bus I&T

**Figure description:** The organizational chart shows Project/Science
Management at the top, with Payload, Flight, Mission, and Launch systems
below it. The Spacecraft/Bus is decomposed into the Level 4 spacecraft
subsystems. Colored outlines identify approximate course scope: **331a**
around the spacecraft subsystems, **331b** around a broader
spacecraft/payload region, and **ASTE 421** around the higher-level
project/system organization.

The slide emphasizes that **Systems Engineering exists as part of each
element (L1–L4).**

------------------------------------------------------------------------

# 2. GRAIL Conceptual Design

> **Source: Slide 10**

Slide 10 begins **Part 2: GRAIL Conceptual Design**.

------------------------------------------------------------------------

## GRAIL Mission Introduction

> **Source: Slide 11**

The following slides walk through the **GRAIL early mission concept**.

The **Gravity Recovery and Interior Laboratory (GRAIL)** was a lunar
science mission in NASA's Discovery Program. It used high-quality
gravitational-field mapping of the Moon to determine its interior
structure.

Mission facts:

- Two small spacecraft
- Launch date: **September 10, 2011**
- Launch vehicle: **Delta II**
- Cruise duration: approximately **3–4 months**
- Lunar arrivals approximately **25 hours apart**
  - December 31, 2011
  - January 1, 2012
- Both spacecraft impacted the lunar surface on **December 17, 2012**

**Figure description:** The slide shows the triangular GRAIL mission
logo and an artist's rendering of the two spacecraft flying above the
Moon. Lines between the spacecraft illustrate their paired measurement
geometry.

------------------------------------------------------------------------

## Study Objectives

> **Source: Slide 12**

### Background

- In **2009**, NASA Headquarters released an **Announcement of
  Opportunity (AO)** for Discovery Program missions.
- The Discovery Program selects science-led space mission investigations
  under a **not-to-exceed cost cap** that address NASA planetary-science
  goals.
  - These goals are defined in **Decadal Studies** and NASA exploration
    roadmaps.
- Several NASA centers and other organizations responded with **more
  than 20 different concepts** with varying levels of risk and cost.
- JPL proposed several concepts, including GRAIL, which was eventually
  selected.

### Initial GRAIL Study Objectives

- Determine concept feasibility of a lunar gravity-mapping mission.
- Target a lower-risk, lower-cost mission given increasingly risk-averse
  selections by NASA Headquarters.
- Coordinate with **Maria Zuber**, identified on the slide as a leading
  planetary geologist and MIT department chair.

### Constraints

- Minimize risk.
  - No new technologies.
  - Ensure robust margins for mass, power, etc.
- Cost cap:

$$
\leq \$425\text{ million}
$$

- Launch no earlier than **January 2012**.
- Schedule:
  - **4–5 years** for development
  - **3–6 months** operations

**Figure description:** The slide includes a Discovery Program graphic
and a mission-family diagram showing multiple NASA planetary missions.
The visual reinforces that NASA uses AOs to solicit mission proposals
within defined programmatic and science constraints.

------------------------------------------------------------------------

## Mission Objectives

> **Source: Slide 13**

### Initial Idea

**GRACE at the Moon**

The concept adapts the paired-spacecraft gravity-measurement approach
used by GRACE to lunar science.

### Science Objectives — from Decadal Survey

- Determine the structure of the lunar interior, from crust to core.
- Advance understanding of the thermal evolution of the Moon.
- Extend knowledge gained on the internal structure and thermal
  evolution of the Moon to other terrestrial planets.

### Additional Objective

- Produce the detailed lunar gravity field required for future
  scientific or exploration objectives.
- The slide references the **Constellation Program, 2005–2009**.

**Figure description:** The slide shows a GRACE spacecraft configuration
and a GRACE mission-system graphic, emphasizing the heritage
relationship between GRACE and the proposed lunar GRAIL concept.

------------------------------------------------------------------------

## Basic Concept of Operations

> **Source: Slide 14**

The early concept of operations contains five major phases.

### 1. Launch

The spacecraft begin the mission at Earth.

### 2. Cruise

The spacecraft travel from Earth toward the Moon.

### 3. Lunar Orbit Insertion

The spacecraft enter lunar orbit.

### 4. Science Operations at the Moon

Approximate duration:

$$
\sim 90\text{ days}
$$

Both spacecraft operate in approximately:

$$
50\text{ km polar orbits}
$$

The slide indicates a spacecraft separation distance of approximately:

$$
50\text{–}500\text{ km}
$$

### 5. Decommission

The spacecraft are decommissioned by crashing onto the lunar surface.

### Communication with Earth

- Deep Space Network
- Likely **34-m antenna**
- Communication while on the lunar near side

### Initial Questions

- Payload requirements?
- Mission design, i.e. trajectory, for Lunar Orbit Insertion (LOI)?
- Spacecraft design?

**Figure description:** A red trajectory line starts at Earth, passes
through cruise, and points toward lunar-orbit insertion. A second
graphic shows two spacecraft flying over the lunar surface in low polar
orbit.

------------------------------------------------------------------------

## Payload Description

> **Source: Slides 15–16**

Each spacecraft carries an **Enhanced Ka-Band Ranging & Instrument
Assembly** based on the GRACE KBR instrument developed by JPL.

The instrument uses a **Ka-band radio frequency** to precisely determine
satellite-to-satellite range. The two spacecraft must point at one
another.

### Expected Requirements

| Parameter            | Value                                          |
|----------------------|------------------------------------------------|
| Instrument           | Enhanced Ka-Band Ranging & Instrument Assembly |
| Mass                 | 15 kg (10 kg + 50% contingency)                |
| Power                | 15 W (10 W + 50% contingency)                  |
| Pointing Control     | 0.25 deg                                       |
| Pointing Knowledge   | 200 arcsec                                     |
| Instrument Data Rate | 10 MB/day                                      |

### Driving Requirements

- Two spacecraft
- Accommodate a **15 kg, 15 W payload**
- **3-axis stabilized**
- Pointing and data rate should not be drivers, but must be accommodated

### Instrument Diagram

**Figure description:** The diagram shows GRAIL-A and GRAIL-B, each with
a Ka-band ranging chain. Components include a KBR, microwave assembly,
Ka transmitter, Ka antenna, ultra-stable oscillator, time-transfer
electronics, processor unit, and supporting radio components.

The inter-spacecraft link is labeled near **32 GHz**, with a second
frequency offset by approximately **670 kHz**. Lower-frequency
time-transfer signals are also shown. Each side outputs range data at
approximately **10 samples/s**.

------------------------------------------------------------------------

## Mission Design

> **Source: Slides 17–19**

### Destination

- **50 × 50 km polar lunar orbit**
- **90-degree inclination**

### Trade 1 — Earth Escape vs. Staging

#### Option 1: Earth Escape

- Launch-vehicle insertion to lunar rendezvous.

#### Option 2: Staging

- Launch-vehicle insertion to approximately: 185 x 43,800 km
- Five chemical burns to spiral outward to lunar rendezvous.

### Trade 2 — Direct Insertion vs. Low Energy

#### Option 1: Direct Insertion

- Lunar-orbit insertion to approximately: 100 x 8,000 km
- Five chemical burns to spiral inward to the final 50 × 50 km lunar orbit.

#### Option 2: Low Energy

- Uses Lagrangian points.
- Launch-vehicle insertion into a low-energy trajectory.
- Lunar-orbit insertion to approximately: 100 x 8,000 km
- Five chemical burns to spiral inward to the 50 × 50 km lunar orbit.

### Low-Energy Trajectory Figure

**Figure description:** The example trajectory leaves the Earth-Moon
region, loops toward the Earth Libration Point 1 region, and returns
toward lunar-orbit insertion. Multiple trajectory-correction maneuvers
are marked along the path. The Moon's orbit, Earth, Moon, and direction
toward the Sun are identified.

### Four Mission-Design Options

| Parameter                                      | Option 1: Earth Escape + Direct | Option 2: Earth Escape + Low Energy | Option 3: Staging + Direct | Option 4: Staging + Low Energy |
|------------------------------------------------|--------------------------------:|------------------------------------:|---------------------------:|-------------------------------:|
| LV Injection                                   |                       C3 = -2.0 |                           C3 = -0.7 |            185 × 30,000 km |                185 × 30,000 km |
| Taurus 3113 Capability                         |                          445 kg |                              435 kg |                     637 kg |                         637 kg |
| Delta 2326-9.5 Capability                      |                          605 kg |                              585 kg |                     920 kg |                         920 kg |
| LV Correction                                  |                         ~30 m/s |                             ~30 m/s |                    ~15 m/s |                        ~15 m/s |
| Escape Burn                                    |                           0 m/s |                              30 m/s |                    813 m/s |                        870 m/s |
| Lunar Targeting                                |                           5 m/s |                               5 m/s |                      5 m/s |                          5 m/s |
| Lunar Orbit Insertion                          |                         825 m/s |                             697 m/s |                    825 m/s |                        697 m/s |
| Lunar Descent Burn                             |                          23 m/s |                              23 m/s |                     23 m/s |                         23 m/s |
| Mass Delivered to Final Orbit — Taurus 3113    |                          299 kg |                              305 kg |                     298 kg |                         308 kg |
| Mass Delivered to Final Orbit — Delta 2326-9.5 |                          406 kg |                              411 kg |                     431 kg |                         445 kg |
| Total Delta-V                                  |                         883 m/s |                             785 m/s |                   1681 m/s |                       1610 m/s |
| Total Flight Time (Cruise)                     |                         ~6 days |                            ~90 days |                   ~15 days |                       ~99 days |
| Maximum Earth Range                            |                     ~400,000 km |                        1,500,000 km |                ~400,000 km |                   1,500,000 km |

**Trade-table comments:**

- The Taurus capability assumes a **63-inch fairing**, approximately 60
  kg less performance than the larger fairing.
- Escape burns may be divided into segments depending on the propulsion
  system.
- Lunar-orbit insertion may also be divided into segments depending on
  the propulsion system.
- Delivered-mass estimates assume:

$$
I_{sp}=226\text{ s}
$$

for the Delta-V burns.

- Flight times are approximate.

### Driving Requirements

The trajectory trade produces the following spacecraft-driving
requirements:

- Delta-V:

$$
800\text{–}1600\text{ m/s}
$$

- Flight time:

$$
5\text{–}100\text{ days}
$$

- Maximum Earth range:

$$
400{,}000\text{–}1{,}500{,}000\text{ km}
$$

The slide identifies approximately **100–200 kg for each spacecraft**,
considered small spacecraft.

### Questions Generated by Mission Design

**Propulsion System**

- Integrated propulsion system or separate?
- Bipropellant vs. monopropellant?

------------------------------------------------------------------------

## Propulsion Trades

> **Source: Slide 20**

### Propulsion-System Questions

- Integrated propulsion system or separate?
- Bipropellant vs. monopropellant?

### Spacecraft Stacking Concepts

**Figure description:** Two launch-fairing concepts are shown.

The first uses:

``` text
S/C #1
Attachment Mechanism
S/C #2
Propulsion Stage
Adapter (S/C side)
Adapter (LV side)
```

The second removes the dedicated propulsion stage:

``` text
S/C #1
Attachment Mechanism
S/C #2
Adapter (S/C side)
Adapter (LV side)
```

The trade is therefore whether the required propulsion capability should
be provided by a separate stage or integrated into the spacecraft.

### Launch Vehicle

Candidate launch vehicles:

- Taurus 3113
- Delta II

The slide notes an approximately: $50M difference at the time.

**Figure description:** Taurus and Delta II launch vehicles are shown
side by side with a height scale, emphasizing their substantial
size/capability difference.

------------------------------------------------------------------------

## Orbit Maintenance and Operations

> **Source: Slide 21**

### Orbit Parameters

- 2 spacecraft
- 50 × 50 km polar orbit
- Period: 113.0 minutes
- Separation distance: 50 km

### Mission Operations

**Duration**

- 3 months

**Tracking — on near side**

- Continuous

**Downlink**

- Approximately 10 MB/day

**Ground Network**

- 34-m DSN

### Figure Description

GRAIL-1 and GRAIL-2 are shown at approximately 50-km altitude above the
Moon. Their separation is labeled approximately **200 km** in the
example geometry shown in the figure, while the orbit-parameter list
gives a nominal **50 km separation distance**. Vectors $r_1$ and $r_2$
extend from the two spacecraft toward Earth, illustrating the
simultaneous spacecraft-Earth tracking geometry.

------------------------------------------------------------------------

## Updated Mission Requirements

> **Source: Slide 22**

### Mission Design

| Item                 | Requirement / Current Design                         | Rationale           |
|----------------------|------------------------------------------------------|---------------------|
| Launch Date          | January 2012, flexible                               | AO                  |
| Mission Duration     | 5–100 day cruise; 3 months prime operations          | Trajectory Analysis |
| Trajectory & Delta-V | See prior charts                                     | Trajectory Analysis |
| Operations           | 58 m/s for maintenance                               | Orbital Analysis    |
| Launch Vehicle       | Taurus 3113, includes Star 37FM with 63-inch fairing | Largest Taurus LV   |

### Flight System

| Item          | Requirement / Current Design                              | Rationale               |
|---------------|-----------------------------------------------------------|-------------------------|
| Flight System | TBD; 100–150 kg dry mass, with monoprop vs. biprop system | Open design             |
| Redundancy    | Single string with functional redundancy                  | Short Duration Mission  |
| Stabilization | 3-axis with reaction wheels (?) and propulsion system     | Lunar Orbit Maintenance |
| Prop Stage    | TBD; monoprop or biprop stage to deliver spacecraft       | Trajectory Analysis     |
| Telecom       | 64 kbps S-band?                                           | Link Budget Analysis    |

### Programmatic

**Schedule**

- Phase A: 7 months
- Phase B: 11 months
- Phase C/D: 36 months

**Reserves**

- 30% for mass, power, and cost unless noted otherwise

The slide identifies the schedule and reserve assumptions as **rules of
thumb**.

------------------------------------------------------------------------

## Survey of Industry Spacecraft

> **Source: Slide 23**

### Survey Criteria

- Mass \< 150 kg
- Pointing knowledge \< 350 arcsec
- ACS is 3-axis with reaction wheels and no magnetic torquers
- Includes propulsion system
- Primarily RSDO spacecraft considered, excluding most foreign
  spacecraft

### Results

- Most small satellites are designed for Earth orbit and use magnetic
  torquers rather than RCS propulsion systems.
- **Spectrum-Astro SA-200S** is close in mass and carries a
  monopropulsion system.
- Additional non-RSDO spacecraft should be further investigated.

### RSDO Spacecraft Survey

| Organization       | Model       | Dry Mass (kg) | Data Rate (kbps) | Pointing Knowledge (arcsec) | ACS                       | Propulsion   |
|--------------------|-------------|--------------:|-----------------:|----------------------------:|---------------------------|--------------|
| Surrey             | SNAP        |           6.5 |              100 |                        3600 | 3-axis, mom-bias, mag tqs | Liq. Butane  |
| Surrey             | Microsat-70 |          44.7 |             2048 |                        1800 | 3-axis, zero-mom, mag tqs | —            |
| Orbital            | PicoStar    |          52.7 |              100 |                        3600 | Spinner                   | —            |
| Orbital            | MicroStar   |          58.6 |             2000 |                        2880 | 3-axis, zero-mom, mag tqs | —            |
| Spectrum Astro     | SA-200B     |            90 |             2500 |                         317 | 3-axis, zero-mom, mag tqs | —            |
| Orbital            | MiniStar    |           100 |            115.2 |                         540 | Spinner                   | —            |
| **Spectrum Astro** | **SA-200S** |       **129** |         **2500** |                     **2.8** | **3-axis, zero-mom**      | **Monoprop** |
| Orbital            | LeoStar-2   |           166 |             2000 |                         108 | 3-axis, zero-mom, mag tqs | —            |
| TRW                | T100        |         184.1 |              200 |                         694 | 3-axis, zero-mom          | Monoprop     |
| Ball Aerospace     | BCP 600     |           203 |            17000 |                          12 | 3-axis, zero-mom          | —            |
| Surrey             | Minisat-400 |         206.7 |             2048 |                          72 | 3-axis, zero-mom          | Cold Gas     |
| TRW                | T200A       |         242.4 |             1400 |                         324 | 3-axis, zero-mom          | Monoprop     |
| TRW                | T200B       |           278 |             2048 |                           2 | 3-axis, zero-mom          | Monoprop     |
| Swales             | EO-SB       |           332 |             2000 |                          36 | 3-axis, zero-mom, mag tqs | —            |
| Spectrum Astro     | SA-200HP    |           354 |           80,000 |                         0.5 | 3-axis, zero-mom          | Monoprop     |
| Astrium            | FlexBus     |           383 |             1000 |                       206.3 | 3-axis, zero-mom          | Cold Gas     |
| Lockheed Martin    | LM 900      |           492 |              TBD |                         100 | 3-axis, zero-mom          | Monoprop     |
| Orbital            | StarBus     |         566.3 |             1000 |                         390 | 3-axis, zero-mom          | Monoprop     |
| Orbital            | MidStar     |           580 |             1024 |                          10 | 3-axis, zero-mom          | —            |
| Ball Aerospace     | BCP 2000    |           608 |           320000 |                           3 | 3-axis, zero-mom          | Monoprop     |
| TRW                | T-310       |           718 |             1024 |                          43 | 3-axis, zero-mom          | Biprop       |

### Additional Non-RSDO Spacecraft — Not Considered

| Spacecraft Bus             | Mass (kg) | Power (W) |
|----------------------------|----------:|----------:|
| Oersted, Terma, DEN        |        50 |        26 |
| Sloshsat, Dutch Space, NET |        58 |        35 |
| Constellation, SSTL, UK    |        60 |       120 |
| IRIS, Fuchs Gruppe, BEL    |        67 |        44 |
| STRV, DERA, UK             |        70 |        60 |
| RS300, Ball, USA           |        74 |       120 |
| Myriade, Astrium, CNES, FR |        74 |        80 |
| Bird, GER                  |        78 |        40 |
| TechSat21, MicroSat, USA   |        82 |       433 |
| XSS-11, LM, USA            |        85 |       100 |
| TE, MicroSat, USA          |        90 |       120 |
| ODIN, SSC, SWE             |        90 |       160 |
| PROBA, Verhaert, BEL       |        94 |        30 |
| MMB-100, SpaceDev          |       100 |        80 |
| PegaStar, Orbital, USA     |       100 |       150 |
| MITA, Fuchs Gruppe, ITA    |       120 |       100 |
| SciSat, Bristol, CA        |       150 |        70 |

**Note on slide:** GRACE used Astrium's Flexbus.

------------------------------------------------------------------------

## Spacecraft Bus RFI and Selection

> **Source: Slide 24**

- Based on a preliminary design, a **Spacecraft Bus Request for
  Information (RFI)** was released to solicit bus concepts.
- The RFI included:
  - Trajectory/propulsion options — this trade was still open
  - Payload specifications
  - Flight-system requirements
- The result was that **Lockheed** was chosen with a bus derived from
  its prior **XSS-11 spacecraft**.
- The initial study concluded that the concept was feasible.
- Likely budget estimate: $310-$350 M

The slide notes that this was very close to the final cost.

### Figure Description

The preliminary spacecraft drawing labels:

- Lightband separation device
- S-band radio-science beacon
- LGA-1
- Two solar arrays
- 22-N thruster
- Ka-band horn
- S-band payload antenna

------------------------------------------------------------------------

# 3. Overview of Spacecraft Subsystems

> **Source: Slide 25**

Slide 25 begins **Part 3: Overview of Spacecraft Subsystems**.

------------------------------------------------------------------------

## Propulsion

> **Source: Slide 26**

### Function

- Provides thrust for trajectory-design maneuvers and often attitude
  control.
- The primary driver is typically the trajectory and corresponding
  Delta-V budget.
- Across all subsystems, components are typically selected as those that
  meet the minimum requirements with the lowest mass, power, and cost.

### GRAIL Example

- 1 × 22-N thruster
- 8 × 0.8-N thrusters
- Warm gas generator
- Fuel tank
- Miscellaneous hardware
- Total: ~15 kg

### Common Components

**Chemical Propulsion — Mono/Biprop**

- Fuel tanks
- Thrusters, often different types tailored for small/large maneuvers
- Integration and related hardware

Other types:

- Solid rocket motors (SRMs)
- Electric propulsion systems

### Key Trades and Analyses

- Propulsion type:
  - Solid
  - Monopropellant
  - Bipropellant
  - Electric
- Thruster and fuel-tank sizing
- Heritage from prior systems

### Key Parameters

- Subsystem mass
- Power
- Cost
- Thruster $I_{sp}$
- Thruster locations
- Cant angles
- Propellant load
- Margins

### Figure Description

A subsystem block diagram shows the fuel tank connected through the
propulsion system to a warm-gas generator and two thrust branches: one
**22-N thruster** and **eight 0.8-N thrusters**.

------------------------------------------------------------------------

## Attitude Control System (ACS)

> **Source: Slide 27**

### Function

- Provide attitude control, knowledge, and stability to support
  spacecraft pointing.

Primary drivers for pointing:

- Science observations — instrument FOVs
- Trajectory-course maneuvers — thrust
- Telecom — uplink/downlink to Earth
- Thermal — orientation with respect to the Sun, Earth, etc.

Other names include:

- GNC
- ADCS
- AOCS

### GRAIL Example

- 1 star tracker
- 3 reaction wheels
- 1 inertial measurement unit (IMU)
- 1 sun sensor
- Total: ~5 kg

### Common Components

**Sensors**

- Sun sensors
- Magnetometers
- Gyros
- GPS receivers
- Star trackers

**Control Effectors**

- Reaction or momentum wheels
- Control moment gyros
- Magnetic torquers
- Reaction-control thrusters

### Key Trades and Analyses

- 3-axis control, spin, gravity gradient, etc.
- Reaction wheels vs. thrusters
- Control/knowledge/stability analyses and error budgets
- Heritage from prior systems

### Key Parameters

- Mass
- Power
- Cost
- Pointing control
- Pointing knowledge
- Stability/jitter

### Figure Description

The GRAIL attitude-control block shows an **Inertial Measurement Unit**,
**Star Tracker**, **Sun Sensor**, and **3 Reaction Wheels**.

------------------------------------------------------------------------

## Telecommunications

> **Source: Slide 28**

### Function

- Provides communication to/from the spacecraft.
- Communication is typically with Earth but can include other
  spacecraft.
- Occasionally used for radio science.
- Primary driver is typically spacecraft-Earth distance.

### GRAIL Example

- S-band transponder and diplexer
- Low-gain antenna (LGA)
- Miscellaneous hardware
- Total: ~5 kg

### Common Components

- Radio/transponder
- Amplifier
- Antennas:
  - High-gain antenna (HGA)
  - Medium-gain antenna (MGA)
  - Low-gain antenna (LGA)

### Key Trades and Analyses

- Fixed vs. articulated
- Data-rate and volume analysis
- Link budget and antenna sizing
- Radio band and power level
- Heritage from prior systems

### Key Parameters

- Mass
- Power
- Cost
- Transmission power
- Data
- Margin

### Figure Description

Two low-gain antennas, **LGA1** and **LGA2**, feed the
telecommunications chain. The block diagram also identifies an **S-band
transponder** and **diplexer**.

------------------------------------------------------------------------

## Control and Data Handling (C&DH)

> **Source: Slide 29**

### Function

- Provide spacecraft command and control along with internal data
  handling.
- Includes flight software (FSW) with boot/reset functionality.
- Primary drivers are redundancy, interfaces, and complexity of
  downstream components such as the payload.
- Also called the **Flight Computer**.

### GRAIL Example

- RAD750 processor
- I/F cards
- Converters
- Backplane
- Chassis assembly
- Total: ~5 kg

### Common Components

Electronics box/chassis containing:

- Processor, e.g. RAD750
- Payload-interface cards
- Data-interface cards
- Memory

Depending on complexity, these functions may be implemented in one box
or multiple boxes.

### Key Trades and Analyses

- Functional block diagram
  - Interface types such as 1553, LVDS, RS-422, etc.
- Onboard memory storage
- CPU utilization percentage
- Radiation-shielding analysis
- Heritage from prior systems

### Key Parameters

- Mass
- Power
- Cost

### Figure Description

The GRAIL C&DH architecture shows:

- cPCI Bus
- RAD750 Processor
- Telecom & Payload I/F
- Payload Storage I/F
- State of Health & ACS I/F

A photograph below the diagram shows the associated electronics
hardware.

------------------------------------------------------------------------

## Electrical Power System (EPS)

> **Source: Slide 30**

### Function

- Provide electrical power and distribution throughout the spacecraft.

Primary drivers:

- Sun-spacecraft distance
- Power profiles during science and telecom operations
- Launch for battery sizing
- Redundancy

EPS is often paired with C&DH under **Avionics**.

### GRAIL Example

- Power electronics:
  - Interface cards
  - Converters
- 1 × 30 Ahr battery
- 2 solar arrays
- Total: ~30 kg

### Common Components

**Generators**

- Solar arrays
- Radioisotope thermoelectric generators (RTGs)

**Storage Devices**

- Fuel cell
- Primary battery
- Secondary battery

**Power Processors**

- Regulate voltage
- Distribute current

### Key Trades and Analyses

- Solar arrays vs. RTGs
- Battery type, e.g. primary vs. secondary
- Array and battery sizing
- Power Equipment List (PEL) and power analysis
- Heritage from prior systems

### Key Parameters

- System power loads
- Profiles
- Margins
- Worst-case depth of discharge

### Figure Description

The slide shows spacecraft electronics and a power-system block with a
**30 A-hr Li-ion battery** and **two solar arrays**.

------------------------------------------------------------------------

## Thermal

> **Source: Slide 31**

### Function

- Provide appropriate thermal control throughout the spacecraft.

The primary driver is the overall thermal model, including temperatures
from:

- Avionics — usually room temperature
- Instruments — e.g. cold FPAs or hot sample analyses
- Batteries
- Mechanisms
- Propulsion

All components must remain within their qualification temperature
limits.

### GRAIL Example

- Paint
- Films
- Multi-layer insulation (MLI)
- Instrument thermal-mass plate
- Heaters
- Thermostats
- Sensors
- Related hardware
- Total: ~10 kg

### Common Components

**Surface Coatings and Treatments**

- Films
- Paints
- MLI

**Conductors and Insulators**

**Heat-Transfer Regulators**

- Heat pipes
- Louvers
- Phase-change devices
- Heat switches

### Key Trades and Analyses

- Active vs. passive
- Thermal analysis
- Radiator design
- Radiator locations
- Margins

### Key Parameters

- Mass
- Power
- Cost
- Updated attitude profile

### Figure Description

The thermal block highlights **Temperature Sensors** and **Heaters,
Thermostats** alongside a photograph of the spacecraft wrapped in
thermal-control material.

------------------------------------------------------------------------

## Mechanical

> **Source: Slide 32**

### Function

- Provides structure to support spacecraft and payload.
- Includes mechanisms and separation systems.

Primary drivers:

- Spacecraft type — orbiter vs. rover
- Payload — camera vs. sampling system
- Overall dry and wet mass
- Articulated arrays, antennas, and instruments

Also called **Structure & Mechanisms**, and often includes the harness,
i.e. wiring.

### GRAIL Example

- 4 side panels
- Propulsion and payload panels
- Tank support and fittings
- Solar-array deployment mechanism
- Launch-vehicle separation system
- Total: ~35 kg

### Common Components

**Primary Structure**

- Core structure
- Panels
- etc.

**Secondary Structure**

- Tank support
- Fittings
- Payload support
- Booms

**Payload Elements**

- Wheels
- Sample-return canisters
- etc.
- These may alternatively be categorized under Payload.

**Additional Elements**

- Mechanisms
- Launch-vehicle and spacecraft adapters

### Key Trades and Analyses

- Configuration
- CAD
- FOV design
- Loads and stiffness analysis
- Master Equipment List
- Mechanism and torque analyses

### Key Parameters

- Mass
- Power
- Cost

### Figure Description

The slide shows the GRAIL spacecraft structure mounted on a cylindrical
adapter/support. The spacecraft bus consists of compact structural
panels carrying integrated spacecraft hardware.

------------------------------------------------------------------------

# 4. Mission Requirements Flow-Down

> **Source: Slide 33**

Slide 33 begins **Part 4: Mission Requirements Flow-Down**.

------------------------------------------------------------------------

## Requirements Introduction

> **Source: Slides 34–35**

### Requirement Definition

A requirement is a documented physical or functional need that a design,
product, or process is intended to satisfy.

### Requirements in the Aerospace Industry

Requirements are used to map a **system hierarchy** to a corresponding
set of required functions so that the project can achieve the mission
objectives.

### Example Requirements Flow

**Level 1**

``` text
The Mission shall achieve an Earth orbit that supports the science requirements.
```

↓

**Level 2**

``` text
The Project shall place an Orbiter in a 500 km, geocentric Earth orbit.
```

↓

**Level 3**

``` text
The Spacecraft shall provide a total Delta-V capability of 1,000 m/s.
```

↓

**Level 4**

``` text
The propellant tank shall store 100 kg of propellant.
```

### Shall Statements

Requirements are written using **shall statements**:

``` text
The XYZ shall...
```

### Organization, Requirements, and Product Deliveries

The slide notes that there is typically a strong correlation between:

- Organization — people
- Requirements — tasks
- Functional product deliveries — spacecraft and subsystems

### Protecting Capability and Margins

Requirements also protect capability and margins across the flight
system, particularly across organizational interfaces.

Example:

- Project systems team knows the spacecraft will provide:

$$
1000\text{ m/s}
$$

- Actual need:

$$
900\text{ m/s}
$$

Another example:

- Spacecraft team knows propulsion will provide:

$$
100\text{ kg}
$$

- Actual need:

$$
90\text{ kg}
$$

### Requirements and Contracts

Requirements form the basis of many contracts:

- Customer to contractor
- Contractor to subcontractor

Payment is often contingent on meeting the requirements.

### Institutional Best Practices

Requirements can also enforce institutional best practices.

Example from the slide:

``` text
The Spacecraft shall perform DSN compatibility testing using the Flight System prior to launch.
```

------------------------------------------------------------------------

## Questions About Requirements

> **Source: Slide 36**

### Why Do We Write Requirements?

- Understand the end-to-end design prior to hardware.
- Communicate between customer and supplier.

### What Do We Write Requirements For?

- Typically for new developments.
- For existing hardware, requirements are written on its operation.

### When Do We Stop Writing Requirements?

- When there are no more new-development items in the system
  description.

### Why Do We Verify Requirements?

- Ensure that the system meets its specified requirements.
- Understand the degree to which it meets the requirements.

### Requirements Development Timing

Iterating on the end-to-end design to produce detailed requirements
generally occurs in the first:

$$
\frac{1}{2}\text{ to }\frac{1}{3}
$$

of the project, for example approximately **2–3 years**.

### Life-Cycle Cost Figure

**Figure description:** The horizontal axis progresses through:

1.  Conceptual / preliminary design
2.  Detail design / development
3.  Production and/or construction
4.  Product use / support / phaseout / disposal

Three curves are shown:

- **LCC Committed** rises rapidly early.
- **Cost Incurred** rises later.
- **Ability to Influence** begins high and falls as the project
  progresses.

A green circle highlights the early conceptual and detailed-design
period. The figure emphasizes that a large fraction of life-cycle cost
is committed while the ability to influence the design is still high and
before most costs have actually been incurred.

------------------------------------------------------------------------

## Requirements Hierarchy

> **Source: Slide 37**

Requirements are organized into hierarchical **requirements sets**.

``` text
L1 — Program / Sponsor
 |
 +-- L2 — Project
      |
      +-- L3 — System
           |
           +-- L4 — Subsystem
                |
                +-- L5 — Assembly / SW
                     |
                     +-- L6
                          |
                          +-- L7
```

### Purpose of the Hierarchy

The requirement hierarchy exists to:

- Organize requirements work
- Generally follow the product architecture
- Assign responsibility for generating or meeting requirements to
  elements or teams

### Figure Description

The diagram is a branching tree. One L1 requirement set branches into
multiple L2 sets; those branch into L3, L4, L5, and lower-level sets.
Different branches can decompose to different depths.

------------------------------------------------------------------------

## Requirements Level Definitions

> **Source: Slides 38–43**

The lecture builds the hierarchy progressively.

### L1 — Program / Sponsor

> **Source: Slide 38**

**Program / Sponsor**

Sponsoring-organization or program-derived and allocated requirements on
the Project.

``` text
Program / Sponsor
       |
      L1
```

------------------------------------------------------------------------

### L2 — Project

> **Source: Slides 39–40**

**Project**

Derived Project functionality and the allocated functions to each
**System**.

The slides identify project-level requirement sets such as:

- Project / Mission
- Science

``` text
             L1
              |
      +-------+-------+
      |               |
Project/Mission     Science
      L2              L2
```

Slide 40 visually combines **Project/Mission Science** into the
project-level requirement-set representation while retaining the same
definition of Project-level functionality.

------------------------------------------------------------------------

### L3 — System

> **Source: Slide 41**

**System**

Derived System functionality and the allocated functions to each
**Subsystem**.

Example systems shown:

- Spacecraft
- Payload
- Ground System
- Launch System

``` text
                   Project
                      |
      +---------------+---------------+
      |               |               |
 Spacecraft        Payload       Ground System
                                      |
                                 Launch System
```

------------------------------------------------------------------------

### L4 — Subsystem

> **Source: Slide 42**

**Subsystem**

Derived Subsystem functionality and the allocated functions to each
**Element**.

``` text
Program / Sponsor
       |
     Project
       |
     System
       |
   Subsystem
       |
    Element
```

------------------------------------------------------------------------

### L5 — Assembly / Software

> **Source: Slide 43**

**Assembly / SW**

Derived Elements and allocated functions for the parts within each
Element.

The complete hierarchy shown across the slides is:

| Level | Scope                                   |
|-------|-----------------------------------------|
| L1    | Program / Sponsor                       |
| L2    | Project                                 |
| L3    | System                                  |
| L4    | Subsystem                               |
| L5    | Assembly / Software                     |
| L6    | Lower-level element as required         |
| L7    | Further lower-level element as required |

### Figure Description

Slides 38–43 progressively add levels to the same branching requirements
tree. The sequence demonstrates that high-level program requirements are
decomposed into project, system, subsystem, and assembly/software
requirement sets.

------------------------------------------------------------------------

## Deriving Next-Level Requirements

> **Source: Slide 44**

Requirements development is coupled to:

- Trade Studies
- Architecture
- Design

The process is iterative rather than purely top-down.

``` text
Higher-Level Requirements
          |
          v
 Trade Studies / Architecture / Design
          |
          v
Lower-Level Requirements
          |
          +------ iteration ------+
```

The diagram shows circular iteration arrows beside multiple levels of
the hierarchy and dashed connections from design/trade activity into the
requirement sets.

### Key Point

The slide states:

> In order to produce high-quality L1 requirements, you really need to
> understand L3/L4s.

This emphasizes that high-level requirements cannot be developed
effectively without sufficient understanding of the lower-level
architecture and design.

------------------------------------------------------------------------

## Example Requirements Flow-Down

> **Source: Slide 45**

The final slide gives an example of requirements flow-down for a
comet-imaging mission.

### Sponsor / Program

``` text
The Mission shall characterize the surface features of the comet.
```

↓

### Science

``` text
The project shall obtain high quality images of a comet.
```

↓

### Spacecraft

``` text
The spacecraft shall provide a scan platform with slew position deviation
of less than 10 percent of the imaging Field of View.
```

This creates the quantitative relationship:

$$
\text{Slew Position Deviation} < 0.10(\text{Imaging FOV})
$$

↓

### Attitude Control Subsystem

``` text
The Attitude control subsystem shall control the scan platform with a
stability of 8 micro Rad/second.
```

Therefore:

$$
\text{Scan Platform Stability} = 8\ \mu\text{rad/s}
$$

### Complete Flow

``` text
SPONSOR / PROGRAM
The Mission shall characterize the surface features of the comet.
                         |
                         v
SCIENCE
The project shall obtain high quality images of a comet.
                         |
                         v
SPACECRAFT
The spacecraft shall provide a scan platform with slew position
deviation of less than 10 percent of the imaging Field of View.
                         |
                         v
ATTITUDE CONTROL SUBSYSTEM
The Attitude control subsystem shall control the scan platform
with a stability of 8 micro Rad/second.
```

The example demonstrates how a broad mission objective is progressively
converted into specific, quantitative engineering requirements that can
be allocated to and verified at lower levels of the system.

------------------------------------------------------------------------

# Lecture Summary

> **Source: Slides 1–45**

This lecture introduces the fundamental systems-engineering framework
used throughout spacecraft design.

A spacecraft is not an isolated object. It exists within a hierarchy of
systems, subsystems, organizations, interfaces, and requirements.
Systems engineering coordinates these elements so that the complete
mission can satisfy stakeholder objectives.

The GRAIL conceptual-design case study demonstrates a typical
progression:

``` text
Science Objectives
       |
       v
Program Constraints
       |
       v
Concept of Operations
       |
       v
Payload Requirements
       |
       v
Mission / Trajectory Trades
       |
       v
Driving Spacecraft Requirements
       |
       v
Subsystem Trades
       |
       v
Spacecraft Architecture
       |
       v
Detailed Requirements
```

For GRAIL, the science concept required two spacecraft performing
precise inter-spacecraft ranging in low lunar orbit. That concept
created requirements for payload accommodation, pointing, propulsion,
telecommunications, power, spacecraft mass, and operations.

The mission-design trade generated important driving requirements
including:

$$
\Delta V \approx 800\text{–}1600\text{ m/s}
$$

$$
\text{Flight Time} \approx 5\text{–}100\text{ days}
$$

$$
\text{Maximum Earth Range} \approx 400{,}000\text{–}1{,}500{,}000\text{ km}
$$

The lecture introduces seven major spacecraft subsystem areas:

| Subsystem          | Primary Function                                                       |
|--------------------|------------------------------------------------------------------------|
| Propulsion         | Provides thrust for trajectory maneuvers and often attitude control    |
| ACS                | Provides attitude control, knowledge, and stability                    |
| Telecommunications | Provides communication to/from the spacecraft                          |
| C&DH               | Provides command, control, flight software, and internal data handling |
| EPS                | Generates, stores, regulates, and distributes electrical power         |
| Thermal            | Maintains hardware within allowable temperature limits                 |
| Mechanical         | Provides structure, mechanisms, separation, and physical integration   |

Requirements formally connect mission objectives to engineering
implementation.

The generalized hierarchy is:

``` text
L1 — Program / Sponsor
         |
         v
L2 — Project
         |
         v
L3 — System
         |
         v
L4 — Subsystem
         |
         v
L5 — Assembly / Software
         |
         v
L6 / L7 — Lower-Level Elements as Required
```

Requirements help:

- Organize engineering work
- Allocate functionality
- Assign responsibility
- Communicate between customers and suppliers
- Protect capability and engineering margins
- Establish contractual commitments
- Capture institutional best practices
- Define measurable criteria for verification

Requirements flow-down is iterative. Trade studies, architecture, and
design influence requirements at multiple levels, and understanding
lower-level implementation is necessary to create meaningful high-level
requirements.
