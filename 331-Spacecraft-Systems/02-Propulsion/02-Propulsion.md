# ASTE-331a: Propulsion System

**Course:** ASTE-331a: Spacecraft Systems Engineering\
**Lecture:** Propulsion System\
**Date:** September 5, 2025\
**Instructors:** Jim Chase, Danielle Marsh\
**TAs:** Daejah Dandrich, Luis Diaz, Liam Kerrigan, Emerson Lo\
**Source:** `331_02_Propulsion_20250905.pdf`

> **Source distribution notice:** The presentation states that this
> content is protected and may not be shared, uploaded, or distributed.
> Confirm that you have permission before publishing this document
> publicly.

------------------------------------------------------------------------

## Lecture Overview

This lecture develops spacecraft propulsion from first principles
through subsystem architecture, requirements, schematics, sizing,
hardware selection, and integrated-system trades. It covers chemical,
solid, cold-gas, and electric propulsion; the rocket equation and ideal
gas law; propellant and pressurant sizing; valves, regulators, tanks,
thrusters, and propellant-management hardware; and real spacecraft
examples including OSIRIS-REx, Cassini, GPM, EO-1, Magellan, and
MESSENGER.

### Main Topics

1.  **Propulsion Fundamentals**
2.  **Propulsion Architecture & Requirements**
3.  **Propulsion Schematics**
4.  **Propulsion Sizing**
5.  **Propulsion Hardware**
6.  **Integrated Propulsion System**

------------------------------------------------------------------------

# Lecture Overview

## Propulsion System Purpose

*Source slide 1*

ASTE-331a: Spacecraft Systems Engineering (aka Propulsion or simply
Prop) Instructors: Jim Chase, Danielle Marsh TAs: Daejah Dandrich, Luis
Diaz, Liam Kerrigan, Emerson Lo September 5th, 2025 This content is
protected and may not be shared, uploaded, or distributed.

## Overview

*Source slide 2*

-   Function
-   Example: Small Solar Orbiter
    -   Provides thrust for both trajectory design maneuvers and

    -   12 0.7 N orbit & attitude control thrusters (often) attitude
        control

    -   8 0.04 N warm gas thrusters

    -   The primary driver is typically the trajectory and

    -   Warm gas generator corresponding $\Delta V$ budget.

    -   Propellant tank

    -   Across all subsystems, components are typically selected

    -   Misc. hardware as those that meet the minimum requirements with
        the

    -   Total = \~13 kg lowest mass, power, & cost.
-   Common Components
-   Key Trades & Analyses
    -   Chemical Propulsion (Mono/Biprop)
    -   Propulsion type (solid, mono/bi, electric)
-   Fuel tanks
    -   Thruster & fuel tank sizing
-   Thrusters (often different types tailored for small/large
    -   Heritage from prior systems maneuvers)
-   Integration/etc. hardware
-   Key Parameters
    -   Solid rocket motors (SRMs)
    -   Subsystem mass, power, cost
    -   Electric Propulsion Systems
    -   Thruster $I_{sp}$, locations, cant angles
    -   Propellant load & margins

## Basic Mechanics of Propulsion...

*Source slide 3*

Pressurant Pressurant Tanks... Manifold Pressurant

-   Propellant & Pressurant Tanks Propellant Gas (Ox or Fu)

-   Thrusters

-   Manifold

    -   Lines, filters, regulators, and flow control devices
    -   Valves (solenoid, check, pyro, etc.)
    -   Pressure transducers & temperature sensors Manifold

-   Redundancy and sizing Design

-   Iterate... ...Thrusters/Engines/Motors

## Common Propulsion Systems

*Source slide 4*

-   Cold Gas Thruster Systems

-   Solid Rocket Motors

    -   Use the expansion of a pressurized gas to generate thrust
    -   Use the combustion of a solid propellant to generate thrust
    -   Typically used for orbit maintenance and/or attitude control
    -   Typically used for ascent & orbit insertion
    -   Simpler system with lower mass & cost
    -   Simpler design (no moving parts)
    -   Lower specific impulse (45-73)
    -   High specific impulse (290-304)

-   Liquid Propulsion Systems

-   Electric Propulsion

    -   Use the liquid propellant(s) to generate thrust

    -   Uses electrical power to accelerate a propellant (via an
        electrical

    -   Used for orbit insertion, maintenance, & attitude control or
        magnetic field) to generate thrust

    -   Specific impulse varies with system type

    -   Typically used for interplanetary trajectories, orbit
        maintenance,

-   Monopropellant (200-235) & attitude control

-   Bipropellant (274-467)

    -   Increased complexity & cost

-   Dual-mode (varies, 200-467)

    -   Very high specific impulse (500-3,000)
    -   Complexity and cost vary

-   Traded with efficiency and mass

## OSIRIS-REx: Asteroid Sample Return Mission

*Source slide 5*

(Currently, on its way back to Earth.) OSIRIS-REx has a monoprop

### system with a total of 28 engines

-   4 high-thrust main engines
-   6 medium-thrust engines
-   16 attitude control thrusters (2/corner)
-   2 specialized low-thrust engines for the Touch-and-Go sample collect

## Cassini: Saturn Orbiter

*Source slide 6*

...it's actually not that bad ☺, and you'll be able to understand it as
part of this course.

------------------------------------------------------------------------

# 1. Propulsion Fundamentals

## Rocket Equation

*Source slide 7*

Ideal rocket equation

-   The Rocket Equation is used to calculate the propellant required to
    generate changes in velocity ($\Delta V$)

-   It applies to the acceleration of vehicles that produce thrust by
    expelling mass

    -   It is based on the conservation of momentum

-   Momentum (P1) at T1 = Momentum (P2) at T2

-   Momentum = mass x velocity; $$P = mv$$

    -   Using this principle, the rocket equation can be derived as: Or,
        equivalently...

> From www.physics.info/momentum-conservation

-   Where m 0 = initial mass, $m_f$ = final mass, $\Delta V$ = change in
    velocity, and $v_e$ = exhaust velocity

-   With thrusters, we typically characterize their efficiency using
    specific \### impulse (or $I_{sp}$), where

    -   Exhaust velocity ($v_e$) = $g_0$ $I_{sp}$ \> From Wikipedia,
        Rocket Equation

Messenger Trajectory (many $\Delta V$ events)

-   Relating back to spacecraft, we have...

    -   Initial mass ($m_0$) = spacecraft wet mass \### Other Common Use
        Cases

-   Launch & landings

    -   Final mass ($m_f$) = spacecraft dry mass

-   Inclination changes

    -   Propellant mass ($m_p$) = $m_0$ -- $m_f$

-   Orbit maintenance

    -   This assumes a total $\Delta V$ and propellant, but this can
        also be applied sequentially

-   Attitude control to individual burns, which is necessary if the dry
    mass changes (eg, a probe is

-   Momentum dumps released)

## The Ideal Gas Law (aka, general gas equation)

*Source slide 8*

-   In propulsion systems, gases are commonly used either directly as a
    Pressurized Liquid Propellant System means of generating thrust (eg,
    cold gas systems) or indirectly to

> From faa.gov, Rockets & Launch Vehicles

pressurize the liquid propellant.

-   To function within specifications, thrusters require gas/liquid
    propellant to enter the thruster at a specified pressure. Cold Gas
    System

-   The ideal gas law is used to determine how much \> From faa.gov,
    Rockets & Launch Vehicles

pressurant & volume is required.

-   The equation provides the relationship between pressure,
    temperature, and volume of a hypothetical ideal gas, which is a
    useful approximation for the majority of gases used in propulsion
    systems.

-   The equation is: $$PV = nRT$$ Where: P = pressure (pascal) V =
    volume (m3) T = temperature (K) n = amount (kg) Rs = specific
    constant (J / kg K) Or, frequently, we'll use bar (pressure) and
    liters (volume), and then the equation $$PV = nRT$$ / 100

-   In some instances (eg, hydrogen gas), other equations/factors need
    to be used.

------------------------------------------------------------------------

# 2. Propulsion Architecture & Requirements

## Architecture Selection: Lunar Sample Return Example

*Source slide 9*

-   Review the Concept of Operations
    -   Where & how much thrust is needed?
-   Trajectory maneuvers & orbit insertion
-   Orbit maintenance
-   Attitude control (propulsion versus GN&C)
-   Special considerations (eg, lunar ascent)
    -   What type of system accommodates each use?
-   Mass efficiency & cost
-   Consolidation of different types of system
    -   Identify key requirements & selection discriminators
-   Delta-V and dry mass
-   Redundancy, sample contamination, optical instruments
-   Perform analysis and iterate
    -   Consider design at both the system and subsystem level
    -   Develop propulsion schematic for each required propulsion system
    -   Select off-the-shelf tanks & thrusters per sizing analyses
        Excluding the LV, how many thrusters/engines above? Assume each
        system is single-string.

## Architecture Selection: Lunar Sample Return Example

*Source slide 10*

-   Launch
    -   Atlas V class Launch vehicle
    -   Liquid engines + SRM boosters
-   Lunar Breaking & Landing System
    -   SRM (ejected) + Monoprop
    -   12 high thrust engines
-   Ascent System
    -   SRM + Monoprop System
    -   6 high thrust engines
    -   8 attitude control thrusters
-   Sample Return Capsule
    -   None (Earth atmosphere for breaking, low mass/drag ratio for
        slow velocity, helicopter catch)
-   Comsat
    -   Single-string Monoprop system
    -   1 mid-thrust engine
    -   8 attitude control thrusters Total = 37 (2 SRMs + 35 thrusters,
        excl. LV)

## Propulsion System Architecture

*Source slide 11*

Simpler, shorter duration missions, Architecture Gas Cold Gas Blowdown
with far simpler/safer I&T. Type? Simpler and cheaper Same as above, but
now mitigates system for smaller Hot Gas Regulated mission, but does not
leakage and provides longer life. scale well if Uses hydrazine gas
generator requirements increase. to provide low thrust. Chemical Typical
propulsion system that supports $\Delta V$ burns and/or Simplest design
for shorter duration, Liquid Monopropellant Blowdown attitude control
functions. lower thrust missions. Typical for mid-to- Simplest & most
reliable for Higher complexity and mass, but Electric Propulsion large
spacecraft to missions that require Regulated (EP) support a variety of
moderate capability. ($\Delta V$ in improves efficiency & lifetime.
trajectory and orbital the 100s of m/s) Very high efficiency for large
Additional tank(s) for recharge option $\Delta V$ trajectories and/or
long- requirements. Recharge Integrated System duration attitude control
(eg, commercial GEO), but requires significant power (kW). Highest
efficiency, but lack of low Bipropellant Bipropellant thrust generally
requires added sys. Typical, but strong Higher efficiency for larger
Solar EP dependency on Reduces complexity, mass, and cost missions, but
more complex Dual Mode over separate biprop/monoprop sys. solar power.
and costly. Costly, but removes Typically used for high-performance
Nuclear EP dependency on Cryogenic on launch vehicles and/or boosters
solar power for larger missions. Used for specific applications, such as
a kick stage or SRM Solid Rock Motor (SRM) spacecraft spin, where no
other prop system is needed. EP for long-term $\Delta V$ EP Hybrid
and/or ACS, whereas Typical SRMs are SRMs are sometimes paired w/liquid
prop. systems to provide chemical for shorter simple, highly reliable,
SRM Hybrid high thrust during specific maneuvers (eg, orbit insertion).
maneuvers. and lowest cost, but typically inflexible once cast. Higher
cost, less common applications that can vary, SRM (other) terminate,
and/or restart thrust.

## Requirements: Example L3 & L4

*Source slide 12*

ASTE-331a 12

## Requirements: Example L4

*Source slide 13*

ASTE-331a 13

## Detailed Propellant Budget

*Source slide 14*

> UPDATED

AFTER 9/10

-   Below is an example of a more detailed propellant budget
    -   The rocket equation is used to determine the propellant based on
        the $\Delta V$ and initial mass
    -   For each maneuver, a propulsion system is selected (which
        determines $I_{sp}$)
    -   Additionally, there is a column for released payloads (such as a
        probe), which will reduce the mass/propellant for later
        maneuvers
    -   Not shown here, but sometimes included is an engine 'cant' (or
        incidence angle that results in the slight loss of thrust). This
        can be fixed or (with gimbals) articulated.

### Selection of monoprop vs. biprop based on

Initial Mass (1) Thrust required / burn-time, (2) efficiency, and (eg,
LV Capability) Mo = Previous Mp = Rocket Equation (3) timing relative to
re-pressurization events. Mf - ∆Dry Mo - Mf Mf = f(Mo, $\Delta V$,
$I_{sp}$) This pattern repeats across each of the sequential maneuvers,
until the final delivered mass (Mf) is the actual s/c dry mass that is
available.

------------------------------------------------------------------------

# 3. Propulsion Schematics

## Schematic Diagrams

*Source slide 15*

-   The first critical step of designing a propulsion subsystem is
    creating the draft schematic diagram.

    -   This diagram will help you understand the system requirements
        and features

-   Before you start, you need to understand the general architecture

    -   Context of overall mission & requirements
    -   Type of propulsion system?

-   Cold gas, monoprop, biprop, dual-mode, SRM, electric

-   Blowdown versus regulated

-   Number and size of propellant and/or pressurant tanks

-   Number and size of thrusters

    -   Type of redundancy?

-   Single-string (any single fault will cause the design to fail)

-   Selected redundancy (more critical or less reliable parts are
    redundant)

-   Full redundancy (two faults required for failure, although there are
    some common exceptions depending on the mission, such as tanks, main
    engine, some propellant lines, etc.)

    -   If some of this information is unavailable, be sure to state
        your assumptions before continuing...

## Approach

*Source slide 16*

Tanks... Pressurant Manifold Pressurant • Objectives

### Tank

### Legend

-   Provide the propellant needed by the thrusters Tank w/Pressurant
    Pressurant

-   Where, when, how much, etc. System Filter Propellant

    -   Ensure no leaks, mixing, backflow, contaminants, etc. Isolation
        / Latch Valve, LV (Ox or Fu) Gas

    -   Provide adequate monitoring, servicing, & testing Pyrotechnic
        Valve, PV-NC Pyrotechnic Valve, PV-NO

-   Approach Check Valve, CV, single string

    -   Place tanks & thrusters based on architecture Check Valve, CV,
        dual-string

    -   Add lines, filters, regulators, etc. Service Valve, SV

    -   Select and add valves (select types based on function) R
        Dual-stage Pressure Regulator Manifold

    -   Add pressure & temperature monitoring Cavitating Venturi Design
        P Pressure Transducer

-   Review & Iteration T Temperature Sensor

    -   Review for required redundancy Thruster, single valve

    -   Iterate at system & subsystem levels to minimize cost for the
        Thruster, dual valve Solid Rocket Motor appropriate level of
        risk Lines & Fittings Consider what you need, and add one
        component at a time. There is rarely a perfect answer and
        individual designs will vary on a variety of constraints
        ...Thrusters/Engines/Motors and acceptable level of risk. Be
        able to defend your selections.

## Component Symbols and Descriptions

*Source slide 17*

### Tank

Used to store propellant and include (for liquid Dual-stage Controls
downstream pressure (within certain systems) internal devices for
separation of R Pressure constraints) mechanically or electrically. Dual
(w/ & without propellant and pressurant, along with reducing Regulator
stage ensures steady flow rate. pressurant) propellant movement (slosh).
Provides control of pressure drops Removes unexpected particulates from
the Cavitating independent on downstream fluctuations. System Filter
fluid. Typically placed just downstream of the Venturi Useful in
maintaining oxidizer/fuel mixture tank(s) and service valves. ratio
and/or preventing water hammer. Provide controlled open/closed flow that
Monitors pressure to support both ground Pressure remains in position
without the application of P and flight operations (for safety,
performance, Isolation Valve Transducer continuous electric power.
Required between & anomalies). / Latch Valve tank and thruster, but also
useful for isolating (LV) Monitors temperature to support ground
thruster sides (eg, A vs. B), multiple tanks, etc. Temperature testing
and flight operations. Placed on lines Often called solenoid valves as
well. T Sensor throughout system, but typically not shown on Single-use
valves that start in either an open or a schematic. closed position, and
then can be changed (via Pyrotechnic A small rocket engine used to
adjust the pyro activation) once. Useful for either isolating Valve (PV)
course or attitude of a spacecraft. These can systems on ground for
safety (and then opened Thruster (normally closed vs. have single or
redundant valves representing normally open) in flight) or in flight
(closed to prevent leaks (single/dual valve by X's. If there are
multiple types of thrusters, early or late in long missions).
redundancy) the size is often used to represent the relative NO =
Normally open, NC = Normally closed thrust-levels. Check Valve Allows
fluid to only a flow in one direction and, Solid Rocket Solid Rocket
Motor (only requires data/power (CV) for example, prevent unintended
fuel/oxidizer Motor interface, which is not required in schematic)
(single/dual mixing. These can be single or redundant. redundancy) Lines
& Fittings Typically titanium or stainless steel. Service Valve
Positioned to both fill & drain tanks and (SV) functional testing of
end-to-end system

> Sources

> Note: The above table represents common

> For component pictures & specs, see

-   SMAD, FSS, wikipedia, etc. components and symbols, but it's not
    fully

-   https://www.space-propulsion.com/index.html \> Interesting Failures

comprehensive and individual propulsion

-   https://www.moog.com/products/propulsion-controls/...

-   https://www.thespacereview.com/... systems and symbols may vary.

-   https://www.valcor.com/missiles-and-aerospace/

-   https://spacenews.com/faulty-valve...

## Other Symbol Variations...

*Source slide 18*

Pulled from many existing propulsion system schematics, along with SMAD

## Schematic Examples

*Source slide 19*

Examples For each example, identify each component & understand its
function.

## Example 1: Microsat

*Source slide 20*

Cold Gas System The propulsion system consists of the propellant tank,
filter, high pressure latch valve, pressure regulators, and a
four-branch manifold that feeds into four thruster assemblies. Each
thruster assembly includes one solenoid valve and a nozzle through which
the propellant is released. In addition to the components listed above,
the propulsion system also includes a high pressure transducer, a low
pressure transducer, and a fill and vent valve for propellant loading.
Krypton HP = 160 bar (2321 psi) Propulsion System Requirements

-   ≥ 150 N s total impulse

-   ≤ 2 kg for prop system mass

-   Non-toxic, non-flammable, non- More common to use a single
    dual-stage explosive propellant pressure regulator (vs. HP & LP
    regulators)

-   80 mN total thrust LP = 2 bar (29 psi)

> From: "Fabrication and Testing of the Cold Gas Propulsion
> Adelis-SAMSON satellite cold gas propulsion system

System Flight Unit for the Adelis-SAMSON Nano-Satellites"

## Example 2

*Source slide 21*

Simple Monoprop Blowdown Systems

-   Assumptions Pressure monitor

    -   Diaphragm tank with no external pressurant P system F/D Valve

    -   One-year mission life \> Note that service (fill &

drain valves are located at Hydrazine the top & bottom of the

-   Notes tank to aid ground

    -   Additional service valve added after pyro valve operations). to
        ensure adequate testing F/D Valve

    -   Since the pyro valve is more likely to add Pyro valve enables
        the PV system for use contaminants (rather than be affected by
        contaminants), the filter is placed after the pyro valve and
        prior to the latch valve. Filter Latch valve controls the LV
        propellant flow to the thrusters.

### Thrusters

### Thrusters

## Example 3: GPM Earth Orbiter

*Source slide 22*

Monoprop Blowdown System

### Overview

> From SMAD

Redundant pressure transducers to

-   Global Precipitation Measurement (GPM) monitor tank pressure

-   Mass = 3850 kg, power = 1.95 kW

-   RCS (Reaction Control Subsystem) uses a chemical propulsion system
    for attitude control, reaction wheels momentum dumps and Low Earth
    Orbit maintenance Filter downstream of tank

### Thrusters

-   12 total thrusters Cavitating venturis to reduce flow

-   8 aft (4 straight, 4 90-deg nozzles) and prevent downstream water

-   4 forward-facing hammer (likely due to length of line

-   All thrusters are for attitude and RW dumps & desire to protect
    valves)

-   Only forward thrusters are for maneuvers

-   Generate thrust by catalytic decomposition of hydrazine using
    Isolation valves (in addition to heated platinum/palladium catalyst
    beds redundant valves on thrusters) See how the thrust

-   Thrusters provide decreases over the

-   44.5 N at 27.6 bar (launch) mission duration due

-   13.3 N at 6.8 bar (end of life) to 'blowdown' design.

-   Attitude control is accomplished in pulse mode, whereas orbital
    Watch out for similar symbols maneuvers use steady state with
    different meanings

### Tank

-   At launch, holds 545 kg hydrazine at 27.6 bar

-   Qualified to 34.5 bar w/55.2 burst press.

-   Minimum flight pressure is 6.8 bar.

-   2 to 50 ºC temperature range with a ten-year minimum storage life of
    the hydrazine

-   Tank pressurization is w/6.2 kg of N2

## Example 4: EO-1

*Source slide 23*

Another Monoprop Blowdown System Low cost technology demonstrator (EO-1)

-   EO-1 had magnetic torquers, reaction wheels, & electric propulsion,
    so monoprop system was primarily for orbit raises P

### Legend

GN 2 P Pressure Transducer N2H2 T Temperature Sensor L Latch Valve (w/
BPR in direction shown) Service Valve Cavitating Venturi Combines a
cavitating venturi with a back pressure regulator (BPR) to maintain a
System Filter defined downstream pressure L REA with Dual Valves T1 T2
T3 T4

## Example 5: Cassini

*Source slide 24*

Biprop Main Engine Assembly (MEA) To pressurant system

-   This is the Cassini Main Engine Assembly for orbit insertion and \>
    100 other maneuvers.

-   It is a fully redundant biprop system with NTO & MMH

-   REA-B was the redundant main engine and was ultimately never used
    Barber, T. "Final Cassini Propulsion System In-Flight
    Characterization." AIAA, 2018.

## Example 5: Cassini

*Source slide 25*

Biprop Main Engine Assembly (MEA) To pressurant system 235 psia
pressure, 237 psia pressure, primary oxidizer lines primary fuel lines
216 psia pressure, 193 psia primary oxidizer pressure, 0 psia pressure
lines primary (vented), redundant • This is the Cassini Main Engine fuel
lines oxider & fuel lines Assembly for orbit insertion and \> 100 other
maneuvers. • It is a fully redundant biprop system with NTO & MMH •
REA-B was the redundant main engine and was ultimately never used
Barber, T. "Final Cassini Propulsion System In-Flight Characterization."
AIAA, 2018.

## Example 5: Cassini

*Source slide 26*

Biprop Main Engine Assembly (MEA) To pressurant system

> Note that the oxidizer

manifold is identical to fuel manifold. 1. Pyro-valve (starts open,
closes for swap to backup engine) 2. Cavitating venturi to restrict flow
and protect downstream latch valve BPR 3. Primary latch valve with
back-pressure regulator (BPR) to drop pressure. 4. Secondary pyro valve.
If primary latch valve fails closed, then this valve will open. 5.
Oxidizer & fuel valves that control actual engine operation & mix ratio.

## Example 5: Cassini

*Source slide 27*

Biprop Main Engine Assembly (MEA) Another view... Pyro valves select
primary vs. redundant main engine

> Note that the first two are open (for primary engine)

Isolation (with backup pyro) valve minimize potential leaks

> Note that pyros have the 'bar' in the middle.

Engine valves control thrust duration

## Example 5: Cassini

*Source slide 28*

Biprop Main Engine Assembly (MEA) If an engine valve fails... Open four
valves Valve fails stuck closed Fire backup engine Valve fails closed

> Source: Weld, D. "CSE 592: Reconfiguring for a failed engine.", AIAA
> 1998

## Pyro-Ladders

*Source slide 29*

-   Pressurization using a pyro-ladder
-   Open Pyro-NC-1
-   Tank pressurizes
-   Close Pyro-NO-1
-   Repeat for each "rung" of the pyro
-   For example, in this schematic, the oxidizer can be pressurized 4
    times

> Source: Wiley, S. "Design and Development of the Messenger Propulsion
> System.", AIAA 2003.

------------------------------------------------------------------------

# 4. Propulsion Sizing

## Propulsion Schematic Instructions

*Source slide 30*

1.  Place estimated propellant & pressurant tanks 2. Add thrusters

-   Typically in groups to provide greater clarity/organization (eg,
    thruster types, A vs. B string, etc.)
-   Use size to indicate relative thrust differences.

3.  Add lines, filters, regulators, & flow control devices downstream of
    tanks

-   Use filters to remove contaminants (eg, from pyro valves) and
    protect more sensitive components (eg, regulators)

-   Add pressure regulators, venturis, and or back-pressure-regulators
    (BPRs) to protect downstream components \### 4. Add valves
    appropriate for function

-   Isolation valves for basic on/off flow control

-   Pyrotechnical and/or check valves for ground or flight safety
    (particularly for long durations)

-   Use a "pyro ladder" that combines multiple pyro valves to produce
    some on/off control while minimizing leaks

    -   Service valves for fueling, draining, and testing

-   For example, if there are closed pyro valves, need to additional
    service valve to test

5.  Add pressure transducers & temperature sensors for monitoring

-   Pressure transducers are typically added opposite to service valves
    (temp sensors are usually not shown)

6.  Review for desired level of redundancy

-   If fully redundant, then no single fault should cause mission
    failure (w/exceptions of tank, SRM, main engine, etc.)

7.  Additional checks & labeling

-   Design to avoid back-flowing filters
-   Ensure all components can be tested at the system level (ie, tested
    after spacecraft integration)
-   Adjust sizes and add labels (oxidizer, fuel, & pressurant names,
    thruster & SRM names, additional notes)

8.  Determine component sizing, factor in complexity/costs, & iterate

-   This is done in concert with overall propulsion system design and
    analysis

## Schematic Template

*Source slide 31*

Reminder: There is rarely a perfect answer and individual designs vary
on a variety of constraints and an acceptable level of risk. This is
intended to be an initial design,

### Tank

### Legend

prior to a more detailed analysis. At this stage, the most important
item is that you Tank w/Pressurant understand and can defend the
components you'$v_e$ selected... System Filter Isolation / Latch Valve,
LV Pyrotechnic Valve, PV-NC Pyrotechnic Valve, PV-NO Check Valve, CV,
single string Check Valve, CV, dual-string Service Valve, SV R
Dual-stage Pressure Regulator Cavitating Venturi P Pressure Transducer T
Temperature Sensor Thruster, single valve Thruster, dual valve Solid
Rocket Motor Lines & Fittings

## Propulsion Subsystem Design Steps

*Source slide 32*

-   Step 1: Create a draft schematic
-   Step 2: Use $\Delta V$ to determine propellant quantity
-   Step 3: Use propellant quantity to determine tank size
-   Step 4: Use tank size to determine pressurant quantity and tank size
-   Step 5: Estimate wet/dry system mass

## Step 1: Determine Architecture & Draft Schematic

*Source slide 33*

-   Identify Candidate Propulsion System Architecture
-   Draft Preliminary Schematic
    -   See Propulsion Schematic class handout (charts)
    -   Consider writing out the specific functions that you require
-   Number and type of tanks
-   Number and type of thrusters
-   Add pressure regulator for pressurized (rather than blow-down)
    system
-   Add latch valves for nominal control
-   Consider adding/swapping pyro valves/ladders to preserve
    pressurization and/or add redundancy
-   Add check valves & cavitating venturis to control direction and
    magnitude
-   Add service valves for access
-   Add pressure and temperature sensors
    -   Important
-   For a back-of-the-envelope design (eg, exam question), you may not
    need to create a propulsion schematic, but you should be able to
    estimate the \# of regulators, valves, sensors, etc.

## Step 2: Calculating Propellant

*Source slide 34*

-   Calculate required usable propellant, based on total ΔV, S/C mass &
    specific impulse

    -   Use rocket equation equation to calculate required propellant
        mass ΔV = gc Is LN (Mi / Mf) (m/s) where, gc = 9.8067 Is = Ave.
        specific impulse (s) Mi = Initial S/C mass (kg) Mf = Final S/C
        burnout mass (kg)

-   Typically, either initial total S/C mass or final S/C burn out (dry)
    mass is known

-   In each case, S/C mass includes unknown PROP mass; therefore, PROP
    mass must be initially estimated to yield net S/C mass

    -   Mp = Mf \[exp (ΔV/gc Is) -- 1\]

## Step 2: Calculating Propellant

*Source slide 35*

-   Add additional propellant to cover ACS, margin, and other needs

-   Margin may be included due to:

    -   Trajectory uncertainty (this is typically already included as
        additional $\Delta V$)
    -   Propulsion system performance variations (temperature, $I_{sp}$,
        biprop MR, thruster, etc.)

-   Conservative estimates of thruster performance typically account for
    this margin

    -   ACS and/or additional propellant margin

-   ACS propellant margin is typically provided by ACS subsystem (as
    part of their propellant estimate)

-   Often, no additional margin is carried (eg, HW2)

-   Resulting total propellant is then increased to account for
    residuals/hold-up (ie, non-usable propellant)

    -   1% is typical for monopropellant systems
    -   3.5% is typical for bipropellant systems

## Step 2: Calculating Propellant

*Source slide 36*

-   For bipropellant & dual mode systems, total propellant load must be
    split into fuel & oxidizer
    -   Mtot prop = Mox + Mfu and mass ratio (MR) = Mox / Mfu,
        therefore, Mox = Mfu \* MR

    -   For biprop, typical assembly requires MR = 1.65
-   For N2O4/MMH, this equates to equal Fu/Ox tanks
-   Common tanks reduces the cost
    -   For dual mode, typical assembly requires MR = 1.05
-   For N2O4/N₂H₄, this equates to either unequal or non-optimum tanks
-   Either a cost hit or mass penalty

## Step 3: Calculate Tank Size

*Source slide 37*

-   Number of Tanks
    -   The number of tanks for fuel and oxidizer (as well as
        pressurant) is typically based on the amount of propellant
        versus available heritage tanks

    -   Goal is to select the type & quantity of tanks that minimizes
        mass (& cost)

    -   Note that wherever possible, identical tanks should be used
-   For example, oxidizer & fuel or multiples of each
-   This is typically much cheaper versus manufacturing different tanks
-   Tank Size
    -   Cold gas: See pressurant sizing on the following charts
    -   Monoprop & Biprop
-   Use propellant density to determine the required volume
-   Add initial 20% for margin against total tank capacity
    -   Also, need to add the pressurant for simple monoprop blowdown
        (see following charts)
-   Select heritage tanks that meet the volume specification
-   In concert with pressurant calculations, iterate through the options
    to find the minimum mass
    -   Note that mass is often used as a proxy for cost when cost #'s
        are unavailable

## Step 4: Determine Pressurant...

*Source slide 38*

-   The role of pressurant is to ensure adequate propellant pressures at
    the thruster inlet nozzle
    -   For example, a typical cold gas thruster might require 100 psia
        to maintain the desired thrust level (eg, in the context of the
        prop system, including pressure regulators, etc.)
-   Pressurant Sizing Approach
    -   The propulsion system (and specifically mass & volume of
        pressurant) needs to be sized such that
-   At the beginning of mission (BOM), the pressure is within the tank
    specification
-   At the end of mission (EOM) the pressure is still sufficient for the
    thrusters
-   The Ideal Gas Law
    -   For some monoprop/biprop systems (eg, w/GN₂), the ideal gas law
        can be assumed
-   $$PV = nRT$$ \### Where

P = pressure (pascal), V = Volume (m\^3) n = mass (kg), R = Gas Constant
(J / kg K) T = Temperature (K)

-   The ideal gas law is used to trade mass, volume, & pressure
-   For typical spacecraft, T can be assumed at room temperature (\~300
    K)
-   Gas constants are fixed (such as 296.8 J / kg K for GN₂)

## Step 4: Determine Pressurant...

*Source slide 39*

-   For pressurant (gas) calculations, there are several variations,
    including:

    -   Cold Gas Propellant: Gas released is the propellant required
        (derived from the rocket equation)

    -   Monoprop Blowdown: No gas is released (constant mass), but
        volume increases to fill the void left by the expended liquid
        propellant

    -   Regulated Monoprop: Same as the above, but there is an
        additional pressurant tank (with a fixed volume) to consider
        Cold Gas Propellant Approach A) Beginning of Mission (BOM) B)
        End of Mission (EOM) C) Propellant Mass

-   Pressurant tank is filled to maximum expected

-   Pressurant tank is nearly empty with the

-   The difference between BOM and EOM operating pressure (MEOP) lower
    limit of the minimum pressurants is the actual pressurant mass

-   Using the ideal gas law, we have: regulator/thruster operating
    pressure

-   For cold gas systems, this is calculated

-   PBOM x V = nBOM x 296.8 x 300 reached using the rocket equation

-   Using the ideal gas law, we have:

-   nBOM -- nEOM = npropellant

-   PEOM x V = nEOM x 296.8 x 300 BOM EOM Propellant Expended - = For
    example, GN₂ (gaseous For example, GN₂ (gaseous nitrogen) at 300
    bar. nitrogen) at 100 bar

> Note that 296.8 is the specific gas constant for GN₂

(J/kg K) and 300K is a standard temperature

### Margin

assumption.

-   It's a best practice to carry margin on the tank capacity (eg, 20%)
    in case the $\Delta V$ \### Approach

requirements need to be increased. To account for this, propellant mass
remains the

-   We can use the ideal gas equation in the following two forms same,
    but the volume that is used to calculate the residual gas pressure
    and mass (at

-   PBOM-EOM x V = npropellant x 296.8 x 300, where PBOM-EOM = PBOM -
    PEOM EOM) should be increased by the specified margin.

-   PEOM x V = nEOM x 296.8 x 300

-   In other words, you will plan to underfill your tank slightly, but
    still meet your EOM

-   The first equation can be used to solve for volume pressure
    requirements. On the day of launch, you'll still fill to MEOP and
    thus convert

-   And then the second equation can solve for nEOM this tank capacity
    margin into operations propellant margin

## Step 4: Determine Pressurant...

*Source slide 40*

-   For pressurant (gas) calculations, there are several variations,
    including:

    -   Cold Gas Propellant: Gas released is the propellant required
        (derived from the rocket equation

    -   Monoprop Blowdown: No gas is released (constant mass), but
        volume increases to fill the void left by the expended liquid
        propellant

    -   Regulated Monoprop: Same as the above, but there is an
        additional pressurant tank (with a fixed volume) to consider
        Monoprop Blowdown Approach A) Beginning of Mission (BOM) B) End
        of Mission (EOM) C) Volume Change

-   Propellant tank holds the required liquid

-   As the liquid propellant is exhausted, the

-   The difference between BOM and EOM propellant and then is 'topped'
    off with pressurant fills the resulting void until the volumes
    corresponds to the volume of the pressurant (at MEOP) minimum
    pressure is reached expended propellant, which can be found

-   Using the ideal gas law, we have:

-   Using the ideal gas law, we have: using the rocket and density
    equations

-   PBOM x VBOM = n x 296.8 x 300

-   PEOM x VEOM = n x 296.8 x 300

-   For cold gas systems, this is calculated using the rocket equation

-   VEOM -- VBOM = Vpropellant For example, GN₂ (gaseous For example,
    GN₂ (gaseous Expended Hydrazine nitrogen) at 20 bar. nitrogen) at 5
    bar Propellant (liquid) At EOM, assume the residuals/hold-up are in
    the manifold, such that all of the propellant is expended from the
    tank.

### Approach

> Note that 296.8 is the specific gas constant for GN₂

-   Given that volume and pressure are inversely proportional for a
    constant gas (mass (J/kg K) and 300K is a standard temperature

### & temperature), the following equation can be derived

### Margin

assumption.

-   VEOM / Vpropellant = PBOM / PBOM-EOM
-   Tank capacity margin is applied to the propellant volume (rather
    than the
-   This can equation can be used to solve for the tank volume (VEOM),
    which can then be final tank volume). This ensures that the
    calculations for pressurant used to solve for the pressurant mass &
    finally initial pressurant volume include this additional tank
    volume.

## Step 4: Determine Pressurant...

*Source slide 41*

-   Other Combinations...
    -   Note that propellant is solved using the rocket equation, so the
        combinations below are slightly more complex (and require a
        balance between tanks) Regulated Tanks Multiple Blowdown Tanks
        (ie, separate pressurization system) Beginning... End...
        Beginning... End... GN₂ GN₂ GN₂ GN₂ GN₂ GN₂ Hydrazine Hydrazine
        Hydrazine Hydrazine Remember to add latch valves to control flow
        from separate tanks Hydrazine Hydrazine
-   When the ideal gas law breaks down (eg, Helium)
    -   Create an estimate using the ideal gas law  sufficient for this
        class
    -   Use real gas relationships (Van der Waals) or multiply time an
        appropriate factor (eg, 1.2)

## Step 5: Estimate Wet/Dry System Mass

*Source slide 42*

-   Compile a mass list of all hardware in the schematic

    -   Tanks\*

-   Provided in homework

    -   Thrusters\* and/or online search

    -   Pressure transducer, 0.3 kg

    -   Temperature sensor, 0.1 kg \> Note that if you can't find a
        mass,

use a guess/estimate and add a

-   Latch valve, 0.7 kg comment such as "placeholder"

-   Service valve, 0.25 kg

-   System filter, 0.9 kg

-   Cavitating venturi, 0.1 kg

-   Accumulator, 0.25 kg (stores limited fuel quantities and/or
    stabilizes flow)

-   Burst disk, 0.2 kg (provides pressure release \[via rupture\] when a
    specified threshold is reached

-   System tubing & fittings, 5% of above

-   Mounting brackets, fasteners, etc., 5% of above

-   The values listed above are current best estimates (CBEs).

    -   To these values, add contingency (ie, growth allowance) to
        accommodate for likely increases (tanks/thrusters 10%,
        valves/regulators/etc. 20%, tubing/brackets/etc. 30%)

-   System tubing/line estimates can be improved using a rough estimate
    of the spacecraft size and where tanks/thrusters would be located

## Step 5: Estimate Wet/Dry System Mass

*Source slide 43*

-   One more: Solid Rocket Motor

    -   See https://en.wikipedia.org/wiki/Star\_(rocket_stage)
    -   No additional propulsion system mass required
    -   However, the use of an SRM needs to be coordinated with
        Structures, which needs to ensure an adequate supporting
        structure and (if required) a separation system

-   Solid Rocket Motors are used for one-time $\Delta V$ burns, where it
    can be more efficient and/or cost effective than a biprop system

    -   See the site above for total impulse capabilities for various
        star motors

-   Total Impulse capability = SRM Force (kN) x time (s)

    -   Required impulse

-   Total Impulse required = Spacecraft wet mass x $\Delta V$ required

    -   Typically, trajectories are designed for these to be equal.
        However, if there is a difference, this needs to be a
        accommodated by a separate propulsion system

## Step 5: Estimate Wet / Dry Mass

*Source slide 44*

-   Based on the design, create the corresponding dry mass & propellant
    tables
    -   As part of an exam question, you would just need to enter the
        component name (via pull-down) and quantity Dry Mass Unit Mass
        Quantity Mass Contingency Total Mass Component Name kg \# kg %
        kg Comments 490-N Thruster 3.76 1 3.76 5% 3.95 4-N Thrusters
        0.37 10 3.70 5% 3.89 Pressurant Tank 6.00 1 6.00 5% 6.30
        NG-80558-1 (16 liters) Fuel Tank 11.70 1 11.70 5% 12.29
        NG-80394-1 (229 liters) Oxidizer Tank 11.70 1 11.70 5% 12.29
        NG-80394-1 (229 liters) Pressure Transducers 0.30 12 3.60 5%
        3.78 Temperature Sensors 0.10 24 2.40 5% 2.52 Integrated System
        Pressure Regulator 1.10 2 2.20 5% 2.31 Latch Valves 0.70 10 7.00
        5% 7.35 Service Valves 0.25 10 2.50 5% 2.63 System Filters 0.90
        10 9.00 5% 9.45 Cavitating Venturi 0.10 2 0.20 5% 0.21 System
        Tubes, fittings 3.19 30% 4.14 5% of above Mounting brackets,
        fasteners 3.35 30% 4.35 5% of above TOTAL 75.44 Propellant Mass
        Propellant Mass Propellant kg Comments Pressurant 2.2 Hydrazine
        176.4 Oxidizer 139.3

## ACS Thruster Design & Placement

*Source slide 45*

-   Often called a Reaction Control System (RCS) when used only for
    attitude control

    -   From propulsion, these are typically the smallest thrusters.
        Often, they functionally back-up a reaction wheels in case of a
        failure, but they do not provide the same precision

-   Characteristics

    -   Performance: 0.1-5.0 deg pointing control
    -   Various sizes available, with different levels of performance
        (ie, control)
    -   Propellant-limited and may introduce contamination
    -   Capable of very high torque
    -   Accuracy limited by thruster configuration (impulse bit)

## ACS Thruster Design & Placement

*Source slide 46*

-   RCS Thruster control? zb 1-DOF translational (+y-axis) 1-DOF
    rotational (+z-axis) y y yb xb z x x z

-   The above graphic shows "coupled" thrusters that act through the
    center of mass (CM) • Thus, 1-DOF = two coupled thrusters • This is
    not required, but results in much simpler operations & improved
    control

-   Redundancy • Dual-redundancy typically means two strings (A & B) •
    Thus, 1-DOF = four coupled, redundant thrusters (A-string, B-string)

-   Thrusters are typically placed • On opposite sides of the CM as
    shown above • On the outer edge (or beyond it) to provide greater
    control for a longer moment-arm • Typically in clusters of 2-4
    thrusters that face different directions

------------------------------------------------------------------------

# 5. Propulsion Hardware

## RCS Thruster Configuration

*Source slide 47*

-   Notional diagram for a set of 16 thrusters in 4 clusters

    -   6 DOF thruster configuration

    -   Arrows indicate plume direction -Y 6

    -   Examples -Z

-   For +X, fire 1 & 9 2 5 7

-   For --Z, fire 8 & 16 1 3 8 4

-   For rotation about +Y, 3 & 9 -X +X 14 10 13 15 9 11 12 +Y 16 +Z

## RCS Thruster Configuration

*Source slide 48*

-   Notional diagram for a set of 16 thrusters in 4 clusters

    -   6 DOF thruster configuration

    -   Arrows indicate plume direction -Y 6

    -   Examples -Z

-   For +X, fire 1 & 9 2 5 7

-   For --Z, fire 8 & 16 1 3 8 4

-   For rotation about +Y, 3 & 9 Rotations about Y -X +X 14 10 13 15 9
    11 12 +Y 16 +Z

## RCS Thruster Configuration

*Source slide 49*

-   Notional diagram for a set of 16 thrusters in 4 clusters

    -   6 DOF thruster configuration

    -   Arrows indicate plume direction -Y 6

    -   Examples -Z

-   For +X, fire 1 & 9 2 5 7

-   For --Z, fire 8 & 16 1 3 8 4

-   For rotation about +Y, 3 & 9 Rotations about X -X +X 14 10 13 15 9
    11 12 +Y 16 +Z

## RCS Thruster Configuration

*Source slide 50*

-   Notional diagram for a set of 16 thrusters in 4 clusters

    -   6 DOF thruster configuration

    -   Arrows indicate plume direction -Y 6

    -   Examples -Z

-   For +X, fire 1 & 9 2 5 7

-   For --Z, fire 8 & 16 1 3 8 4

-   For rotation about +Y, 3 & 9 Rotations about Z -X +X 14 10 13 15 9
    11 12 +Y 16 +Z

## Thrusters (1 of 3)

*Source slide 51*

-   Primary Thruster Characteristics
    -   Thrust-level (eg, 1-N vs. 490-N), which determines the ability
        to provide thrust and thus $\Delta V$
    -   Efficiency (ie, $I_{sp}$), which is based on both type of
        thruster & propellant
    -   Minimum impulse bit (MIB) is the smallest control torque that
        can be applied to the spacecraft
-   Primary Uses
    -   Trajectory Correct Maneuvers (TCMs) for changing $\Delta V$
    -   Orbital Maintenance
    -   Momentum dumps
    -   Attitude (or reaction) control
    -   Thrust vector control (TVC) that provide guidance on larger
        maneuvers
-   Matching Thrusters to Spacecraft
    -   Consider necessary functions: large $\Delta V$ maneuvers,
        attitude control, etc.
    -   Thrusters should be evaluated for min/max burn times
-   Minimum burn time should be consistent with the minimum impulse bit
-   Maximum burn time should be consistent with the type of maneuver
    (eg, orbit insertion, burn time \< 2-3 hrs)
    -   Result is often something like...
-   RCS thrusters for attitude control, momentum dumps, etc.
-   Main engine(s) for large & more efficient $\Delta V$ maneuvers
-   Other mid-size thrusters where the above thrusters aren't sufficient
    (eg, thrust vector control on a large $\Delta V$ burn)
    -   Reminder that thrust-level can be scaled with the number of
        thrusters

## Thrusters (2 of 3)

*Source slide 52*

ASTE-331a 52

## Thrusters (3 of 3)

*Source slide 53*

ASTE-331a 53

## Thrusters (3 of 3)

*Source slide 54*

Actual Thrust θ Lateral Thrust Intended/unintended Check Your Work
0-deg: Thrust = actual thrust 90-deg: Zero thrust (burn-time is
infinite) Actual

-   When the a thrust vector is misaligned or canted, Thrust there is a
    "cosine loss" that needs to be accounted for (Factual)

    -   The equation is: Intended Thruster Spec.
        $$F_{actual}=F_{spec}\cos(\theta)$$ Alignment (Fspec)

    -   Example for a 5N and 10-deg cant angle θ 5 N x COS (10-deg) =
        4.92 N Actual Alignment When solving for what size thruster is
        needed, the cosine term is divided from the required value (ie,
        slightly more thrust is needed due to this effect).

> Note that the reason to cant thrusters (when coupled) is that it

Misalignment Angle (when unintended) provides additional lateral
stability. If not coupled or if the alignments are not equal, this
introduces an error. Cant Angle (when intended)

## Thruster Stability & Duration

*Source slide 55*

-   The graph below shows a typical thruster firing
    -   The Rise Time & Tail-Off result in slight inefficiencies

    -   Additionally, the minimum duration thruster firing is known as
        the minimum impulse bit. This determines the resolution/control
        of thruster firings, which can drive both maneuver and attitude
        control

    -   Note that a thruster may be fired in steady state or pulse mode.

## Tanks (1 of 3)

*Source slide 56*

ASTE-331a 56

## Tanks (2 of 3)

*Source slide 57*

ASTE-331a 57

## Tanks (3 of 3)

*Source slide 58*

ASTE-331a 58

## Solid Rocket Motors (SRMs)

*Source slide 59*

ASTE-331a 59

## Propellant Management Devices

*Source slide 60*

-   While diaphragms are often used to prevent mixing between the
    propellant and pressurant, there also may be no barrier as well, and
    the propellant liquid is controlled via vanes and other devices
    (based on liquid surface tension) ASTE-331a 60

## Primary Propulsion Design Artifacts

*Source slide 61*

-   Master Equipment List (MEL)
-   Propellant budget
-   Power analysis (next semester)
-   Cost estimate (next semester) Dry Mass Unit Mass Quantity Mass
    Contingency Total Mass Loosely related examples... Component Name kg
    \# kg % kg Comments 490-N Thruster 3.76 1 3.76 5% 3.95 4-N Thrusters
    0.37 10 3.70 5% 3.89 Pressurant Tank 6.00 1 6.00 5% 6.30 NG-80558-1
    (16 liters) Fuel Tank 11.70 1 11.70 5% 12.29 NG-80394-1 (229 liters)
    Oxidizer Tank 11.70 1 11.70 5% 12.29 NG-80394-1 (229 liters)
    Pressure Transducers 0.30 12 3.60 5% 3.78 Temperature Sensors 0.10
    24 2.40 5% 2.52 Pressure Regulator 1.10 2 2.20 5% 2.31 Latch Valves
    0.70 10 7.00 5% 7.35 Service Valves 0.25 10 2.50 5% 2.63 System
    Filters 0.90 10 9.00 5% 9.45 Cavitating Venturi 0.10 2 0.20 5% 0.21
    System Tubes, fittings 3.19 30% 4.14 5% of above Mounting brackets,
    fasteners 3.35 30% 4.35 5% of above TOTAL 75.44 Propellant Mass
    Propellant Mass Propellant kg Comments Pressurant 2.2 Hydrazine
    176.4 Oxidizer 139.3

------------------------------------------------------------------------

# 6. Integrated Propulsion System

## Example Requirements

*Source slide 62*

-   Flight System
    -   The total flight system mass shall be less 500 kg
-   Orbital Mechanics
    -   The flight system shall provide 500 m/s of $\Delta V$ capability
        post-launch
    -   The flight system shall support a maximum $\Delta V$ burn of 400
        m/s
-   Or, flight system shall support the trajectory $\Delta V$ budget in
    Table X-X
-   Attitude Control
    -   The propulsion system shall be capable of 3-axis control while
        orbiting Mars
    -   The propulsion system shall provide a +X axis spin of 1.0 rpm
-   Propellant
    -   The propellant tanks shall store 100 to 110 kg of propellant
-   Thrusters
    -   The main engine shall be capable of a maximum duration burn of
        40 min
-   Pressurization
    -   The pressurization system shall maintain a 400 psia for Mars
        Orbit Insertion (JOI)
-   Redundancy
    -   The propulsion system shall be fully redundant
-   Contamination Control
    -   The propulsion system shall not release hydrazine contaminants
-   Note
    -   "should" = you don't really have to...
    -   For a goal, you would say.. The spacecraft shall X, with an
        objective \[or goal\] of Y

## Example Requirements

*Source slide 63*

-   Flight System Be able to rewrite the rocket equation to use

    -   The total flight system mass shall be less 500 kg dry mass or
        wet mass

-   Orbital Mechanics

    -   The flight system shall provide 500 m/s of $\Delta V$ capability
        post-launch Use $\Delta V$ and mass to

    -   The flight system shall support a maximum $\Delta V$ burn of 400
        m/s determine the required propellant & pressurant

-   Or, flight system shall support the trajectory $\Delta V$ budget in
    Table X-X

-   Attitude Control More of an ACS question, but

    -   The propulsion system shall be capable of 3-axis control while
        orbiting Mars determine the number &

    -   The propulsion system shall provide a +X axis spin of 1.0 rpm
        placement of thrusters

-   Propellant Be able to incorporate lower-

    -   The propellant tanks shall store 100 to 110 kg of propellant
        level requirements/constraints in a

-   Thrusters design

    -   The main engine shall be capable of a maximum duration burn of
        40 min Size thrusters based

-   Pressurization on pressure & burn

    -   The pressurization system shall maintain a 400 psia for Mars
        Orbit Insertion (MOI) duration

-   Redundancy Apply redundancy

    -   The propulsion system shall be fully redundant throughout the
        system

-   Contamination Control

    -   The propulsion system shall not release hydrazine contaminants
        Consider alternative designs or propellants for specific
        constraints

## Interpreting Schematics

*Source slide 64*

-   What are the components?

-   What type of propulsion system is this? P GN₂

-   What is the mission duration? Hydrazine

    -   Short (≤ 1 year) versus long (\> 2 years)

-   What's wrong with this design? PV LV Thruster(s) Thruster(s)
    Single-string, RCS

## Interpreting Schematics

*Source slide 65*

-   What are the components?

-   What type of propulsion system is this? P F/D Valve

    -   Simple monoprop blowdown hydrazine system GN₂

-   What is the mission duration? Hydrazine

    -   Short (≤ 1 year) versus long (\> 2 years)

-   What's wrong with this design?

    -   No filter downstream of the pyro valve PV

    -   No service valve below monoprop tank

    -   No service valve downsteam of pyrovalve to test the latch Filter
        valve LV Thruster(s) Thruster(s) Single-string, RCS

## Interpreting Schematics

*Source slide 66*

-   What are the components?

-   What type of propulsion system is this? He -- P

-   What is the mission duration? PV

    -   Short (≤ 1 year) versus long (\> 2 years)

-   What's wrong with this design? P R P -- CV CV Ox Fu Dual-string,
    coupled thrusters for both attitude control & large $\Delta V$ burns

## Interpreting Schematics

*Source slide 67*

-   What are the components?

-   What type of propulsion system is this? He

    -   Regulated bipropellant F&D SV P LV

-   What is the mission duration? Test SV

    -   Short (≤ 1 year) versus long (\> 2 years) PV

-   What's wrong with this design? Filter

    -   No flow control (beyond regulator) after first use P R P

-   Added high pressure latch valve

    -   Insufficient control of oxidizer vapors Pyro CV CV Ladder

-   Added pyro ladder

    -   Untestable regulator

-   Added service valves Ox Fu Dual-string, coupled thrusters for both
    attitude control & large $\Delta V$ burns

## Interpreting Schematics

*Source slide 68*

-   How many pressurization recharges can be accomplished?
-   What are the thrusters used for?
-   Single string or dual-string design? P P NC GHe NC P GHe N₂H₄ NC NC
    NC NC P P NO NO NC NC NO NO L L To 0.9-N Thrusters (2 22 N sets
    of 6) To 22-N & 445-N 0.9 N REAs (2 sets of 2*22- N & 4*445-N)
    Typical REM (4 plcs) 445 N

## Example 7: Magellan Venus Orbiter

*Source slide 69*

More Complex Monoprop Blowdown System Redundant pressurant system that
is opened just P P

-   Magellan used a more complex before Venus insertion to ensure full
    pressure. monoprop blowdown system that NC GHe incorporated an
    external pressurant system, 12 0.9-N thrusters for NC GHe P attitude
    control and 4 22-N & 8 445- N for orbit insertion & orbit N₂H₄ NC NC
    maintenance NC NC

-   The STAR 48 SRM was used for orbit P insertion with the 22-N & 445-N
    P thrusters providing additional NO NO NC NC control. A-side B-side
    A-side B-side NO NO

-   The \> 1-year flight time and L L redundancy requirements result in
    the series of pyro-valves to minimize To 0.9-N leaks, but allowing
    the ability to A-side Attitude Thrusters (2 enable/disable the
    individual Control sets of 6) To 22-N & 445-N thruster branches.
    REAs (2 sets of 2*22-N & 4*445-N)

-   Note that the SRM is not connected to the manifold and thus not
    shown x4 Provide control for SRM Burn (except for the graphic)
    B-side B-side 22 N 0.9 N Attitude SRM Control A-side 445 N

## Interpreting Schematics

*Source slide 70*

-   For a given area, describe the propellant / pressurant flow?
-   Estimate the minimum number electrical cables/wires needed for this
    design?
-   Describe three areas of redundancy?

## Example 6: Messenger

*Source slide 71*

Biprop Pressurization Design

-   Messenger executed trade study to select a pressurization system
    -   Constraint: 6-year trajectory with 6 large maneuvers distributed
        over the last three years of the cruise phase
    -   This long flight time & multiple maneuvers required an
        innovative design to minimize leaks & missing Option #1 Option
        #2

> Note the use of a pyro-ladder that

allows for a discrete number of valve on/off events, but using pyros to
reduce the possibility of leaking.

> Note the same components, but slightly different symbols Option #3

Option #4

> Source: Wiley, S. "Design And Development Of The

Messenger Propulsion System.", AIAA, 2003

## Example 6: Messenger

*Source slide 72*

Biprop Pressurization Design

-   Messenger executed trade study to select a pressurization system
    -   Constraint: 6-year trajectory with 6 large maneuvers distributed
        over the last three years of the cruise phase
    -   This long flight time & multiple maneuvers required an
        innovative design to minimize leaks & missing Option #1 Option
        #2

### Design Selection

-   Option 1 does not provide adequate protection of mixing (Mars
    Observer lessoned learned)

-   Options 2 & 3 are good, but result Option #3 in heavier & costlier
    systems Option #4

-   Option 4 required a slightly new type of tank design, but was more
    efficient and safer.

> Source: Wiley, S. "Design And Development Of The

Messenger Propulsion System.", AIAA, 2003

## Propulsion System Trades (1 of 2)

*Source slide 73*

Pros Cons Solid Rocket • Simple design (few/no moving parts)

-   Inadvertent ignition or explosion, potentially Motor

-   Minimal pre-launch preparation catastrophic

-   Easy to get ready to operate on-orbit

-   Inflexible for propellant mass changes, once

-   No leakage/slosh concerns cast and machined

-   Least total system mass for certain range of

-   Complex, toxic exhaust gases can be total impulse problematic for
    some applications

-   Highly reliable solution for kick stage (fixed total impulse)
    applications Electric

-   Very high efficiency for high $\Delta V$ trajectories

-   Requires significant power (eg, kW)

-   Minimizes overall flight system mass Cold Gas

-   Lowest total system mass and cost for low $I_{sp}$ • Leakage
    concerns, especially for long-life

-   Generally simpler than liquid design missions

-   Simple pre-launch preparation (non-hazardous • Late increases in
    required total impulse can fluid) quickly result in non-optimum
    system

-   Easy to prepare for on-orbit operation

-   No slosh/cg issues

## Propulsion System Trades (2 of 2)

*Source slide 74*

Pros Cons Monopropellant • Simple, reliable blowdown system

-   Some tank mass inefficiency w/blowdown • Reasonable mass-efficient
    choice for

-   Regulated monoprop systems more mass small/medium $\Delta V$ systems
    efficient but added cost and complexity

-   Variety of heritage tanks & thrusters available • Hydrazine is toxic
    (fueling)

-   Very stable operation over a wide range of

-   Not mass-efficient for very small total impulse impulse bits and
    burn durations systems

-   Small thrusters qualified for \> 1M pulses

-   More expensive than a cold gas system

-   Stable operation for very long-life missions

-   Simple set of exhaust products Bipropellant

-   High specific impulse results in good mass

-   No qualified thrusters for low thrust efficiency for medium/large
    $\Delta V$ systems applications (\<10N)

-   Biprop mixture ratio equates to equal volume

-   Requires regulated pressurization system fuel/oxidizer tanks for
    commonality

-   Exhaust products much more complex and

-   Variety of heritage tanks & thrusters available toxic than monoprop

-   Stable operating over a range of press/temp

-   Bipropellants are toxic (fueling)

-   Long-burns (\> 60 min) demonstrated

-   System more complex than monoprop systems, with resultant higher
    cost and lower reliability Dual-Mode

-   Higher performance over biprop; good mass

-   Less stable operating range versus biprop (Mono + Biprop) efficiency
    for medium/large systems

-   Mixture ratio is results in different size fuel &

-   Simpler hardware layout (vs. having separate oxidizer tanks systems)

-   More limited selection of heritage thrusters

-   Complexity comparable to biprop systems

## Case Study: Mars Observer

*Source slide 75*

-   JPL launched Mars Observer on 9/25/92 to study the Martian...

    -   Surface
    -   Atmosphere
    -   Climate
    -   Magnetic field

-   Three days prior to orbit insertion, communication was lost and
    never re-established.

------------------------------------------------------------------------
