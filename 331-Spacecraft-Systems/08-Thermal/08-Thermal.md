# Thermal Control System

**Course:** ASTE-331a — Spacecraft Systems Engineering  
**Lecture:** 08 — Thermal  
**Instructors:** Jim Chase, Danielle Marsh    
**Source:** `331_08_Thermal_20251121.pdf`

------------------------------------------------------------------------

## Lecture Overview

This lecture develops the spacecraft thermal-control subsystem from its basic function and temperature requirements through thermal architecture, spacecraft environments, heat-transfer principles, thermal power balance, hardware selection, modeling, testing, and preliminary design.

The main analytical workflow is:

1. Understand spacecraft and payload temperature requirements.
2. Understand mission geometry and thermal environments.
3. Select a preliminary thermal architecture.
4. Select target temperatures and hot/cold bias.
5. Select materials, coatings, radiators, heat pipes, MLI, heaters, and other thermal-control hardware.
6. Create back-of-the-envelope heat-transfer estimates.
7. Build the spacecraft thermal-balance model.
8. Size thermal-control hardware.
9. Verify the design using thermal-vacuum testing.
10. Iterate with the broader spacecraft team.

The lecture uses GRAIL as an introductory subsystem example and Exo-C as a mission example for thermal stability, heater sizing, and solar-shield trade studies.

------------------------------------------------------------------------

## Table of Contents

1. [Thermal Introduction](#1-thermal-introduction)
2. [Temperature Requirements and Environments](#2-temperature-requirements-and-environments)
3. [Thermal Design Practices](#3-thermal-design-practices)
4. [Radiation Properties and Surface Treatments](#4-radiation-properties-and-surface-treatments)
5. [Thermal Power Balance](#5-thermal-power-balance)
6. [Radiated Emissions and Solar Flux](#6-radiated-emissions-and-solar-flux)
7. [Thermal-Control Hardware](#7-thermal-control-hardware)
8. [Thermal Modeling and Mission Example](#8-thermal-modeling-and-mission-example)
9. [Thermal Trade Study](#9-thermal-trade-study)
10. [Thermal-Vacuum Testing](#10-thermal-vacuum-testing)
11. [Thermal Design Process](#11-thermal-design-process)
12. [Lecture Summary](#lecture-summary)

------------------------------------------------------------------------

# 1. Thermal Introduction

## Thermal Overview

> **Source: Slide 2**

### Function

The thermal subsystem:

- Provides appropriate thermal control throughout the spacecraft.
- Is primarily driven by the overall thermal model that includes temperatures from:
  - Avionics, usually room temperature
  - Instruments, such as cold FPAs or hot sample analyses
  - Batteries
  - Mechanisms
  - Propulsion
- Must keep all components within their qualification temperature limits.

### GRAIL Example

- Paint and films
- Multi-Layer Insulation (MLI)
- Instrument thermal mass plate
- Heaters, thermostats, sensors, etc.
- Total mass: approximately 10 kg

### Common Components

- Surface coatings and treatments
  - Films
  - Paints
  - MLI
- Conductors and insulators
- Heat-transfer regulators
  - Heat pipes
  - Louvers
  - Phase-change devices
  - Heat switches

### Key Trades and Analyses

- Active versus passive
- Thermal analysis
- Radiator design, locations, and margins

### Key Parameters

- Mass
- Power
- Cost
- Updated attitude profile

**Figure description:** The GRAIL example identifies temperature sensors, heaters, and thermostats as representative thermal-control hardware.

------------------------------------------------------------------------

## Thermal Control System Scope

> **Source: Slide 3**

The thermal-control system must:

> Maintain spacecraft system elements within specified temperature limits.

Temperature levels are limited to support:

- Chemistry
  - Batteries
  - Thrusters
- Phase and viscosity
  - Propellants
  - Lubricants
- Thermal stress
  - Electronics
  - Alignments
- Mechanical properties
- Other temperature-sensitive hardware
  - Low-temperature sensors

------------------------------------------------------------------------

## Architecture Objectives

> **Source: Slide 4**

### Maximize System Operability

**Pointing**

- Allow the spacecraft to freely point without exceeding thermal limits.

**Power**

- Minimize the impact of constraints on operability.
- Examples include relationships with battery and array temperature.

### Provide Robustness

- Insensitive to environment and system characteristics
- Insensitive to small design changes
- Simplifies testing

**Figure description:** The slide includes a spacecraft with extensive external thermal-control surfaces, emphasizing the connection between thermal architecture and spacecraft configuration.

------------------------------------------------------------------------

# 2. Temperature Requirements and Environments

## Typical Subsystem Requirements

> **Source: Slide 5**

| Component / Subsystem | Operating Temperature | Survival Temperature |
|---|---:|---:|
| Digital Electronics — modern avionics, rad-hard CPUs, FPGAs | -20 to +70 °C | -40 to +85 °C |
| Analog Electronics | -20 to +55 °C | -40 to +85 °C |
| Batteries — modern Li-ion spacecraft cells | 0 to +30 °C | -20 to +50 °C |
| IR Detectors — HgCdTe, bolometers, cooled arrays | -253 to -173 °C (20–100 K) | -253 to +30 °C |
| Solid-State Particle Detectors — Si PIN, CdTe | -40 to +20 °C | -50 to +40 °C |
| Momentum Wheels / Reaction Wheels / Motors | -20 to +60 °C | -30 to +70 °C |
| Solar Panels — modern triple-junction GaAs | -150 to +135 °C | -180 to +150 °C |

------------------------------------------------------------------------

## Thermal Control Environments

> **Source: Slide 6**

| Phase | Time Period | Environment |
|---|---|---|
| Ground Operations | Months to years before launch | Cleanroom (ISO-8 to ISO-5), 18–23 °C, controlled humidity (30–50%), transportation vibration/shock, EMI/EMC test environments, thermal-vac testing, integration and test facilities |
| Launch | ~10–15 minutes ascent + ~5–20 minutes coast | High acoustic loads (140–150 dB), intense vibration, pyro-shocks, fairing thermal gradients, plume heating, rapidly changing g-loads (0–6 g), launch-vehicle RF environment |
| Transfer Orbit | Hours to weeks | Sun/Earth/Moon thermal cycles, albedo variations, eclipse periods, outgassing and contamination, arbitrary or constrained attitudes, initial propulsion burns, higher radiation |
| Final Orbit / Operational Phase | Years to decades | Stable or cycling thermal environment depending on orbit, solar cycles, radiation, seasonal beta angles, varying attitudes, payload-driven modes, station keeping, and end-of-life degradation |

------------------------------------------------------------------------

# 3. Thermal Design Practices

> **Source: Slide 7**

## Heat-Transfer Mechanisms

### Conduction

- Typically dominates at the component level.

### Radiation

- Dominates at the system level.

### Convection

- Generally not applicable.
- Due to vacuum / zero-g environment.

## Good Thermal Design Practices

- Co-locate components/systems with similar requirements.
- Place high-power devices near exterior radiators.
- Point radiators toward deep space.
- Limit view factors of radiators.
  - View factors are the fraction of other spacecraft structure/components in FOV.
- Use cold biasing.
  - Design regions to operate below design temperature.
  - Use heaters to provide positive control.
  - Provides margin.

**Figure description:** A heated-pot illustration compares conduction, convection, and radiation.

------------------------------------------------------------------------

# 4. Radiation Properties and Surface Treatments

## Conservation of Energy

> **Source: Slide 8**

### Reflectivity

Reflectivity, ρ, is the fraction of incident radiant energy reflected by a surface.

- Range: 0 to 1
- ρ = 1 means all incoming energy is reflected.
- ρ = 0 means no energy is reflected.

### Absorptivity

Absorptivity, α, is the fraction of incident radiant energy absorbed by a surface.

- Range: 0 to 1
- α = 1 means all incoming energy is absorbed.
- α = 0 means no energy is absorbed.

### Transmissivity

Transmissivity, τ, is the fraction of incident radiant energy that passes through a material.

- Range: 0 to 1
- τ = 1 means all energy is transmitted.
- τ = 0 means none is transmitted.

### Emissivity

Emissivity, ε, measures how effectively a surface emits thermal radiation compared with an ideal blackbody.

- Range: 0 to 1
- ε = 1 means the surface behaves like a perfect blackbody.

For a given wavelength and direction:

```math
\alpha = \epsilon
```

Kirchhoff's Law of Thermal Radiation.

### Conservation Relationship

```math
\rho + \alpha + \tau = 1
```

The lecture notes that transmissivity is typically assumed to be 0.

**Figure description:** Incident radiation reaches a surface and is divided into reflected, absorbed, and transmitted energy. Absorbed energy can accumulate as heat and be re-radiated.

------------------------------------------------------------------------

## Surface Coatings and Treatments

> **Source: Slide 9**

Because spacecraft thermal balance in space is dominated by radiation, the optical properties of external surfaces are critical drivers of temperature control.

Spacecraft use:

- Thermal-control films and paints
  - White paints
  - OSRs
  - Kapton
- Second-surface mirrors
- Multi-Layer Insulation
- Anodized surfaces
- Other chemical surface treatments

| Surface Property | Absorptivity α | Emissivity ε | Comments |
|---|---:|---:|---|
| Optical Solar Reflector | 0.07 | 0.80 | 8 mil Quartz mirrors |
| White Paint | 0.22 | 0.85 | S13G-LO |
| Black Paint | 0.97 | 0.84 | 3M Black Velvet |
| Aluminized Kapton | 0.38 | 0.67 | 1 mil |
| Metallic | 0.13 | 0.04 | Vapor Deposited Aluminum |
| MLI — white beta cloth cover | 0.45 | 0.04 | Estimate |
| MLI — aluminized beta cloth cover | 0.37 | 0.04 | Estimate |
| MLI — Tedlar reinforced cover | 0.30 | 0.04 | Estimate |
| MLI — Teflon-backed cover | 0.10 | 0.04 | Estimate |

------------------------------------------------------------------------

# 5. Thermal Power Balance

## Energy Conservation and Thermal Balance

> **Source: Slide 10**

### Equation 1

```math
Q_{\text{out}} = Q_{\text{in}}
```

Heat leaving the spacecraft:

```math
Q_{\text{out}} = Q_{\text{rad}} + Q_{\text{vent}}
```

where:

- **Qout** = total heat leaving the spacecraft
- **Qrad** = emitted radiation from the spacecraft
- **Qvent** = heat contained within matter that is vented/ejected, typically 0

Heat entering the spacecraft:

```math
Q_{\text{in}} = Q_s + Q_{rs} + Q_p + Q_d + Q_o
```

where:

- **Qin** = total heat entering the spacecraft
- **Qs** = direct input from the Sun
- **Qrs** = reflected solar flux, e.g. Sun → Earth → spacecraft
- **Qp** = infrared energy from planets, e.g. Earth
- **Qd** = electric power dissipated within the spacecraft
- **Qo** = input power from other system elements, e.g. arrays; assume 0 for the lecture homework

Lowercase `q` is heat flux across a boundary, typically W/m².

Uppercase `Q` is total heat/power transferred, measured in W.

```math
Q = Aq
```

------------------------------------------------------------------------

## Thermal Power-Balance Diagram

> **Source: Slide 11**

The diagram identifies:

- Direct solar radiation, Qs
- Reflected solar radiation, Qrs
- Planetary input, Qp
- Internal power
- Radiated heat, Qrad

**Figure description:** A cube-shaped spacecraft receives direct solar radiation from the Sun and reflected solar radiation from Earth. Earth also contributes an upward planetary thermal input. The spacecraft radiates heat outward to space.

------------------------------------------------------------------------

# 6. Radiated Emissions and Solar Flux

## Stefan-Boltzmann Law

> **Source: Slide 12**

### Equation 2

```math
Q_{\text{rad}} = A\epsilon\sigma T^4
```

where:

- **Qrad** = radiated heat, W
- **A** = surface area, m²
- **ε** = emissivity of the material; perfect blackbody = 1
- **σ** = Stefan-Boltzmann constant, W/(m²·K⁴)
- **T** = temperature of the object, K

## Direct Solar Flux

### Equation 3

```math
Q_s = A G_s \alpha
```

where:

- **Gs** = solar flux
- **α** = surface absorptivity, unitless

Assume at 1 AU:

```math
G_s = 1370\ \frac{W}{m^2}
```

## Reflected Solar Flux

### Equation 4

```math
Q_{rs} = A G_{rs}\alpha
```

where:

```math
G_{rs} = a K G_s \sin^2\rho
```

and:

- **a** = albedo; assume 0.3 for Earth, although this varies
- **K** = correction factor for reflected Earth energy
- **ρ** = angular radius of the planet, rad

```math
K = 0.665 + 0.521\rho - 0.203\rho^2
```

The term:

```math
\sin^2\rho
```

represents the view factor, ranging from 0 to 1, for how much available energy reaches the spacecraft.

```math
\rho = \arcsin\left(\frac{R_p}{r}\right)
```

where:

- **Rp** = radius of planet, km; assume 6,370 km for Earth
- **r** = orbit radius, km

## Infrared Energy from Earth

### Equation 5

```math
Q_p = A G_p \alpha
```

where:

```math
G_p = \epsilon_p \sigma T_p^4 \sin^2\rho
```

and:

- **εp** = emissivity of planet; for Earth assume 0.5
- **Tp** = temperature of planet; for Earth assume 300 K
- **α** = surface absorptivity

At Earth's IR wavelength, the lecture states:

```math
\epsilon_s = \alpha
```

------------------------------------------------------------------------

## Effective Area for Planetary View Factor

> **Source: Slide 13**

### Equation 6

Spacecraft altitude determines the planetary view factor.

At low altitude, the planet fills much of the spacecraft's 180-degree field of view. At a distant orbit, the planet fills only a small fraction.

The lecture uses a simple spacecraft cube:

- 1 zenith panel
- 4 side panels
- 1 nadir panel

### Nadir

```math
A_e = A
```

The surface receives all available energy from Earth, either IR or reflected light.

### Zenith

```math
A_e = A \times 0 = 0
```

The surface receives no energy from Earth.

### Side

```math
A_e = 0.5A(1-\cos\rho)
```

where:

- **0.5** represents that only half of the planet is in view
- **(1 − cos ρ)** represents the 90-degree rotation of ρ

**Figure description:** A simple cube spacecraft is shown above a planet with angular radius ρ drawn between the spacecraft and visible edges of the planet.

## Dissipated Power within the Spacecraft

### Equation 7

`Qd` is the total power dissipated onboard the spacecraft.

This:

- Includes heater power
- Excludes Telecom RF power, which is radiated from the spacecraft

The difference between DC input power and RF output power is primarily amplifier inefficiency and is converted to heat.

A simplified spacecraft model may neglect appendages such as:

- Arrays
- Deployed instruments
- Antennas

For a solar array, use the power dissipated within spacecraft electronics and do not include power/heat left on the array or the array's own thermal properties and temperatures.

If an instrument is on the end of a long boom, subtract power provided to that instrument across the boom/harness interface from spacecraft dissipated power if it is modeled separately.

------------------------------------------------------------------------

# 7. Thermal-Control Hardware

## Multi-Layer Insulation

> **Source: Slide 14**

The slide provides visual examples of Multi-Layer Insulation (MLI).

**Figure description:** A close-up shows the multiple thin layers within an MLI blanket. A spacecraft photograph shows large portions of the vehicle covered with gold-colored MLI.

------------------------------------------------------------------------

## Heat Pipes

> **Source: Slide 15**

- Constant-conduction heat pipes transfer heat in one direction.
- Loop heat pipes recirculate liquid/vapor.

The loop heat-pipe diagram identifies:

- Compensation chamber
- Cylindrical evaporator
- Vapor line
- Vapor-line temperature measurement
- Condenser
- Cold plate
- Liquid return line
- Liquid-line temperature measurement

**Figure description:** The loop heat pipe connects an evaporator and compensation chamber to a condenser/cold plate through vapor and liquid return lines.

------------------------------------------------------------------------

## Louvers

> **Source: Slide 16**

Louvers:

- Can provide approximately 5× reduction in heat transfer.
- Can be active or passive.
- Passive approaches use:
  - Bimetallic strips
  - Shape-memory materials

The slide states:

```text
Radiated Heat = f(blinds)
```

**Figure description:** Reflective "Venetian blinds" cover a radiator. The amount of heat radiated to space depends on blind position.

------------------------------------------------------------------------

## Heaters

> **Source: Slide 17**

Survival heaters often use mechanical thermostats for control to ensure that, independently of flight software, minimum temperatures are maintained.

**Figure description:** The slide shows a flexible electrical heater and heater elements mounted to spacecraft hardware.

------------------------------------------------------------------------

# 8. Thermal Modeling and Mission Example

## Thermal Modeling

> **Source: Slide 18**

The slide shows a spacecraft thermal model color-coded by IR emissivity.

The scale ranges from approximately 0 to greater than 0.87.

**Figure description:** Two spacecraft views show the bus, internal equipment, and solar arrays divided into modeled surfaces with different infrared-emissivity values.

------------------------------------------------------------------------

## Exo-C Mission Example

> **Source: Slide 19**

The lecture uses Exo-C as a thermal-design mission example.

The slide identifies:

- Science imager
- Imaging detector
- Optical layout of coronagraph
- Mechanical layout of coronagraph instrument
- Spacecraft bus
- Telescope
- Primary mirror
- Barrel assembly
- Solar panels
- Launch configuration

The Science Imager has a:

```text
41 milliarcsecond/pixel
```

plate scale to image the dark-hole region around the target star.

The Exo-C solar panels are configured so the barrel assembly receives the same solar thermal power at:

```text
+15°
```

and:

```text
−15°
```

relative to the Sun.

The results are intended to provide:

```text
10⁻¹⁰ contrast stability
```

for differential image-speckle subtraction.

**Figure description:** The slide combines the coronagraph optical and mechanical layouts with the spacecraft bus, primary-mirror and barrel temperature maps, solar-panel geometry, and launch configuration.

------------------------------------------------------------------------

## Telescope Heater Power Analysis

> **Source: Slide 20**

The Exo-C observatory thermal model includes:

- Spacecraft bus
- Telescope, including vibration-isolation system
- Instrument bench
- Flat solar panel that also serves as a sunshield

The spacecraft and instrument bench are modeled as constant-temperature boundary conditions.

The stability of the telescope is simulated over varying Sun angles.

The required heater power depends strongly on the set-point temperatures.

| Telescope Heater Location | Number of Heaters | Set Point (K) | Peak Power (W) |
|---|---:|---:|---:|
| Primary Support Structure | 3 | 200 | 118 |
| Lower Barrel | 18 | 190 | 63 |
| Upper Barrel | 11 | 170 | 56 |
| Barrel Scarf | 8 | 150 | 111 |
| Primary Mirror | 6 | 240 | 33 |
| Primary Mirror Bipods | 6 | 240 | 5 |
| Secondary Mirror | 2 | 240 | 1 |
| **Total** | **60** | — | **387** |
| **Total with 30% contingency** | — | — | **503** |

------------------------------------------------------------------------

# 9. Thermal Trade Study

> **Source: Slide 21**

Three solar-shield configurations are compared:

1. Passive outer barrel
2. Kepler-like MLI tent
3. Flat solar panel

| Criterion | Outer Barrel | MLI Tent | Flat Solar Panel |
|---|---|---|---|
| Mass | Poor | Good | Good |
| Fast recovery from thermal transient | Poor | Good | Good |
| Contrast stability at steady state | Good | Good | Good |
| Contrast stability over 30° roll and 45° pitch | Not analyzed | ~2–5 × 10⁻⁹ stability | >10⁻¹⁰ stability |

**Figure description:** The slide shows all three sunshield configurations above the trade table.

------------------------------------------------------------------------

# 10. Thermal-Vacuum Testing

## Thermal-Vacuum Facilities

> **Source: Slide 22**

The slide provides two TVAC examples:

- M2020 / Perseverance Rover in JPL TVAC
- ESA's Euclid Mission

**Figure description:** Mars 2020 hardware is suspended inside a large JPL thermal-vacuum chamber. Euclid is shown inside another thermal-vacuum facility.

------------------------------------------------------------------------

## DAXSS CubeSat Test Profile

> **Source: Slide 23**

The DAXSS CubeSat Thermal Vacuum Cycle Test Profile includes:

### Survival Conditions

Hot survival:

```text
+60 °C
```

Cold survival:

```text
−40 °C
```

### Operational Conditions

Hot operational:

```text
+35 °C
```

Cold operational:

```text
−20 °C
```

The plot includes eight hot and eight cold operational cycles.

Test activities include:

- DAXSS Power Off
- DAXSS Power On
- Power Cycle with Aliveness Test
- CPT
- LPT
- Mission Simulation during 3-hour dwells

Representative voltage values shown include:

- 7.7 V
- 7.0 V
- 8.4 V

The key identifies:

- Cycle #5 — X123 off during eclipse
- Cycle #6 — DAXSS off during eclipse

**Figure description:** Temperature is plotted through a hot survival cycle, cold survival cycle, and repeated operational hot/cold cycles while functional tests and mission simulations are performed.

------------------------------------------------------------------------

# 11. Thermal Design Process

> **Source: Slide 24**

## Review and Understand Design Information

- Mission Description and Concept of Operations
- System and Subsystem Requirements
  - Mission geometry
  - Payload temperature requirements
  - Subsystem temperature requirements

## Create a Preliminary Design

### Identify a Preliminary Architecture

Select target temperatures, for example:

```text
+20 °C / −20 °C
```

Consider:

- Hot bias
- Cold bias
- Cryogenic elements, approximately 3–120 K
- Operability
- Materials
- Coatings
- Radiators
- Heat pipes

### Create Back-of-the-Envelope Heat-Transfer Estimates

Perform preliminary sizing of:

- Radiators
- MLI
- Heat pipes
- Other thermal hardware

### Create Thermal Balance Model

Optimize with respect to:

- Robustness
- Fault scenarios
- Other mission considerations

### Create Component Mass List

Capture thermal-control hardware in the subsystem mass estimate.

## Review and Iterate with the Broader Team

Revisit options such as:

- Heat straps
- Heat switches
- Louvers
- Other thermal-control approaches

```text
Mission Description / ConOps
          |
          v
System + Subsystem Requirements
          |
          v
Mission Geometry + Temperature Requirements
          |
          v
Preliminary Thermal Architecture
          |
          v
Target Temperatures / Hot-Cold Bias
          |
          v
Materials + Coatings + Radiators + Heat Pipes
          |
          v
Back-of-the-Envelope Heat Transfer
          |
          v
Preliminary Hardware Sizing
          |
          v
Thermal Balance Model
          |
          v
Robustness / Fault Scenario Review
          |
          v
Component Mass List
          |
          v
Broader Team Review
          |
          +------ Iterate ------+
```

------------------------------------------------------------------------

# Lecture Summary

> **Source: Slides 1–24**

The thermal subsystem provides appropriate thermal control throughout the spacecraft and keeps spacecraft elements within specified temperature limits.

The thermal architecture should:

- Maximize system operability.
- Allow spacecraft pointing without exceeding thermal limits.
- Minimize thermal constraints on power-system operability.
- Remain insensitive to environment and system characteristics.
- Remain insensitive to small design changes.
- Simplify testing.

The lecture emphasizes:

| Heat-Transfer Mechanism | Spacecraft Importance |
|---|---|
| Conduction | Typically dominates at component level |
| Radiation | Dominates at system level |
| Convection | Generally not applicable in vacuum / zero-g |

Radiation analysis uses:

- Reflectivity, ρ
- Absorptivity, α
- Transmissivity, τ
- Emissivity, ε

with:

```math
\rho + \alpha + \tau = 1
```

The overall thermal balance is:

```math
Q_{\text{out}} = Q_{\text{in}}
```

where:

```math
Q_{\text{out}} = Q_{\text{rad}} + Q_{\text{vent}}
```

and:

```math
Q_{\text{in}} = Q_s + Q_{rs} + Q_p + Q_d + Q_o
```

Core equations include the Stefan-Boltzmann Law:

```math
Q_{\text{rad}} = A\epsilon\sigma T^4
```

direct solar input:

```math
Q_s = A G_s\alpha
```

reflected solar input:

```math
Q_{rs} = A G_{rs}\alpha
```

planetary infrared input:

```math
Q_p = A G_p\alpha
```

planetary angular radius:

```math
\rho = \arcsin\left(\frac{R_p}{r}\right)
```

and side-panel effective area:

```math
A_e = 0.5A(1-\cos\rho)
```

Thermal-control hardware discussed includes:

- Surface coatings and treatments
- Multi-Layer Insulation
- Heat pipes
- Louvers
- Heaters
- Mechanical thermostats

The Exo-C example connects thermal design directly to payload performance and heater-power requirements. The thermal trade study compares an outer barrel, MLI tent, and flat solar panel. TVAC testing verifies spacecraft behavior through hot, cold, operating, and survival conditions.

The lecture's design process is iterative:

```text
Requirements
     |
     v
Thermal Architecture
     |
     v
Target Temperatures
     |
     v
Materials / Coatings / Hardware
     |
     v
Heat-Transfer Estimates
     |
     v
Thermal Balance Model
     |
     v
Hardware Sizing
     |
     v
TVAC / Verification
     |
     v
Broader Team Review
     |
     +------ Iterate ------+
```
