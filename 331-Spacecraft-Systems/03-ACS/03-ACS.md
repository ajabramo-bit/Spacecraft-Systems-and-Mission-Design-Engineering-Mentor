# Attitude Control System (ACS)

**Course:** ASTE-331a --- Spacecraft Systems Engineering\
**Lecture:** 03 --- Attitude Control System (ACS)\
**Instructors:** Jim Chase, Danielle Marsh\
**Source:** `331_03_ACS_20250926(2).pdf`

------------------------------------------------------------------------

## Lecture Overview

This lecture introduces the spacecraft **Attitude Control System (ACS)**
and develops the relationship between spacecraft pointing requirements,
attitude knowledge, control effectors, disturbance torques, mission
geometry, rotational dynamics, and end-to-end simulation.

The lecture begins with the purpose and terminology of attitude
determination and control, then uses **OSIRIS-REx** as a detailed
mission example. It develops the major disturbance sources that drive
ACS performance, including aerodynamic, gravity-gradient, magnetic,
solar-radiation, mass-expulsion, and internal torques. It then examines
spacecraft pointing constraints from payload operations, communications,
power, thermal design, trajectory maneuvers, and agility.

The hardware portion covers the major **attitude-determination
sensors**---sun sensors, Earth sensors, magnetometers, star trackers,
gyroscopes/IMUs, and GPS receivers---and the primary **GN&C
actuators/effectors**---reaction wheels, momentum wheels, control moment
gyros, magnetic torque rods, and reaction-control thrusters. The lecture
also discusses redundancy, component sizing, architecture selection, and
physical/logical block diagrams.

The spacecraft-dynamics portion develops the rotational physics used in
ACS analysis, including kinematics of rotation, rotational kinetic
energy, moment of inertia, angular acceleration, parallel/perpendicular
axis theorems, inertia tensors, angular momentum, torque, Euler's moment
equations, and Euler angles.

Finally, the lecture uses the **Phoenix radar** and **Deep Impact star
tracker** case studies to demonstrate why simulation fidelity, realistic
testing, coordinate-frame verification, phasing tests, fault-response
independence, and careful investigation of all observables are critical
to spacecraft GN&C.

## Table of Contents

-   [1. ACS Overview and Fundamentals](#1-acs-overview-and-fundamentals)
-   [2. OSIRIS-REx Mission and ACS
    Example](#2-osiris-rex-mission-and-acs-example)
-   [3. Spacecraft Disturbances](#3-spacecraft-disturbances)
-   [4. Pointing Concerns and Mission
    Geometry](#4-pointing-concerns-and-mission-geometry)
-   [5. Attitude Determination
    Sensors](#5-attitude-determination-sensors)
-   [6. GN&C Actuators and Effectors](#6-gnc-actuators-and-effectors)
-   [7. ACS Design, Redundancy, and
    Architectures](#7-acs-design-redundancy-and-architectures)
-   [8. Spacecraft Dynamics](#8-spacecraft-dynamics)
-   [9. Phoenix Radar Case Study](#9-phoenix-radar-case-study)
-   [10. Deep Impact Star Tracker
    Anomaly](#10-deep-impact-star-tracker-anomaly)
-   [Lecture Summary](#lecture-summary)

------------------------------------------------------------------------

# 1. ACS Overview and Fundamentals

> **Source: Slides 2--7**

## Lecture Outline

The lecture is organized around:

-   **Overview**
-   **Design**
    -   Disturbances (aerodynamic, gravity gradient, magnetic, solar
        radiation, mass expulsion, internal)
    -   Sensors (sun, earth, magnetometer, star tracker, gyroscope/IMU,
        GPS)
    -   Actuators & Effectors (reaction wheels, momentum wheels, CMGs,
        torque rods, RCS thrusters)
    -   Block Diagrams (physical & logical architectures)
    -   Architectures (eg, 3-axis, spinning)
    -   Mission Geometry & Pointing Concerns
    -   Sizing
-   **Example: ISS**
-   **Control & Logic**
    -   Rotational Kinematics
    -   Moments of Inertial & Angular Acceleration
    -   Angular Momentum & Torque
    -   Euler's Equations
    -   Modeling, Slew Rates, & Spacecraft Motion
-   **Example: Osiris Rex Sample Collection**
-   **Case Study: Phoenix EDL**
-   **Case Study: Deep Impact Star Tracker Anomaly**

## Attitude Determination and Control

Attitude Determination and Control is the spacecraft subsystem that
provides **attitude control, knowledge, and stability**, including the
actuators, sensors, and onboard logic/control.

### Also Known As

-   **AACS:** Attitude and Articulation Control System
-   **ACS:** Attitude Control System
-   **ADCS:** Attitude Determination Control System
-   **ADACS:** Attitude Determination and Control System
-   **AOCS:** Attitude and Orbit Control System
-   **G&C:** Guidance and Control System
-   **GN&C:** Guidance, Navigation, and Control
-   **PCS:** Pointing Control System

## Attitude Control Subsystem

> **Source: Slides 4**

### Function

-   Provide attitude control, knowledge, and stability to support
    spacecraft pointing.
-   Primary drivers for pointing are:
    -   Science observations (instrument FOVs)
    -   Trajectory course maneuvers (thrust)
    -   Telecom (uplink/downlink to Earth)
    -   Thermal (wrt sun, Earth, etc.)
-   Also called ACS, ADCS, AOCS, etc.

### GRAIL Example

-   1 star tracker
-   3 reaction wheels
-   1 inertial measurement unit (IMU)
-   1 sun sensor (x4)
-   Total = \~5 kg

### Common Components

-   **Sensors**
    -   Sun sensors, magnetometers
    -   Gyros, GPS receivers
    -   Star trackers
-   **Control Effectors**
    -   Reaction or momentum wheels
    -   Control moment gyros
    -   Magnetic torquers
    -   Reaction control thrusters (see propulsion)

### Key Trades & Analyses

-   3-axis control, spin, gravity gradient...
    -   Reaction wheels vs. thrusters, etc.
-   Control/knowledge/stability analyses and error budgets
-   Heritage from prior systems

### Key Parameters

-   Mass, power, and cost
-   Pointing control, knowledge, stability/jitter

## Closed-Loop Attitude Control

The lecture's block diagram shows the basic feedback loop:

``` text
Ground or Autonomous Commands
            ↓
        Controller
            ↓
        Actuators
            ↓
          System
            ↓
         Sensors
            └──────────────→ measured attitude feedback
```

Disturbances can act on both the spacecraft system and the sensors.

The attitude error is:

``` text
Attitude Error = Commanded Attitude - Measured Attitude
```

**Figure description:** The diagram shows commanded attitude entering
the controller, device commands flowing to the actuators, the actuators
changing the spacecraft system, and sensors feeding measured attitude
back to the controller. Separate disturbance inputs act on the system
and sensors.

## Slew Rates and Spacecraft Motion

The lecture asks:

-   **What do typical spacecraft motions look like?**

**Figure description:** The slide shows a spacecraft-pointing
visualization with a 3-D Earth view and a map projection. Sensor
latitude, longitude, and target elevation are displayed to illustrate
how a spacecraft's pointing geometry changes relative to locations on
Earth.

## ACS Terminology

-   **Attitude:** Orientation of a defined reference system attached to
    the spacecraft body.
-   **Determination:** Knowledge within a specified tolerance (realtime
    or post-facto).
-   **Control:** Maintenance of specified attitude within a given
    tolerance.
-   **Pointing Error:** Low frequency component of attitude
    misalignment.
-   **Jitter:** Spacecraft stability, consisting of the high frequency
    component of attitude error (minimized by design).

**Figure description:** A telescope boresight example compares the
actual attitude, desired attitude based on payload requirements, and
attitude knowledge based on sensors. A second graphic separates attitude
error into low-frequency **pointing** error, which is typically
corrected, and high-frequency **jitter/stability**, which is typically
uncorrected.

------------------------------------------------------------------------

# 2. OSIRIS-REx Mission and ACS Example

> **Source: Slides 8--18**

## Mission Objectives and Spacecraft

OSIRIS-REx stands for **Origins, Spectral Interpretation, Resource
Identification, Security-Regolith Explorer**.

### Mission Objectives

-   Launched on Sept. 8, 2016, the spacecraft traveled to a near-Earth
    asteroid called Bennu.
-   It has collected a sample of rocks and material from the surface
    that it returned to Earth on Sept. 24, 2023.
-   The mission will help scientists investigate how planets formed and
    how life began, as well as improve our understanding of asteroids
    that could impact Earth.

**Figure description:** The slide combines three views: the spacecraft
near Bennu, a solar-system trajectory graphic showing Earth, Venus,
Mars, and Bennu, and a labeled OSIRIS-REx spacecraft diagram. The
spacecraft diagram identifies the 2-m HGA, solar arrays, 2-axis gimbal,
MGA/LGA, star trackers, 200-N thrusters, helium tank, MRO-like core
structure, TAGSAM, OVIRS, OTES, OCAMS, OLA, REXIS, SRC, and GN&C LIDAR.

## Asteroid Sample Collection Overview

**Figure description:** The mission timeline runs from launch in 2016
through Earth gravity assist, approach maneuver, asteroid operations,
sample collection in 2020, departure maneuver, return cruise, sample
return in 2023, and sample analysis. The main image shows the spacecraft
maneuvering near Bennu during the sample-collection mission.

## Instrument Deck

### Instruments

-   **OCAMS:** Camera Suite (UofA)
    -   PolyCam: Narrow angle, high resolution (8-inch telescope)
    -   MapCam: Wide angle, high resolution (4-color, asteroid mapping)
    -   SamCam: Monitors TAG and sample acquisition
-   **OLA:** LIDAR for high-resolution topography (CSA contribution)
-   **OTES:** Thermal Spectrometer, 5.7-100 microns (ASU)
-   **OVIRS:** Visible & IR Spectrometer, 0.4-4.3 microns (GSFC)
-   **REXIS:** X-ray Spectrometer (student experiment)

### GN&C Components

-   4 Sun Sensor Assemblies (SSA)
    -   4 heads & 2 heads (x2 = 12)
-   4 Reaction Wheels
-   2 Star Trackers
-   2 MIMUs (Miniature IMUs)
-   2 LIDARs (40 cm @ 3 km)
-   TAGCAMs
    -   2 NavCams (Optical Nav)
    -   StowCam
    -   Camera Electronics
-   16 ACS thrusters
-   2 TAG thrusters

**Figure description:** A detailed instrument-deck rendering identifies
the locations of REXIS, OCAMS, OTES, OVIRS, StowCam, NavCams, LIDARs,
camera electronics, star trackers, thrusters, and sun-sensor locations.
The slide ties the component list directly to the physical spacecraft
layout.

## Spacecraft Block Diagram

**Figure description:** The full spacecraft block diagram shows how GN&C
interfaces with propulsion, avionics, telecom, EPS, payloads, TAGSAM,
mechanisms/thermal, and the sample-return capsule. The GN&C portion
includes sun sensors, star trackers, MIMUs, GN&C LIDAR, NavCams,
TAGCAMS/DVR, StowCam, and reaction-wheel assemblies, with interface
types and redundancy indicated by the legend.

## ACS Design Discussion

### Discussion Topics

-   Sensors, Actuators, Electronics, and software?
-   Redundancy?
-   Heritage?

**Figure description:** The GN&C architecture is shown next to the
avionics system. It illustrates GN&C sensors and actuators interfacing
with C&DH and power electronics through Mil-Spec 1553, analog/other
connectors, and an LVDS connector. The legend identifies build-to-print,
minor modification, new development, cross-strapped units, block
redundancy, functional redundancy, and interface types.

## Touch & Go (TAG)

### Questions from Last Year

-   Why was there no realtime video? (What was the downlink rate?)
-   How does the prediction compare to the sample?

**Figure description:** The slide shows mission-control operations and
two views of the TAG event: the spacecraft descending toward Bennu and
the TAGSAM head contacting the asteroid surface.

## Onboard Sample

### 1--2 Days Later

-   Collector lid likely not fully closing due to larger rocks, thus
    leaking...
-   Forgoing sample measurement in favor or earlier stowing (significant
    sample observed)

**Figure description:** The image shows the TAGSAM collection head with
material visible around the collector opening, illustrating the concern
that larger rocks prevented the collector lid from fully closing.

## Sample Stowage and Earth Return

-   Stow successful and ready for its return.
-   Delivery achieved on 9/24/2023.
-   Entry, descent, and landing:
    -   Heatshield to slow high-speed entry
    -   Parachute to reduce speed further
    -   Landing area is the Utah test range

**Figure description:** The slide shows the sample-return capsule being
positioned and enclosed during stowage, together with a spacecraft
animation of the stow sequence.

## Questions from Last Year

### Touch-and-Go Performance

-   From 1 to 10, how bad was the slight error the OSIRIS-REX Touch and
    Go? Are these kinds of things usually expected or was it a complete
    surprise?
    -   Likely well within the modeled capability (\~3).
    -   Typically, videos are based on the 'nominal' scenario, but
        analysis is far more encompassing.
    -   That said, there are still surprises... (both MER rovers were
        barely within their performance envelopes).

### Mission Development Time

-   How long is each step in the Osiris Rex mission take? As in, how
    long until NASA decides to return to the asteroid for a second
    sample if needed?
    -   Scientific consensus & technology development: Varies greatly
        (many years possible)
    -   Proposal Process: 1-3 years
    -   Development: 4-5 years
    -   Operations and Sample Return: 5-10 years
    -   Total: ≥ 10-20 years

### Changing Uplink/Downlink During a Mission

-   Options for increasing the uplink/downlink rates:
    -   Greater use of data compression
    -   Increase downlink at the expense of the bit error rate (BER)
    -   Adjust trajectory to reduce distance (mission dependent)
-   Going to look at this in detail when we talk about Telecom.

### TAG Approach Velocity

-   At touch-down, expected 0.4 m/s.
-   Comparison: Phoenix lander touched down around 1.5 m/s.
-   MER Rovers (w/airbags): \< 26 m/s.

### Propellant vs. Asteroid Uncertainty

-   Bounding estimates are developed for the asteroid size, shape,
    gravity map.
-   Sufficient propellant margin is carried to encompass these
    estimates.
-   Prior to approach, significant observations (at 2-3 km) are
    undertaken (along with fly by's) to improve fidelity of the gravity
    field.

### Is the Spacecraft Actually Orbiting Bennu?

-   Yes, 62 hrs/orbit and more or less circular.
-   Using features on Bennu for attitude knowledge.
-   Simple fault protection:
    -   If something goes wrong, burn towards the sun.

**Figure description:** The final OSIRIS-REx question slide includes a
"Playing TAG with Bennu" trajectory diagram showing the spacecraft's
approach, orbit, and TAG geometry around Bennu.

------------------------------------------------------------------------

# 3. Spacecraft Disturbances

> **Source: Slides 19--25**

## Disturbance Torque

Disturbances are torques that are typically induced on the spacecraft by
external forces.

-   Typically modeled as a force (representing a center of pressure)
    acting on the spacecraft body at some radius from the center of
    mass.

The general torque relationship is:

``` math
\boldsymbol{\tau}=\mathbf{r}_{CP}\times\mathbf{F}
```

where:

-   **$\mathbf{r}_{CP}$** = radius from center of mass
-   **$\mathbf{F}$** = force

Examples:

-   Launch vehicle tip-off
-   Aerodynamic
-   Gravity Gradient
-   Magnetic
-   Solar Radiation
-   Mass Expulsion
-   Internal

**Figure description:** A spacecraft near Earth is surrounded by arrows
representing disturbance sources. The figure identifies solar radiation,
magnetic effects, gravity gradient, atmospheric drag, and cover ejection
or deployment.

## Aerodynamic Torque

The lecture describes the **"weathervane" effect of Center of
Mass/Center of Pressure (CM/CP) offset**.

Aerodynamic torque:

``` math
\boldsymbol{\tau}_a=\mathbf{r}_{CP}\times\mathbf{F}_a
```

Aerodynamic force:

``` math
F_a=\frac{1}{2}\rho S C_Dv^2
```

where:

- $\mathbf{r}_{CP}$ = center of pressure position vector in body fixed frame
- $\mathbf{F}_a$ = aerodynamic force
- $\rho$ = atmospheric density
- $v$ = spacecraft velocity
- $S$ = projected area (perpendicular to $v$)
- $C_D$ = drag coefficient (use 2 as for a worst case analysis)

For example, at 400 km altitude, there might be a **3.11 × 10⁻⁵ N·m
torque**, which would result in an attitude error of **82-deg after one
orbit**.

**Source on slide:** "Attitude Determination and Control", Joel Sercel,
2003.

## Gravity Gradient

Gravity gradient creates a torque tending to rotate the spacecraft to
align its minimum inertia axis with the local vertical.

The slide gives the gravity-gradient torque relationship in terms of
orbital rate, the Earth-to-vehicle unit vector, and the spacecraft
inertia tensor.

Typical values shown:

-   ΔI = 1000 kg·m²
-   n = 0.001 s⁻¹
-   τ = 6.7 × 10⁻⁵ N·m/deg

**Figure description:** The diagram shows a spacecraft in orbit with
pitch angle θ relative to the local vertical. The gravity-gradient
effect tends to align the spacecraft's minimum-inertia axis with that
vertical direction.

**Source on slide:** "Attitude Determination and Control", Joel Sercel,
2003.

## Magnetic Torque

Present when in orbit around a planet with a substantial magnetic field,
like Earth and Jupiter.

``` math
\boldsymbol{\tau}_m=\mathbf{M}\times\mathbf{B}
```

where:

-   **M** is the spacecraft magnetic dipole moment due to current loops
    and residual magnetization in the spacecraft. It is expressed in
    A·m².
-   **B** is the planet magnetic field vector expressed in spacecraft
    coordinates.

Typical values for a small spacecraft in LEO:

``` math
B=3\times10^{-5}\ \text{T}
```

``` math
M=0.1\ \text{A}\cdot\text{m}^2
```

``` math
\tau_m=3\times10^{-6}\ \text{N}\cdot\text{m}
```

**Source on slide:** "Attitude Determination and Control", Joel Sercel,
2003.

## Solar Radiation

In body coordinates, the solar-radiation-pressure torque is:

``` math
\boldsymbol{\tau}_s=\mathbf{r}\times\mathbf{F}_s
```

The slide defines the force using surface reflectivity, projected area,
solar intensity, speed of light, and distance from the Sun.

Typical values for a spacecraft in Earth orbit:

- $r = 0.1\ \text{m}$
- $S_{\perp} = 5\ \text{m}^2$
- $I_s = 1400\ \text{W/m}^2$ (Solar intensity at 1 AU)
- $K = 0.5$
- $c = 3 \times 10^8\ \text{m/s}$
- $\tau_s = 3.5 \times 10^{-6}\ \text{N}\cdot\text{m}$

Dominant effect in:

-   GEO Orbits
-   Deep space cruise

Notes:

1.  The torque vector is always perpendicular to the sun line.
2.  Independent of altitude and velocity as long as in sunlight.

**Source on slide:** "Attitude Determination and Control", Joel Sercel,
2003.

## Mass Expulsion

Mass expulsion includes a wide range of activities:

-   **Jettison:** Probes, covers, expended SRMs, etc.
-   **Deliberate:** Thrusters, gas venting, etc.
-   **Accidental:** Leaks, misalignments

If significant, it can dominate the overall forces and result in changes
to the attitude control system.

Mass-expulsion torque:

``` math
\boldsymbol{\tau}_{ME}=\mathbf{r}_{CP}\times\mathbf{F}_{ME}
```

where **FME varies considerably**.

**Figure description:** Cassini is shown releasing the Huygens probe,
illustrating a deliberate mass-expulsion event that can impart force and
torque to the parent spacecraft.

## Internal Torque

Internal torque is typically caused by:

-   **Deployments:** Solar arrays, antennas, booms, instruments
-   **Recurring Motions:** Instrument scanning, sample retrieval, fluid
    flow, thermal louvers, etc.

It has no effect on total system angular momentum, but it still effects
attitude.

**Figure description:** Mars Odyssey is shown with its deployed boom,
solar array, high-gain antenna, star cameras, and science instruments.
The boom deployment is highlighted as an example of an internal motion
that can disturb spacecraft attitude.

------------------------------------------------------------------------

# 4. Pointing Concerns and Mission Geometry

> **Source: Slides 26--38**

## Typical Pointing Concerns

### Payload

-   Perform science observations
    -   With the sun often within a specified phase angle range
-   Avoid Sun on sensitive instruments (eg, camera boresight)

### Communications

-   Avoid solar conjunction

### Solar Arrays for Power

-   Minimize solar incidence angle

### Thermal

-   Spacecraft design typically favors or excludes a particular geometry

### Trajectory Maneuvers

-   Pointing & stability for maneuvers

### Spacecraft Agility

-   How quickly can the spacecraft change directions?

**Figure description:** The first pointing slide uses a spacecraft
body-fixed coordinate system to identify the **xb, yb, and zb axes** and
the corresponding **roll, pitch, and yaw** rotations.

## Payload Pointing and Phase Angle

Payload science observations often require the Sun to remain within a
specified **phase-angle** range, while sensitive instruments may also
require Sun-avoidance constraints.

The slide notes that phase angle is **often a driver for control,
knowledge, & error**.

**Figure description:** The spacecraft body axes are shown relative to
the Sun and an asteroid target. Two vectors at the target define the
phase angle used for science-observation geometry.

## Payload Observation Architectures

The lecture compares three ways to point a payload:

1.  **Spacecraft points at the target as a rigid body**
    -   Typically controlled by onboard ACS.
2.  **Actuators adjust the instrument or scanning-platform pointing.**
3.  **Instrument collector is oversized**
    -   Allows the instrument to internally point/filter data.

Onboard ACS is typical, but other approaches can occasionally produce
improved performance while maintaining cost.

### Terminology

-   **Nadir:** pointing towards (eg, Earth)
-   **Zenith:** pointing away (eg, Earth)

**Figure description:** Three instrument concepts are drawn above Earth:
whole-spacecraft pointing, an independently articulated instrument, and
an oversized collector capable of internal pointing/filtering.

## Communications Pointing

-   Avoid solar conjunction (**SEP angle near 0-deg**).
-   Low gain antennas typically provide communication at any nominal
    attitude.
-   High gain antennas often require 3-axis control (combined w/science
    & communications).

**Figure description:** The spacecraft's HGA boresight is shown pointing
toward Earth while the Sun-Earth-Probe (SEP) angle defines the
communications geometry.

## Solar Arrays for Power

-   Minimize solar incidence angle.
-   Maintain power while transmitting.

Arrays will often be **single- or dual-axis articulated** to minimize
solar incidence angle.

The slide also notes that arrays will occasionally be **oversized to
relax pointing requirements**.

**Figure description:** The Sun-Probe-Earth (SPE) angle and
solar-incidence angle are shown relative to the spacecraft body axes,
illustrating the need to balance solar-array pointing and Earth-pointing
communications.

## 3-Axis vs. Dual-Spin Stabilization

In this example, a solar array that wraps-around a spacecraft minimizes
the required pointing control.

**Figure description:** A three-axis stabilized spacecraft and a
dual-spin stabilized spacecraft are compared in Earth orbit. The
dual-spin spacecraft uses a cylindrical wrap-around solar array,
reducing the need to continually point a planar array toward the Sun.

## Thermal Pointing

Spacecraft design typically favors or excludes a particular geometry.

**Figure description:** Thermal-analysis graphics and a telescope
spacecraft illustrate how spacecraft attitude affects thermal loading.
The spacecraft layout shows the telescope, solar-panel shield, outer
shell, spacecraft bus, star trackers, and antennas.

## Trajectory Maneuvers

-   Pointing & stability for maneuvers.

**OSIRIS-REx example:**

-   4 200-N thrusters
-   Exhaust vector

**Figure description:** The OSIRIS-REx trajectory is shown together with
the spacecraft and its four 200-N thrusters. The exhaust vector
illustrates how spacecraft orientation is constrained during major
trajectory maneuvers.

## Spacecraft Agility

How quickly can the spacecraft change attitude?

Typically driven by opportunities & threats:

-   Additional science observations?
-   Science vs. communication latency?
-   Attitude changes due to eclipse?

**Figure description:** An Earth-orbit diagram shows changing spacecraft
orientations around an orbit, including Sun-pointing and Earth-pointing
geometries, illustrating why attitude changes can be driven by mission
opportunities and environmental events.

## Slew Rates and Spacecraft Motion

### How fast does a typical spacecraft turn?

-   Typical spacecraft requirement is **1 deg/sec**.
-   Might vary between **0.25 deg/sec to 3 deg/sec**.
-   Faster slew rates require **"settling time"** to achieve stability
    requirements.
-   ISS slew rate is **\< 0.1 deg/sec**.

### How much does the typical satellite actually have to maneuver?

-   Majority of spacecraft are for either imagery or communications
    (across the EM spectrum).
-   Therefore, most have telescopes, antennas, and/or detectors that
    require some degree of pointing (typically between **0.001-deg and
    0.1-deg**).
-   ACS activity is a function of the disturbance environment
    vs. spacecraft activity.
    -   Whenever spacecraft are "holding" their attitude, they are using
        their ACS actuators.
-   Maneuvers (including slews) tend to vary greatly, for example:
    -   Mars Reconnaissance Orbiter (MRO) can take dozens of pictures
        each day.
    -   Communications satellite in geo might desaturate its wheels
        once/week.

## Mission Geometry --- Key Angles

In concept formulation, these key angles will often drive the early
design:

-   **Sun-Earth-Probe (SEP) Angle**
-   **Sun-Probe-Earth (SPE) Angle**
-   **Phase Angle**

The Mission Design & Nav. Engineer will typically produce plots of these
in addition to trajectory designs and ΔV budgets.

**Figure description:** The geometry diagram places the Sun, Earth,
spacecraft probe, and target in a common view and defines SEP at Earth,
SPE at the probe, and phase angle at the target.

## Mission Geometry Example --- Asteroid Rendezvous

Based on the chart:

-   Rendezvous is occurring at a favorable phase angle wrt science
    observations.
-   Communications blackout when **SEP \< 2-deg** (solar conjunction).
-   **0 to 45-deg SPE range** suggests articulated arrays and/or antenna
    to maintain both power and communication.

**Figure description:** The trajectory-geometry plot charts phase, SEP,
and SPE angles over time. Shaded regions identify asteroid rendezvous
and solar conjunction, showing how mission events align with the
changing geometry.

## Thermal/ACS Relationship

### What does it mean to design a spacecraft that favors or excludes a particular geometry?

-   While spacecraft are generally designed to be robust even in the
    event of attitude errors, spacecraft will still have thermal
    constraints.
-   For example, SIRTF must keep its solar array on the sun both to
    provide power **AND** to keep the telescope barrel (and especially
    the cryogenic detector) shaded.

### How do you evaluate SEP, SPE, and phase angle?

These angles are based on outputs from trajectory or visualization
software (eg, STK).

**Strategic Evaluation:**

-   **Phase Angle**
    -   Mission Design & Nav. consider trajectory/orbital mechanics to
        ensure best lighting for science ops (30-60-deg incidence).
-   **Sun-Probe-Earth (SPE)**
    -   Power/Telecom engineers consider solar array vs. antenna
        pointing during mission.
-   **Sun-Earth-Probe (SEP)**
    -   Mission Design & Nav. and Telecom engineers consider solar
        conjunction wrt communications (eg, 2-deg).

**Tactical Evaluation:**

-   What is the best attitude at any given point during the mission with
    respect to sun (power & thermal) and Earth (telecom)?

**Figure description:** A SIRTF/Spitzer-style telescope spacecraft is
shown with the telescope, solar panel/shield, spacecraft bus, star
trackers, and antennas, illustrating the coupling between ACS pointing
and thermal design.

------------------------------------------------------------------------

# 5. Attitude Determination Sensors

> **Source: Slides 39--47**

The lecture identifies the following attitude-determination sensors:

-   Sun Sensors
-   Earth Sensors
-   Magnetometers
-   Star Trackers / Stellar Reference Units (SRUs)
-   Gyroscopes / Internal Reference Units (IRUs)
-   GPS Receivers

**Figure description:** The closed-loop ACS diagram is repeated with the
**Sensors** block emphasized, reinforcing that attitude-determination
hardware measures the spacecraft state and feeds the controller.

## Sensor Accuracy

The lecture compares sensor accuracy against **cost, mass, power, &
complexity**.

  -----------------------------------------------------------------------
  Relative Class          Sensors                 Approximate Accuracy /
                                                  Cost Region
  ----------------------- ----------------------- -----------------------
  **Low**                 Magnetometers; Coarse   Around 0.1-deg; \<
                          sun sensors; IR Earth   \$100k region
                          sensors                 

  **Medium**              Digital Sun Sensors;    Around 0.01-deg; \<
                          Earth sensors; Gyros;   \$1M region
                          GPS Receivers           

  **High**                Star Trackers; Fine sun Around 0.001-deg; \<
                          sensors                 \$10M region
  -----------------------------------------------------------------------

Additionally, custom sensors can be built or payload instruments can be
leveraged to perform similar functions.

**Figure description:** Three overlapping ellipses labeled Low, Medium,
and High move toward increasing accuracy and increasing
cost/mass/power/complexity. Star trackers and fine sun sensors occupy
the highest-accuracy region.

## Sun Sensors

Used for basic attitude estimation, especially with respect fault
protection.

-   For example, spacecraft with sun-pointing constraints (eg,
    telescopes) will have additional sun sensors to trigger safe
    attitude.
-   Often used in orthogonally mounted pairs (4 sensors provide
    hemispherical coverage).

### Analog 4-Detector Pyramid

-   Analog current output, digitized by s/c.
-   Performance: **1.5-deg**, mass = **0.12 kg**.

The analog output is converted in software using the cosine law.

### Fine Sun Sensor

-   Analog current output, digitized by s/c.
-   Performance: **\< 0.016-deg (1 arcmin)**.

**Figure description:** The slide shows an Adcole analog sun-sensor
pyramid, an output-current-versus-Sun-angle curve, and a micro sun
sensor in development.

## Star Trackers

Star Trackers map the positions & magnitudes of observed stars to a star
catalog to provide highly accurate attitude knowledge.

-   **Fixed Type (common):** Scans the star field electronically (or via
    spacecraft motion) using a 5-20-deg FOV. It then processes,
    calibrates, and resolves the signal to provide quaternions.
-   Catalog typically contains 100s to 1000s of stars.
-   Precision star trackers are heavy & costly.
-   Don't function well with high attitude rates (used for higher
    precision science missions).
-   Performance: **0.001-1 deg**, Mass **1-10 kg**.

**Figure description:** A star-tracker image is compared with a catalog
visualization. Arrows connect recognizable star patterns in the catalog
to corresponding stars in the camera image, illustrating how the tracker
determines attitude.

## Star Map Example

-   Stars are not distributed uniformly (tend to appear in groups).
-   Understand the application requiring the star tracker:
    -   Primarily staring or moving?
    -   Max angular rate?
    -   Fraction of sky covered?
-   How will the system react to star tracker errors?

**Figure description:** A polar star map shows highly nonuniform star
density across the sky, reinforcing why star-tracker performance depends
on where and how the spacecraft points.

## Magnetometers

Magnetometers:

-   Measure 3 perpendicular components of the planet's magnetic field.
-   Compare measurements to standard model.
    -   Tilted center dipole is the standard used.
-   Precision: typical **1.5° ± 0.5°**.
-   Commonly used with mag torquers (field model not reqd.).

**Figure description:** The slide shows a Billingsley Magnetic TFM100S
Attitude Control Magnetometer together with representative
specifications including radiation tolerance, field measurement range,
accuracy, linearity, sensitivity, zero shift with temperature, frequency
response, weight, and size.

## Gyroscopes (IRUs/IMUs)

Gyros are used to maintain continuous attitude reference between updates
from external references (eg, Sun, Earth, stars, etc.).

-   Majority of recent missions use ring-laser or fiber optic gyros,
    such as the LN-200 IMU.

### Internal Processing

-   The gyro uses internal dynamics, environmental, and error models to
    produce a best estimate for the current attitude.
-   Over time (eg, **0.1-deg/hr**), the error will increase.

LN-200 IMU example:

-   0.7 kg
-   10 W
-   9 × 9 cm

**Figure description:** The slide compares an LN-200 IMU, a traditional
mechanical gyroscope with gimbal/rotor/spin-axis labels, and a
ring-laser gyroscope.

## GPS Receiver

Using GPS for attitude knowledge has become increasingly common.

-   Spacecraft velocities to up **16,000 m/s**.
-   Performance varies with distance (**200 km to 45,000 km**).
-   LEO Performance **\< 0.1 deg**.

Example:

-   GD Sentinel M-Code GPS Receiver
-   Mass 2.5 kg

**Figure description:** The slide shows the GPS receiver hardware and a
Global Positioning System constellation diagram with seven visible
satellites.

## Summary of Sensors

-   **Sun Sensor**
    -   Simple, reliable, cheap, but also intermittent depending on sun.
-   **Earth Sensor**
    -   Less common with narrower applications.
-   **Magnetometer**
    -   Simple, reliable, cheap, but also requires low Earth orbit.
-   **Star Tracker**
    -   Higher precision, narrow angle star trackers, but heavy &
        complex.
    -   Less expensive versions, but not as precise.
-   **Gyroscope**
    -   Generally required for maintaining knowledge between attitude
        updates from external references.
-   **GPS Receiver**
    -   Cheap, simple, but requires proximity to functioning GPS.

------------------------------------------------------------------------

# 6. GN&C Actuators and Effectors

> **Source: Slides 48--60**

## Actuator / Effector Overview

### Affect System Momentum

-   Reaction Wheels --- **0.0001-0.1 deg**
-   Momentum Wheels --- **0.1-2.0 deg**
-   Control Moment Gyros (CMGs) --- **0.001-0.1 deg**

### Do Not Affect System Momentum

-   Magnetic Torquers / Torque Rods --- **1.0-10.0 deg**
-   Reaction Control Thrusters --- **0.1-5.0 deg**

The values above are presented on the slide as **Typical Accuracy**.

## Reaction Wheels

-   Electric motor spins a wheel. The rotation is aligned with the
    control axes (one wheel per axis).
    -   Typical arrangement is 4 wheels in a tetrahedron for redundancy.
        -   Three are required (1 for each axis), so the fourth one is
            redundant.
-   Characteristics (**0.0001-0.1-deg**):
    -   Low torque, high accuracy (very fast response possible, tens of
        Hertz).
    -   Not limited by propellant, but limited by angular momentum
        capacity.
    -   Nominally operate at low speeds.
    -   Saturation level is defined by peak motor speed.
        -   Once wheels reach peak speed, required momentum dumping (eg,
            thruster firing) to unload.
        -   That is, reduce the speed without impacting the attitude.

**Figure description:** The slide shows representative reaction-wheel
hardware and a tetrahedral four-wheel arrangement. The geometry
illustrates how four wheels provide three-axis control with one
redundant wheel.

## Reaction Wheel Sizing and Trade Studies

### What determines the sizing of momentum wheels?

-   Reaction wheels provide torque (**0.01 to 1 Nm**).
-   Size of reaction wheel depends on the size of the torque that is
    needed.
-   For the quiz example, relevant torques were:
    -   Magnetic torque (Tm), **2.1 × 10⁻⁵ Nm**
    -   Slew torque (T) = **2.9 × 10⁻⁴ Nm**
    -   Momentum dumps due to gravity gradient (h) = **0.039 Nms**
-   Torque from RWs needs to be \> than torque from disturbance to
    maintain attitude.
-   For accumulated changes (such as momentum dumps):
    -   Slew rate (s) × torque (Nms) = momentum (Nms)

### How long is the trade study process?

-   Varies significantly...
-   "Team X" design is typically done via rules of thumb & general
    principles (**\< 2-3 hrs**).
-   Detailed GN&C analysis for a more complex mission can take
    **months**, including multiple simulations and reviews to finalize
    architecture.

## Momentum Wheels

-   Wheel operating at non-zero momentum to provide gyroscopic stiffness
    to the spacecraft.
-   Characteristics:
    -   Performance: **0.1-2.0 deg**
    -   Effectively these are heavier reaction wheels that operate at a
        constant speed.
    -   Often used to cancel the momentum of rotating payload.

**Figure description:** A cutaway momentum wheel identifies the bottom
cover, flywheel, motor, control electronics, and bearing unit.

## Control Moment Gyros (CMGs)

-   CMG is a gimbaled momentum wheel.
    -   A torque is applied via the gimbal to produce a change in
        angular momentum, and thus a reaction torque on the body.
-   Characteristics:
    -   Performance: **0.001-0.1 deg**
    -   Momentum wheel operating at nearly steady (high) speed.
    -   Higher control authority than momentum wheels (**up to 100x
        times**).
    -   Relatively noisy (they induce vibrations due to the spin rate).

**Figure description:** The slide shows a set of large spacecraft CMGs
and a schematic of a gimbaled spinning wheel, with body, gimbal, spin,
and angular-momentum axes labeled.

## International Space Station CMGs

### Do they carry a surplus of gyros on the ISS?

-   No, not worth flying additional spare units beyond the 1 (of 4)
    installed that is redundant.
-   History:
    -   CMG-1 failed in 2002 and replaced in 2005 (first post-Columbia
        shuttle flight).
    -   CMG-2 had two circuit breaker failures.
    -   CMG-3 failed in 2006 and replaced in 2007.

**Figure description:** Three images show one CMG during Integration &
Test, four CMGs installed in the ISS Z-1 Truss, and a CMG being replaced
during a 7-hour spacewalk in 2005. A second slide locates the Z1 Truss
on the full ISS assembly.

## Attitude Control Redundancy

If part of your system controlling attitude is damaged, how can you
compensate for that without losing the S/C entirely?

-   Most spacecraft include significant redundancy for attitude control.

### Typical Redundancy

**Reaction Wheels or CMGs**

-   Provide highest performance (w/low propellant use).
-   Typically, three wheels are required to maintain 3-axis attitude
    control.
-   A fourth one is included, such that any three can provide full
    3-axis control.
-   ISS requires a minimum of 2 CMGs (uses gravity gradient as well).

**Thrusters**

-   Larger, higher-value (ie, Class A/B) missions will have redundant
    coupled thrusters that can provide reasonable attitude control.
-   This is called **functional redundancy**. Thrusters will generally
    not perform as well and/or use-up greater propellant, so there will
    typically be some impact to the mission that is assessed.

**Or simply, by any available means...**

-   Dawn used its electric propulsion system to provide attitude control
    (after 3 RW failures).
-   ISS incorporates the gravity gradient to minimize attitude control
    requirements.
-   For attitude knowledge error, onboard instruments can be pressed
    into service...
-   Etc.

## Electric Propulsion

Would some kind of electric propulsion thruster have enough thrust to be
an effective control system?

-   Yes. On Dawn, the 3 electric propulsion thrusters can provide **90
    mN of thrust**.
-   In Geostationary orbits, electric propulsion systems regularly
    provide attitude control given their extremely high efficiency (**\>
    3,000 Isp**) versus the very low disturbances.
-   For a small spacecraft:
    -   drag = none
    -   Gravity gradient = **5 × 10⁻⁹ Nm**
    -   Solar radiation pressure = **6 × 10⁻⁶ Nm**

**Figure description:** Dawn is shown firing an ion thruster. A system
block diagram shows the spacecraft power/control architecture feeding
three electric-propulsion thrusters.

## Magnetic Torque Rods

-   Electromagnets that are energized to provide a electromagnetic
    torque on the spacecraft via the local magnetic field.
-   Characteristics:
    -   Performance: **1.0-10.0 deg**
    -   Clean way to dump momentum (with no consumables)
    -   Generally consist of simple iron rods (or loops)
    -   Very reliable and cheap
    -   Primarily applicable to planetary/Earth orbiters with large
        magnetic fields.

**Figure description:** A long cylindrical magnetic torque rod is shown
with its mounting brackets.

## Thrusters

Often called a **Reaction Control System (RCS)** when used only for
attitude control.

-   From propulsion, these are typically the smallest thrusters.
-   Often, they functionally back-up reaction wheels in case of a
    failure, but they do not provide the same precision.

### Characteristics

-   Performance: **0.1-5.0 deg**
-   Various sizes available, with different levels of performance (ie,
    control)
-   Propellant-limited and may introduce contamination
-   Capable of very high torque
-   Accuracy limited by thruster configuration (impulse bit)

### Primary Thruster Characteristics

-   Thrust-level (eg, 1-N vs. 490-N), which determines the ability to
    provide thrust and thus ΔV.
-   Efficiency (ie, Isp), which is based on both type of thruster &
    propellant.
-   Minimum impulse bit (MIB) is the smallest control torque that can be
    applied to the spacecraft.

### Primary Uses

-   Trajectory Correct Maneuvers (TCMs) for changing ΔV
-   Orbital Maintenance
-   Momentum dumps
-   Attitude (or reaction) control
-   Thrust vector control (TVC) that provide guidance on larger
    maneuvers

### Matching Thrusters to Spacecraft

-   Consider necessary functions: large ΔV maneuvers, attitude control,
    etc.
-   Thrusters should be evaluated for min/max burn times.
    -   Minimum burn time should be consistent with the minimum impulse
        bit.
    -   Maximum burn time should be consistent with the type of maneuver
        (eg, orbit insertion, burn time \< 2-3 hrs).
-   Result is often something like:
    -   RCS thrusters for attitude control, momentum dumps, etc.
    -   Main engine(s) for large & more efficient ΔV maneuvers.
    -   Other mid-size thrusters where the above thrusters aren't
        sufficient (eg, thrust vector control on a large ΔV burn).
-   Reminder that thrust-level can be scaled with the number of
    thrusters.

## Attitude Control on Spin-Stabilized Spacecraft

### Spin Rate

-   Two pairs of coupled thrusters act on opposite sides to change spin
    rate.

### Velocity

-   After the spin axis is changed to the desired orientation, the
    thrusters on the HGA side fire simultaneously for translational
    maneuver.

### Attitude

-   Pair of coupled thrusters rotate the spin-axis.
-   Thrusters are fired in brief pulses at a precise position in the
    spacecraft rotation.
-   Each pulse moves the axis a few tenths of a degree until the desired
    attitude is reached.

**Figure description:** The Pioneer 10 graphic shows thruster placement
on a spin-stabilized spacecraft and illustrates how paired pulses change
spin rate, translate the spacecraft, or reorient the spin axis.

------------------------------------------------------------------------

# 7. ACS Design, Redundancy, and Architectures

> **Source: Slides 61--70**

## ACS Design Steps

### Review & Understand Design Information

-   Mission Description and/or Concept of Operations
-   System and Subsystem Requirements
    -   ConOps & mission geometry
    -   Payload pointing requirements
    -   Expected disturbances

### Create a Preliminary Design

-   Identify the most likely architecture (eg, 3-axis)
-   Identify likely components (eg, sun sensors, star trackers, etc.)
-   Size control effectors (eg, reaction wheels, CMGs, thrusters, etc.)
    -   Consider functional redundancy, system cost, etc.
-   Create end-to-end kinematic simulation, error budgets, etc.
-   Understand fault scenarios
-   There is often a trade between thrusters & reaction wheels
-   Create component mass list

### Review & Iterate (w/broader team)

-   Revisit other options & trades

The slide points students to **HW7 for additional detail**.

## Additional Guidance

### Three Primary Functions

-   Control, knowledge, & stability...

### Common Sensors Across \~All Missions

-   Sun sensors
-   Gyros / IMUs

### Destination Dependencies

-   Low-Earth Orbit (LEO): Horizon sensors, GPS receivers, magnetic
    torquers
-   Sun \< 2-3 AU: Electric propulsion for attitude control
-   Deep Space: Star trackers
-   Close Proximity Ops: Radars, LIDARs, etc.

### Functional Dependencies

-   Imaging s/c typically require reaction wheels, although cold gas
    systems are increasingly capable.
-   Thrusters-only vs. reaction wheels is a common trade between cost &
    performance.
-   Larger, more agile s/c typically need CMGs.
-   Layers of redundancy increase with mission duration & budget.

While the sizing of individual components is based on specific
requirements, one can generally estimate a likely architecture based on
a mission description and relative budget.

## Interpreting a Block Diagram

The lecture asks:

-   What function do each of the GN&C components provide?
-   What types of missions do they support?
-   If component X fails, how does the failure propagate?
    -   Assuming realtime telemetry at 1 Hz, what is the ground likely
        to see?
    -   Is there a possibility of recovering the mission?

## MRO GN&C Architecture

**Figure description:** The MRO physical architecture connects redundant
C&DH processors and interface cards to GN&C sensors and actuators.
Sensors include two IMUs, two star trackers, two 4-detector sun sensors,
and four 2-detector sun sensors. Actuators include four reaction wheels,
reaction-wheel electronics, S/A and HGA gimbal-drive electronics, and
thrusters. The diagram also identifies 8 × 0.9-N ACS thrusters, 6 × 22-N
TCM thrusters, and 6 × 170-N MOI thrusters, together with analog,
RS-422, 1553, tach, valve-command, and multifunction-bus interfaces.

## Phoenix GN&C Architecture

**Figure description:** The Phoenix architecture connects redundant RAD
6000 C&DH processors and I/O/interface cards to two IMUs, two Sun Sensor
Assemblies, two cruise-stage star trackers, the cruise-stage landing
radar, and thrusters. The thruster set is labeled 4 × 5-lb (DV, P/Y), 4
× 1-lb (R/P/Y), and 12 × 68-lb (DV, R/P/Y). The legend distinguishes
Mars '01 modified hardware, Mars '01 heritage, other heritage, and new
development.

## MSL GN&C Architecture

**Figure description:** The MSL architecture is distributed across the
cruise stage, descent stage, and rover. It includes redundant Rover
Compute Elements, power/avionics modules, RIMU, NavCams, HazCams, star
scanner electronics/optics, Sun Sensor heads/electronics, descent IMU,
radar electronics/antennas/transceivers, cruise RCS, entry RCS, Mars
landing engines, motor controllers, and separate rover/EDL 1553 buses.
The diagram identifies inherited, build-to-print, and new-development
hardware.

## MSL GN&C Architecture --- Control System

**Figure description:** The logical control-system view separates
**vehicle hardware & planetary environment**, **GNC algorithms and
functions**, and **GNC models**. Functions include HGA pointing,
instrument pointing, hazard avoidance, attitude determination, position
determination, rover 3DOF control, celestial-body position propagation,
visual odometry, hazard detection, and odometry. Inputs include the
RIMU, Nav Camera, Haz Camera, rover hardware, Mars rotation, Sun/Earth
positions, and terrain; outputs drive wheel/steer actuators and pointing
gimbals.

## Questions from Prior Class

### Most Common Actuators

-   Magnetic torquers for LEO satellites (cheap, simple)
-   Thrusters (low precision) and reaction wheels (high precision)

### GN&C Actuator Failures

Major driver of spacecraft failures & reliability, including both infant
mortality & lifetime failures.

Examples:

-   **Phasing of sensors**
    -   Genesis --- backwards G-switch (phasing tests are a critical
        part of testing)
-   **Loss of lubrication or unexpected friction**
    -   Dawn --- reaction wheels; several failed prematurely, but Dawn
        was able to use electric prop.
    -   ISS --- failed gyros (reoccurring failures)
    -   SOHO --- failed gyro, coupled with inadequate fault response
        nearly failed the mission

### At What Altitude Does Drag Start to Disappear?

-   Varies with drag coefficient & solar minimum/maximum.
-   At **\> 600 km**, gravity gradient dominates over drag.
-   At **\> 2,000 km**, disappears entirely.

### Launch Attitude Control

-   Primarily the main engine gimbals.

### Small, Cheap Ground-Based Star Sensor?

-   Yes, and there are similar iPhone applications.
-   Drivers are likely ensuring adequate camera sensitivity and then
    going through the math, but similar image processing is
    well-published in literature.

### Reaction Wheels vs. Cold-Gas RCS

-   Greater control via reaction wheels.
-   Cold gas thrusters are improving, but difficult to compete against
    **0.0001-deg RWs**.

### New GN&C Technology

-   On MSL, the landing radar was developed for the mission (overcame
    issues with Phoenix radar reliability).
-   There is continued work to reduce the size of sensors & actuators.

### Who Owns Attitude-Control Thrusters?

-   Depends on the overall design.
-   For a small RCS system with no other propulsion, then it's all under
    ACS and no propulsion subsystem required.
-   Otherwise, it would typically be covered under propulsion.

### GPS at Mars

-   A GPS system functions by receiving 3+ GPS signals and then
    triangulating position.
-   Cost of deploying a constellation at Mars is prohibitive.
-   If this can be solved, the next issue would be power --- GPS signals
    on Earth required \~500 W. On Mars, this translates to approximately
    **10 m² just for the GPS power output**.

### Sudden vs. Gradual Attitude-Estimate Updates

-   Not many missions require sudden, large updates, but some would be
    landers for terrain avoidance.

### How Many Stars Have Been Cataloged?

-   Over a billion stars have been cataloged.
-   Typically, star tracker catalogs contain thousands (eg, 10,000).

### Deep Impact Sample Return?

-   Only data.
-   Instruments, including a spectrometer that can analyze the
    composition of the plume, transmitted data back to Earth.
-   The probe relayed its data via the observing spacecraft.

### Staying in Contact with Older Spacecraft

-   It's case-by-case.
-   All missions have a specific, funded lifetime.
-   As the mission approaches its end-of-life, the team will typically
    propose a mission extension.
-   This extension needs to include all applicable costs to maintain and
    communicate with the spacecraft.
-   It is then evaluated for cost & benefit.
-   In the case Voyager, the DSN 70-meter stations continue to be
    maintained to support communication, along with supporting
    personnel, spacecraft knowledge, etc.

------------------------------------------------------------------------

# 8. Spacecraft Dynamics

> **Source: Slides 71--88**

## Introduction

### Kinematics

Describes the motion of points, bodies (objects), and systems of bodies
(groups of objects) **without considering the forces that cause them to
move**.

### Translational Motion

-   Changes in the position and velocity of an object.
-   For spacecraft design, this primarily corresponds with understanding
    position relative a gravity field and changes in ΔV (vs. thrust).

### Rotational Motion

-   Changes in the attitude of an object.
-   For spacecraft design, this corresponds to attitude determination
    and control.

### Importance

Understanding and/or modeling the spacecraft attitude provides insight
into:

-   Precision of sensors & actuators required
-   Performance capability to meet payload, ascent/descent,
    communication, and/or other requirements
-   Amount of propellant required
-   Detailed Concept of Operations, including required spacecraft
    behavior and responses
-   Margin/risk assessment

**Figure description:** The slide includes a comparison table between
translational and rotational motion, pairing quantities such as
inertia/mass, displacement/angular displacement, velocity/angular
velocity, acceleration/angular acceleration, momentum/angular momentum,
force/torque, and corresponding laws of motion.

## Kinematics of Rotation

When a rigid body rotates about a fixed axis, all radial lines rotate
through the same angle and have the same angular velocity **ω**.

The magnitude of the velocity of a point depends on its distance from
the rotation axis:

``` math
v_i = |\boldsymbol{\omega}\times\mathbf{r}_i|
```

The perpendicular distance to the axis is:

``` math
R_i=\sqrt{x_i^2+y_i^2}
```

and therefore:

``` math
v_i=\omega R_i
```

### Comments

-   Since the angular velocity varies with the radius, it is more
    difficult to calculate basic physical relationships, and thus the
    next several charts are intended to provide additional background.
-   The lecture reuses charts from Joel Sercel's class.

**Figure description:** A point on a rigid body is shown rotating around
a fixed z-axis, with the position vector and perpendicular radius used
to relate angular velocity to linear velocity.

## Rotational Kinetic Energy

For a rotating rigid body:

``` math
K=\frac{1}{2}I_z\omega^2
```

where:

-   **Iz** is a constant (ie, rotational inertia) that governs how a
    body behaves when a force (ie, torque) is applied.
-   This is similar to mass in translational physics.
-   **Iz** is the moment of inertia about the z-axis.

The moment of inertia for discrete particles is:

``` math
I_z=\sum_{i=1}^{n}m_i(x_i^2+y_i^2)
```

**Figure description:** The slide compares translational kinetic energy,
( `\frac{1}{2}`{=tex}mv\^2 ), with rotational kinetic energy, (
`\frac{1}{2}`{=tex}I`\omega`{=tex}\^2 ).

## Moment of Inertia and Angular Acceleration

Applying Newton's second law in the tangential direction leads to:

``` math
\tau_z=I_z\alpha
```

Notes:

-   The torque **τz** and moment of inertia **Iz** must be with respect
    to the same fixed axis.
-   This also applies to a rigid body.
-   The torque must be from external forces.

Comments:

-   Moment of Inertia can now be related to Newton's 2nd Law (**F =
    ma**), resulting in a loose equivalent wrt torques.
-   **α** = angular acceleration (eg, radians/s²).

**Figure description:** A force acting at a distance from a pivot
produces torque; the diagram labels torque, distance, and force.

## Calculating Moment of Inertia

For a system of discrete particles:

``` math
I_z=\sum_{i=1}^{n}m_i(x_i^2+y_i^2)
```

For a continuous rigid body about the z-axis:

``` math
I_z=\int(x^2+y^2)\,dm
```

or:

``` math
I_z=\int(x^2+y^2)\rho(\mathbf r)\,dV
```

If uniform:

``` math
\rho=\frac{m}{V}=\text{constant}
```

Comments:

-   Note that **ρ is density here**.
-   Effectively, you are integrating x,y over the volume at a given
    density to calculate the moment of inertia about the z-axis.
-   SI units are **kg·m²**.

## Moment of Inertia of a Ring

For a uniform thin ring of radius **R** and mass **m**:

``` math
I=mR^2
```

For a uniform disk about its center:

``` math
I=\frac{1}{2}mR^2
```

**Figure description:** The slide derives the moment of inertia by
integrating mass elements around a thin ring and then across the radius
of a disk.

## Additional Moment-of-Inertia Examples

-   Many published formulas exist for basic shapes.
-   This is highly relevant because you can determine the moments of
    inertia of complex shapes by summing the individual components.
-   We can do this via:
    -   Parallel Axis theorem
    -   Perpendicular Axis theorem
-   Early in formulation, the ACS engineer will estimate the s/c moment
    of inertia based on a general approximate of a few shapes & masses.

**Figure description:** A reference table shows moments of inertia for
several common shapes and axes, including rods, rings/disks, and
cylinders.

## Parallel Axis Theorem

If **ICM** is the moment of inertia of an object about an axis passing
at CM, its moment of inertia about another parallel axis is:

``` math
I=I_{CM}+Mh^2
```

where:

-   **M** = mass
-   **h** = distance between the two parallel axes

This formula is critical to combining moments of inertia in order to
estimate more complex shapes.

## Moment of Inertia of a Disk About Its Edge

For a uniform disk:

``` math
I_{CM}=\frac{1}{2}mR^2
```

Using the parallel-axis theorem:

``` math
I=I_{CM}+mR^2
```

so:

``` math
I=\frac{3}{2}mR^2
```

The slide notes that this formula also applies for a uniform rod.

## Perpendicular Axis Theorem

For a thin flat plate in the x-y plane:

``` math
I_z=I_x+I_y
```

This is helpful for "thin" objects that are dominated by inertias about
x & y.

## Moment of Inertia as a Tensor

Mass is a scalar, but moment of inertia requires multiple components.

The inertia tensor relates angular momentum and angular velocity:

``` math
\mathbf h=\mathbf I\boldsymbol{\omega}
```

Comments:

-   This is the equivalent of momentum = mass × velocity, but wrt
    rotation.
-   Whereas in translational physics, we can just use "mass", here we
    need to use a 2nd order tensor to fully define the inertia.
-   We need each inertial component about the axis and their products
    for asymmetric shapes.

## Angular Momentum

For a rigid body:

``` math
\mathbf h=\mathbf I\boldsymbol{\omega}
```

Comments:

-   This is the equivalent of our translational **h = mv**.
-   Previously, total impulse (**Ft**) was used to solve for thrust.
-   Similarly, angular momentum allows us to solve for the torques
    required to change rotational velocity.
-   Momentum is often defined as **h** or **L**.

**Figure description:** A conservation-of-angular-momentum illustration
shows that changes in rotational inertia produce corresponding changes
in angular velocity while angular momentum is conserved.

## Moments and Products of Inertia

-   Moments of inertia (**x, y, z**) are always positive.
-   Products of inertia (**xy, yz, etc.**) are measures of symmetry.
-   If an object is symmetrical across a plane (eg, XY plane), then the
    products associated with any axis perpendicular are zero (**Ixz, Iyz
    = 0**).

## Torque

Newton's law for rotational motion is:

``` math
\mathbf T=\frac{d\mathbf h}{dt}
```

Comments:

-   Note the restrictions above (rigid body, etc.).
-   If the goal is to maintain constant angular momentum, disturbances
    must be offset with counter torques.

## Euler's Moment Equations

The components of the rotational equation of motion are:

``` math
\tau_1=\dot h_1+\omega_2h_3-\omega_3h_2
```

``` math
\tau_2=\dot h_2+\omega_3h_1-\omega_1h_3
```

``` math
\tau_3=\dot h_3+\omega_1h_2-\omega_2h_1
```

These equations dictate the rotational movement of a rigid body with
respect to each axis.

Using principal axes:

``` math
\dot h_1=I_1\dot\omega_1=T_1+(I_2-I_3)\omega_2\omega_3
```

``` math
\dot h_2=I_2\dot\omega_2=T_2+(I_3-I_1)\omega_3\omega_1
```

``` math
\dot h_3=I_3\dot\omega_3=T_3+(I_1-I_2)\omega_1\omega_2
```

These equations relate the change in momentum to the torques acting on a
spacecraft and can be used to create an attitude-control simulation.

The lecture notes that this will be part of **HW3c**.

## Euler's Angles

Euler angle rotation is a successive angular rotation about the three
orthogonal axes of the body frame.

Euler's angles are a commonly used set of angles to define the
orientation of a body with respect to a reference frame.

**The order of the rotations matters.**

-   12 possible choices.
-   The sequence shown in the lecture is commonly used for orbits around
    a planet.
-   For some choices, the Euler rotation matrix might be singular
    (locking).

The lecture notes that this leads back to **roll, pitch, and yaw** and
introduces rotation matrices.

------------------------------------------------------------------------

# 9. Phoenix Radar Case Study

> **Source: Slides 89--97**

## Phoenix Entry, Descent, and Landing Sequence

The Phoenix case-study sequence is organized into:

### Hypersonic

-   Entry
-   Hypersonic 2
-   Peak Heating
-   Peak Deceleration
-   Hypersonic 5
-   Pre-chute

### Parachute

-   Parachute Deploy
-   Heatshield Separation
-   Leg Deploy
-   MRD Initialization
-   Radar Ground Lock-up
-   Attitude Convergence
-   Velocity Convergence

### Terminal Descent

-   Lander Separation
-   Tip-up
-   Gravity Turn Start
-   Constant Velocity
-   Radar Stop (30m)
-   Touchdown

**Figure description:** Slides 89--92 progressively walk through the
Phoenix EDL sequence. The diagrams highlight parachute deployment,
heatshield separation, and radar ground lock-up while showing the
lander's path from atmospheric entry to powered touchdown.

## How Do You Create Simulations?

### Phoenix EDL Major Sim Components

-   Simulation integrator
-   Atmospheric model
-   Hypersonic aerodynamics model
-   Gravity model
-   Dispersed hypersonic aerodynamics model
-   Parachute drag model
-   Parachute inflation model
-   Wrist mode model (x2 types)
-   Configuration aerodynamics models (x 3 configs)
-   Winds model (x2 types)
-   RCS propulsion model
-   IMU model
-   Radar model (low fidelity)
-   Descent engine propulsion model
-   Phoenix flight software
-   ADAMS model (mechanical simulation)

### Resulting Higher-Level Models

-   6-DOF Langley simulation
-   6-DOF Lockheed Martin sim
-   6-DOF Mechanical simulation
-   Flowtran Lander simulation
-   Flight software simulation

### Validated by Tests & Peer Reviews

-   Extensive literature & past missions (eg, Mars atmosphere, winds,
    terrain, etc.)
-   Wind tunnel testing (eg, parachute)
-   Radar field testing (added for PHX)
-   Thrusters (live-fire vacuum testing)

**Figure description:** The slide places the simulation-component list
beside the higher-level model and validation lists, with a photograph of
a Phoenix-like lander undergoing powered testing.

## Radar Assumptions

Originally, the Mars '01 (not flown) and Phoenix project had a
simplified model for the radar which made the following assumptions:

-   Infinite, sloped, flat plain
-   Noise/bias characteristics that matched the requirements
-   Very sharp, single-peak FFT velocity measurement outputs
-   Assumed perfect angle-of-arrival (radar beam canted to be an offset
    from this)
-   The radar will only have one target (ground only)

Those assumptions proved to be inadequate via field test data and
development of a higher-fidelity simulation in the following ways:

-   Terrain relief and brightness variation causes the look-vector to
    migrate.
-   Noise/bias characteristics change with varying terrain and target
    brightness.
-   FFT signatures are broader and show multiple peaks from nadir
    contamination, and wider FFT spectra peaks.
-   The angle of arrival is actually biased towards nadir from the
    original assumed angle.
-   The radar is guaranteed to see two targets (**ground +
    heatshield**).

## The Model Also Missed...

### Several Key Items

-   Multiple targets can confuse the search logic in the radar firmware
    to cause locks on false targets and ambiguities.
-   Never-before-discovered bugs in the radar firmware which can cause
    the radar to have prolonged lockup times under certain thermal &
    timing conditions.
-   Bi-modal lock-up behavior under certain conditions.

### Result

-   Significant time required just prior to launch and during cruise to
    build, test, and incorporate a high-fidelity radar model into the
    Phoenix EDL simulation.
-   This fixed several anomalies that had the potential to fail the
    mission. But, it also uncovered new anomalies....

## Updated Simulation

The updated Phoenix simulation replaces the low-fidelity radar model
with a **low & added high fidelity** radar model.

The resulting higher-level models remain:

-   6-DOF Langley simulation
-   6-DOF Lockheed Martin sim
-   6-DOF Mechanical simulation
-   Flowtran Lander simulation
-   Flight software simulation

Validation includes:

-   Extensive literature & past missions
-   Wind tunnel testing
-   Radar field testing
-   Thrusters (live-fire vacuum testing)

## Radar Data from Simulation

**Figure description:** Four simulation plots show radar-related failure
signatures: **Nav State Jump at Low Altitude due to Radar Error**,
**Late- or Non-Radar-Lockup (wrist-mode-related)**, **Barker Code Side
Lobe (most likely sim artifact)**, and **Radar Slant-Range Lockup
(non-sep-related)**. The plots annotate low-probability events that
could lead to out-of-specification landing behavior and were used to
quantify residual radar risk.

------------------------------------------------------------------------

# 10. Deep Impact Star Tracker Anomaly

> **Source: Slides 98--106**

## Deep Impact

Deep Impact was a NASA spacecraft designed to study the interior
composition of a comet by releasing an impactor into the comet.

-   Launched in 2005.
-   Resulted in a successful comet impact.
-   However, it almost never made it...

**Figure description:** The slide shows the observing spacecraft and
impactor, an impact timeline from impactor release through closest
approach, and imagery of the comet impact.

## Deep Impact Attitude Estimation

### Attitude Estimation

-   Combines weighted measurement from multiple sensors into a single
    attitude estimate.
-   Typically uses include gyro(s) for rate data and star tracker(s) for
    celestial attitude data.
-   Able to propagate for limited times in the absence of star tracker
    data (given an initial reference).
-   Weights chosen to match strengths of sensor.
    -   Low weights indicate that the sensor cannot abruptly change the
        estimate as fast as other sensors.
    -   Conversely, high weights allow a sensor to make sudden, large
        updates.

### Star Tracker --- Primary & Redundant

-   Matches star images to a catalog to produce a full 3-axis attitude
    with respect to a standard CS reference (eg, J2000).
-   Can quickly determine attitude without any initial knowledge.
-   Can't sustain lock under fast rotations.
-   Requires clear view of the sky (can be dazzled by bright objects
    nearby or in FOV).
-   Needs adequate star density.

### Gyros

-   Provide angular rates, which can be integrated over time to obtain
    angular position relative to a given reference.
-   Generally operate in "relative mode," relative to an assumed
    reference and propagating changes in attitude without having
    absolute knowledge.
-   Able function under relatively "fast" rotations whereas other
    sensors may not.
-   Low signal-to-noise ratio (ie, less accurate).
-   Generally, there is bias "or drift" rate over long periods of
    integration without an absolute reference.

## Background

After launch, Deep Impact enters a planned **safe-mode**.

-   In safe mode, it uses gyros and sun sensors, holding +Y axis on the
    sun and rotating once every 4 hours ("sunline" ACS state).
-   Star trackers are mounted on the backside, facing somewhat anti-sun.
    They are not used at the beginning of the mission.

Attitude Estimator (ATE) is integrating gyro data from a **"wake-up"
frame**. This frame is defined as the s/c frame at the instant that the
s/c is commanded to sunline mode.

After post-launch orbit check-out and initial spacecraft health
assessment, the star trackers are turned on by ground command.

Nominally, ATE will accept data from the star trackers and will slowly
correct its estimate to reflect the data coming from the STs.

-   The ATE mixes in gyro data with ST data with much greater weight
    placed on the gyro data.
-   Over time, the STs will "win," but in the short time the current ATE
    estimate wins.
-   This is considered a **"slow drip" correction**.

The nominal plan is that after the ATE has converged, the ground will
command the spacecraft to go from safe-mode to 3-axis control.

**Figure description:** The slide shows the locations of the star
trackers on the spacecraft and explains why they are initially not used
in sunline safe mode.

## Attitude Estimation Anomaly

Twice every 4 hours, the ATE estimate jumps up & down discontinuously.

-   The jumps are **11-12 min apart**.
-   Note that 1 full rotation = **4 hours**.

**Figure description:** A time-history plot shows the attitude-estimate
jumps recurring during the four-hour spacecraft rotation.

## Star Tracker Lock State

Coincident with the jumps are star tracker outages.

-   Interval between jumps corresponds to **19-deg** (relative alignment
    of star trackers), suggesting a systemic issue.
-   Star tracker data alone suggests the sun is significantly
    (**\~90-deg**) off from expectations.
-   Given sun sensor & solar array data, this suggests possible ST
    alignment issue.
-   Data suggests this issue is occurring when star trackers are pointed
    towards celestial true north.

### Possible Issues

-   Star tracker alignment
-   ACS/ATE software
-   Earth in FOV
-   "Dark spot" in sky

## Documentation Discovery

Going through documentation, an error in the coordinate-frame
transformation was discovered.

-   A **90-deg rotation** to translate from mechanical frame to
    spacecraft frame was dropped.
-   All three star trackers (including impactor) had incorrect
    alignments.

## Virtual Star Tracker

"Twisted" refers to the **90-deg coordinate frame error**.

When both star trackers are on and in-lock, the attitude algorithm only
uses the **boresight vectors** of the actual trackers, which are
correct.

However, when only **1 star tracker is in-lock**, the whole quaternion
from the star tracker is used for the attitude, which includes the
**90-deg error**.

**Figure description:** The diagram compares actual star-tracker
pointing with the virtual-star-tracker representation and shows how the
coordinate-frame twist affects the attitude solution when only one
tracker is available.

## Another Discovery --- Star Catalog

-   Star Catalogs contain large numbers of stars, indexed, and sorted by
    declination.
-   While these star trackers had significant heritage, additional stars
    were added to the catalog to ensure a high density given the mission
    in deep space.
-   However, when these stars were added, there was a corresponding
    parameter that set the length of the list --- and it wasn't
    increased.
-   Therefore, the list was cut-off at declinations of **greater than
    80-deg**.
-   Thus, the failure to lock attitude near the celestial North Pole.

**Figure description:** A star-catalog representation shows the catalog
organization and helps illustrate why truncating the list by declination
removed stars near the celestial North Pole.

## Lessons Learned

### Keep It Simple

-   "Virtual Star Tracker" seemed like a good idea, but it obscured the
    problem...
-   Fortunately, safe mode wasn't relying on ATE for attitude estimate.
-   This allowed the anomaly to be de-bugged while in sunline mode (via
    coarse sun sensors).

### Phasing Tests Are Critical

-   A star tracker phasing test "should" have identified the
    mis-alignment.
-   Unclear whether it occurred or properly verified.

### Explain All the Observables

-   Multiple errors occasionally occur and require significant
    exploration even after some/most of the issues have been explained.
-   This is the benefit of using a fishbone diagram and driving to
    closure.

### Beware of Heritage

-   Initially, the team was very skeptical that there was a star tracker
    issue given the significant heritage.
-   Finally, after significant convincing, the team investigated and
    discovered the incorrect parameter.

> **Note from the slide:** The alignment error was found on all three
> star trackers, including the one on the impactor. If it had been
> limited to the impactor, the issue may not have been caught until
> there was insufficient time to fix prior to the comet flyby.

------------------------------------------------------------------------

# Lecture Summary

> **Source: Slides 1--106**

The Attitude Control System provides spacecraft **attitude control,
knowledge, and stability** by combining attitude-determination sensors,
control effectors, onboard logic, spacecraft dynamics, and
mission-specific pointing requirements.

Key takeaways:

-   **ACS Fundamentals:** Commanded attitude is compared with measured
    attitude to determine attitude error and command the appropriate
    control response.
-   **Disturbances:** Aerodynamic, gravity-gradient, magnetic,
    solar-radiation, mass-expulsion, and internal torques drive
    control-authority and momentum-management requirements.
-   **Mission Geometry:** Payload observations, communications,
    solar-array pointing, thermal constraints, trajectory maneuvers, and
    agility all place constraints on spacecraft attitude.
-   **Sensors:** Sun sensors, magnetometers, star trackers, gyros/IMUs,
    GPS receivers, and mission-specific sensors provide different
    combinations of accuracy, cost, mass, power, and operating
    constraints.
-   **Actuators:** Reaction wheels, momentum wheels, CMGs, magnetic
    torque rods, and thrusters provide different levels of precision,
    torque authority, momentum capacity, and redundancy.
-   **Design:** ACS architecture is developed from mission geometry,
    pointing requirements, expected disturbances, component sizing,
    redundancy, simulations, error budgets, and fault scenarios.
-   **Dynamics:** Moment of inertia, angular momentum, torque, Euler's
    equations, and rotation representations provide the physical basis
    for modeling spacecraft attitude.
-   **Phoenix:** The radar case study shows why simplified models must
    be challenged with field testing and higher-fidelity simulation.
-   **Deep Impact:** The star-tracker anomaly shows the importance of
    coordinate-frame verification, phasing tests, independent safe
    modes, complete anomaly investigation, and skepticism toward
    unverified heritage assumptions.

Overall, ACS design connects **mission pointing requirements and the
disturbance environment to the sensors, actuators, control logic,
dynamics, redundancy, and verification needed to maintain spacecraft
attitude throughout the mission**.

