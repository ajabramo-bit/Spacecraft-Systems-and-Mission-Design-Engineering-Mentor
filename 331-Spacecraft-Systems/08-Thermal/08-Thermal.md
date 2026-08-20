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
- [11. Multi-Layer Insulation](#11-multi-layer-insulation)
- [12. Heat Pipes](#12-heat-pipes)
- [13. Louvers](#13-louvers)
- [14. Heaters and Thermostats](#14-heaters-and-thermostats)
- [15. Thermal Modeling](#15-thermal-modeling)
- [16. Mission Example](#16-mission-example)
- [17. Thermal Trade Study](#17-thermal-trade-study)
- [18. Thermal-Vacuum Testing](#18-thermal-vacuum-testing)
- [19. Thermal Design Process](#19-thermal-design-process)
- [20. Lecture Summary](#20-lecture-summary)

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
- Examples: Films, Paints, Multi-layer insulation

Conductors and Insulators
- Used to control the path and magnitude of heat transfer.

Heat-Transfer Regulators
- Examples: Heat pipes, Louvers, Phase-change devices, Heat switches

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

If: ρ = 1 all incoming energy is reflected.

If: ρ = 0 none of the incoming energy is reflected.

---

## Absorptivity

Absorptivity, represented by `α`, is the fraction of incident radiant energy absorbed by the surface.

Range:

```math
0 \le \alpha \le 1
```

If: α = 1 all incoming energy is absorbed.

If: α = 0 none is absorbed.

---

## Transmissivity

Transmissivity, represented by `τ`, is the fraction of incident energy that passes through a material.

Range:

```math
0 \le \tau \le 1
```

If: τ = 1 all incident energy passes through.

If: τ = 0 none passes through.

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

> **Source: Slides 12–13**

## Stefan-Boltzmann Law

The Stefan-Boltzmann Law describes the radiated emission from the spacecraft:

```math
Q_{\text{rad}}
=
A\epsilon\sigma T^4
```

where:

- **Qrad** = radiated heat, W
- **A** = surface area, m²
- **ε** = emissivity of the material, where a perfect blackbody has ε = 1
- **σ** = Stefan-Boltzmann constant, W/(m²·K⁴)
- **T** = temperature of the object, K

## Direct Solar Flux

Direct solar flux absorbed by the spacecraft is:

```math
Q_s
=
A G_s \alpha
```

where:

- **Qs** = direct solar heat absorbed by the spacecraft, W
- **A** = surface area, m²
- **Gs** = solar flux, W/m²
- **α** = surface absorptivity, unitless

For the lecture calculations, assume the solar flux at 1 AU is:

```math
G_s
=
1370\ \frac{W}{m^2}
```

## Reflected Solar Flux

Reflected solar flux is solar energy reflected from a planet and then received by the spacecraft.

The heat absorbed by the spacecraft is:

```math
Q_{rs}
=
A G_{rs}\alpha
```

where:

- **Qrs** = absorbed reflected solar heat, W
- **A** = effective spacecraft surface area, m²
- **Grs** = reflected solar flux, W/m²
- **α** = surface absorptivity, unitless

The reflected solar flux is:

```math
G_{rs}
=
a K G_s \sin^2\rho
```

where:

- **a** = albedo
  - Assume approximately 0.3 for Earth
  - This value can vary, for example due to cloud cover
- **K** = correction factor for reflected Earth energy
- **Gs** = direct solar flux
- **ρ** = angular radius of the planet, rad

The correction factor for reflected Earth energy is:

```math
K
=
0.665
+
0.521\rho
-
0.203\rho^2
```

The term:

```math
\sin^2\rho
```

represents the **view factor**, ranging from 0 to 1, for how much available energy reaches the spacecraft.

The angular radius of the planet is:

```math
\rho
=
\arcsin\left(\frac{R_p}{r}\right)
```

where:

- **ρ** = angular radius of the planet, rad
- **Rp** = radius of the planet, km
  - Assume 6,370 km for Earth
- **r** = orbit radius, km

## Infrared Energy from Earth

Infrared energy from Earth absorbed by the spacecraft is:

```math
Q_p
=
A G_p \alpha
```

where:

- **Qp** = infrared heat absorbed from the planet, W
- **A** = effective spacecraft surface area, m²
- **Gp** = planetary infrared flux, W/m²
- **α** = surface absorptivity

The planetary infrared flux is:

```math
G_p
=
\epsilon_p
\sigma
T_p^4
\sin^2\rho
```

where:

- **εp** = emissivity of the planet
  - For Earth, assume approximately 0.5
- **σ** = Stefan-Boltzmann constant
- **Tp** = temperature of the planet
  - For Earth, assume approximately 300 K
- **ρ** = angular radius of the planet

At Earth's infrared wavelength, surface absorptivity can be assumed to be the same as the spacecraft surface emissivity:

```math
\alpha
=
\epsilon_s
```

---

## Effective Area for Planetary View Factor

> **Source: Slide 13**

When a spacecraft is orbiting a planet, the altitude of the spacecraft determines the **planetary view factor**.

At low altitude, the planet fills much of the spacecraft's 180° field of view.

At a distant orbit, the planet fills only a small fraction of the field of view.

The view factor is measured using the angular radius of the planet, **ρ**, calculated as part of the reflected solar flux relationship above.

This geometry also produces an **effective area**, **Ae**, depending on the orientation of each spacecraft surface.

The lecture uses a simple spacecraft cube consisting of:

- 1 zenith panel
- 4 side panels
- 1 nadir panel

### Nadir Surface

The nadir surface faces toward Earth.

```math
A_e
=
A
```

The surface receives all of the available energy from Earth, either:

- infrared energy; or
- reflected solar energy.

### Zenith Surface

The zenith surface faces away from Earth.

```math
A_e
=
A\times0
=
0
```

The surface does not receive energy from Earth.

### Side Surface

The side surfaces are normal to Earth.

Their effective area is:

```math
A_e
=
0.5A(1-\cos\rho)
```

where:

- **0.5** represents that only half of the planet is in view
- **(1 − cos ρ)** represents the 90° rotation of **ρ**

Thus, depending on how each spacecraft surface is oriented, it will have a different effective area.

## Dissipated Power within the Spacecraft

> **Source: Slide 13**

The total power dissipated onboard the spacecraft is:

```math
Q_d
=
\text{Total power dissipated onboard the spacecraft}
```

This includes **heater power**.

It excludes **Telecom RF power**, because RF power is radiated from the spacecraft.

For RF systems, the difference between the **DC input power** and the **RF output power** is primarily power lost due to amplifier inefficiency.

That lost power is converted to heat.

Conceptually:

```text
Dissipated RF Amplifier Power
=
DC Input Power − RF Output Power
```

## Simplified Spacecraft Model

A simplified spacecraft model may neglect appendages such as:

- solar arrays;
- deployed instruments;
- antennas; and
- other externally mounted hardware.

For example, a solar array delivers electrical power to the spacecraft that is primarily dissipated within the electronics.

For the simplified model, use the **power dissipated within the spacecraft** and do **not** include:

1. power or heat remaining on the solar array; or
2. the thermal properties and temperatures of the solar array itself.

Similarly, if an instrument is located at the end of a long boom, subtract the power provided to that instrument across the boom/harness interface from the spacecraft dissipated-power term if the instrument is being treated separately.


# 13. Multi-Layer Insulation

> **Source: Slide 14**

Multi-Layer Insulation (MLI) is used extensively on spacecraft for thermal control.

The slide shows two examples:

- a close-up of the layered construction of an MLI blanket; and
- a spacecraft covered with MLI blankets.

The close-up shows that MLI consists of multiple thin layers of material rather than a single layer of insulation.

**Figure description:** The spacecraft shown on the slide is extensively covered with gold-colored MLI. The close-up image shows the multiple individual layers that make up the blanket.

---

# 14. Heat Pipes

> **Source: Slide 15**

Heat pipes are used to transfer heat through the spacecraft.

Two types are identified in the lecture:

- **Constant-conduction heat pipes** transfer heat in one direction.
- **Loop heat pipes** recirculate liquid and vapor.

## Loop Heat Pipe

The loop heat pipe shown on the slide contains:

- Compensation chamber
- Cylindrical evaporator
- Vapor line
- Vapor-line temperature measurement
- Condenser
- Cold plate
- Liquid return line
- Liquid-line temperature measurement

**Figure description:** The diagram shows the cylindrical evaporator and compensation chamber connected to a vapor line. The vapor line carries the working fluid toward the condenser mounted to the cold plate. A liquid return line then returns the fluid toward the evaporator, creating a circulating liquid/vapor loop.

---

# 15. Louvers

> **Source: Slide 16**

Louvers are used to control the amount of heat radiated from the spacecraft.

The lecture notes that louvers:

- can provide approximately a **5× reduction in heat transfer**; and
- can be either **active or passive**.

A passive approach can use:

- bimetallic strips; or
- shape-memory materials.

The amount of radiated heat depends on the position of the louver blinds.

```text
Radiated Heat = f(blinds)
```

**Figure description:** The slide compares the louver system to reflective "Venetian blinds" installed over a spacecraft radiator. Changing the position of the blinds changes how directly the radiator is exposed to space and therefore changes the amount of heat radiated away from the spacecraft.

---

# 16. Heaters

> **Source: Slide 17**

Heaters provide active thermal control for spacecraft hardware.

The lecture specifically notes that **survival heaters often use mechanical thermostats for control**.

This ensures that minimum temperatures can be maintained **independently of flight software**.

In other words, survival heating does not necessarily depend on the spacecraft computer being available to command the heater.

**Figure description:** The slide shows a flexible electrical heater element and examples of heater elements installed directly onto spacecraft hardware.

---

# 17. Thermal Modeling

> **Source: Slide 18**

Thermal modeling is used to represent the thermal behavior of the spacecraft.

The slide shows a spacecraft thermal model with surfaces represented using different thermal properties.

The displayed model is specifically color-coded according to **IR emissivity**.

**Figure description:** Two views of the spacecraft thermal model show the spacecraft body and solar arrays divided into individual modeled surfaces. A color scale labeled **IR Emissivity** ranges from values near 0 to values greater than approximately 0.87. Different spacecraft surfaces are assigned different emissivity values based on their materials and surface treatments.

---

# 18. Mission Example

> **Source: Slides 19–20**

The lecture uses the **Exo-C observatory** as a mission example.

The system shown on the slide includes:

- Coronagraph instrument
- Imaging detector
- Optical layout of the coronagraph
- Mechanical layout of the coronagraph instrument
- Spacecraft bus
- Telescope
- Primary mirror
- Barrel assembly
- Solar panels
- Launch configuration

## Solar-Panel Configuration

The Exo-C solar panels are configured so that the barrel assembly receives approximately the same solar thermal power at:

```text
+15° relative to the Sun
```

and:

```text
−15° relative to the Sun
```

The resulting thermal stability is intended to provide approximately:

```text
10⁻¹⁰ contrast stability
```

for differential image-speckle subtraction.

**Figure description:** The mission overview shows the spacecraft bus supporting a large telescope and coronagraph instrument. Thermal maps are shown for the approximately 1.4-m primary mirror and barrel assembly. A separate view shows the observatory folded inside the launch vehicle.

---

## Exo-C Thermal Model

> **Source: Slide 20**

The Exo-C observatory thermal model includes:

- Spacecraft bus
- Telescope
  - Including the vibration-isolation system
- Instrument bench
- Flat solar panel that also serves as a sunshield

The spacecraft and instrument bench are modeled as **constant-temperature boundary conditions**.

The thermal stability of the telescope is simulated over varying Sun angles.

**Figure description:** The thermal model shows the telescope structure mounted above the spacecraft bus with the large flat solar-panel/sunshield structure alongside it. Different colors represent the modeled thermal conditions across the structure.

---

## Telescope Heater Power Analysis

The required heater power depends strongly on the **set-point temperatures**.

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

The total peak heater power is:

```text
387 W
```

With a 30% contingency, the total becomes:

```text
503 W
```

---

# 19. Example Trade Study

> **Source: Slide 21**

The lecture compares three different solar-shield configurations:

1. **Outer barrel**
2. **MLI tent**
3. **Flat solar panel**

The configurations are compared using:

- Mass
- Fast recovery from thermal transients
- Contrast stability at steady state
- Contrast stability over 30° roll and 45° pitch

| Trade Criterion | Outer Barrel | MLI Tent | Flat Solar Panel |
|---|---|---|---|
| Mass | Poor | Good | Good |
| Fast recovery from thermal transient | Poor | Good | Good |
| Contrast stability at steady state | Good | Good | Good |
| Contrast stability over 30° roll and 45° pitch | Not analyzed | ~2–5 × 10⁻⁹ stability | >10⁻¹⁰ stability |

**Figure description:** The slide shows thermal models of all three sunshield configurations above the trade table: a passive outer barrel, a Kepler-like MLI tent, and a flat solar panel.

The flat solar-panel configuration performs well for:

- Mass
- Thermal-transient recovery
- Steady-state contrast stability
- Contrast stability over the specified roll and pitch range

---

# 20. Testing in Thermal-Vacuum

> **Source: Slide 22**

Thermal-vacuum testing, or **TVAC**, is used to test spacecraft in a vacuum chamber under controlled thermal conditions.

The slide shows two spacecraft examples undergoing TVAC testing:

- Mars 2020 / Perseverance rover hardware in JPL TVAC
- ESA's Euclid mission

**Figure description:** The Mars 2020 hardware is suspended inside a large JPL thermal-vacuum chamber. The Euclid spacecraft is shown positioned inside another large thermal-vacuum test facility.

---

# 21. Thermal-Vacuum Test Profile

> **Source: Slide 23**

The lecture provides a **DAXSS CubeSat Thermal Vacuum Cycle Test Profile** as an example.

The test begins with survival-temperature testing and then proceeds through repeated operational thermal cycles.

## Survival Temperatures

### Hot Survival Cycle

```text
+60 °C
```

### Cold Survival Cycle

```text
−40 °C
```

## Operational Temperatures

### Hot Operational Temperature

```text
+35 °C
```

### Cold Operational Temperature

```text
−20 °C
```

The example contains:

```text
8 hot operational cycles
```

and:

```text
8 cold operational cycles
```

## Activities During Testing

The test profile identifies several activities performed at different points during the thermal cycles:

- Power Cycle with Aliveness Test
- CPT
- LPT
- Mission Simulation

The spacecraft is operated at several voltage levels during the test, including values shown on the plot such as:

- 7.7 V
- 7.0 V
- 8.4 V

Mission simulations are performed during approximately:

```text
3-hour dwells
```

The plot also identifies specific eclipse-related test configurations.

**Figure description:** The test profile plots temperature against the sequence of thermal cycles. The spacecraft is first exposed to the hot and cold survival limits, then repeatedly cycled between approximately −20 °C and +35 °C while functional tests and mission simulations are performed.

---

# 22. Thermal Design Steps

> **Source: Slide 24**

The thermal design process begins by reviewing and understanding the available design information.

## Review and Understand Design Information

Review:

- Mission Description and Concept of Operations
- System requirements
- Subsystem requirements

Important inputs include:

- Mission geometry
- Payload temperature requirements
- Subsystem temperature requirements

## Create a Preliminary Design

Identify a preliminary thermal architecture.

### Select Target Temperatures

Representative target temperatures may include:

```text
+20 °C
```

or:

```text
−20 °C
```

Determine whether the design should use:

- Hot bias
- Cold bias

### Consider Cryogenic Elements

Cryogenic elements may operate approximately within:

```text
3–120 K
```

Their operability must be considered as part of the thermal architecture.

### Consider Thermal-Control Options

Consider:

- Materials
- Coatings
- Radiators
- Heat pipes

### Create Back-of-the-Envelope Heat-Transfer Estimates

Use preliminary calculations to estimate thermal behavior before completing the detailed thermal model.

## Preliminary Sizing

Perform preliminary sizing of:

- Radiators
- MLI
- Heat pipes
- Other thermal-control hardware

## Create Thermal Balance Model

Develop the spacecraft thermal-balance model.

Optimize the design with respect to:

- Robustness
- Fault scenarios
- Other mission-specific considerations

## Create Component Mass List

Include thermal-control components in the spacecraft mass estimate.

## Review and Iterate with the Broader Team

Thermal design is iterative.

Revisit other options as needed, including:

- Heat straps
- Heat switches
- Louvers
- Other thermal-control approaches

The overall process is:

```text
Review Mission and System Information
↓
Identify Preliminary Thermal Architecture
↓
Select Target Temperatures
↓
Consider Materials and Thermal-Control Hardware
↓
Create Back-of-the-Envelope Heat-Transfer Estimates
↓
Preliminary Hardware Sizing
↓
Create Thermal Balance Model
↓
Optimize for Robustness and Fault Scenarios
↓
Create Component Mass List
↓
Review and Iterate with Broader Team
```