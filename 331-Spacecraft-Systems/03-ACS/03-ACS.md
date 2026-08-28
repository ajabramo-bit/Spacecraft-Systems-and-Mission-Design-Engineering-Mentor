# Attitude Control System (ACS)

**Course:** ASTE-331 --- Spacecraft Systems Engineering\
**Lecture:** 03 --- Attitude Control System (ACS)\
**Instructors:** Jim Chase, Danielle Marsh\
**Source:** `331_03_ACS_20250926.pdf`

------------------------------------------------------------------------

## Lecture Overview

This lecture introduces the **Attitude Control System (ACS)**, the spacecraft subsystem responsible for providing **attitude control, knowledge, and stability**, including the sensors, actuators, and onboard logic/control required to maintain or change spacecraft orientation.

The lecture begins with the fundamental purpose and terminology of attitude determination and control, including the distinction between **attitude, determination, control, pointing error, and jitter/stability**. It then examines the closed-loop ACS architecture in which commanded attitude is compared with measured attitude to generate an attitude error that drives the spacecraft controller and actuators.

The major areas covered in the lecture include:

- **ACS functions and architecture**
  - Attitude control, knowledge, and stability
  - Sensors, actuators/effectors, electronics, and onboard control logic
  - Physical and logical block diagrams
  - Redundancy and heritage

- **Spacecraft disturbances**
  - Launch vehicle tip-off
  - Aerodynamic torque
  - Gravity-gradient torque
  - Magnetic torque
  - Solar-radiation torque
  - Mass expulsion
  - Internal torque

- **Pointing and mission geometry**
  - Payload science observations and instrument FOVs
  - Communications and solar conjunction
  - Solar-array pointing and solar-incidence angle
  - Thermal pointing constraints
  - Trajectory maneuvers
  - Spacecraft agility and slew rates
  - Sun-Earth-Probe (SEP) angle
  - Sun-Probe-Earth (SPE) angle
  - Phase angle

- **Attitude determination sensors**
  - Sun sensors
  - Earth sensors
  - Magnetometers
  - Star trackers / Stellar Reference Units (SRUs)
  - Gyroscopes / Internal Reference Units (IRUs)
  - GPS receivers

- **GN&C actuators and effectors**
  - Reaction wheels
  - Momentum wheels
  - Control Moment Gyros (CMGs)
  - Magnetic torquers / torque rods
  - Reaction Control System (RCS) thrusters
  - Electric propulsion for attitude control

- **ACS design and sizing**
  - Selection of sensors and control effectors
  - Reaction-wheel sizing
  - Momentum management
  - Functional redundancy
  - Thrusters vs. reaction wheels
  - Component sizing and mass estimates
  - End-to-end kinematic simulation and error budgets

- **Spacecraft rotational dynamics**
  - Kinematics of rotation
  - Rotational kinetic energy
  - Moment of inertia
  - Angular acceleration
  - Parallel and perpendicular axis theorems
  - Inertia tensors
  - Angular momentum and torque
  - Euler's moment equations
  - Euler angles and rotation matrices

The lecture also uses several mission examples and case studies to connect ACS theory to real spacecraft:

- **OSIRIS-REx** — spacecraft architecture, GN&C hardware, mission geometry, pointing, Touch-and-Go (TAG), and asteroid sample collection
- **International Space Station (ISS)** — Control Moment Gyros and attitude-control redundancy
- **Phoenix** — Entry, Descent, and Landing simulation fidelity and radar modeling
- **Deep Impact** — attitude estimation, star tracker anomalies, coordinate-frame errors, star-catalog errors, and lessons learned

Overall, the lecture connects **mission pointing requirements and spacecraft disturbances to the sensors, actuators, control logic, dynamics, redundancy, and simulations required to determine and control spacecraft attitude**.

------------------------------------------------------------------------

## Table of Contents

-   [1. ACS Overview](#1-acs-overview)
-   [2. OSIRIS-REx Example](#2-osiris-rex-example)
-   [3. Disturbances](#3-disturbances)
-   [4. Pointing Concerns, Mission Geometry, and Spacecraft
    Motion](#4-pointing-concerns-mission-geometry-and-spacecraft-motion)
-   [5. Attitude Determination
    Sensors](#5-attitude-determination-sensors)
-   [6. GN&C Actuators and Effectors](#6-gnc-actuators-and-effectors)
-   [7. ACS Design and Architectures](#7-acs-design-and-architectures)
-   [8. Questions from Prior Class](#8-questions-from-prior-class)
-   [9. Spacecraft Dynamics](#9-spacecraft-dynamics)
-   [10. Phoenix Radar Case Study](#10-phoenix-radar-case-study)
-   [11. Deep Impact Star Tracker
    Anomaly](#11-deep-impact-star-tracker-anomaly)
-   [Lecture Summary](#lecture-summary)

------------------------------------------------------------------------

------------------------------------------------------------------------

# 1. ACS Overview

### Outline

> **Source: Slide 2**

-   Overview

-   ## Design

    ## Disturbances (aerodynamic, gravity gradient, magnetic, solar radiation, mass expulsion, internal)

    ## Sensors (sun, earth, magnetometer, star tracker, gyroscope/IMU, GPS)

    ## Actuators & Effectors (reaction wheels, momentum wheels, CMGs, torque rods, RCS thrusters)

    ## Block Diagrams (physical & logical architectures)

    ## Architectures (eg, 3-axis, spinning)

    ## Mission Geometry & Pointing Concerns

    Sizing

-   Example: ISS

-   ## Control & Logic

    ## Rotational Kinematics

    ## Moments of Inertial & Angular Acceleration

    ## Angular Momentum & Torque

    ## Euler's Equations

    Modeling, Slew Rates, & Spacecraft Motion

-   Example: Osiris Rex Sample Collection

-   Case Study: Phoenix EDL

-   Case Study: Deep Impact Star Tracker Anomaly 9/26/2025 2 Notes

-   I'm likely to move the order around a bit..

-   And, I haven't had a chance to update the overall format (eg,
    film-strip, wide-screen, etc.)

### Overview (1 of 2)

> **Source: Slide 3**

-   Attitude Determination and Control
    -   Spacecraft subsystem that provides attitude control, knowledge,
        and stability, including the actuators, sensors, and onboard
        logic/control
-   Also Known As...
    -   AACS: Attitude and Articulation Control System
    -   ACS: Attitude Control System
    -   ADCS: Attitude Determination Control System
    -   ADACS: Attitude Determination and Control System
    -   AOCS: Attitude and Orbit Control System
    -   G&C: Guidance and Control System
    -   GN&C: Guidance, Navigation, and Control
    -   PCS: Pointing Control System
    -   ... 9/26/2025 3

### Attitude Control Subsystem

> **Source: Slide 4**

-   Function
    -   Provide attitude control, knowledge, and stability to support
        spacecraft pointing
    -   Primary drivers for pointing are:
-   Science observations (instrument FOVs)
-   Trajectory course maneuvers (thrust)
-   Telecom (uplink/downlink to Earth)
-   Thermal (wrt sun, Earth, etc.)
    -   Also called ACS, ADCS, AOCS, etc. 9/26/2025 4
-   GRAIL Example
    -   1 star tracker
    -   3 reaction wheels
    -   1 inertial measurement unit (IMU)
    -   1 sun sensor (x4)
    -   Total = \~5 kg
-   Common Components
    -   Sensors
-   Sun sensors, magnetometers
-   Gyros, GPS receivers
-   Star trackers
    -   Control Effectors
-   Reaction or momentum wheels
-   Control moment gyros
-   Magnetic torquers
-   Reaction control thrusters (see propulsion)
-   Key Trades & Analyses
    -   3-axis control, spin, gravity gradient...
-   Reaction wheels vs. thrusters, etc.
    -   Control/knowledge/stability analyses and error budgets
    -   Heritage from prior systems
-   Key Parameters
    -   Mass, power, and cost
    -   Pointing control, knowledge, stability/jitter

### Overview (2 of 2)

> **Source: Slide 5**

9/26/2025 5 Disturbances System Actuators Sensors Controller
Disturbances Ground or Autonomous Commands Spacecraft Measured attitude
Commanded attitude Device Commands Attitude Error = Commanded attitude
-- Measured attitude - Attitude Determination and Control - Spacecraft
subsystem that provides attitude control, knowledge, and stability,
including the actuators, sensors, and onboard logic/control

### Slew Rates & Spacecraft Motion

> **Source: Slide 6**

-   What do typical spacecraft motions look like? 9/26/2025 6

### Some Terminology

> **Source: Slide 7**

9/26/2025 7 - Attitude: Orientation of a defined reference system
attached to the spacecraft body - Determination: Knowledge within a
specified tolerance (realtime or post- facto) - Control: Maintenance of
specified attitude within a given tolerance - Pointing Error: Low
frequency component of attitude misalignment - Jitter: Spacecraft
stability, consisting of the high frequency component of attitude error
(minimized by design) For example, imagine the boresight of a telescope
is represented by the vectors shown below: x y z Attitude (actual)
Desired attitude (eg, payload requirements) Attitude knowledge (based on
sensors) Attitude Errors Jitter/Stability (typically uncorrected)
Pointing (typically corrected)

------------------------------------------------------------------------

# 2. OSIRIS-REx Example

### OSIRIS-REX Example

> **Source: Slide 8**

9/26/2025 8

### Origins, Spectral Interpretation, Resource Identification,

> **Source: Slide 9**

Security-Regolith Explorer (OSIRIS-REx) Mission Objectives - Launched on
Sept. 8, 2016, the spacecraft traveled to a near-Earth asteroid called
Bennu - It has collected a sample of rocks and material from the surface
that it returned to Earth on Sept. 24, 2023 - The mission will help
scientists investigate how planets formed and how life began, as well as
improve our understanding of asteroids that could impact Earth.
9/26/2025 9

### OSIRIS-REx Asteroid Sample Collection

> **Source: Slide 10**

Overview 9/26/2025 10

### Instrument Deck

> **Source: Slide 11**

9/26/2025 11 Instruments OCAMS: Camera Suite (UofA) - PolyCam: Narrow
angle, high resolution (8-inch telescope) - MapCam: Wide angle, high
resolution (4-color, asteroid mapping) - SamCam: Monitors TAG and sample
acquisition OLA: LIDAR for high-resolution topography (CSA contribution)
OTES: Thermal Spectrometer, 5.7-100 microns (ASU) OVIRS: Visible & IR
Spectrometer, 0.4-4.3 microns (GSFC) REXIS: X-ray Spectrometer (student
experiment) OCAMS OLA OTES OVIRS REXIS GN&C Components 4 Sun Sensor
Assemblies (SSA) - 4 heads & 2 heads (x2 = 12) 4 Reaction Wheels 2 Star
Trackers 2 MIMUs (Miniature IMUs) 2 LIDARs (40 cm @ 3 km) TAGCAMs - 2
NavCams (Optical Nav) - StowCam - Camera Electronics 16 ACS thrusters 2
TAG thrusters Star Trackers StowCam NavCams LIDARs Camera Electronics
Thrusters Thrusters Thrusters Thrusters SSA?

### Block Diagram

> **Source: Slide 12**

9/26/2025 12

### ACS Design

> **Source: Slide 13**

-   ## Discussion Topics

    ## Sensors, Actuators, Electronics, and software?

    ## Redundancy?

    Heritage? 9/26/2025 13 LVDS Connector Analog/Etc. Connectors
    Mil-Spec 1553 Interfaces C&DH Power Electronics

### Touch & Go (TAG)

> **Source: Slide 14**

-   ## Questions from Last Year

    ## Why was there no realtime video? (What was the downlink rate?)

    How does the prediction compare to the sample? 9/26/2025 14

### Onboard Sample

> **Source: Slide 15**

-   ## 1-2 Days Later

    ## Collector lid likely not fully closing due to larger rocks, thus leaking...

    Forgoing sample measurement in favor or earlier stowing (significant
    sample observed) 9/26/2025 15

### Sample Stowage & Earth Return

> **Source: Slide 16**

-   Stow successful and ready for its return

-   Delivery achieved on 9/24/2023

-   ## Entry, descent, and landing

    ## Heatshield to slow high-speed entry

    ## Parachute to reduce speed further

    Landing area is the Utah test range 9/26/2025 16

### Questions from Last Year (1 of 2)

> **Source: Slide 17**

-   From 1 to 10, how bad was the slight error the OSIRIS-REX Touch and
    Go? Are these kinds of things usually expected or was it a complete
    surprise?
    -   Likely well within the modeled capability (\~3)
    -   Typically, videos are based on the 'nominal' scenario, but
        analysis is far more encompassing
    -   That said, there are still surprises... (both MER rovers were
        barely within their performance envelopes)

-   How long is each step in the Osiris Rex mission take? As in, how
    long until NASA decides to return to the asteroid for a second
    sample if needed?
    -   Scientific consensus & technology development: Varies greatly
        (many years possible)
    -   Proposal Process: 1-3 years
    -   Development: 4-5 years
    -   Operations and Sample Return: 5-10 years
    -   Total: ≥ 10-20 years

-   ## Is there a way to change the downlink or uplink in the middle of a mission?

    Options for increasing the uplink/downlink rates:

-   Greater use of data compression

-   Increase downlink at the expense of the bit error rate (BER)

-   ## Adjust trajectory to reduce distance (mission dependent)

    Going to look at this in detail when we talk about Telecom 9/26/2025
    17

### •

> **Source: Slide 18**

In situations like the Osiris Rex touch and go, ...what is a reasonable
approach velocity to expect? - At touch-down, expected 0.4 m/s -
Comparison: Phoenix lander touched down around 1.5 m/s - MER Rovers
(w/airbags): \< 26 m/s - How is propellant estimated versus the
uncertainty of the asteroid size/shape? - Bounding estimates are
developed for the asteroid size, shape, gravity map - Sufficient
propellant margin is carried to encompass these estimates - Prior to
approach, significant observations (at 2-3 km) are undertaken (along
with fly by's) to improve fidelity of the gravity field. - Is the
asteroid massive enough that the SC is actually orbiting the asteroid? -
Yes, 62 hrs/orbit and more or less circular - Using features on Bennu
for attitude knowledge - Simple fault protection: - If something goes
wrong, burn towards the sun 9/26/2025 18 Questions from Last Year (2 of
2)

------------------------------------------------------------------------

# 3. Disturbances

### Disturbances

> **Source: Slide 19**

-   Disturbances are torques that are typically induced on the
    spacecraft by external forces.
    -   Typically modeled as a force (representing a center of pressure)
        acting at on the spacecraft body at some radius from the center
        of mass.
-   Torque (τ) = rCP x F
    -   Radius from center of mass = rCP
    -   Force = F
-   Examples
    -   Launch vehicle tip-off
    -   Aerodynamic
    -   Gravity Gradient
    -   Magnetic
    -   Solar Radiation
    -   Mass Expulsion
    -   Internal 9/26/2025 19 Cover ejection or deployment Solar
        Radiation Gravity Gradient Magnetic Atmospheric Drag

**Equation(s) shown on slide:**

``` math
\boldsymbol{\tau}=\mathbf{r}_{CP}\times\mathbf{F}
```

### Aerodynamic Torque

> **Source: Slide 20**

9/26/2025 20 For example, at 400 km altitude, there might be a 3.11x10-5
N torque, Which would result in an attitude error of 82-deg after one
orbit From "Attitude Determination and Control", Joel Sercel, 2003

**Equation(s) shown on slide:**

``` math
\boldsymbol{\tau}_a=\mathbf{r}_{CP}\times\mathbf{F}_a
```

``` math
F_a=\frac{1}{2}\rho S C_D v^2
```

### Gravity Gradient

> **Source: Slide 21**

9/26/2025 21 From "Attitude Determination and Control", Joel Sercel,
2003

### Magnetic Torque

> **Source: Slide 22**

9/26/2025 22 From "Attitude Determination and Control", Joel Sercel,
2003

**Equation(s) shown on slide:**

``` math
\boldsymbol{\tau}_m=\mathbf{M}\times\mathbf{B}
```

### Solar Radiation

> **Source: Slide 23**

9/26/2025 23 From "Attitude Determination and Control", Joel Sercel,
2003

**Equation(s) shown on slide:**

``` math
\boldsymbol{\tau}_s=\mathbf{r}\times\mathbf{F}_s
```

``` math
F_s=(1+K)p_sS_\perp
```

### Mass Expulsion

> **Source: Slide 24**

-   Mass expulsion includes a wide range of activities:
    -   Jettison: Probes, overs, expended SRMs, etc.
    -   Deliberate: Thrusters, gas venting, etc.
    -   Accidental: Leaks, misalignments
-   If significant, it can dominate the overall forces and result in
    changes to the attitude control system
-   Mass expulsion torque:
    -   Torque (τME) = rCP x FME
-   Where FME varies considerably 9/26/2025 24 Cassini's release of the
    Huygen's probe

### Internal Torque

> **Source: Slide 25**

-   Internal torque is typically caused by
    -   Deployments: Solar arrays, antennas, booms, instruments
    -   Recurring Motions: Instrument scanning, sample retrieval, fluid
        flow, thermal louvers, etc.
-   It has no effect on total system angular momentum, but it still
    effects attitude 9/26/2025 25 Boom deployment (Mars Odyssey)

------------------------------------------------------------------------

# 4. Pointing Concerns, Mission Geometry, and Spacecraft Motion

### Typical Pointing Concerns

> **Source: Slide 26**

-   Payload
    -   Perform science observations
-   With the sun often within a specified phase angle range
    -   Avoid Sun on sensitive instruments (eg, camera boresight)
-   Communications
    -   Avoid solar conjunction
-   Solar Arrays for Power
    -   Minimize solar incidence angle
-   Thermal
    -   Spacecraft design typically favors or excludes a particular
        geometry
-   Trajectory Maneuvers
    -   Pointing & stability for manuevers
-   Spacecraft Agility
    -   How quickly can the spacecraft change directions? 9/26/2025 26
        Typical Spacecraft Body-fixed

(b) Coordinate Systems xb zb yb roll yaw pitch

### Typical Pointing Concerns

> **Source: Slide 27**

-   Payload
    -   Perform science observations
-   With the sun often within a specified phase angle range
    -   Avoid Sun on sensitive instruments (eg, camera boresight)
-   Communications
    -   Avoid solar conjunction
-   Solar Arrays for Power
    -   Minimize solar incidence angle
-   Thermal
    -   Spacecraft design typically favors or excludes a particular
        geometry
-   Trajectory Maneuvers
    -   Pointing & stability for manuevers
-   Spacecraft Agility
    -   How quickly can the spacecraft change directions? 9/26/2025 27
        xb zb yb Phase Angle Target Often a driver for control,
        knowledge, & error

### Payload Observation Architectures

> **Source: Slide 28**

9/26/2025 28 Spacecraft points at the target as a rigid body (typically
controlled by onboard ACS) Actuators adjust the instrument (or scanning
platform) pointing Instrument collector is oversized, such that it can
internally point/filter data Onboard ACS is typical, but other
approaches can occasionally produce improved performance while
maintaining cost. Terminology - Nadir: pointing towards (eg, Earth) -
Zenith: pointing away (eg, Earth)

### Typical Pointing Concerns

> **Source: Slide 29**

-   Payload
    -   Perform science observations
-   With the sun often within a specified phase angle range
    -   Avoid Sun on sensitive instruments (eg, camera boresight)
-   Communications
    -   Avoid solar conjunction (SEP angle near 0-deg)
-   Solar Arrays for Power
    -   Minimize solar incidence angle
-   Thermal
    -   Spacecraft design typically favors or excludes a particular
        geometry
-   Trajectory Maneuvers
    -   Pointing & stability for manuevers
-   Spacecraft Agility
    -   How quickly can the spacecraft change directions? 9/26/2025 29
        Sun-Earth-Probe (SEP) Angle xb zb yb High Gain Antenna (HGA)
        pointing XHGA Low gain antennas typically provide communication
        at any nominal attitude High gain antennas often require 3-axis
        control (combined w/science & communications)

### Typical Pointing Concerns

> **Source: Slide 30**

-   Payload
    -   Perform science observations
-   With the sun often within a specified phase angle range
    -   Avoid Sun on sensitive instruments (eg, camera boresight)
-   Communications
    -   Avoid solar conjunction (SEP angle near 0-deg)
-   Solar Arrays for Power
    -   Minimize solar incidence angle
    -   Maintain power while transmitting
-   Thermal
    -   Spacecraft design typically favors or excludes a particular
        geometry
-   Trajectory Maneuvers
    -   Pointing & stability for manuevers
-   Spacecraft Agility
    -   How quickly can the spacecraft change directions? 9/26/2025 30
        Sun-Probe-Earth (SPE) Angle xb zb yb Solar Incidence angle
        Arrays will often be single- or dual-axis articulated to
        minimize solar incidence angle Note that arrays will
        occasionally be oversized to relax pointing requirements

### Example

> **Source: Slide 31**

3-axis vs. Dual-Spin Stabilization 9/26/2025 31 In this example, a solar
array that wraps-around a spacecraft minimizes the required pointing
control

### Typical Pointing Concerns

> **Source: Slide 32**

-   Payload
    -   Perform science observations
-   With the sun often within a specified phase angle range
    -   Avoid Sun on sensitive instruments (eg, camera boresight)
-   Communications
    -   Avoid solar conjunction
-   Solar Arrays for Power
    -   Minimize solar incidence angle
-   Thermal
    -   Spacecraft design typically favors or excludes a particular
        geometry
-   Trajectory Maneuvers
    -   Pointing & stability for manuevers
-   Spacecraft Agility
    -   How quickly can the spacecraft change directions? 9/26/2025 32

### Typical Pointing Concerns

> **Source: Slide 33**

-   Payload
    -   Perform science observations
-   With the sun often within a specified phase angle range
    -   Avoid Sun on sensitive instruments (eg, camera boresight)
-   Communications
    -   Avoid solar conjunction
-   Solar Arrays for Power
    -   Minimize solar incidence angle
-   Thermal
    -   Spacecraft design typically favors or excludes a particular
        geometry
-   Trajectory Maneuvers
    -   Pointing & stability for maneuvers
-   Spacecraft Agility
    -   How quickly can the spacecraft change directions? 9/26/2025 33
        OSIRIS-REx Example 4 200-N thrusters Exhaust vector

### Typical Pointing Concerns

> **Source: Slide 34**

-   Payload
    -   Perform science observations
-   With the sun often within a specified phase angle range
    -   Avoid Sun on sensitive instruments (eg, camera boresight)
-   Communications
    -   Avoid solar conjunction
-   Solar Arrays for Power
    -   Minimize solar incidence angle
-   Thermal
    -   Spacecraft design typically favors or excludes a particular
        geometry
-   Trajectory Maneuvers
    -   Pointing & stability for manuevers
-   Spacecraft Agility
    -   How quickly can the spacecraft change attitude? 9/26/2025 34
        Typically driven by opportunities & threats
-   Additional science observations?
-   Science vs. communication latency?
-   Attitude changes due to eclipse?

### Slew Rates & Spacecraft Motion

> **Source: Slide 35**

-   How fast (or slow) does a typical spacecraft turn when making
    attitude adjustments? Is there a typical time frame for certain
    attitude alterations? (few minutes? hours?)
    -   Typical spacecraft requirement is 1 deg/sec
    -   Might vary between 0.25 deg/sec to 3 deg/sec
    -   Note that faster slew rates require "settling time" to achieve
        stability requirements
    -   ISS slew rate is \< 0.1 deg/sec

-   How much does the typical satellite actually have to maneuver? Are
    they often just pointing at Earth or do they switch targets?
    -   Majority of spacecraft are for either imagery or communications
        (across the EM spectrum)
    -   Therefore, most have telescopes, antennas, and/or detectors that
        require some degree of pointing (typically between 0.001-deg and
        0.1-deg)
    -   ACS activity is a function of the disturbance environment
        vs. spacecraft activity

-   ## Whenever spacecraft are "holding" their attitude, they are using their ACS actuators

    Maneuvers (including slews) tend to vary greatly, for example:

-   Mars Reconnaissance Orbiter (MRO) can take dozens of pictures each
    day

-   Communications satellite in geo might desaturate its wheels
    once/week 9/26/2025 35

### Mission Geometry (key angles)

> **Source: Slide 36**

9/26/2025 36 Sun Earth Probe Sun-Earth-Probe (SEP) Angle Sun-Probe-Earth
(SPE) Angle Phase Angle Target In concept formulation, these key angles
will often drive the early design - The Mission Design & Nav. Engineer
will typically product plots of these in addition to their trajectory
designs and ∆V budgets

### Mission Geometry Example

> **Source: Slide 37**

Asteroid Rendezvous 9/26/2025 37 Based on the chart below... -
Rendezvous is occurring at a favorable phase angle wrt science
observations - Communications blackout when SEP \< 2-deg (solar
conjunction) - 0 to 45-deg SPE range suggests articulated arrays and/or
antenna to maintain both power and communication

### Thermal/ACS Relationship

> **Source: Slide 38**

-   For the thermal analysis of ACS pointing concerns, what does it mean
    to design a S/C that will typically favor or exclude particular
    geometry?
    -   While spacecraft are generally designed to be robust even in the
        even of attitude errors, spacecraft will still have thermal
        constraints.
    -   For example, SIRTF must keep it's solar array on the sun both to
        provide power AND to keep the telescope barrel (and especially
        the cryogenic detector) shaded. 9/26/2025 38
-   How do you evaluate SEP, SPE, and phase angle?
-   These angles are based on outputs from trajectory or visualization
    software (eg, STK)
-   Strategic Evaluation:
-   Phase Angle
-   Mission Design & Nav. consider trajectory/orbital mechanics to
    ensure best lighting for science ops (30-60-deg incidence)
-   Sun-Probe-Earth (SPE)
-   Power/Telecom engineers consider solar array vs. antenna pointing
    during mission (close to 0-deg depending on array/antenna margin;
    greater flexibility with solar arrays)
-   Sun-Earth-Probe (SEP)
-   Mission Design & Nav. And Telecom engineers consider solar
    conjunction wrt communications (eg, 2-deg)
-   Tactical Evaluation
-   What is the best attitude at any given point during the mission with
    respect to sun (power & thermal) and Earth (telecom)

------------------------------------------------------------------------

# 5. Attitude Determination Sensors

### Attitude Determination Sensors

> **Source: Slide 39**

-   Sun Sensors
-   Earth Sensors
-   Magnetometers
-   Star Trackers / Stellar Reference Units (SRUs)
-   Gyroscopes / Internal Reference Units (IRUs)
-   GPS Receivers 9/26/2025 39

### Sensor Accuracy

> **Source: Slide 40**

9/26/2025 40 0.1-deg 0.01-deg 0.001-deg \< \$100 k \< \$1 M \< \$10 M
Accuracy Cost, mass, power, & complexity Low - Magnetometers - Coarse
sun sensors - IR Earth sensors Medium - Digital Sun Sensors - Earth
sensors - Gyros - GPS Receivers High - Star Trackers - Fine sun sensors
Adapted from "Attitude Determination and Control", Joel Sercel, 2003
Additionally, custom sensors can be built or payload instruments can be
leveraged to perform similar functions.

### Sun Sensors

> **Source: Slide 41**

-   ## Used for basic attitude estimation, especially with respect fault protection

    For example, spacecraft with sun-pointing constraints (eg,
    telescopes) will have additional sun sensors to trigger safe
    attitude
    -   Often used in orthogonally mounted pairs (4 sensors provide
        hemispherical coverage) 9/26/2025 41 Analog Sun Sensor (from
        Adcole)

-   Analog 4-detector pyramid (picture on left)

-   Analog current output, digitized by s/c

-   Performance: 1.5-deg, mass = 0.12 kg Analog output (converted in
    software using cosine law)

-   Fine Sun Sensor

-   Analog current output, digitized by s/c

-   Performance: \< 0.016-deg (1 arcmin) Micro Sun Sensor (in
    development)

### Star Trackers

> **Source: Slide 42**

-   Star Trackers map the positions & magnitudes of observed stars to a
    star catalog to provide highly accurate attitude knowledge
    -   Fixed Type (common): Scans the star field electronically (or via
        spacecraft motion) using a 5-20-deg FOV. It then processes,
        calibrates, and resolves the signal to provide quaternions.
    -   Catalog typically contains 100s to 1000s of stars
    -   Precision star trackers are heavy & costly.
    -   Don't function well with high attitude rates (used for higher
        precision science missions)
    -   Performance: 0.001-1 deg, Mass 1-10 kg 9/26/2025 42 Catalog
        Visualization Star Tracker Image

### Star Map Example...

> **Source: Slide 43**

9/26/2025 43 Note that stars are not distributed uniformly (tend to
appear in groups) Understand the application requiring the star
tracker - Primarily staring or moving? Max angular rate? Fraction of sky
covered? - How will the system react to star tracker errors?

### Magnetometers

> **Source: Slide 44**

9/26/2025 44 From "Attitude Determination and Control", Joel Sercel,
2003

### Gyroscopes (IRUs/IMUs)

> **Source: Slide 45**

-   Gyros are used to maintain continuous attitude reference between
    updates from external references (eg, Sun, Earth, stars, etc.)

-   ## While there are several types of gyros, the...

    Majority of recent missions use ring-laser or fiber optic gyros,
    such as the LN-200 IMU

-   ## Internal Processing

    The gyro uses internal dynamics, environmental, and error models to
    produce a best estimate for the current attitude
    -   Over time (eg, 0.1-deg/hr), the error will increase 9/26/2025 45
        LN-200 IMU 0.7 kg, 10 W 9 x 9 cm Traditional Gyroscope
        Ring-Laser Gyroscope

### GPS Receiver

> **Source: Slide 46**

-   ## Using GPS for attitude knowledge has become increasingly common

    ## Spacecraft velocities to up 16,000 m/s

    Performance varies with distance (200 km to 45,000 km)

-   LEO Performance \< 0.1 deg 9/26/2025 46 Global Positioning System GD
    Sentinel M-Code GPS Receiver Mass 2.5 kg

### Summary of Sensors

> **Source: Slide 47**

-   ## Sun Sensor

    Simple, reliable, cheap, but also intermittent depending on sun

-   ## Earth Sensor

    Less common with narrower applications

-   ## Magnetometer

    Simple, reliable, cheap, but also requires low Earth orbit

-   ## Star Tracker

    ## Higher precision, narrow angle star trackers, but heavy & complex

    Less expensive versions, but not as precise

-   ## Gyroscope

    Generally required for maintaining knowledge between attitude
    updates from external references

-   ## GPS Receiver

    Cheap, simple, but requires proximity to functioning GPS 9/26/2025
    47

------------------------------------------------------------------------

# 6. GN&C Actuators and Effectors

### GN&C Actuators/Effectors

> **Source: Slide 48**

-   Affect System Momentum
    -   Reaction Wheels 0.0001-0.1 deg
    -   Momentum Wheels 0.1-2.0 deg
    -   Control Moment Gyros (CMGs) 0.001-0.1 deg
-   Do Not Affect System Momentum
    -   Magnetic Torquers / Torque Rods 1.0-10.0 deg
    -   Reaction Control Thrusters 0.1-5.0 deg 9/26/2025 48 Typical
        Accuracy

### Reaction Wheels

> **Source: Slide 49**

-   Electric motor spins a wheel. The rotation is aligned with the
    control axes (one wheel per axis)
    -   Typical arrangement is 4 wheels in a tetrahedron for redundancy

-   Three are required (1 for each axis), so the fourth one is redundant

-   ## Characteristics (0.0001-0.1-deg)

    ## Low torque, high accuracy (very fast response possible, tens of Hertz)

    ## Not limited by propellant, but limited by angular momentum capacity

    ## Nominally operate at low speeds

    Saturation level is defined by peak motor speed

-   Once wheels reach peak speed, required momentum dumping (eg,
    thruster firing) to unload

-   That is, reduce the speed without impacting the attitude 9/26/2025
    49

### Reaction Wheel Sizing & Trade Studies

> **Source: Slide 50**

-   It wasn't clear from SMAD that any one equation was ideal for
    momentum wheel sizing; what determines the sizing of momentum
    wheels?
    -   Reaction wheels provide torque (0.01 to 1 Nm)
    -   Size of reaction wheel depends on the size of the torque that is
        needed

-   ## For the quiz example, relevant torques were:

    ## Magnetic torque (Tm), 2.1 x 10\^-5 Nm

    ## Slew torque (T) = 2.9 x 10\^-4 Nm

    ## Momentum dumps due to gravity gradient (h) = 0.039 Nms

    ## Torque from RWs needs to be \> than torque from disturbance to maintain attitude

    For accumulated changes (such as momentum dumps), then

-   Slew rate (s) x torque (Nms) = momentum (Nms)

-   How long is the trade study process (typically) in determining
    attitude control mechanisms for a given satellite architecture?
    -   Varies significantly...

-   "Team X" design is typically done via rules of thumb & general
    principles (\< 2-3 hrs)

-   Detailed GN&C analysis for a more complex mission can take months,
    including multiple simulations and reviews to finalize architecure
    9/26/2025 50

### Momentum Wheels

> **Source: Slide 51**

-   Wheel operating at non-zero momentum to provide gyroscopic stiffness
    to the spacecraft

-   ## Characteristics

    ## Performance: 0.1-2.0 deg

    ## Effectively these are heavier reaction wheels that operate at a constant speed

    Often used to cancel the momentum of rotating payload 9/26/2025 51

### Control Moment Gyros (CMGs)

> **Source: Slide 52**

-   ## CMG is a gimbaled momentum wheel

    A torque is applied via the gimbal to produce a change in angular
    momentum, and thus a reaction torque on the body

-   Characteristics
    -   Performance: 0.001-0.1 deg
    -   Momentum wheel operating at nearly steady (high) speed;
    -   Higher control authority than momentum wheels (up to 100x times)
    -   Relatively noisy (they induce vibrations due to the spin rate)
        9/26/2025 52

### •

> **Source: Slide 53**

"Do they carry a surplus of gyros on the ISS now after being close to
critical loss of the station or is it still not worth the weight/space
resources?" - No, not worth flying additional spare units beyond the 1
(of 4) installed that is redundant. - History - CMG-1 failed in 2002 and
replaced in 2005 (first post-Columbia shuttle flight). - CMG-2 had two
circuit breaker failures - CMG-3 failed in 2006 and replaced in 2007
9/26/2025 53 1 of 4 CMGs during Integration & Test 4 CMGs installed in
ISS Z-1 Truss (as of 2000) 1 CMG Replaced in 2005 via a 7-hr Space Walk
International Space Station (CMGs)

### International Space Station (CMGs)

> **Source: Slide 54**

9/26/2025 54 Z1 Truss (location of CMGs)

### Attitude Control Redundancy

> **Source: Slide 55**

-   If part of your system controlling attitude is damaged, how can you
    compensate for that without losing the S/C entirely?
    -   Most spacecraft include significant redundancy for attitude
        control

-   ## Typical redundancy:

    Reaction Wheels or CMGs provide highest performance (w/low
    propellant use)

-   Typically, three wheels are required to maintain 3-axis attitude
    control

-   A fourth one is included, such that any three can provide full
    3-axis control

-   ## ISS requires a minimum of 2 CMGs (uses gravity gradient as well)

    Thrusters

-   Larger, higher-value (ie, Class A/B) missions will have redundant
    coupled thrusters that can provide reasonable attitude control

-   This is called "functional" redundancy. Thrusters will generally not
    perform as well and/or use- up greater propellant, so there will
    typically be some impact to the mission that is assessed
    -   Or simply, by any available means...

-   Dawn used it's electric propulsion system to provide attitude
    control (after 3 RW failures)

-   ISS incorporates the gravity gradient to minimize attitude control
    requirements

-   For attitude knowledge error, onboard instruments can be pressed
    into service...

-   Etc. 9/26/2025 55

### Electric Propulsion

> **Source: Slide 56**

-   Would some kind of electric propulsion thruster have enough thrust
    to be an effective control system?
    -   Yes. On Dawn, the 3 electric propulsion thrusters can provide 90
        mN of thrust.
    -   In Geostationary orbits, electric propulsion systems regularly
        provide attitude control given their extremely high efficiency
        (\> 3,000 Isp) versus the very low disturbances

-   ## For a small spacecraft

    ## drag = none

    ## Gravity gradient = 5 x 10\^-9 Nm

    Solar radiation pressure = 6 x 10\^-6 Nm 9/26/2025 56

### Magnetic Torque Rods

> **Source: Slide 57**

-   Electromagnets that are energized to provide a electromagnetic
    torque on the spacecraft via the local magnetic field
-   Characteristics
    -   Performance: 1.0-10.0 deg
    -   Clean way to dump momentum (with no consumables)
    -   Generally consist of simple iron rods (or loops)
    -   Very reliable and cheap
    -   Primarily applicable to planetary/Earth orbiters with large
        magnetic fields. 9/26/2025 57

### Thrusters (1 of 2)

> **Source: Slide 58**

-   Often called a Reaction Control System (RCS) when used only for
    attitude control
    -   From propulsion, these are typically the smallest thrusters.
        Often, they functionally back-up a reaction wheels in case of a
        failure, but they do not provide the same precision

-   ## Characteristics

    ## Performance: 0.1-5.0 deg

    ## Various sizes available, with different levels of performance (ie, control)

    ## Propellant-limited and may introduce contamination

    ## Capable of very high torque

    Accuracy limited by thruster configuration (impulse bit) 9/26/2025
    58

### Thrusters (2 of 2)

> **Source: Slide 59**

-   ## Primary Thruster Characteristics

    ## Thrust-level (eg, 1-N vs. 490-N), which determines the ability to provide thrust and thus ∆V

    ## Efficiency (ie, Isp), which is based on both type of thruster & propellant

    Minimum impulse bit (MIB) is the smallest control torque that can be
    applied to the spacecraft

-   ## Primary Uses

    ## Trajectory Correct Maneuvers (TCMs) for changing ∆V

    ## Orbital Maintenance

    ## Momentum dumps

    ## Attitude (or reaction) control

    Thrust vector control (TVC) that provide guidance on larger
    maneuvers

-   ## Matching Thrusters to Spacecraft

    ## Consider necessary functions: large ∆V maneuvers, attitude control, etc.

    Thrusters should be evaluated for min/max burn times

-   Minimum burn time should be consistent with the minimum impulse bit

-   ## Maximum burn time should be consistent with the type of maneuver (eg, orbit insertion, burn time \< 2-3 hrs)

    Result is often something like...

-   RCS thrusters for attitude control, momentum dumps, etc.

-   Main engine(s) for large & more efficient ∆V maneuvers

-   ## Other mid-size thrusters where the above thrusters aren't sufficient (eg, thrust vector control on a large ∆V burn)

    Reminder that thrust-level can be scaled with the number of
    thrusters 9/26/2025 59

### Attitude Control on Spin Stabilized S/C

> **Source: Slide 60**

-   ## Spin Rate

    Two pairs of coupled thrusters act on opposite sides to change spin
    rate

-   ## Velocity

    After the spin axis is changed to the desired orientation, the
    thrusters on the HGA side fire simultaneously for translational
    maneuver

-   ## Attitude

    Pair of coupled thrusters rotate the spin-axis. Thrusters are fired
    in brief pulses at a precise position in the spacecraft rotation.
    Each pulse moves the axis a few tenths of a degree until the desired
    attitude is reached 9/26/2025 60 Graphic from Pioneer 10 spacecraft,
    history.nasa.gov

------------------------------------------------------------------------

# 7. ACS Design and Architectures

### ACS Design Steps

> **Source: Slide 61**

-   Review & Understand Design Information
    -   Mission Description and/or Concept of Operations
    -   System and Subsystem Requirements
-   ConOps & mission geometry
-   Payload pointing requirements
-   Expected disturbances
-   Create a Preliminary Design
    -   Identify the most likely architecture (eg, 3-axis)
    -   Identify likely components (eg, sun sensors, star trackers,
        etc.)
    -   Size control effectors (eg, reaction wheels, CMGs, thrusters,
        etc.)
-   Consider functional redundancy, system cost, etc.
-   Create end-to-end kinematic simulation, error budgets, etc.
-   Understand fault scenarios
-   There is often a trade between thrusters & reaction wheels
    -   Create component mass list
-   Review & Iterate (w/broader team)
    -   Revisit other options & trades 9/26/2025 61 See HW7 for
        additional detail.

### Additional Guidance

> **Source: Slide 62**

-   ## Three Primary Functions

    Control, knowledge, & stability...

-   ## Common Sensors Across \~All Missions

    ## Sun sensors

    Gyros / IMUs

-   ## Destination Dependencies

    ## Low-Earth Orbit (LEO): Horizon sensors, GPS receivers, magnetic torquers

    Sun \< 2-3 AU: Electric propulsion for attitude control
    -   Deep Space: Star trackers
    -   Close Proximity Ops: Radars, LIDARs, etc.

-   ## Functional Dependencies

    Imaging s/c typically require reaction wheels, although cold gas
    systems are increasingly capable

-   ## Thrusters-only vs. reaction wheels is a common trade between cost & performance

    ## Larger, more agile s/c typically need CMGs

    Layers of redundancy increase with mission duration & budget
    9/26/2025 62 While the sizing of individual components is based on
    specific requirements, one can generally estimate a likely
    architecture based on a mission description and relative budget.

### ACS System Design

> **Source: Slide 63**

## Interpreting a Block Diagram

What function do each of the GN&C components provide? - What types of
missions do they support? - If component X fails, how does the failure
propagate? - Assuming realtime telemetry at 1 Hz, what is the ground
likely to see? - Is there a possibility of recovering the mission?
9/26/2025 63

### MRO GN&C Architecture

> **Source: Slide 64**

9/26/2025 64 GN&C Sensors C&DH (2) I/F & Controller RAD 750 CPU GN&C I/F
(GIF) Card Analog Acquisition Card (AAC) Signal Cond 1553 D/A IMU RS-422
A/D Pyro Initiation Unit (PIU) Valve Driver Module Multi-Function Bus
IMU (2) (gyros & accels)I Actuators Star Tracker (2) 4-Detector Sun
Sensors (2) 2-Detector Sun Sensors (4) angle, lin velocity, status @ 200
Hz photocell current photocell current ST cmds, quaternions, status @ 5
Hz Reaction Wheels (4) Reaction Wheel Electronics (4) Digital Tach I/F
Multi-Function Bus Power Distribution & Drive Unit (PDDU) 28 V dc
(unregulated) S/A and HGA Gimbal Drive Electronics Thrusters GN&C
Component Non-GN&C Component Analog I/F Digital I/F Legend 8 0.9-N (ACS)
6 22-N (TCM) 6 170-N (MOI) tach & direction RW cmds valve cmds gimbal
cmds, positions, rate, status @ 5 Hz

### Phoenix GN&C Architecture

> **Source: Slide 65**

9/26/2025 65 RPAM RBAU RPA RCE RMCA RPFA ≈ 40 mm Sensors I/F &Controller
Actuators Thrusters 4 - 5# (DV, P/Y) 4 - 1# (R/P/Y) 12 - 68# (DV, R/P/Y)
C&DH Payload & Att Cntrl I/F Card I/O Card (1553, A/D,Dis) RAD 6000 CPU
(VME BUS) (2) 28 V RS-422 IMU (2) IMU (2) (gyros & accels) delta ang
delta vel status @200Hz Legend: analog digital multi-function bus temp
Sun Sensor Assembly (2) photocell output CRUISE Stage Star Tracker (2)
CRUISE Stage Landing Radar 1553 Cmds, Beam Data Pyro Initiaion Unit
Valve Driver Module Power Dist & Drive Unit multi-function bus Cmds
Quaternions 1553 valve cmds Legend: Mars '01 Modified Mars '01 Heritage
Other Heritage New Development

### MSL GN&C Architecture

> **Source: Slide 66**

9/26/2025 66 Rover Power and Avionics Module (RPAM) B Bridge Bridge
Descent Power and Avionics Module (DPAM) B Rover Compute Element (RCE) B
Cruise Power and Avionics Module (CPAM) B RIMU NavCams A NavCams B
HazCams A Star Scanner Optics Star Scanner Elect A Star Scanner Elect B
EDL 1553 Bus RS-422 LVDS LVDS LVDS RS-485 Cruise RCS Entry RCS Mars
Landing Engines Cruise Power and Avionics Module (CPAM) A Rover Compute
Element (RCE) A Rover Motor Controller Assy (RMCA) Mobility, HGA, etc
Descent Power and Avionics Module (DPAM) A Descent IMU I/F I/F EDL 1553
Bridge BC BC Sun Sensor Heads A Sun Sensor Elect A Sun Sensor Heads B
Sun Sensor Elect B Radar Elect Radar Antens Radar T/Rs Inherited
Build-to-print New development Rover Power and Avionics Module (RPAM) A
Bridge Bridge Descent Motor Controller Assy (DMCA) RS-422 (DIMU repeat)
8 8 BC BC BC BC BC BC 8 Rover 1553 Bus EDL 1553 Bus Cruise Stage Descent
Stage Rover FSW FSW Flyaway FPGA

### MSL GN&C Architecture (Control System)

> **Source: Slide 67**

9/26/2025 67 wheel motors (6 drive, 4 steer) RIMU navcam stereo pair RSM
gimbal hazcam stereo pair (2) HGA gimbal IVP celestial bodies wrt each
other rover position and attitude wrt Mars terrain HGA Pointing
Instrument Pointing Instrument Pointing vehicle hardware & planetary
environment GNC algorithms and functions HGA Pointing Hazard Avoidance
Attitude Determination Position Determination Rover 3DOF Control
Celestial body Pos Propagator Visual Odometry Hazard Detection Odometer
Wheel/Steer Actuator RIMU Nav Camera Az/El Az/El Haz Camera Rover
Hardware Mars Rotation, Sun/Earth Positions Terrain GNC models

------------------------------------------------------------------------

# 8. Questions from Prior Class

### Questions from Prior Class (1 of 3)

> **Source: Slide 68**

-   ## What are the most commonly used actuators and why?

    ## Magnetic torquers for LEO satellites (cheap, simple)

    Thrusters (low precision) and reaction wheels (high precision)

-   ## Are there any missions that failed due to errors of GN&C actuators?

    ## Major driver of spacecraft failures & reliability, including both infant mortality & lifetime failures

    Phasing of sensors

-   ## Genesis- backwards G-switch (note that phasing tests are a critical part of testing)

    Loss of lubrication or unexpected friction

-   Dawn- reaction wheels; several failed prematurely, but Dawn was able
    to use electric prop.

-   ISS- failed gyros (reoccurring failures)

-   ## SOHO- failed gyro- (coupled with inadequate fault response nearly failed the mission)

    In 331b, we'll look at a few significant NASA failures...

-   ## At what altitude does some of the drag force start to disappear?

    ## Varies with drag coefficient & solar minimum/maximum

    At \> 600 km, gravity gradient dominates over drag. At \> 2,000 km
    disappears entirely

-   What attitude control happens at launch for the whole vehicle. Just
    gimbal of the main engines?
    -   Primarily the main engine gimbals 9/26/2025 68

### Questions from Prior Class (2 of 3)

> **Source: Slide 69**

-   Would it be possible to build a small cheap star sensor that worked
    from the Earth's surface assuming a cloudless night? Or would the
    components be far too expensive?
    -   Yes, and there are similar iPhone applications
    -   Drivers are likely ensuring adequate camera sensitivity and then
        going through the math, but similar image processing is
        well-published in literature

-   ## Is there any reason to use reaction wheels over cold gas RCS?

    Greater control via reaction wheels. Cold gas thrusters are
    improving, but difficult to compete against 0.0001-deg RWs

-   ## Have there been cases where new GN&C technology needed to be developed?

    ## On MSL, the landing radar was developed for the mission (overcame issues with Phoenix radar reliability)

    There is continued work to reduce the size of sensors & actuators
    (significant ongoing work on aircraft that drives space)

-   Would attitude control thrusters fall under the jurisdiction of the
    ADACS or the propulsion teams?
    -   Depends on the overall design
    -   For a small RCS system with no other propulsion, then it's all
        under ACS and no propulsion subsystem required
    -   Otherwise, it would typically be covered under propulsion

-   I'd like to know more about the GPS method for attitude
    determination. ... Would a GPS system at Mars be feasible?
    -   A GPS system functions by receiving 3+ GPS signals and then
        triangulating position
    -   Cost of deploying a constellation at Mars is prohibitive. If
        this can be solved, the next issue would be power -- GPS signals
        on Earth required \~500 W. On Mars, this translates to
        approximately 10 m\^2 just for the GPS power output. 9/26/2025
        69

### •

> **Source: Slide 70**

On weights attached to sensors in Chart 23, what missions might require
sudden, large updates of ATE versus more gradual updates? - Not many,
but some would be landers for terrain avoidance - How many total stars
have been cataloged? - Over a billion stars have been cataloged -
Typically, star tracker catalogs contain thousands (eg, 10,000) - How
was the comet sample in the Deep Impact mission relayed back to Earth?
Was it just the analysis of the videos and the plume, or was there a
physical sample that made it back to Earth? - Only data. Instruments
(including a spectrometer that can analyze the composition of the plume)
transmitted data back to Earth. The probe relayed its data via the
observing spacecraft. - How have we still been able to stay in contact
with older s/c like voyager, and when are we expected to lose any
communication with it and similar spacecraft? - It's case-by-case. - All
missions have a specific, funded lifetime. As the mission approaches its
end-of-life, the team will typically propose a mission extension. This
extension needs to include all applicable costs to maintain and
communicate with the spacecraft. It is then evaluated for cost &
benefit. - In the case Voyager, the DSN 70-meter stations continue to be
maintained to support communication, along with supporting personnel,
spacecraft knowledge, etc. 9/26/2025 70 Questions from Prior Class (3 of
3)

------------------------------------------------------------------------

# 9. Spacecraft Dynamics

### Part 4: Spacecraft Dynamics

> **Source: Slide 71**

9/26/2025 71

### Introduction

> **Source: Slide 72**

-   ## Kinematics

    Describes the motion of points, bodies (objects), and systems of
    bodies (groups of objects) without considering the forces that cause
    them to move.

-   ## Translational Motion

    ## Changes in the position and velocity of an object

    For spacecraft design, this primarily corresponds with understanding
    position relative a gravity field and changes in ∆V (vs. thrust)

-   ## Rotational Motion

    ## Changes in the attitude of an object

    For spacecraft design, this corresponds to attitude determination
    and control.

-   ## Importance

    Understanding and/or modeling the spacecraft attitude provides
    insight into:

-   Precision of sensors & actuators required

-   Performance capability to meet payload, ascent/descent,
    communication, and/or other requirements

-   Amount of propellant required

-   Detailed Concept of Operations, including required spacecraft
    behavior and responses

-   Margin/risk assessment 9/26/2025 72
    http://pinkmonkey.com/studyguides/subjects/physics/chap5/p0505103.asp

### Kinematics of Rotation

> **Source: Slide 73**

9/26/2025 73 From ADCS Handout, Joel Sercel, 2003 Comments - Since the
angular velocity varies with the radius, it is more difficult to
calculate basic physical relationships, and thus the next several charts
are intended to provide additional background - I'm reusing charts from
Joel Sercel's class, which should provide a good discussion found across
numerous references

### Rotational Kinetic Energy

> **Source: Slide 74**

9/26/2025 74 From ADCS Handout, Joel Sercel, 2003 Comments - Kinetic
Energy equation leads to K = ½ Iz ω\^2 - Where Iz is a constant (ie,
rotational inertia) that governs how a body behaves when a force (ie,
torque) is applied. - This is similar to mass in translational physics -
Iz is the moment of inertia about the z-axis

### Moment of Inertia & Angular Acceleration

> **Source: Slide 75**

9/26/2025 75 From ADCS Handout, Joel Sercel, 2003 Comments - Moment of
Inertia can now be related to Newton's 2nd Law (F=ma), resulting in a
loose equivalent wrt torques - α = angular acceleration (eg,
radians/s\^2)

**Equation(s) shown on slide:**

``` math
\tau_z=I_z\alpha
```

### Calculate Moment of Intertia

> **Source: Slide 76**

9/26/2025 76 From ADCS Handout, Joel Sercel, 2003 Comments - Note that ρ
is density here - Effectively, you are integrating x,y over the volume
at a given density to calculate the moment of inertia about the z-axis -
SI units are kg m\^2

**Equation(s) shown on slide:**

``` math
I_z=\sum_{i=1}^{n}m_i(x_i^2+y_i^2)
```

``` math
I_z=\int(x^2+y^2)\,dm=\int(x^2+y^2)\rho(\mathbf r)\,dV
```

### Example

> **Source: Slide 77**

Moment of Inertia of a Ring 9/26/2025 77 From ADCS Handout, Joel Sercel,
2003 Comments - Example for Iz of a thin 'ring'

### Additional Examples

> **Source: Slide 78**

9/26/2025 78 Sources - https://en.wikipedia.org/wiki/Moment_of_inertia -
https://en.wikipedia.org/wiki/List_of_moments_of_inertia Comments - Many
published formulas exist for basic shapes - This highly relevant because
you can determine the moments of inertia of complex shapes by summing
the individual components - We can do this via... - Parallel Axis
theorem - Perpendicular Axis theorem - Early in formulation, the ACS
engineer will estimate the s/c moment of inertia based on a general
approximate of a few shapes & masses

### Parallel Axis Theorem

> **Source: Slide 79**

9/26/2025 79 From ADCS Handout, Joel Sercel, 2003 Comments - This
formula is critical to combining moments of inertia in order to estimate
more complex shapes.

**Equation(s) shown on slide:**

``` math
I=I_{CM}+Mh^2
```

### Example

> **Source: Slide 80**

Moment of Inertia of Disk about Edge 9/26/2025 80 From ADCS Handout,
Joel Sercel, 2003

### Perpendicular Axis Theorem

> **Source: Slide 81**

9/26/2025 81 From ADCS Handout, Joel Sercel, 2003 Comments - This is
helpful for "thin" objects that are dominated by inertias about x & y

**Equation(s) shown on slide:**

``` math
I_z=I_x+I_y
```

### Moment of Inertia as a Tensor

> **Source: Slide 82**

9/26/2025 82 From ADCS Handout, Joel Sercel, 2003 Comments - This is the
equivalent of moment = mass x velocity (but wrt rotation) - Whereas in
translational physics, we can just use 'mass', here we need to use a 2nd
order tensor to fully define the inertia - We need each inertial
component about the axis (and their products for asymmetric shapes)
Angular rates are about each axis. This equation defines the momentum
(h) about each axis

**Equation(s) shown on slide:**

``` math
\mathbf h=\mathbf I\boldsymbol{\omega}
```

### Angular Momentum

> **Source: Slide 83**

9/26/2025 83 From ADCS Handout, Joel Sercel, 2003 ω Comments - This is
the equivalent of our translational h = mv - Previously, we used total
impulse (=Ft) to solve for thrust - Similarly, this will allow us to
solve for the torques required to change rotational velocity - Note:
momentum often defined as 'h' or 'L' Conservation of Angular Momentum

**Equation(s) shown on slide:**

``` math
\mathbf h=\mathbf I\boldsymbol{\omega}
```

### Moments & Products of Inertia

> **Source: Slide 84**

9/26/2025 84 From ADCS Handout, Joel Sercel, 2003 Comments - Note that
moments of inertia (x, y, z) are always positive - Products of inertia
(xy, yz, etc.) are measures of symmetry. If an object is symmetrical
across a plane (eg, XY plane), then the products associated with any
axis perpendicular are zero (Ixz, Iyz = 0)

### Torque

> **Source: Slide 85**

9/26/2025 85 Comments - Note the restrictions above (rigid body, etc.) -
For example, if goal is to maintain constant angular moment, then we
need to offset disturbances with counter torques From ADCS Handout, Joel
Sercel, 2003

**Equation(s) shown on slide:**

``` math
\mathbf T=\frac{d\mathbf h}{dt}
```

### Euler's Moment Equations

> **Source: Slide 86**

9/26/2025 86 Comments - These equations dictate the rotational movement
of a rigid body with respect to each axis - ω is angular velocity and h
= angular momentum; h = I ω From ADCS Handout, Joel Sercel, 2003

**Equation(s) shown on slide:**

``` math
\tau_1=\dot h_1+\omega_2h_3-\omega_3h_2
```

``` math
\tau_2=\dot h_2+\omega_3h_1-\omega_1h_3
```

``` math
\tau_3=\dot h_3+\omega_1h_2-\omega_2h_1
```

### Euler's Moment Equations

> **Source: Slide 87**

9/26/2025 87 From ADCS Handout, Joel Sercel, 2003 Comments - These
equations that relate the change in momentum to the torques acting on a
spacecraft can then be used to create an attitude control simulation -
This will be part of HW3c

**Equation(s) shown on slide:**

``` math
\dot h_1=I_1\dot\omega_1=T_1+(I_2-I_3)\omega_2\omega_3
```

``` math
\dot h_2=I_2\dot\omega_2=T_2+(I_3-I_1)\omega_3\omega_1
```

``` math
\dot h_3=I_3\dot\omega_3=T_3+(I_1-I_2)\omega_1\omega_2
```

### Euler's Angles

> **Source: Slide 88**

9/26/2025 88 Comments - Which leads us all the way back to roll, pitch,
and yaw and introduces rotation matrices. From ADCS Handout, Joel
Sercel, 2003

------------------------------------------------------------------------

# 10. Phoenix Radar Case Study

### Case Study

> **Source: Slide 89**

Phoenix Radar 9/26/2025 89

### Case Study

> **Source: Slide 90**

Phoenix Radar 9/26/2025 90

### Case Study

> **Source: Slide 91**

Phoenix Radar 9/26/2025 91

### Case Study

> **Source: Slide 92**

Phoenix Radar 9/26/2025 92

### How do you create simulations?

> **Source: Slide 93**

-   ## Phoenix EDL Major Sim Components (code, analysis, HW testing, etc.)

    ## Simulation integrator

    ## Atmospheric model

    ## Hypersonic aerodynamics model

    ## Gravity model

    ## Dispersed hypersonic aerodynamics model

    ## Parachute drag model

    ## Parachute inflation model

    ## Wrist mode model (x2 types)

    ## Configuration aerodynamics models (x 3 configs)

    ## Winds model (x2 types)

    ## RCS propulsion model

    ## IMU model

    ## Radar model (low fidelity)

    ## Descent engine propulsion model

    ## Phoenix flight software

    ADAMS model (mechanical simulation) 9/26/2025 93 Resulting
    Higher-Level Models

-   6-DOF Langley simulation

-   6-DOF Lockheed Martin sim

-   6-DOF Mechanical simulation

-   Flowtran Lander simulation

-   Flight software simulation Validated by Tests & Peer Reviews

-   Extensive literature & past missions (eg, Mars atmosphere, winds,
    terrain, etc.)

-   Wind tunnel testing (eg, parachute)

-   Radar field testing (added for PHX)

-   Thrusters (live-fire vacuum testing)

### Radar Assumptions

> **Source: Slide 94**

-   Originally, the Mars '01 (not flown) and Phoenix project had a
    simplified model for the radar which made the following assumptions:
    -   Infinite, sloped, flat plain
    -   Noise/bias characteristics that matched the requirements
    -   Very sharp, single-peak FFT velocity measurement outputs
    -   Assumed perfect angle-of-arrival (radar beam canted to be an
        offset from this)
    -   The radar will only have one target (ground only)
-   Those assumptions proved to be inadequate via field test data and
    development of a higher-fidelity simulation in the following ways:
    -   Terrain relief and brightness variation causes the look-vector
        to migrate
    -   Noise/bias characteristics change with varying terrain and
        target brightness
    -   FFT signatures are broader and show multiple peaks from nadir
        contamination, and wider FFT spectra peaks
    -   The angle of arrival is actually biased towards nadir from the
        original assumed angle
    -   The radar is guaranteed to see two targets (ground + heatshield)
        9/26/2025 94

### The model also missed...

> **Source: Slide 95**

-   Several Key Items...
    -   Multiple targets can confuse the search logic in the radar
        firmware to cause locks on false targets and ambiguities
    -   Never-before-discovered bugs in the radar firmware which can
        cause the radar to have prolonged lockup times under certain
        thermal & timing conditions
    -   Bi-modal lock-up behavior under certain conditions
-   Result
    -   Significant time required just prior to launch and during cruise
        to build, test, and incorporate a high-fidelity radar model into
        the Phoenix EDL simulation
    -   This fixed several anomalies that had the potential to fail the
        mission. But, it also uncovered new anomalies.... 9/26/2025 95

### How do you create simulations?

> **Source: Slide 96**

-   ## Phoenix EDL Major Sim Components (code, analysis, HW testing, etc.)

    ## Simulation integrator

    ## Atmospheric model

    ## Hypersonic aerodynamics model

    ## Gravity model

    ## Dispersed hypersonic aerodynamics model

    ## Parachute drag model

    ## Parachute inflation model

    ## Wrist mode model (x2 types)

    ## Configuration aerodynamics models (x 3 configs)

    ## Winds model (x2 types)

    ## RCS propulsion model

    ## IMU model

    ## Radar model (low & added high fidelity)

    ## Descent engine propulsion model

    ## Phoenix flight software

    ADAMS model (mechanical simulation) 9/26/2025 96 Resulting
    Higher-Level Models

-   6-DOF Langley simulation

-   6-DOF Lockheed Martin sim

-   6-DOF Mechanical simulation

-   Flowtran Lander simulation

-   Flight software simulation Validated by Tests & Peer Reviews

-   Extensive literature & past missions (eg, Mars atmosphere, winds,
    terrain, etc.)

-   Wind tunnel testing (eg, parachute)

-   Radar field testing

-   Thrusters (live-fire vacuum testing)

### Radar Data from Simulation

> **Source: Slide 97**

9/26/2025 97

------------------------------------------------------------------------

# 11. Deep Impact Star Tracker Anomaly

### Case Study

> **Source: Slide 98**

## Deep Impact Star Tracker Anomaly

  ep Impact
  ----------------------------------------------------------
  SA spacecraft designed to study the interior composition
  a comet by releasing an impactor into the comet

  unched in 2005, it resulted in a successful comet impact
  ----------------------------------------------------------
  wever, it almost never made it...
  26/2025

### Deep Impact Attitude Estimation

> **Source: Slide 99**

9/26/2025 99 - Attitude Estimation - Combines weighted measurement from
multiple sensors into a single attitude estimate - Typically uses
include gyro(s) for rate data and star tracker(s) for celestial attitude
data - Able to propagate for limited times in the absence of star
tracker data (given an initial reference) - Weights chosen to match
strengths of sensor - Low weights indicate that the sensor cannot
abruptly change the estimate as fast as other sensors - Conversely, high
weights allow a sensor to make sudden, large updates - Star Tracker
(Primary & Redundant) - Matches star images to a catalog to produce a
full 3- axis attitude with respect to a standard CS reference (eg,
J2000) - Can quickly determine attitude without any initial knowledge -
Can't sustain lock under fast rotations - Requires clear view of the sky
(can be dazzled by bright objects near by or in FOV) - Needs adequate
star density - Gyros - Provide angular rates, which can be integrated
over time to obtain angular position relative to a given reference -
Generally operate in "relative mode", relative to an assumed reference
and propagating changes in attitude without having absolute knowledge -
Able function under relatively "fast" rotations whereas other sensors
may not - Low signal-to-noise ratio (ie, less accurate) - Generally,
there is bias "or drift" rate over long periods of integration without
an absolute reference

### Background

> **Source: Slide 100**

-   ## After launch, Deep Impact enters a planned "safe-mode."

    In safe mode, it uses gyros and sun sensors, holding +Y axis on the
    sun and rotating once every 4 hours ("sunline" ACS state)
    -   Star trackers are mounted on the backside, facing somewhat
        anti-sun. They are not used at the beginning of the mission

-   Attitude Estimator (ATE) is integrating gyro data from a "wake- up"
    frame. This frame is defined as the s/c frame at the instant that
    the s/c is commanded to sunline mode

-   After post-launch orbit check-out and initial spacecraft health
    assessment, the star trackers are turned on by ground command

-   Nominally, ATE will accept data from the star trackers and will
    slowly correct its estimate to reflect the data coming from the STs.
    -   The ATE mixes in gyro data with ST data with much greater weight
        placed on the gyro data. Over time, the STs will 'win' but in
        the short time the current ATE estimate wins. This is considered
        a "slow drip" correction.

-   The nominal plan is that after the ATE has converged, the ground
    will command the spacecraft to go from safe-mode to 3-axis control
    9/26/2025 100 Star Trackers

### Attitude Estimation

> **Source: Slide 101**

-   Twice every 4 hours, the ATE estimate jumps up & down
    discontinuously. The jumps are 11-12 min apart
    -   Note that 1 full rotation = 4 hours 9/26/2025 101 4 hours

### Star Tracker "Lock" State

> **Source: Slide 102**

-   Coincident with the jumps are star tracker outages...
-   Interval between jumps corresponds to 19-deg (relative alignment of
    star trackers), suggesting a systemic issue...
-   Star tracker data alone suggests the sun is significantly (\~90-deg)
    off from expectations. Given sun sensor & solar array data, this
    suggests possible ST alignment issue
-   Data suggests this issue is occurring when star trackers are pointed
    towards celestial true north 9/26/2025 102 Possible Issues
-   Star tracker alignment
-   ACS/ATE software
-   Earth in FOV
-   "Dark spot" in sky

### Documentation Discovery...

> **Source: Slide 103**

-   Going through documentation, an error in the coordinate frame
    transformation was discovered...
    -   A 90-deg rotation to translate from mechanical from to
        spacecraft frame was dropped...
    -   All three star trackers (including impactor) had incorrect
        alignments 9/26/2025 103

### Virtual Star Tracker

> **Source: Slide 104**

9/26/2025 104 Star Tracker pointing "Twisted" refers to the 90-deg
coordinate frame error Virtual Star Tracker When both star trackers on
and in- lock, the attitude algorithm only uses the boresight vectors of
the actual trackers (which are correct) However, when only 1 star
tracker is in-lock, the whole quaternion from the star tracker is used
for the attitude, which includes the 90-deg error

### Another Discovery...

> **Source: Slide 105**

-   Star Catalogs contain large numbers of stars, indexed, and sorted by
    declination
-   While these star trackers had significant heritage, additional stars
    were added to the catalog to ensure a high density given the mission
    in deep space
-   However, when these stars were added, there was a corresponding
    parameter that set the length of the list -- and it wasn't increased
-   Therefore, the list was cut-off at declinations of greater than
    80-deg.
-   Thus, the failure to lock attitude near the celestial North Pole
    9/26/2025 105 Star Catalog (representation)

### Lessons Learned

> **Source: Slide 106**

-   ## Keep It Simple

    ## "Virtual Star Tracker" seemed like a good idea, but it obscured the problem...

    ## Fortunately, safe mode wasn't relying on ATE for attitude estimate

    This allowed the anomaly to be de-bugged while in sunline mode (via
    coarse sun sensors)

-   ## Phasing Tests Are Critical...

    ## A star tracker phasing test "should" have identified the mis-alignment.

    Unclear whether it occurred or properly verified

-   ## Explain All the Observables

    Multiple errors occasionally occur and require significant
    exploration even after some/most of the issues have been explained
    -   This is the benefit of using a fishbone diagram and driving to
        closure

-   ## Beware of Heritage

    Initially, the team was very skeptical that there was a star tracker
    issue given the significant heritage. Finally, after significant
    convincing, the team investigated and discovered the incorrect
    parameter 9/26/2025 106 Note that the alignment error was found on
    all three star trackers, including the one on the impactor. If it
    had been limited to the impactor, the issue may not have been caught
    until there was insufficient time to fix prior to the comet flyby.

------------------------------------------------------------------------

# Lecture Summary

> **Source: Full Lecture**

The Attitude Control System provides spacecraft **attitude control,
knowledge, and stability** using sensors, control effectors, and onboard
logic/control.

Key takeaways:

-   **ACS Functions:** Pointing is driven by science observations,
    trajectory maneuvers, telecom, thermal constraints, power
    generation, and spacecraft agility.
-   **Disturbances:** Important disturbance torques include aerodynamic,
    gravity-gradient, magnetic, solar-radiation, mass-expulsion, launch
    tip-off, and internal torques.
-   **Sensors:** Sun sensors, Earth sensors, magnetometers, star
    trackers, gyros/IMUs, GPS receivers, and mission-specific sensors
    provide attitude knowledge at different levels of accuracy and
    complexity.
-   **Control Effectors:** Reaction wheels, momentum wheels, CMGs,
    magnetic torque rods, and reaction-control thrusters provide
    different combinations of accuracy, control authority, momentum
    capacity, and propellant use.
-   **Redundancy:** ACS commonly uses hardware or functional redundancy
    because loss of attitude control can threaten the mission.
-   **Mission Geometry:** SEP, SPE, phase angle, solar-incidence angle,
    payload FOV, thermal constraints, and communications geometry can
    drive spacecraft pointing.
-   **Spacecraft Dynamics:** Moment of inertia, angular momentum,
    torque, Euler's moment equations, and Euler angles provide the basis
    for modeling rotational motion.
-   **Case Studies:** Phoenix demonstrates the importance of simulation
    fidelity and realistic testing. Deep Impact demonstrates the
    importance of coordinate-frame verification, phasing tests,
    explaining all observables, and carefully validating heritage
    hardware and parameters.

