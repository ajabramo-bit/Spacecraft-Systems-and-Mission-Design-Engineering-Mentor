# Attitude Control System (ACS)

**Course:** ASTE-331 — Spacecraft Systems Engineering  
**Lecture:** 03 — Attitude Control System (ACS)  
**Instructors:** Jim Chase, Danielle Marsh    
**Source:** `331_03_ACS_20250926.pdf`

------------------------------------------------------------------------

## Lecture Overview

This lecture introduces spacecraft Attitude Determination and Control,
commonly called the Attitude Control System (ACS), ADCS, AOCS, GN&C, and
related names.

The lecture develops ACS from the full spacecraft-system perspective. It
begins with the purpose of attitude determination and control,
spacecraft pointing terminology, and the closed-loop relationship
between commands, controllers, actuators, the spacecraft, sensors, and
external disturbances. The OSIRIS-REx mission is used as an early
example of a spacecraft whose science, navigation, propulsion, and
sample-collection operations depend heavily on GN&C.

The design portion examines the major environmental and internal
disturbances that create spacecraft torque, including aerodynamic drag,
gravity gradient, magnetic torque, solar-radiation pressure, mass
expulsion, and internal moving hardware. It then connects these
disturbances to mission geometry and pointing constraints from payloads,
telecommunications, solar arrays, thermal control, trajectory maneuvers,
and spacecraft agility.

The lecture surveys the major attitude-determination sensors—sun
sensors, Earth sensors, magnetometers, star trackers, gyroscopes/IMUs,
and GPS receivers—and the major actuators/effectors—reaction wheels,
momentum wheels, control moment gyros, magnetic torque rods, and
reaction-control thrusters.

Several spacecraft architectures are used to demonstrate how these
elements become an integrated system, including OSIRIS-REx, Mars
Reconnaissance Orbiter, Phoenix, Mars Science Laboratory, and the
International Space Station.

The final portion introduces spacecraft rotational dynamics: rotational
kinematics, rotational kinetic energy, moments of inertia, angular
acceleration, the parallel- and perpendicular-axis theorems, the inertia
tensor, angular momentum, torque, Euler's moment equations, and Euler
angles. Phoenix EDL and the Deep Impact star-tracker anomaly are then
used as case studies showing why high-fidelity simulation, sensor
fusion, coordinate frames, software, hardware testing, and fault
response are critical to ACS design.

------------------------------------------------------------------------

## Table of Contents

- [1. ACS Overview and Terminology](#1-acs-overview-and-terminology)
- [2. OSIRIS-REx ACS Example](#2-osiris-rex-acs-example)
- [3. Spacecraft Disturbances](#3-spacecraft-disturbances)
- [4. Mission Geometry and Pointing
  Concerns](#4-mission-geometry-and-pointing-concerns)
- [5. Attitude Determination Sensors](#5-attitude-determination-sensors)
- [6. GN&C Actuators and Effectors](#6-gnc-actuators-and-effectors)
- [7. ACS Design and Architectures](#7-acs-design-and-architectures)
- [8. Spacecraft Dynamics](#8-spacecraft-dynamics)
- [9. Phoenix Radar and EDL Simulation Case
  Study](#9-phoenix-radar-and-edl-simulation-case-study)
- [10. Deep Impact Star Tracker
  Anomaly](#10-deep-impact-star-tracker-anomaly)
- [Lecture Summary](lecture-summary)

------------------------------------------------------------------------

# 1. ACS Overview and Terminology

> **Source: Slides 1–7**

## Attitude Determination and Control

> **Source: Slides 3–5**

Attitude Determination and Control is the spacecraft subsystem that
provides:

- Attitude control
- Attitude knowledge
- Stability
- Sensors
- Actuators/effectors
- Onboard logic and control

The subsystem may be referred to by several names:

| Acronym | Meaning                                   |
|---------|-------------------------------------------|
| AACS    | Attitude and Articulation Control System  |
| ACS     | Attitude Control System                   |
| ADCS    | Attitude Determination Control System     |
| ADACS   | Attitude Determination and Control System |
| AOCS    | Attitude and Orbit Control System         |
| G&C     | Guidance and Control System               |
| GN&C    | Guidance, Navigation, and Control         |
| PCS     | Pointing Control System                   |

### Primary Pointing Drivers

Spacecraft pointing is commonly driven by:

- Science observations and instrument fields of view
- Trajectory-course maneuvers and thrust-vector orientation
- Telecommunications uplink/downlink geometry
- Thermal orientation relative to the Sun, Earth, and other bodies

### GRAIL Example

The GRAIL ACS example contains:

- 1 star tracker
- 3 reaction wheels
- 1 inertial measurement unit (IMU)
- 1 sun-sensor assembly with multiple heads
- Approximate ACS mass:

```math
\sim 5\ \text{kg}
```
### Common ACS Components

**Sensors**

- Sun sensors
- Magnetometers
- Gyroscopes
- GPS receivers
- Star trackers

**Control Effectors**

- Reaction wheels
- Momentum wheels
- Control moment gyros
- Magnetic torquers
- Reaction-control thrusters

### Key Trades and Analyses

- 3-axis control vs. spin stabilization vs. other architectures
- Reaction wheels vs. thrusters
- Control analysis
- Knowledge analysis
- Stability/jitter analysis
- Error budgets
- Heritage

### Key Parameters

- Mass
- Power
- Cost
- Pointing control
- Pointing knowledge
- Stability / jitter

------------------------------------------------------------------------

## Closed-Loop Attitude Control

> **Source: Slide 5**

The attitude-control system is a closed-loop control system.

```text
Ground or Autonomous Commands
             |
             | Commanded Attitude
             v
         Controller
             |
             | Device Commands
             v
          Actuators
             |
             v
           System <----- Disturbances
             |
             v
          Sensors <----- Disturbances
             |
             | Measured Attitude
             +---------------------> Controller
```

The attitude error is:

```math
\text{Attitude Error}
=
\text{Commanded Attitude}
-
\text{Measured Attitude}
```
The controller uses the difference between desired and measured attitude
to command actuators that correct the spacecraft orientation.

------------------------------------------------------------------------

## Slew Rates and Spacecraft Motion

> **Source: Slide 6**

The lecture introduces the question:

> What do typical spacecraft motions look like?

The slide uses a spacecraft visualization showing a sensor/spacecraft
line of sight moving over Earth. This establishes that spacecraft
attitude is dynamic and must be understood relative to the target,
orbit, and reference coordinate system.

------------------------------------------------------------------------

## ACS Terminology

> **Source: Slide 7**

### Attitude

Orientation of a defined reference system attached to the spacecraft
body.

### Determination

Knowledge of attitude within a specified tolerance, either:

- Real-time
- Post-facto

### Control

Maintenance of a specified attitude within a given tolerance.

### Pointing Error

The low-frequency component of attitude misalignment.

Pointing errors are generally corrected by the ACS.

### Jitter

Spacecraft stability represented by the high-frequency component of
attitude error.

Jitter is typically minimized primarily by design rather than actively
corrected at every instant.

### Figure Description

The slide uses a telescope boresight example with three vectors:

- Actual attitude
- Desired attitude
- Attitude knowledge based on sensors

It also compares a low-frequency pointing-error waveform with a
higher-frequency jitter/stability waveform.

------------------------------------------------------------------------

# 2. OSIRIS-REx ACS Example

> **Source: Slides 8–18**

## Mission Objectives

> **Source: Slide 9**

OSIRIS-REx stands for:

**Origins, Spectral Interpretation, Resource Identification,
Security-Regolith Explorer**

Mission facts:

- Launch: September 8, 2016
- Destination: near-Earth asteroid Bennu
- Collected rocks and surface material from Bennu
- Sample returned to Earth on September 24, 2023

The mission helps investigate:

- Planet formation
- Origins of life
- Asteroids that could impact Earth

### Spacecraft Figure

The spacecraft drawing identifies major elements including:

- OCAMS
- OTES
- OVIRS
- REXIS
- OLA
- TAGSAM
- Sample Return Capsule
- GN&C LIDAR
- High-gain antenna
- Medium-gain antenna
- Low-gain antenna
- Star trackers
- Helium tank
- 200-N thrusters
- Solar arrays
- Two-axis gimbal

------------------------------------------------------------------------

## Sample Collection Overview

> **Source: Slide 10**

The mission timeline includes:

- Launch
- Earth gravity assist
- Approach maneuver
- Asteroid operations
- Sample collection
- Departure maneuver
- Return cruise
- Sample return
- Sample analysis

The sample-collection sequence requires tightly controlled spacecraft
position and attitude relative to Bennu.

------------------------------------------------------------------------

## Instrument Deck and GN&C Components

> **Source: Slide 11**

### Instruments

**OCAMS — Camera Suite**

- PolyCam: narrow-angle, high-resolution, 8-inch telescope
- MapCam: wide-angle, high-resolution, four-color asteroid mapping
- SamCam: monitors TAG and sample acquisition

**OLA**

- LIDAR for high-resolution topography

**OTES**

- Thermal spectrometer:

```math
5.7\text{–}100\ \mu\text{m}
```
**OVIRS**

- Visible and IR spectrometer:

```math
0.4\text{–}4.3\ \mu\text{m}
```
**REXIS**

- X-ray spectrometer
- Student experiment

### GN&C Components

- 4 Sun Sensor Assemblies (SSA)
- 4 reaction wheels
- 2 star trackers
- 2 Miniature IMUs (MIMUs)
- 2 LIDARs
  - Approximately 40-cm performance at 3 km as indicated on the slide
- TAGCAM system
  - 2 NavCams
  - StowCam
  - Camera electronics
- 16 ACS thrusters
- 2 TAG thrusters

**Figure description:** The instrument-deck drawing identifies the
physical location of cameras, LIDARs, star trackers, sun sensors, and
thrusters around the spacecraft. The placement demonstrates that GN&C
design is strongly connected to fields of view, structural
accommodation, redundancy, and plume geometry.

------------------------------------------------------------------------

## OSIRIS-REx System Block Diagram

> **Source: Slides 12–13**

The spacecraft block diagram integrates:

- Propulsion
- Telecommunications
- GN&C
- C&DH
- Power electronics
- EPS
- Mechanisms and thermal
- Payloads
- TAGSAM
- Sample Return Capsule

The GN&C portion includes:

- Sun Sensor Assemblies
- Reaction Wheel Assemblies
- Star trackers
- MIMU
- GN&C LIDAR
- NavCams
- TAGCAMs
- StowCam

The interfaces include several electrical/data standards and power
paths, including:

- MIL-STD-1553
- RS-422 / LVDS
- Analog interfaces
- 28-V power
- Motor-drive power

The ACS design must consider:

- Sensors
- Actuators
- Electronics
- Software
- Redundancy
- Heritage

------------------------------------------------------------------------

## Touch and Go

> **Source: Slides 14–16**

During TAG, OSIRIS-REx descended to Bennu and contacted the surface to
collect a sample.

One to two days later, observations indicated that:

- The collector lid was likely not fully closing because of larger
  rocks.
- Material appeared to be leaking.
- The team chose to forgo the planned sample-mass measurement and stow
  the sample earlier because a significant sample was visibly present.

Sample stowage was successful.

Earth delivery occurred on:

**September 24, 2023**

Entry, descent, and landing used:

- Heatshield for high-speed entry deceleration
- Parachute for additional deceleration
- Utah Test and Training Range as the landing area

------------------------------------------------------------------------

## Questions and Mission Context

> **Source: Slides 17–18**

### TAG Error Severity

The slight TAG error was likely well within modeled capability.

The lecture emphasizes that public mission videos normally show a
nominal scenario, while engineering analysis covers a much wider
performance envelope.

### Mission Development Timeline

A repeat asteroid sample-return mission could require:

- Scientific consensus and technology development: potentially many
  years
- Proposal process: 1–3 years
- Development: 4–5 years
- Operations and sample return: 5–10 years

Total:

```math
\geq 10\text{–}20\ \text{years}
```
### Data Rate Changes

Possible approaches for increasing uplink/downlink include:

- Greater data compression
- Increased rate at the expense of bit-error rate
- Mission-dependent trajectory changes that reduce distance

### TAG Velocity

Expected touchdown speed:

```math
0.4\ \text{m/s}
```
Comparisons:

- Phoenix:

```math
\sim 1.5\ \text{m/s}
```
- MER rovers with airbags:

```math
<26\ \text{m/s}
```
### Bennu Orbit

OSIRIS-REx did orbit Bennu.

Approximate period:

```math
62\ \text{hr/orbit}
```
Features on Bennu could be used for attitude knowledge.

A simple fault-protection concept identified on the slide is:

- If something goes wrong, burn toward the Sun.

------------------------------------------------------------------------

# 3. Spacecraft Disturbances

> **Source: Slides 19–25**

## Disturbance Torque

> **Source: Slide 19**

Disturbances are torques typically induced on the spacecraft by external
forces.

They are often modeled as a force acting at a center of pressure offset
from the center of mass.

```math
\boldsymbol{\tau}
=
\mathbf{r}_{CP}\times\mathbf{F}
```
where:

- r_CP = vector from center of mass to center of pressure
- F = applied force

Examples:

- Launch-vehicle tip-off
- Aerodynamic torque
- Gravity-gradient torque
- Magnetic torque
- Solar-radiation torque
- Mass expulsion
- Internal torque

------------------------------------------------------------------------

## Aerodynamic Torque

> **Source: Slide 20**

Aerodynamic force can act through a center of pressure that does not
coincide with the center of mass, creating a weather-vane-like torque.

```math
\boldsymbol{\tau}_a
=
\mathbf{r}_{CP}\times\mathbf{F}_a
```
The aerodynamic force is related to atmospheric density, spacecraft
velocity, projected area, and drag coefficient.

The slide's example states that at approximately 400-km altitude, a
torque of:

```math
3.11\times10^{-5}\ \text{N}\cdot\text{m}
```
could produce an attitude error of approximately:

```math
82^\circ
```
after one orbit if uncorrected.

------------------------------------------------------------------------

## Gravity-Gradient Torque

> **Source: Slide 21**

Gravity gradient creates a torque tending to align the spacecraft's
minimum-inertia axis with the local vertical.

The effect arises because different portions of an extended spacecraft
experience slightly different gravitational forces.

The slide gives typical example values including:

```math
\Delta I=1000\ \text{kg}\cdot\text{m}^2
```
```math
n=0.001\ \text{s}^{-1}
```
and a representative gravity-gradient torque sensitivity of
approximately:

```math
6.7\times10^{-5}\ \text{N}\cdot\text{m/deg}
```
Gravity gradient can therefore be either:

- A disturbance that ACS must reject
- A stabilizing effect intentionally incorporated into the design

------------------------------------------------------------------------

## Magnetic Torque

> **Source: Slide 22**

Magnetic torque is relevant around bodies with substantial magnetic
fields, including Earth and Jupiter.

```math
\boldsymbol{\tau}_m
=
\mathbf{M}\times\mathbf{B}
```
where:

- M = spacecraft magnetic dipole moment
- B = planetary magnetic-field vector

Representative small-spacecraft LEO values:

```math
B=3\times10^{-5}\ \text{T}
```
```math
M=0.1\ \text{A}\cdot\text{m}^2
```
```math
\tau_m\approx3\times10^{-6}\ \text{N}\cdot\text{m}
```
------------------------------------------------------------------------

## Solar-Radiation Torque

> **Source: Slide 23**

Solar radiation produces force on exposed spacecraft surfaces.

The torque is:

```math
\boldsymbol{\tau}_s
=
\mathbf{r}\times\mathbf{F}_s
```
The solar-radiation force depends on:

- Surface reflectivity
- Projected area
- Solar intensity
- Speed of light
- Distance from the Sun

The slide identifies solar-radiation torque as particularly important
for:

- GEO spacecraft
- Deep-space cruise

The torque vector is perpendicular to the Sun line and remains relevant
whenever the spacecraft is illuminated.

------------------------------------------------------------------------

## Mass Expulsion

> **Source: Slide 24**

Mass expulsion includes:

### Jettison

- Probes
- Covers
- Expended SRMs
- Other released hardware

### Deliberate Expulsion

- Thrusters
- Gas venting

### Accidental Expulsion

- Leaks
- Misalignments

Mass-expulsion torque:

```math
\boldsymbol{\tau}_{ME}
=
\mathbf{r}_{CP}\times\mathbf{F}_{ME}
```
If sufficiently large, mass expulsion can dominate the disturbance
environment and require changes in the ACS design.

The slide uses Cassini's release of the Huygens probe as an example.

------------------------------------------------------------------------

## Internal Torque

> **Source: Slide 25**

Internal torque can be generated by:

### Deployments

- Solar arrays
- Antennas
- Booms
- Instruments

### Recurring Motion

- Instrument scanning
- Sample retrieval
- Fluid flow
- Thermal louvers

Internal torque does **not** change total system angular momentum, but
it can still change the attitude of individual spacecraft elements or
the spacecraft body.

The slide uses the Mars Odyssey boom deployment as an example.

------------------------------------------------------------------------

# 4. Mission Geometry and Pointing Concerns

> **Source: Slides 26–38**

## Typical Pointing Concerns

The major pointing concerns are:

### Payload

- Perform science observations.
- Maintain specified Sun/target phase angles.
- Avoid exposing sensitive instruments to the Sun.

### Communications

- Point antennas toward Earth.
- Avoid solar conjunction.

### Solar Arrays

- Minimize solar-incidence angle.
- Maintain adequate power while transmitting.

### Thermal

- Maintain allowable spacecraft geometry relative to the Sun and other
  thermal environments.

### Trajectory Maneuvers

- Maintain pointing and stability during burns.

### Spacecraft Agility

- Determine how rapidly the spacecraft must change attitude.

------------------------------------------------------------------------

## Body-Fixed Coordinates

> **Source: Slide 26**

A typical spacecraft body-fixed coordinate system uses:

- x_b
- y_b
- z_b

with rotations described as:

- Roll
- Pitch
- Yaw

These axes provide the reference system for describing spacecraft
attitude and control commands.

------------------------------------------------------------------------

## Payload Phase Angle

> **Source: Slide 27**

Science observations are often constrained by a required phase angle
between:

- Sun
- Target
- Spacecraft / instrument line of sight

Phase angle can therefore become a direct driver of:

- Pointing control
- Attitude knowledge
- Pointing-error requirements

------------------------------------------------------------------------

## Payload Observation Architectures

> **Source: Slide 28**

Three broad observation approaches are illustrated.

### Spacecraft Body Pointing

The spacecraft points at the target as a rigid body.

This is the typical onboard-ACS approach.

### Articulated Instrument

Actuators point the instrument or scanning platform independently of the
spacecraft body.

### Oversized Instrument Collector

The instrument collector is oversized so it can internally point or
filter data without requiring equivalent spacecraft-body pointing.

### Terminology

**Nadir**

- Pointing toward the central body, e.g. Earth.

**Zenith**

- Pointing away from the central body.

------------------------------------------------------------------------

## Communications Pointing

> **Source: Slide 29**

Communications may be limited by solar conjunction.

The relevant angle is the:

**Sun-Earth-Probe (SEP) angle**

Low-gain antennas commonly provide communication over a broad range of
nominal spacecraft attitudes.

High-gain antennas often require 3-axis control because communication
pointing must be combined with:

- Science pointing
- Power
- Thermal
- Other mission constraints

------------------------------------------------------------------------

## Solar-Array Pointing

> **Source: Slide 30**

The relevant geometry includes the:

**Sun-Probe-Earth (SPE) angle**

Solar arrays seek to minimize solar-incidence angle.

Arrays are often:

- Single-axis articulated
- Dual-axis articulated

to maintain favorable Sun pointing while the spacecraft satisfies other
pointing requirements.

Arrays may also be oversized to relax pointing constraints.

------------------------------------------------------------------------

## 3-Axis vs. Dual-Spin Stabilization

> **Source: Slide 31**

The slide compares:

- Three-axis stabilization
- Dual-spin stabilization

A wraparound solar array on a spin-stabilized spacecraft can reduce
required solar-pointing control.

**Figure description:** A three-axis spacecraft actively points its
geometry relative to Earth and Sun, while a cylindrical dual-spin
spacecraft rotates and uses a geometry that remains relatively tolerant
to Sun direction.

------------------------------------------------------------------------

## Thermal / ACS Geometry

> **Source: Slides 32 and 38**

Spacecraft are generally designed to tolerate some attitude error, but
thermal constraints still restrict allowable pointing.

The lecture uses SIRTF as an example:

- Solar array must remain toward the Sun for power.
- The same geometry keeps the telescope barrel and cryogenic detector
  shaded.

Therefore thermal and ACS design cannot be treated independently.

------------------------------------------------------------------------

## Trajectory Maneuver Pointing

> **Source: Slide 33**

OSIRIS-REx uses four 200-N thrusters for major maneuvers.

The spacecraft must orient the thruster exhaust / thrust vector
correctly before and during the burn.

This couples:

- Propulsion
- ACS
- Trajectory design

------------------------------------------------------------------------

## Spacecraft Agility

> **Source: Slides 34–35**

A typical spacecraft slew-rate requirement is approximately:

```math
1^\circ/\text{s}
```
A representative range is:

```math
0.25^\circ/\text{s}\text{ to }3^\circ/\text{s}
```
Faster slew rates generally require additional settling time before fine
stability requirements are achieved.

ISS slew rate:

```math
<0.1^\circ/\text{s}
```
Typical pointing requirements for telescopes, antennas, and detectors
may range approximately:

```math
0.001^\circ\text{ to }0.1^\circ
```
Whenever a spacecraft is holding attitude against disturbances, its ACS
actuators are working.

Examples of activity level:

- Mars Reconnaissance Orbiter may take dozens of images each day.
- A GEO communications satellite may desaturate its wheels approximately
  once per week.

------------------------------------------------------------------------

## Mission Geometry

> **Source: Slides 36–38**

Key mission angles include:

- Sun-Earth-Probe (SEP)
- Sun-Probe-Earth (SPE)
- Science phase angle

These often drive early concept formulation.

Mission-design and navigation engineers typically produce geometry plots
along with:

- Trajectory design
- Delta-V budgets

### Asteroid Rendezvous Example

The example plot indicates:

- Rendezvous occurs at favorable science phase angle.
- Communications blackout when:

```math
\mathrm{SEP}<2^\circ
```
- SPE varies approximately:

```math
0^\circ\text{–}45^\circ
```
This suggests articulated solar arrays and/or antennas may be needed to
simultaneously maintain power and communications.

### Strategic Evaluation

**Phase Angle**

- Mission Design and Navigation select trajectory/orbital geometry that
  supports science lighting.
- Example science incidence range:

```math
30^\circ\text{–}60^\circ
```
**SPE**

- Power and telecom engineers evaluate solar-array versus antenna
  pointing.

**SEP**

- Mission Design, Navigation, and Telecom evaluate solar conjunction.

### Tactical Evaluation

At each point in the mission, determine the best attitude relative to:

- Sun for power and thermal
- Earth for telecommunications
- Science target
- Maneuver requirements

------------------------------------------------------------------------

# 5. Attitude Determination Sensors

> **Source: Slides 39–47**

## Sensor Categories

Major attitude-determination sensors include:

- Sun sensors
- Earth sensors
- Magnetometers
- Star trackers / Stellar Reference Units
- Gyroscopes / Internal Reference Units
- GPS receivers

------------------------------------------------------------------------

## Sensor Accuracy and Cost

> **Source: Slide 40**

The slide shows a general trend:

> Greater accuracy generally increases cost, mass, power, and
> complexity.

Approximate categories:

### Low

Typical accuracy near:

```math
0.1^\circ
```
Examples:

- Magnetometers
- Coarse sun sensors
- IR Earth sensors

Approximate cost scale:

```math
<\$100\text{k}
```
### Medium

Typical accuracy near:

```math
0.01^\circ
```
Examples:

- Digital sun sensors
- Earth sensors
- Gyros
- GPS receivers

Approximate cost scale:

```math
<\$1\text{M}
```
### High

Typical accuracy near:

```math
0.001^\circ
```
Examples:

- Star trackers
- Fine sun sensors

Approximate cost scale:

```math
<\$10\text{M}
```
Custom sensors or payload instruments may also be used for attitude
determination.

------------------------------------------------------------------------

## Sun Sensors

> **Source: Slide 41**

Sun sensors provide basic attitude estimation, particularly for fault
protection.

Spacecraft with strict Sun constraints may include additional sensors to
trigger a safe attitude.

They are often mounted in orthogonal groups.

Four sensors can provide approximately hemispherical coverage.

### Analog Four-Detector Pyramid

- Analog current output
- Digitized by spacecraft
- Performance:

```math
1.5^\circ
```
- Mass:

```math
0.12 kg
```
The output is converted to angle in software using a cosine
relationship.

### Fine Sun Sensor

Performance:

```math
<0.016^\circ
```
approximately:

```math
1\ \text{arcmin}
```
------------------------------------------------------------------------

## Star Trackers

> **Source: Slides 42–43**

Star trackers map:

- Observed star positions
- Observed star magnitudes

against a stored star catalog to determine highly accurate spacecraft
attitude.

Typical fixed star trackers:

- Electronically scan the star field or use spacecraft motion.
- Field of view:

```math
5^\circ\text{–}20^\circ
```
- Process and calibrate images.
- Output attitude, commonly as quaternions.
- Catalog contains hundreds to thousands of stars.

Performance:

```math
0.001^\circ\text{–}1^\circ
```
Mass:

```math
1\text{–}10\ \text{kg}
```
Precision star trackers can be:

- Heavy
- Expensive
- Limited at high angular rates

### Star Distribution

Stars are not uniformly distributed across the sky.

The designer must consider:

- Staring vs. moving operations
- Maximum angular rate
- Fraction of sky available
- Response to tracker errors
- Bright-object exclusions
- Star density

------------------------------------------------------------------------

## Magnetometers

> **Source: Slide 44**

Magnetometers measure three perpendicular components of a planet's
magnetic field.

Measured values are compared against a magnetic-field model.

Representative precision:

```math
1.5^\circ\pm0.5^\circ
```
They are commonly paired with magnetic torquers.

The example attitude-control magnetometer has:

- Radiation tolerance \>306 krad
- Field range ±100,000 nT
- Accuracy ±0.5% full scale
- Mass approximately 200 g

------------------------------------------------------------------------

## Gyroscopes / IRUs / IMUs

> **Source: Slide 45**

Gyros maintain continuous attitude reference between updates from
external references such as:

- Sun
- Earth
- Stars

Modern missions commonly use:

- Ring-laser gyros
- Fiber-optic gyros

Example: **LN-200 IMU**

- Mass:

```math
0.7\ \text{kg}
```
- Power:

```math
10\ \text{W}
```
- Approximate dimensions:

```math
9\times9\ \text{cm}
```
Gyro internal processing uses:

- Dynamics models
- Environmental models
- Error models

to produce a best estimate of current attitude.

Error grows over time without an external reference.

Representative drift:

```math
0.1^\circ/\text{hr}
```
------------------------------------------------------------------------

## GPS Receivers

> **Source: Slide 46**

GPS is increasingly used for attitude knowledge.

The slide identifies operation for spacecraft velocities up to
approximately:

```math
16{,}000\ \text{m/s}
```
Performance varies with distance from approximately:

```math
200\ \text{km to }45{,}000\ \text{km}
```
Representative LEO attitude performance:

```math
<0.1^\circ
```
Example receiver:

- GD Sentinel M-Code GPS Receiver
- Mass:

```math
2.5\ \text{kg}
```
------------------------------------------------------------------------

## Sensor Summary

> **Source: Slide 47**

| Sensor       | General Characteristics                                                  |
|--------------|--------------------------------------------------------------------------|
| Sun Sensor   | Simple, reliable, inexpensive; intermittent depending on Sun visibility  |
| Earth Sensor | Less common; narrower application                                        |
| Magnetometer | Simple, reliable, inexpensive; requires useful planetary magnetic field  |
| Star Tracker | High precision; higher mass/complexity; lower-cost versions less precise |
| Gyroscope    | Maintains attitude knowledge between external-reference updates          |
| GPS Receiver | Simple and inexpensive but requires proximity to functioning GPS         |

------------------------------------------------------------------------

# 6. GN&C Actuators and Effectors

> **Source: Slides 48–60**

## Actuator Categories

> **Source: Slide 48**

### Affect System Momentum

| Actuator             | Typical Accuracy |
|----------------------|-----------------:|
| Reaction Wheels      |      0.0001–0.1° |
| Momentum Wheels      |         0.1–2.0° |
| Control Moment Gyros |       0.001–0.1° |

### Do Not Affect System Momentum

| Actuator                        | Typical Accuracy |
|---------------------------------|-----------------:|
| Magnetic Torquers / Torque Rods |        1.0–10.0° |
| Reaction Control Thrusters      |         0.1–5.0° |

------------------------------------------------------------------------

## Reaction Wheels

> **Source: Slides 49–50**

An electric motor spins a wheel aligned with a control axis.

Normally:

- One wheel controls each axis.
- Three wheels are required for full 3-axis control.
- Four wheels are often installed in a tetrahedral arrangement for
  redundancy.

### Characteristics

Performance:

```math
0.0001^\circ\text{–}0.1^\circ
```
- Low torque
- High accuracy
- Fast response, potentially tens of Hz
- No propellant required
- Limited by angular-momentum storage
- Normally operate at relatively low speed

The saturation level is set by peak motor speed.

When a wheel saturates, momentum must be dumped using another actuator,
such as thrusters or magnetic torque rods.

### Sizing

Representative reaction-wheel torque range:

```math
0.01\text{–}1\ \text{N}\cdot\text{m}
```
Example disturbance / maneuver values from the slide:

Magnetic torque:

```math
2.1\times10^{-5}\ \text{N}\cdot\text{m}
```
Slew torque:

```math
2.9\times10^{-4}\ \text{N}\cdot\text{m}
```
Gravity-gradient momentum accumulation:

```math
0.039\ \text{N}\cdot\text{m}\cdot\text{s}
```
Reaction-wheel torque must exceed the disturbance torque to maintain
attitude.

Detailed GN&C trade studies can range from rapid conceptual estimates to
months of simulation and review.

------------------------------------------------------------------------

## Momentum Wheels

> **Source: Slide 51**

Momentum wheels operate at nonzero angular momentum to provide
gyroscopic stiffness.

Characteristics:

- Performance:

```math
0.1^\circ\text{–}2.0^\circ
```
- Similar to heavier reaction wheels operating at approximately constant
  speed
- Often used to cancel momentum from rotating payloads

------------------------------------------------------------------------

## Control Moment Gyros

> **Source: Slides 52–54**

A Control Moment Gyro is a gimbaled momentum wheel.

Torque applied through the gimbal changes wheel angular momentum and
produces a reaction torque on the spacecraft body.

Characteristics:

- Performance:

```math
0.001^\circ\text{–}0.1^\circ
```
- Wheel operates at nearly steady high speed.
- Control authority can be up to approximately 100 times greater than a
  momentum wheel.
- Can generate vibration/noise due to high spin rate.

### ISS CMGs

ISS uses four CMGs installed in the Z1 truss.

The lecture notes several historical CMG issues:

- CMG-1 failed in 2002 and was replaced in 2005.
- CMG-2 experienced circuit-breaker failures.
- CMG-3 failed in 2006 and was replaced in 2007.

A replacement required a spacewalk of approximately seven hours.

------------------------------------------------------------------------

## Attitude-Control Redundancy

> **Source: Slide 55**

Most spacecraft include significant ACS redundancy.

### Wheels / CMGs

- Three wheels are normally needed for 3-axis control.
- A fourth allows any three to provide control after one failure.
- ISS requires at least two CMGs because gravity-gradient effects also
  assist its attitude behavior.

### Thrusters

High-value missions often include redundant coupled thrusters.

Thrusters provide **functional redundancy** for wheels.

They may not match wheel precision and consume propellant, so mission
performance may be degraded.

### Other Functional Backup

Examples:

- Dawn used electric propulsion after three reaction-wheel failures.
- ISS uses gravity gradient to reduce control demand.
- Payload instruments may sometimes assist attitude knowledge.

------------------------------------------------------------------------

## Electric Propulsion for Attitude Control

> **Source: Slide 56**

Electric propulsion can provide attitude control.

Dawn's three electric-propulsion thrusters can provide approximately:

```math
90\ \text{mN}
```
Electric propulsion is regularly used for attitude/orbit functions in
GEO because:

- Disturbances are small.
- Electric propulsion efficiency is extremely high.

The slide cites:

```math
I_{sp}>3000\ \text{s}
```
Representative small-spacecraft GEO disturbances:

Gravity gradient:

```math
5\times10^{-9}\ \text{N}\cdot\text{m}
```
Solar-radiation pressure:

```math
6\times10^{-6}\ \text{N}\cdot\text{m}
```
------------------------------------------------------------------------

## Magnetic Torque Rods

> **Source: Slide 57**

Magnetic torque rods are electromagnets energized to interact with the
local magnetic field.

Characteristics:

- Performance:

```math
1^\circ\text{–}10^\circ
```
- No consumable propellant
- Useful for momentum dumping
- Simple
- Reliable
- Inexpensive
- Primarily applicable around bodies with strong magnetic fields

------------------------------------------------------------------------

## Reaction-Control Thrusters

> **Source: Slides 58–59**

When thrusters are used only for attitude control, the system is
commonly called an **RCS**.

Characteristics:

- Performance:

```math
0.1^\circ\text{–}5^\circ
```
- Many thrust levels available
- Propellant limited
- Can introduce contamination
- Capable of high torque
- Accuracy limited by configuration and minimum impulse bit

Primary thruster characteristics:

- Thrust level
- Specific impulse
- Minimum impulse bit

Primary uses:

- Trajectory Correction Maneuvers
- Orbit maintenance
- Momentum dumps
- Attitude control
- Thrust-vector control

A spacecraft may therefore use:

- Small RCS thrusters for ACS
- Main engines for large Delta-V
- Intermediate thrusters for TVC or other functions

------------------------------------------------------------------------

## Spin-Stabilized Spacecraft

> **Source: Slide 60**

### Spin Rate

Two pairs of coupled thrusters on opposite sides can change spin rate.

### Velocity

After orienting the spin axis, thrusters may fire together for a
translational maneuver.

### Attitude

Coupled thrusters rotate the spin axis.

They are fired in short pulses at precise points in the spacecraft
rotation.

Each pulse changes the spin-axis direction by a small amount until the
desired attitude is reached.

The slide uses Pioneer 10 as the graphical example.

------------------------------------------------------------------------

# 7. ACS Design and Architectures

> **Source: Slides 61–70**

## ACS Design Steps

> **Source: Slide 61**

### Review and Understand Design Information

- Mission description
- Concept of Operations
- System requirements
- Subsystem requirements
- Mission geometry
- Payload pointing
- Expected disturbances

### Create Preliminary Design

- Select likely architecture.
- Select likely sensors.
- Select likely actuators.
- Size control effectors.
- Consider functional redundancy.
- Consider system cost.
- Create end-to-end kinematic simulations.
- Develop error budgets.
- Understand fault scenarios.
- Trade reaction wheels against thrusters.
- Create component mass list.

### Review and Iterate

Revisit options and trades with the broader spacecraft team.

------------------------------------------------------------------------

## General Architecture Guidance

> **Source: Slide 62**

### Three Primary Functions

- Control
- Knowledge
- Stability

### Common Sensors Across Most Missions

- Sun sensors
- Gyros / IMUs

### Destination Dependencies

**LEO**

- Horizon sensors
- GPS receivers
- Magnetic torquers

**Within approximately 2–3 AU of the Sun**

- Electric propulsion may be practical for attitude control.

**Deep Space**

- Star trackers

**Close-Proximity Operations**

- Radar
- LIDAR
- Other relative-navigation sensors

### Functional Dependencies

Imaging spacecraft usually require reaction wheels, although cold-gas
systems are increasingly capable.

Thrusters-only vs. reaction wheels is a common:

**Cost vs. performance trade**

Large/agile spacecraft may require CMGs.

Redundancy generally increases with:

- Mission duration
- Mission value
- Budget

------------------------------------------------------------------------

## Interpreting ACS Block Diagrams

> **Source: Slide 63**

When reviewing an ACS architecture, ask:

- What function does each component provide?
- What missions does it support?
- If a component fails, how does the failure propagate?
- What will ground telemetry show?
- Is recovery possible?

Block diagrams are therefore not only hardware maps; they are tools for
understanding:

- Function
- Interfaces
- Fault propagation
- Redundancy
- Recovery

------------------------------------------------------------------------

## Mars Reconnaissance Orbiter GN&C Architecture

> **Source: Slide 64**

### Sensors

- 2 IMUs with gyros and accelerometers
- 2 star trackers
- 2 four-detector sun sensors
- 4 two-detector sun sensors

### Controller / Interfaces

- 2 C&DH units
- RAD750 CPU
- GN&C Interface Card
- Analog Acquisition Card
- RS-422
- 1553
- Digital and analog interfaces

### Actuators

- 4 reaction wheels
- Solar-array and HGA gimbal-drive electronics
- Thrusters:
  - 8 × 0.9-N ACS
  - 6 × 22-N TCM
  - 6 × 170-N MOI

The architecture shows how GN&C crosses subsystem boundaries through
C&DH, power, propulsion, and mechanisms.

------------------------------------------------------------------------

## Phoenix GN&C Architecture

> **Source: Slide 65**

### Sensors

Cruise stage:

- 2 Sun Sensor Assemblies
- 2 IMUs
- 2 star trackers

EDL:

- Landing radar

### Controller

- Dual C&DH
- RAD6000 CPU
- Payload & Attitude Control interface card
- I/O card
- 1553 / A/D / discrete interfaces

### Actuators

Thrusters include multiple classes for:

- Delta-V
- Pitch/yaw
- Roll/pitch/yaw
- Descent

The architecture also includes:

- Power Distribution & Drive Unit
- Pyro Initiation Unit
- Valve Driver Module

------------------------------------------------------------------------

## Mars Science Laboratory GN&C Architecture

> **Source: Slides 66–67**

MSL GN&C spans:

- Cruise stage
- Descent stage
- Rover

### Sensors / Inputs

- Sun sensors
- Star scanner
- Radar
- Descent IMU
- Rover IMU
- HazCams
- NavCams

### Actuators

- Cruise RCS
- Entry RCS
- Mars landing engines
- Rover mobility actuators
- HGA gimbal
- Instrument gimbals

### Control Functions

- Attitude determination
- Position determination
- Rover 3-DOF control
- Hazard avoidance
- Visual odometry
- Hazard detection
- Celestial-body position propagation
- Instrument pointing
- HGA pointing

### Environment / Models

- Mars rotation
- Sun/Earth positions
- Rover hardware
- Terrain

The control-system diagram demonstrates that GN&C includes algorithms
and environmental models in addition to physical sensors and actuators.

------------------------------------------------------------------------

## Questions from Prior Classes

> **Source: Slides 68–70**

### Common Actuators

- Magnetic torquers for LEO because they are simple and inexpensive.
- Thrusters for lower precision.
- Reaction wheels for high precision.

### GN&C Failure Examples

Examples discussed:

- Genesis: backwards G-switch / phasing issue
- Dawn: reaction-wheel failures
- ISS: recurring gyro/CMG failures
- SOHO: gyro failure combined with inadequate fault response

### Atmospheric Drag

The lecture notes:

- Above approximately 600 km, gravity gradient may dominate over drag.
- Above approximately 2000 km, drag becomes effectively negligible for
  this discussion.

### Launch Vehicle Attitude Control

Primarily accomplished by main-engine gimbals.

### Reaction Wheels vs. Cold Gas

Reaction wheels provide significantly greater precision.

### New GN&C Technology

MSL required development of landing-radar capability building on lessons
from Phoenix.

### ACS vs. Propulsion Ownership

A small spacecraft with only RCS may place the thrusters entirely under
ACS.

If a larger propulsion system exists, thrusters are usually managed
within propulsion while serving ACS functions.

### GPS at Mars

A Mars GPS constellation would be expensive and power intensive.

### Star Catalogs

More than a billion stars have been cataloged overall.

A spacecraft star-tracker catalog commonly contains thousands, e.g.
approximately 10,000.

------------------------------------------------------------------------

# 8. Spacecraft Dynamics

> **Source: Slides 71–88**

## Introduction to Kinematics

> **Source: Slide 72**

### Kinematics

Describes motion of:

- Points
- Bodies
- Systems of bodies

without considering the forces causing the motion.

### Translational Motion

Changes in:

- Position
- Velocity

For spacecraft this relates to:

- Position in a gravity field
- Delta-V
- Thrust

### Rotational Motion

Changes in spacecraft attitude.

This directly supports attitude determination and control.

### Why Dynamics Matter

Modeling spacecraft attitude provides insight into:

- Required sensor precision
- Required actuator performance
- Payload requirements
- Ascent/descent performance
- Communications
- Propellant consumption
- Detailed ConOps
- Margin and risk

------------------------------------------------------------------------

## Rotational Kinematics

> **Source: Slide 73**

Angular velocity depends on radius, making rotational relationships more
complex than basic translational relationships.

The following slides build the mathematical background needed to model
spacecraft rotational motion.

------------------------------------------------------------------------

## Rotational Kinetic Energy

> **Source: Slide 74**

For rotation about the z axis:

```math
K=\frac{1}{2}I_z\omega^2
```
where:

- K = rotational kinetic energy
- I_z = moment of inertia about z
- ω = angular velocity

Moment of inertia plays a role analogous to mass in translational
physics.

------------------------------------------------------------------------

## Moment of Inertia and Angular Acceleration

> **Source: Slides 75–76**

The rotational analogue of Newton's second law relates torque and
angular acceleration.

For a simple fixed-axis case:

```math
\tau=I\alpha
```
where:

- τ = torque
- I = moment of inertia
- α = angular acceleration

Moment of inertia is calculated from mass distribution.

For rotation about z:

```math
I_z=\int(x^2+y^2)\,dm
```
For a continuous body with density ρ, the integration can be
performed over the body's volume.

Units:

```math
\text{kg}\cdot\text{m}^2
```
------------------------------------------------------------------------

## Moment of Inertia Examples

> **Source: Slides 77–78**

The lecture shows standard formulas for common shapes, including a thin
ring.

For a thin ring about its center axis:

```math
I=MR^2
```
Published formulas exist for many basic shapes.

Complex spacecraft can be approximated by:

1.  Breaking the spacecraft into simple components.
2.  Calculating each component's inertia.
3.  Translating inertias to a common reference.
4.  Summing them.

Early in formulation, ACS engineers often estimate spacecraft inertia
using a small number of approximate shapes and masses.

------------------------------------------------------------------------

## Parallel-Axis Theorem

> **Source: Slides 79–80**

The parallel-axis theorem allows the inertia about an offset axis to be
calculated from inertia about a parallel axis through the center of
mass.

```math
I=I_{CM}+Md^2
```
where:

- I_CM = inertia about the center-of-mass axis
- M = body mass
- d = perpendicular offset between axes

The slide applies this to the moment of inertia of a disk about its
edge.

------------------------------------------------------------------------

## Perpendicular-Axis Theorem

> **Source: Slide 81**

For a thin flat plate in the x-y plane:

```math
I_z=I_x+I_y
```
For a symmetric thin disk:

```math
I_x=I_y
```
and:

```math
I_z=\frac{1}{2}MR^2
```
therefore:

```math
I_x=I_y=\frac{1}{4}MR^2
```
This theorem is particularly useful for thin planar objects.

------------------------------------------------------------------------

## Moment of Inertia as a Tensor

> **Source: Slides 82 and 84**

A spacecraft is a 3-dimensional body and generally requires an inertia
tensor rather than one scalar inertia.

The inertia tensor includes:

- I_x
- I_y
- I_z
- Products of inertia such as I_xy, I_xz, and I_yz

The diagonal terms are always positive.

Products of inertia measure asymmetry.

If the body is symmetric about a plane, products associated with axes
perpendicular to that symmetry plane may be zero.

Angular momentum is related to the inertia tensor and angular velocity:

```math
\mathbf{h}=\mathbf{I}\boldsymbol{\omega}
```
------------------------------------------------------------------------

## Angular Momentum

> **Source: Slide 83**

Angular momentum is the rotational analogue of linear momentum.

Linear:

```math
p=mv
```
Rotational:

```math
\mathbf{h}=\mathbf{I}\boldsymbol{\omega}
```
Momentum may be written as:

- h
- L

Conservation of angular momentum is fundamental to understanding:

- Reaction wheels
- Momentum wheels
- CMGs
- Internal spacecraft motion

------------------------------------------------------------------------

## Torque

> **Source: Slide 85**

Torque changes angular momentum.

For attitude hold, disturbances must be offset by counter-torques.

Conceptually:

```math
\boldsymbol{\tau}
=
\frac{d\mathbf{h}}{dt}
```
for the appropriate rigid-body formulation/reference.

This relationship connects:

- Disturbance analysis
- Actuator sizing
- Spacecraft rotational response

------------------------------------------------------------------------

## Euler's Moment Equations

> **Source: Slides 86–87**

Euler's equations describe rigid-body rotational motion about the body
axes.

They relate:

- Applied torque
- Angular velocity
- Angular momentum
- Moments/products of inertia

The lecture emphasizes:

```math
\mathbf{h}=\mathbf{I}\boldsymbol{\omega}
```
Euler's equations can be used to build an attitude-control simulation
that predicts how spacecraft angular momentum and attitude evolve under
applied torques.

------------------------------------------------------------------------

## Euler Angles

> **Source: Slide 88**

The dynamics discussion returns to:

- Roll
- Pitch
- Yaw

and introduces the need for rotation matrices to transform between
coordinate frames.

------------------------------------------------------------------------

# 9. Phoenix Radar and EDL Simulation Case Study

> **Source: Slides 89–97**

## Phoenix Radar

> **Source: Slides 89–92**

The Phoenix case study focuses on the landing radar and the importance
of realistic GN&C simulation during Entry, Descent, and Landing.

The radar was a critical sensor used to determine motion and altitude
relative to the Martian surface during descent.

The case study demonstrates that a sensor can satisfy simplified
requirements while still contain mission-threatening behavior not
represented by the original model.

------------------------------------------------------------------------

## Phoenix EDL Simulation

> **Source: Slides 93 and 96**

Major simulation components included:

- Simulation integrator
- Atmospheric model
- Hypersonic aerodynamics model
- Gravity model
- Dispersed hypersonic aerodynamics model
- Parachute drag model
- Parachute inflation model
- Wrist-mode models
- Multiple configuration aerodynamics models
- Wind models
- RCS propulsion model
- IMU model
- Radar model
- Descent-engine propulsion model
- Phoenix flight software
- ADAMS mechanical model

### Higher-Level Models

- 6-DOF Langley simulation
- 6-DOF Lockheed Martin simulation
- 6-DOF mechanical simulation
- Flowtran lander simulation
- Flight-software simulation

### Validation

Models were validated using:

- Literature
- Past missions
- Mars atmospheric knowledge
- Wind-tunnel testing
- Radar field testing
- Live-fire vacuum thruster testing
- Peer reviews

The later simulation incorporated both low- and high-fidelity radar
models.

------------------------------------------------------------------------

## Original Radar Assumptions

> **Source: Slide 94**

The original Mars '01 / Phoenix simplified radar model assumed:

- Infinite sloped flat plane
- Noise/bias matching requirements
- Very sharp single-peak FFT velocity measurements
- Perfect angle of arrival
- Only one target: the ground

Field tests and higher-fidelity simulation showed these assumptions were
inadequate.

Observed effects included:

- Terrain relief and brightness variation moving the look vector
- Noise/bias changing with terrain and target brightness
- Broader FFT signatures
- Multiple FFT peaks
- Nadir contamination
- Angle-of-arrival bias toward nadir
- Two targets rather than one:
  - Ground
  - Heatshield

------------------------------------------------------------------------

## Additional Radar Problems

> **Source: Slide 95**

The original model also failed to capture:

- Multiple-target confusion in radar search logic
- False-target locks
- Ambiguities
- Previously unknown radar-firmware bugs
- Long lockup times under some thermal/timing conditions
- Bi-modal lockup behavior

### Result

Substantial effort was required:

- Immediately before launch
- During cruise

to build and incorporate a high-fidelity radar model.

This work corrected several anomalies capable of causing mission
failure, but also exposed additional anomalies that had to be resolved.

------------------------------------------------------------------------

## Radar Simulation Data

> **Source: Slide 97**

The slide presents radar data generated from simulation.

The key purpose is to show that detailed sensor behavior must be
represented in the end-to-end EDL model rather than reduced to a simple
ideal measurement.

------------------------------------------------------------------------

# 10. Deep Impact Star Tracker Anomaly

> **Source: Slides 98–106**

## Deep Impact Mission

> **Source: Slide 98**

Deep Impact was a NASA spacecraft designed to investigate comet interior
composition by releasing an impactor into a comet.

- Launched in 2005
- Successfully impacted a comet
- The spacecraft nearly failed earlier in the mission because of an
  attitude-estimation anomaly

------------------------------------------------------------------------

## Attitude Estimation

> **Source: Slide 99**

Attitude estimation combines weighted measurements from multiple sensors
into one estimate.

Typical sensor combination:

- Gyros for rate data
- Star trackers for celestial attitude

The estimator can propagate attitude for limited periods without
star-tracker data if an initial reference exists.

### Sensor Weighting

Low sensor weights:

- Prevent a sensor from abruptly changing the estimate.

High weights:

- Allow large, rapid estimate updates.

### Star Tracker

- Matches images against star catalog.
- Produces full 3-axis attitude relative to a standard coordinate
  reference such as J2000.
- Can determine attitude without initial knowledge.
- Cannot sustain lock at high rotation rates.
- Requires clear sky.
- Can be dazzled by bright objects.
- Requires sufficient star density.

### Gyros

- Provide angular rates.
- Rates can be integrated to determine angular position relative to a
  reference.
- Work at higher rotation rates.
- Less accurate in absolute attitude.
- Experience bias/drift over long integration periods.

------------------------------------------------------------------------

## Deep Impact Safe Mode

> **Source: Slide 100**

After launch, Deep Impact entered planned safe mode.

In safe mode:

- Gyros and sun sensors were used.
- Spacecraft +Y axis pointed toward the Sun.
- Spacecraft rotated once every:

```math
4\ \text{hours}
```
This was called the **sunline ACS state**.

Star trackers were mounted on the back side of the spacecraft and
initially were not used.

The Attitude Estimator integrated gyro data from a wake-up frame.

After checkout:

- Star trackers were turned on by ground command.
- ATE slowly incorporated star-tracker measurements.
- Gyro data initially had much greater weight.
- Star-tracker data gradually corrected the estimate.

This was described as a **slow-drip correction**.

After convergence, the spacecraft was intended to transition from safe
mode to 3-axis control.

------------------------------------------------------------------------

## Attitude Estimate Jumps

> **Source: Slide 101**

Twice during each four-hour rotation, the ATE estimate jumped
discontinuously.

The two jumps were approximately:

```math
11\text{–}12\ \text{min}
```
apart.

This repeated pattern indicated a geometry-dependent or systematic
problem.

------------------------------------------------------------------------

## Star Tracker Lock State

> **Source: Slide 102**

The attitude-estimate jumps coincided with star-tracker outages.

The interval corresponded to approximately:

```math
19^\circ
```
which matched the relative alignment of the star trackers and suggested
a systematic issue.

Star-tracker data suggested the Sun was approximately:

```math
90^\circ
```
from its expected location.

Sun-sensor and solar-array data contradicted this, suggesting a
star-tracker alignment problem.

The anomaly appeared when trackers pointed near celestial true north.

Possible causes considered:

- Star-tracker alignment
- ACS/ATE software
- Earth in field of view
- A dark / low-star-density region of sky

------------------------------------------------------------------------

## Coordinate-Frame Error

> **Source: Slide 103**

Documentation review found a coordinate-frame transformation error.

A:

```math
90^\circ
```
rotation needed to translate from the mechanical frame to spacecraft
frame had been omitted.

All three star trackers, including the impactor's tracker, had incorrect
alignments.

------------------------------------------------------------------------

## Virtual Star Tracker

> **Source: Slide 104**

The system used a **Virtual Star Tracker**.

When both physical star trackers were:

- On
- In lock

the attitude algorithm used only the trackers' boresight vectors, which
were correct.

When only one tracker was in lock:

- The complete quaternion from that tracker was used.
- The quaternion contained the 90-degree coordinate-frame error.

This architecture obscured the problem because system behavior changed
depending on how many trackers were locked.

------------------------------------------------------------------------

## Star Catalog Error

> **Source: Slide 105**

A second independent problem existed.

Star catalogs contain many stars indexed and sorted by declination.

Additional stars had been added to the Deep Impact tracker catalog to
provide high star density in deep space.

However:

- A parameter defining list length was not increased.
- The catalog was therefore truncated.
- Stars above approximately:

```math
80^\circ
```
declination were missing.

This caused star-tracker lock failures near the celestial North Pole.

The anomaly therefore involved **multiple independent errors**, not a
single failure.

------------------------------------------------------------------------

## Lessons Learned

> **Source: Slide 106**

### Keep It Simple

The Virtual Star Tracker concept obscured the underlying problem.

Fortunately, safe mode did not depend on the ATE estimate for attitude
control.

The spacecraft could remain in sunline mode using coarse sun sensors
while the anomaly was debugged.

### Phasing Tests Are Critical

A star-tracker phasing test should have detected the misalignment.

It was unclear whether the test:

- Occurred
- Was properly verified

### Explain All Observables

Multiple errors can occur simultaneously.

Even after one cause is identified, engineers must explain **all
observed behavior** before declaring closure.

The lecture identifies fishbone diagrams and systematic closure
processes as useful tools.

### Beware of Heritage

The team initially doubted that the star tracker itself could be
responsible because the hardware had substantial heritage.

Investigation eventually revealed the incorrect parameter.

The lecture emphasizes that heritage reduces risk but does **not**
eliminate the need for:

- Verification
- Phasing tests
- Interface checks
- Mission-specific validation

The alignment error existed on all three star trackers, including the
impactor tracker. If it had existed only on the impactor, the problem
might not have been discovered until too late to correct before the
comet flyby.

------------------------------------------------------------------------

# Lecture Summary

> **Source: Slides 1–106**

The Attitude Control System provides three central capabilities:

- **Control**
- **Knowledge**
- **Stability**

ACS is fundamentally a closed-loop system:

```text
Commanded Attitude
       |
       v
   Controller
       |
       v
   Actuators
       |
       v
   Spacecraft <---- Disturbances
       |
       v
    Sensors
       |
       +----------> Measured Attitude
```

The controller seeks to minimize:

The attitude error is:

```math
\text{Attitude Error}
=
\text{Commanded Attitude}
-
\text{Measured Attitude}
```
Spacecraft ACS design is driven by both the mission and the disturbance
environment.

Major disturbances include:

- Aerodynamic torque
- Gravity gradient
- Magnetic torque
- Solar-radiation pressure
- Mass expulsion
- Internal moving hardware

The general disturbance relationship is:

```math
\boldsymbol{\tau}
=
\mathbf{r}\times\mathbf{F}
```
Pointing requirements are generated by:

- Payload science
- Telecommunications
- Solar-array power
- Thermal constraints
- Trajectory maneuvers
- Spacecraft agility

Mission geometry commonly requires evaluation of:

- SEP angle
- SPE angle
- Science phase angle

The major attitude sensors introduced are:

| Sensor       | General Role                                               |
|--------------|------------------------------------------------------------|
| Sun Sensor   | Coarse/fine Sun-relative attitude and safe-mode protection |
| Earth Sensor | Earth-relative attitude                                    |
| Magnetometer | Magnetic-field-relative attitude                           |
| Star Tracker | High-precision absolute celestial attitude                 |
| Gyro / IMU   | Continuous relative attitude/rate propagation              |
| GPS Receiver | Position and attitude information near GPS coverage        |

The major actuators/effectors are:

| Actuator            | General Role                                             |
|---------------------|----------------------------------------------------------|
| Reaction Wheel      | High-precision 3-axis control                            |
| Momentum Wheel      | Gyroscopic stiffness / stored momentum                   |
| CMG                 | High-control-authority momentum exchange                 |
| Magnetic Torque Rod | Momentum dumping and coarse control near magnetic bodies |
| RCS Thruster        | High-torque control and functional redundancy            |

ACS design is iterative:

```text
Mission / ConOps
      |
      v
Requirements & Geometry
      |
      v
Disturbance Analysis
      |
      v
Architecture Selection
      |
      v
Sensor Selection
      |
      v
Actuator Selection & Sizing
      |
      v
Block Diagram / Interfaces
      |
      v
Simulation & Error Budgets
      |
      v
Fault / Redundancy Analysis
      |
      +------ Iterate with Spacecraft Team ------+
```

Spacecraft rotational dynamics are based on relationships including:

```math
K=1/2Iω^2
```
```math
\tau=I\alpha
```
```math
\mathbf{h}=\mathbf{I}\boldsymbol{\omega}
```
```math
\boldsymbol{\tau}
=
\frac{d\mathbf{h}}{dt}
```
For complex spacecraft, inertia is represented as a tensor and
rotational motion is described using Euler's moment equations.

The Phoenix case study demonstrates that ACS performance depends on the
fidelity of the entire simulation environment. Simplified radar
assumptions failed to capture terrain effects, multiple targets, FFT
behavior, firmware bugs, and lockup behavior. Higher-fidelity modeling
and hardware testing were required to expose mission-threatening
problems.

The Deep Impact case study demonstrates that sensor fusion and heritage
hardware do not remove the need for careful verification. A missing
90-degree coordinate transformation and a separate star-catalog
truncation error combined to produce confusing attitude-estimation
behavior. Safe-mode independence, systematic troubleshooting, phasing
tests, and explaining every observable were critical to resolving the
anomaly.

The central lesson is that ACS is not merely a collection of sensors and
wheels. It is an integrated spacecraft control system in which mission
geometry, physics, sensors, actuators, software, coordinate frames,
interfaces, disturbances, simulation fidelity, redundancy, and fault
response must all work together.


