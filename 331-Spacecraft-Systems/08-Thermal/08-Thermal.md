# Thermal

**Course:** ASTE-331 — Spacecraft Systems Engineering  
**Lecture:** 08 — Thermal  
**Instructors:** Jim Chase, Danielle Marsh    
**Source:** `331_08_Thermal_20251121.pdf`

---

## Lecture Overview

This lecture introduces spacecraft thermal control: why spacecraft components must remain within specified operating and survival temperature limits, how the space environment drives thermal behavior, how radiation and conduction govern spacecraft heat transfer, and how passive and active thermal-control hardware is selected.

The lecture develops the spacecraft thermal power balance, defines the optical properties used in radiation analysis, introduces equations for emitted radiation, direct solar flux, reflected solar flux, planetary infrared heating, and planetary view factor, and then applies those concepts to thermal hardware, modeling, trade studies, thermal-vacuum testing, and the overall thermal design process.

---

## Table of Contents

- [1. Thermal Subsystem Overview](#1-thermal-subsystem-overview)
- [2. Thermal Control System Scope](#2-thermal-control-system-scope)
- [3. Thermal Architecture Objectives](#3-thermal-architecture-objectives)
- [4. Typical Component Temperature Requirements](#4-typical-component-temperature-requirements)
- [5. Thermal Control Environments](#5-thermal-control-environments)
- [6. Thermal Design Practices](#6-thermal-design-practices)
- [7. Radiation Surface Properties and Conservation of Energy](#7-radiation-surface-properties-and-conservation-of-energy)
- [8. Surface Coatings and Treatments](#8-surface-coatings-and-treatments)
- [9. Thermal Power Balance](#9-thermal-power-balance)
- [10. Radiated Emissions and Solar Flux](#10-radiated-emissions-and-solar-flux)
- [11. Planetary View Factor and Effective Area](#11-planetary-view-factor-and-effective-area)
- [12. Dissipated Spacecraft Power](#12-dissipated-spacecraft-power)
- [13. Multi-Layer Insulation](#13-multi-layer-insulation)
- [14. Heat Pipes](#14-heat-pipes)
- [15. Louvers](#15-louvers)
- [16. Heaters and Thermostats](#16-heaters-and-thermostats)
- [17. Thermal Modeling](#17-thermal-modeling)
- [18. Mission Example](#18-mission-example)
- [19. Thermal Trade Study](#19-thermal-trade-study)
- [20. Thermal-Vacuum Testing](#20-thermal-vacuum-testing)
- [21. Thermal Design Process](#21-thermal-design-process)
- [22. Lecture Summary](#22-lecture-summary)

---

# 1. Thermal Subsystem Overview

> **Source: Slide 2**

### Function

The thermal subsystem provides appropriate thermal control throughout the spacecraft.

The primary driver is the overall spacecraft thermal model, which must account for the temperatures and thermal behavior of:

- Avionics
  - Usually near room temperature
- Instruments
  - Can include very cold focal-plane arrays
  - Can include hot sample-analysis hardware
- Batteries
- Mechanisms
- Propulsion hardware

All components must remain within their qualification temperature limits.

---

### GRAIL Example

The GRAIL thermal subsystem includes:

- Paint
- Thermal-control films
- Multi-layer insulation
- Instrument thermal mass plate
- Heaters
- Thermostats
- Temperature sensors
- Other thermal-control hardware

Total thermal subsystem mass: ~10 kg

---

### Common Components

Surface Coatings and Treatments
- Examples:
    - Films
    - Paints
    - Multi-layer insulation

Conductors and Insulators
- Used to control the path and magnitude of heat transfer.

Heat-Transfer Regulators
- Examples:
    - Heat pipes
    - Louvers
    - Phase-change devices
    - Heat switches

---

### Key Trades and Analyses

- Active vs. passive thermal control
- Thermal analysis
- Radiator design
- Radiator location
- Thermal margins

### Key Parameters

- Mass
- Power
- Cost
- Updated spacecraft attitude profile

The spacecraft attitude profile matters because orientation changes:

- Solar exposure
- Planetary view
- Radiator view to deep space
- Thermal balance

---

# 2. Thermal Control System Scope

> **Source: Slide 3**

The fundamental thermal-control objective is:

**Maintain spacecraft system elements within specified temperature limits.**

Temperature limits are selected to support the physical and operational requirements of spacecraft hardware.

## Chemistry

Examples:

- Batteries
- Thrusters

Chemical performance and lifetime depend strongly on temperature.

## Phase and Viscosity

Examples:

- Propellants
- Lubricants

Temperature affects whether a material remains in the required phase and whether its viscosity remains acceptable.

## Thermal Stress

Examples:

- Electronics
- Precision alignments

Temperature gradients and temperature changes can create:

- Expansion
- Contraction
- Distortion
- Stress

## Mechanical Properties

Material strength, stiffness, dimensions, and other mechanical characteristics can change with temperature.

## Other Temperature-Sensitive Hardware

Examples include low-temperature sensors that intentionally operate far below normal spacecraft electronics temperatures.

---

# 3. Thermal Architecture Objectives

> **Source: Slide 4**

Thermal architecture has two major objectives:

1. Maximize system operability
2. Provide robustness

---

## Maximize System Operability

### Pointing

The thermal system should allow the spacecraft to point as freely as possible without exceeding thermal limits.

A poorly designed thermal architecture can create attitude constraints such as:

- Maximum Sun exposure
- Minimum Sun exposure
- Radiator pointing requirements
- Limited observation geometry

### Power

Thermal constraints should have minimal impact on power-system operability.

Examples include the relationship between:

- Battery temperature and battery performance
- Solar-array temperature and array performance

---

## Provide Robustness

A robust thermal design should be relatively insensitive to:

- Environmental variations
- System characteristics
- Small design changes

Robust thermal architectures can also simplify testing.

The spacecraft image on the slide illustrates the large external thermal-control surfaces and blankets that can dominate the visible configuration of a spacecraft.

---

# 4. Typical Component Temperature Requirements

> **Source: Slide 5**

Different spacecraft components can require dramatically different thermal environments.

| Component / Subsystem | Operating Temperature | Survival Temperature |
|---|---:|---:|
| Digital electronics — modern avionics, rad-hard CPUs, FPGAs | -20 to +70 °C | -40 to +85 °C |
| Analog electronics | -20 to +55 °C | -40 to +85 °C |
| Batteries — modern Li-ion spacecraft cells | 0 to +30 °C | -20 to +50 °C |
| IR detectors — HgCdTe, bolometers, cooled arrays | -253 to -173 °C (20–100 K) | -253 to +30 °C |
| Solid-state particle detectors — Si PIN, CdTe | -40 to +20 °C | -50 to +40 °C |
| Momentum / reaction wheels / motors | -20 to +60 °C | -30 to +70 °C |
| Solar panels — modern triple-junction GaAs | -150 to +135 °C | -180 to +150 °C |

## Operating vs. Survival Limits

**Operating limits** define the temperature range in which hardware is expected to perform its intended function.

**Survival limits** define the broader temperature range the hardware can tolerate without permanent damage when it is not necessarily operating.

A spacecraft thermal design must therefore consider both:

- Normal operating modes
- Non-operating or fault conditions

---

# 5. Thermal Control Environments

> **Source: Slide 6**

The spacecraft thermal environment changes significantly throughout the mission.

| Mission Phase | Time Period | Thermal / Environmental Considerations |
|---|---|---|
| Ground Operations | Months to years before launch | Cleanroom environment, approximately 18–23 °C, controlled humidity of approximately 30–50%, transportation vibration/shock, EMI/EMC testing, TVAC testing, integration and test facilities |
| Launch | ~10–15 min ascent + ~5–20 min coast | High acoustic loads, intense vibration, pyro-shocks, fairing thermal gradients, plume heating, rapidly changing g-loads, launch-vehicle RF environment |
| Transfer Orbit | Hours to weeks | Sun/Earth/Moon thermal cycles, albedo variation, eclipses, outgassing, contamination, changing attitudes, propulsion burns, potentially increased radiation |
| Final Orbit / Operational Phase | Years to decades | Stable or cyclic thermal environment, solar cycles, radiation, seasonal beta angles, changing attitudes, payload-driven modes, station keeping, end-of-life degradation |

The thermal system therefore cannot be designed around only one steady-state condition.

It must support multiple mission phases and combinations of:

- External heat input
- Internal dissipation
- Attitude
- Eclipse
- Operational mode
- Hardware aging

---

# 6. Thermal Design Practices

> **Source: Slide 7**

Spacecraft thermal design is based on the dominant heat-transfer mechanisms in the space environment.

## Conduction

Conduction typically dominates at the **component level**.

Examples include heat transfer:

- From electronics into a mounting panel
- Through a thermal strap
- Through structural interfaces
- From a battery into its enclosure

## Radiation

Radiation dominates at the **spacecraft system level**.

Spacecraft exchange thermal radiation with:

- The Sun
- Planets
- Deep space
- Other spacecraft surfaces

## Convection

Convection is generally not applicable in normal spacecraft operation because of:

- Vacuum
- Zero-g / microgravity environment

The cooking-pot diagram on the slide contrasts conduction, convection, and radiation to show the three familiar heat-transfer modes, while emphasizing that spacecraft in vacuum rely primarily on conduction and radiation.

---

## Good Thermal Design Practices

### Co-Locate Similar Components

Place components with similar thermal requirements near each other when practical.

This can simplify:

- Heater design
- Radiator design
- Thermal isolation
- Temperature control

### Place High-Power Devices Near Exterior Radiators

High-power devices produce significant waste heat.

Short conductive paths to radiators reduce:

- Thermal gradients
- Required conductor mass
- Thermal resistance

### Point Radiators Toward Deep Space

Deep space provides the cold radiative sink used to reject spacecraft heat.

### Limit Radiator View Factors

A radiator should have minimal view of warm spacecraft surfaces or planetary bodies.

A **view factor** describes the fraction of another surface or object within the radiator's field of view.

### Cold Biasing

Cold biasing intentionally designs a spacecraft region to naturally operate below its desired control temperature.

Heaters then add heat to maintain the desired temperature.

This provides positive thermal control and design margin.

---

# 7. Radiation Surface Properties and Conservation of Energy

> **Source: Slide 8**

Several dimensionless optical properties describe what happens when radiation reaches a surface.

## Reflectivity

Reflectivity, represented by `ρ`, is the fraction of incident radiant energy reflected by a surface.

Range:

```math
0 \le \rho \le 1
```

If:

```math
\rho = 1
```

all incoming energy is reflected.

If:

```math
\rho = 0
```

none of the incoming energy is reflected.

---

## Absorptivity

Absorptivity, represented by `α`, is the fraction of incident radiant energy absorbed by the surface.

Range:

```math
0 \le \alpha \le 1
```

If:

```math
\alpha = 1
```

all incoming energy is absorbed.

If:

```math
\alpha = 0
```

none is absorbed.

---

## Transmissivity

Transmissivity, represented by `τ`, is the fraction of incident energy that passes through a material.

Range:

```math
0 \le \tau \le 1
```

If:

```math
\tau = 1
```

all incident energy passes through.

If:

```math
\tau = 0
```

none passes through.

For many spacecraft thermal calculations, transmissivity is assumed to be zero.

---

## Conservation of Incident Radiation

The incident radiation must be:

- Reflected
- Absorbed
- Transmitted

Therefore:

```math
\rho + \alpha + \tau = 1
```

If transmissivity is negligible:

```math
\tau \approx 0
```

then:

```math
\rho + \alpha \approx 1
```

---

## Emissivity

Emissivity, represented by `ε`, measures how effectively a surface emits thermal radiation relative to an ideal blackbody.

Range:

```math
0 \le \epsilon \le 1
```

A perfect blackbody has:

```math
\epsilon = 1
```

For a given wavelength and direction, Kirchhoff's Law of Thermal Radiation gives:

```math
\alpha = \epsilon
```

The slide's radiation diagram shows incident shortwave radiation striking a surface, with portions reflected, transmitted, and absorbed. Absorbed energy raises the material temperature and can later be re-radiated as longer-wavelength thermal radiation.

---

# 8. Surface Coatings and Treatments

> **Source: Slide 9**

Because spacecraft thermal balance is dominated by radiation, the optical properties of external surfaces are critical to temperature control.

Spacecraft use coatings and surface treatments to control:

- Absorptivity
- Emissivity
- Reflectivity

Common options include:

- Thermal-control films
- White paints
- Optical Solar Reflectors
- Kapton
- Second-surface mirrors
- Multi-Layer Insulation
- Anodized surfaces
- Chemical surface treatments

---

## Representative Surface Properties

| Surface | Absorptivity | Emissivity | Notes |
|---|---:|---:|---|
| Optical Solar Reflector | 0.07 | 0.80 | 8 mil quartz mirrors |
| White Paint | 0.22 | 0.85 | S13G-LO |
| Black Paint | 0.97 | 0.84 | 3M Black Velvet |
| Aluminized Kapton | 0.38 | 0.67 | 1 mil |
| Metallic | 0.13 | 0.04 | Vapor-deposited aluminum |
| MLI — white beta cloth cover | 0.45 | 0.04 | Representative estimate |
| MLI — aluminized beta cloth cover | 0.37 | 0.04 | Representative estimate |
| MLI — Tedlar reinforced cover | 0.30 | 0.04 | Representative estimate |
| MLI — Teflon-backed cover | 0.10 | 0.04 | Representative estimate |

These values illustrate why material color alone does not fully determine thermal behavior.

A useful thermal-control surface may combine:

- Low solar absorptivity
- High infrared emissivity

so that it absorbs relatively little solar energy while efficiently radiating spacecraft heat.

---

# 9. Thermal Power Balance

> **Source: Slides 10–11**

The spacecraft thermal model begins with conservation of energy.

At thermal equilibrium:

```math
Q_{\text{out}} = Q_{\text{in}}
```

Heat leaving the spacecraft is:

```math
Q_{\text{out}}
=
Q_{\text{rad}}
+
Q_{\text{vent}}
```

where:

- `Qout` = total heat leaving the spacecraft
- `Qrad` = thermal radiation emitted by the spacecraft
- `Qvent` = heat carried away by vented or ejected matter

For the simplified model:

```math
Q_{\text{vent}} \approx 0
```

---

## Heat Entering the Spacecraft

```math
Q_{\text{in}}
=
Q_s
+
Q_{rs}
+
Q_p
+
Q_d
+
Q_o
```

where:

- `Qs` = direct solar input
- `Qrs` = reflected solar input
- `Qp` = planetary infrared input
- `Qd` = electrical power dissipated within the spacecraft
- `Qo` = heat/power entering from other system elements

For the homework model, the lecture states:

```math
Q_o = 0
```

---

## Heat Flux vs. Total Heat

Lowercase `q` generally represents heat flux across a boundary.

Units:

```math
\frac{W}{m^2}
```

Uppercase `Q` represents total heat/power transfer.

Units:

```text
W
```

They are related by:

```math
Q = Aq
```

where `A` is surface area.

---

## Thermal Balance Diagram

The slide's spacecraft diagram identifies the principal thermal terms:

```text
                  Qrad
                   ↑
                   |
Sun ── Qs ──> Spacecraft
              ↑       ↖
              |        \
             Qp        Qrs
              |          \
            Planet ← Solar Radiation

Internal spacecraft dissipation contributes Qd.
```

The spacecraft reaches a thermal condition determined by the balance of these incoming and outgoing terms.

---

# 10. Radiated Emissions and Solar Flux

> **Source: Slide 12**

## Stefan-Boltzmann Law

Thermal radiation emitted by a spacecraft surface is:

```math
Q_{\text{rad}}
=
A\epsilon\sigma T^4
```

where:

- `Qrad` = radiated heat in W
- `A` = surface area in m²
- `ε` = emissivity
- `σ` = Stefan-Boltzmann constant
- `T` = absolute temperature in K

The fourth-power temperature dependence means radiated heat changes rapidly with temperature.

---

## Direct Solar Flux

Direct absorbed solar power is:

```math
Q_s
=
A G_s \alpha
```

where:

- `A` = illuminated surface area
- `Gs` = solar flux
- `α` = solar absorptivity

At approximately 1 AU, the lecture assumes:

```math
G_s \approx 1370\ \frac{W}{m^2}
```

---

## Reflected Solar Flux

Reflected solar radiation from a planet contributes:

```math
Q_{rs}
=
A G_{rs}\alpha
```

The reflected solar flux is:

```math
G_{rs}
=
a K G_s \sin^2\rho
```

where:

- `a` = planetary albedo
- `K` = correction factor for reflected planetary energy
- `Gs` = direct solar flux
- `ρ` = angular radius of the planet

For Earth, the lecture uses approximately:

```math
a \approx 0.3
```

The correction factor is:

```math
K
=
0.665
+
0.521\rho
-
0.203\rho^2
```

The factor:

```math
\sin^2\rho
```

represents the planetary view factor and ranges from 0 to 1.

The angular radius is:

```math
\rho
=
\arcsin\left(\frac{R_p}{r}\right)
```

where:

- `Rp` = radius of the planet
- `r` = spacecraft distance from the planet center

For Earth, the lecture uses:

```math
R_p \approx 6370\ km
```

---

## Infrared Energy from a Planet

Planetary infrared heating is:

```math
Q_p
=
A G_p \alpha
```

where planetary IR flux is modeled as:

```math
G_p
=
\epsilon_p
\sigma
T_p^4
\sin^2\rho
```

where:

- `εp` = emissivity of the planet
- `Tp` = planetary temperature
- `ρ` = angular radius / view-factor term

For the lecture's Earth assumptions:

```math
\epsilon_p \approx 0.5
```

and:

```math
T_p \approx 300\ K
```

At Earth's infrared wavelength, the spacecraft surface absorptivity can be approximated using its emissivity:

```math
\alpha \approx \epsilon_s
```

---

# 11. Planetary View Factor and Effective Area

> **Source: Slide 13**

The amount of planetary energy reaching a spacecraft depends strongly on altitude.

At low altitude:

- The planet fills a large portion of the spacecraft's field of view.
- Planetary infrared and reflected solar heating can be significant.

At large distance:

- The planet occupies a much smaller fraction of the field of view.
- Planetary heating decreases.

The angular radius `ρ` is used to characterize this geometry.

---

## Effective Area

The effective area depends on how a spacecraft surface is oriented relative to the planet.

The lecture uses a simple spacecraft cube with:

- One zenith panel
- Four side panels
- One nadir panel

### Nadir Surface

A nadir-facing surface directly faces the planet.

```math
A_e = A
```

It receives the full modeled planetary energy available to that surface.

### Zenith Surface

A zenith-facing surface points away from the planet.

```math
A_e = 0
```

### Side Surface

For a side panel:

```math
A_e
=
0.5A(1-\cos\rho)
```

The factor `0.5` represents the geometry in which only half of the planet is visible from the side-facing surface.

The factor:

```math
1-\cos\rho
```

accounts for the angular extent of the planet.

Each spacecraft surface can therefore have a different effective area for:

- Reflected solar input
- Planetary infrared input

---

# 12. Dissipated Spacecraft Power

> **Source: Slide 13**

`Qd` is the total electrical power dissipated onboard the spacecraft as heat.

Most electrical power eventually becomes thermal energy inside the spacecraft.

This includes:

- Electronics dissipation
- Heater power

The lecture excludes telecom RF power that is actually radiated away from the spacecraft.

For an RF amplifier:

```text
DC input power - transmitted RF power
```

is primarily dissipated as amplifier inefficiency and therefore becomes spacecraft heat.

---

## Simplified Spacecraft Model

For preliminary thermal analysis, appendages can be neglected.

Examples:

- Solar arrays
- Deployed instruments
- Antennas

A solar array may deliver electrical power to the spacecraft, but the simplified spacecraft thermal model uses the power eventually dissipated in the spacecraft electronics rather than the array's own thermal state.

Similarly, if an instrument is located at the end of a long boom, power delivered across the boom/harness interface may be subtracted from the main spacecraft dissipated-power term when the instrument is thermally modeled separately.

---

# 13. Multi-Layer Insulation

> **Source: Slide 14**

Multi-Layer Insulation is one of the most recognizable spacecraft thermal-control technologies.

MLI consists of multiple thin reflective layers separated to reduce radiative heat transfer.

The slide shows:

- A close-up of the layered blanket construction
- A spacecraft covered extensively in gold-colored thermal blankets

MLI is used to reduce radiative exchange between the spacecraft and its environment.

Typical purposes include:

- Reduce heat loss from warm spacecraft regions
- Reduce absorbed environmental heat
- Thermally isolate spacecraft surfaces
- Reduce sensitivity to changing external conditions

The gold appearance commonly associated with spacecraft is often produced by thin-film blanket materials rather than solid metallic spacecraft structure.

---

# 14. Heat Pipes

> **Source: Slide 15**

Heat pipes move thermal energy from one location to another.

## Constant-Conductance Heat Pipes

Transfer heat primarily in one direction from a hot region to a colder rejection region.

## Loop Heat Pipes

Loop heat pipes recirculate liquid and vapor.

The diagram on the slide identifies:

- Cylindrical evaporator
- Compensation chamber
- Vapor line
- Condenser
- Cold plate
- Liquid return line

A simplified operating cycle is:

```text
Heat enters evaporator
↓
Working fluid evaporates
↓
Vapor travels toward condenser
↓
Heat is rejected
↓
Vapor condenses to liquid
↓
Liquid returns to evaporator
```

Heat pipes allow thermal energy to be moved efficiently without requiring a conventional mechanically pumped fluid loop.

---

# 15. Louvers

> **Source: Slide 16**

Thermal louvers regulate radiated heat using reflective blinds over a radiator.

The lecture states that louvers can provide approximately:

```text
5× reduction in heat transfer
```

depending on louver position.

Conceptually:

```text
Spacecraft → Radiator → Louvers → Space
```

Radiated heat becomes a function of the blind position.

Louvers can be:

- Active
- Passive

## Passive Louvers

Passive systems can use:

- Bimetallic strips
- Shape-memory materials

Temperature changes mechanically alter the louver position.

When heat rejection should be reduced, louvers cover more of the radiator.

When more heat rejection is needed, the louvers open to expose the radiator more directly to space.

---

# 16. Heaters and Thermostats

> **Source: Slide 17**

Electrical heaters provide active thermal control.

The slide shows flexible heater elements and heaters mounted to spacecraft hardware.

A major application is **survival heating**.

Survival heaters often use mechanical thermostats so that minimum temperatures can be maintained independently of flight software.

This provides fault tolerance.

A simplified control loop is:

```text
Temperature decreases
↓
Mechanical thermostat closes
↓
Heater receives power
↓
Hardware warms
↓
Upper thermostat threshold reached
↓
Heater turns off
```

This is especially important when the spacecraft computer:

- Is powered off
- Is in safe mode
- Has experienced a software fault

---

# 17. Thermal Modeling

> **Source: Slide 18**

Thermal models divide the spacecraft into surfaces, components, and nodes with assigned thermal properties.

The slide shows a detailed spacecraft thermal model with surfaces color-coded by infrared emissivity.

A thermal model can include:

- Spacecraft geometry
- Surface optical properties
- Conductive connections
- Internal power dissipation
- Solar input
- Planetary albedo
- Planetary infrared radiation
- Radiative view factors
- Heaters
- Radiators
- Thermal-control coatings

The purpose is to predict component and structural temperatures for mission conditions before flight.

Thermal modeling supports:

- Hot-case analysis
- Cold-case analysis
- Radiator sizing
- Heater sizing
- Material/coating selection
- Operational constraints
- TVAC test planning
- Model correlation after testing

---

# 18. Mission Example

> **Source: Slides 19–20**

The lecture uses the Exo-C observatory concept as a thermal-design example.

The system includes:

- Coronagraph instrument
- Imaging detector
- Optical system
- Spacecraft bus
- Telescope
- Primary mirror
- Barrel assembly
- Solar shielding
- Launch configuration

The thermal model evaluates temperature distributions throughout the observatory.

---

## Solar-Shield Geometry

The solar panels are configured so the barrel assembly receives approximately the same solar thermal power at spacecraft attitudes of:

```text
+15°
```

and:

```text
-15°
```

relative to the Sun.

The resulting thermal stability is intended to provide approximately:

```text
10^{-10}
```

contrast stability for differential image-speckle subtraction.

This demonstrates how thermal design can directly support science performance.

---

## Telescope Heater Power

> **Source: Slide 20**

The required heater power depends strongly on the selected temperature set points.

| Telescope Heater Location | Number of Heaters | Set Point | Peak Power |
|---|---:|---:|---:|
| Primary Support Structure | 3 | 200 K | 118 W |
| Lower Barrel | 18 | 190 K | 63 W |
| Upper Barrel | 11 | 170 K | 56 W |
| Barrel Scarf | 8 | 150 K | 111 W |
| Primary Mirror | 6 | 240 K | 33 W |
| Primary Mirror Bipods | 6 | 240 K | 5 W |
| Secondary Mirror | 2 | 240 K | 1 W |
| **Total** | **60** | — | **387 W** |
| **Total with 30% contingency** | — | — | **503 W** |

The table illustrates a major thermal-power coupling:

**Temperature set points directly affect heater power and therefore spacecraft power-system sizing.**

The Exo-C thermal model includes:

- Spacecraft bus
- Telescope
- Vibration-isolation system
- Instrument bench
- Flat solar panel acting as a sunshield

The spacecraft and instrument bench are modeled as constant-temperature boundary conditions while telescope stability is evaluated across changing Sun angles.

---

# 19. Thermal Trade Study

> **Source: Slide 21**

The lecture compares three solar-shield configurations:

1. Outer barrel
2. MLI tent
3. Flat solar panel

## Trade Results

| Criterion | Outer Barrel | MLI Tent | Flat Solar Panel |
|---|---|---|---|
| Mass | Poor | Good | Good |
| Fast recovery from thermal transient | Poor | Good | Good |
| Contrast stability at steady state | Good | Good | Good |
| Contrast stability over 30° roll and 45° pitch | Not analyzed | ~2–5 × 10^-9 stability | >10^-10 stability |

The flat solar-panel configuration provides the best stated contrast stability over the roll/pitch attitude range while also performing well in mass and transient recovery.

This trade demonstrates that thermal architecture can be driven by highly sensitive payload-performance requirements rather than simply component survival.

---

# 20. Thermal-Vacuum Testing

> **Source: Slides 22–23**

Thermal-vacuum testing reproduces two defining features of the space environment:

- Vacuum
- Temperature extremes

The lecture shows:

- Mars 2020 / Perseverance hardware in JPL TVAC
- ESA's Euclid mission in a thermal-vacuum facility

TVAC testing is used to:

- Verify thermal performance
- Verify survival
- Exercise hardware over temperature
- Validate thermal models
- Identify workmanship or integration problems
- Demonstrate mission-like operation

---

## Example Thermal-Vacuum Cycle

> **Source: Slide 23**

The DAXSS CubeSat example shows an initial survival cycle followed by repeated operational hot/cold cycles.

### Hot Survival

Approximately:

```text
+60 °C
```

### Cold Survival

Approximately:

```text
-40 °C
```

### Hot Operational Condition

Approximately:

```text
+35 °C
```

### Cold Operational Condition

Approximately:

```text
-20 °C
```

The profile includes eight operational cycles.

During the cycles, the test performs activities such as:

- Power cycling
- Aliveness testing
- CPT
- LPT
- Mission simulation
- Hot and cold dwells

The plot also shows different spacecraft voltage values during selected test points.

The key idea is that TVAC does not simply expose hardware to one hot and one cold temperature. A representative program can combine:

- Survival extremes
- Operational extremes
- Repeated cycles
- Dwell periods
- Functional testing
- Mission simulations

---

# 21. Thermal Design Process

> **Source: Slide 24**

The lecture closes with a preliminary thermal-design workflow.

## Review and Understand Design Information

Start with:

- Mission description
- Concept of Operations
- System requirements
- Subsystem requirements
- Mission geometry
- Payload temperature requirements
- Subsystem temperature requirements

---

## Create a Preliminary Design

### Identify Preliminary Architecture

Select target temperatures.

Examples:

```text
+20 °C
-20 °C
```

Determine whether the design should use:

- Hot bias
- Cold bias

### Consider Cryogenic Elements

Cryogenic elements may operate approximately in the range:

```text
3–120 K
```

Their operability must be considered separately from conventional spacecraft electronics.

### Select Thermal-Control Technologies

Consider:

- Materials
- Coatings
- Radiators
- Heat pipes

### Perform Back-of-the-Envelope Estimates

Estimate heat transfer before creating a high-fidelity model.

---

## Preliminary Hardware Sizing

Size components such as:

- Radiators
- MLI
- Heat pipes
- Heaters

---

## Create Thermal Balance Model

Develop the thermal model using:

- External heat inputs
- Internal dissipation
- Surface properties
- Geometry
- Heat rejection
- Mission attitude

Optimize for:

- Robustness
- Fault scenarios
- Operational flexibility

---

## Create Component Mass List

Thermal-control hardware contributes to spacecraft mass and must be captured in the subsystem mass estimate.

---

## Review and Iterate with the Broader Team

Thermal design is highly coupled to:

- Mechanical configuration
- Power
- Avionics
- Payload
- ACS
- Propulsion
- Mission operations

Revisit alternatives such as:

- Heat straps
- Heat switches
- Louvers
- Different radiator locations
- Different coatings
- Different temperature set points

The process is iterative rather than linear.

---

# 22. Lecture Summary

> **Source: Slides 1–24**

The thermal-control subsystem keeps spacecraft hardware within required operating and survival temperature limits.

Temperature control supports:

- Battery chemistry
- Propellant and lubricant phase/viscosity
- Electronics
- Precision alignment
- Mechanical properties
- Cryogenic sensors

The thermal architecture should:

- Maximize spacecraft operability
- Minimize pointing restrictions
- Minimize power-system constraints
- Remain robust to environmental variation
- Remain robust to small design changes

Spacecraft thermal design is dominated by:

- **Conduction at the component level**
- **Radiation at the spacecraft level**

Convection is generally negligible in the vacuum environment of space.

Radiative surface behavior is characterized by:

- Reflectivity
- Absorptivity
- Transmissivity
- Emissivity

with conservation of incident radiation:

```math
\rho + \alpha + \tau = 1
```

For opaque spacecraft surfaces:

```math
\tau \approx 0
```

and therefore:

```math
\rho + \alpha \approx 1
```

The spacecraft thermal power balance is:

```math
Q_{\text{out}}
=
Q_{\text{in}}
```

with:

```math
Q_{\text{out}}
=
Q_{\text{rad}}
+
Q_{\text{vent}}
```

and:

```math
Q_{\text{in}}
=
Q_s
+
Q_{rs}
+
Q_p
+
Q_d
+
Q_o
```

The emitted thermal radiation is governed by the Stefan-Boltzmann relationship:

```math
Q_{\text{rad}}
=
A\epsilon\sigma T^4
```

Direct absorbed solar energy is:

```math
Q_s
=
A G_s\alpha
```

Reflected planetary solar energy is:

```math
Q_{rs}
=
A G_{rs}\alpha
```

and planetary infrared heating is:

```math
Q_p
=
A G_p\alpha
```

Planetary heating depends on spacecraft altitude and orientation through the planetary view factor and effective area.

Thermal-control hardware includes:

- Surface coatings
- Optical Solar Reflectors
- Paint
- Kapton
- Multi-Layer Insulation
- Radiators
- Heat pipes
- Louvers
- Heat switches
- Heaters
- Thermostats
- Temperature sensors

Cold biasing intentionally creates a naturally cold design and uses heaters for positive temperature control and margin.

Thermal models predict spacecraft temperatures by combining:

- Geometry
- Surface properties
- Conductive paths
- Radiation
- Solar heating
- Planetary heating
- Internal dissipation
- Operational modes

The Exo-C example demonstrates the direct relationship between thermal stability and science performance. Solar-shield architecture and heater set points affect:

- Contrast stability
- Heater power
- Spacecraft power sizing
- Mass
- Operational attitude range

Thermal-vacuum testing validates the spacecraft across:

- Hot survival conditions
- Cold survival conditions
- Hot operational conditions
- Cold operational conditions
- Repeated thermal cycles
- Functional tests
- Mission simulations

The overall thermal design process is:

```text
Mission and System Requirements
↓
Temperature Requirements and Mission Geometry
↓
Preliminary Thermal Architecture
↓
Materials / Coatings / Radiators / Heat Pipes
↓
Back-of-the-Envelope Heat Transfer
↓
Preliminary Hardware Sizing
↓
Thermal Balance Model
↓
Robustness and Fault Optimization
↓
Mass Estimate
↓
Broader System Review
↓
Iterate
```

Thermal design is therefore a spacecraft-level systems-engineering activity. Spacecraft attitude, payload performance, electrical power, mechanical configuration, component lifetime, and mission operations all depend on maintaining a workable thermal balance.
