# Telecommunications (Telecom) and the End-to-End Information System (EEIS)

**Course:** ASTE-331a — Spacecraft Systems Engineering  
**Lecture:** 05 — Telecommunications (Telecom) and the End-to-End Information System (EEIS)  
**Instructors:** Jim Chase, Danielle Marsh   
**Source:** `331_05_Telecom_20251024.pdf`

---

## Lecture Overview

This lecture introduces the spacecraft telecommunications subsystem and the broader End-to-End Information System (EEIS). It covers telecom functions and hardware, spacecraft-to-ground communication paths, RF bands, modulation, antenna gain and radiation patterns, link budgets, atmospheric and trajectory effects, RF compatibility, telecom sizing, and the telecom design process.

The lecture also uses several mission examples—including GRAIL, MRO, Phoenix, Juno, Curiosity, and Galileo—to show how telecom architectures are implemented and how communications performance can affect mission success.

---

## Table of Contents

- [1. Telecom Overview](#1-telecom-overview)
- [2. Telecom Hardware Overview](#2-telecom-hardware-overview)
- [3. MRO Waveguide Transfer Switch Anomaly](#3-mro-waveguide-transfer-switch-anomaly)
- [4. Mission Telecom Examples](#4-mission-telecom-examples)
- [5. End-to-End Information System](#5-end-to-end-information-system)
- [6. Electromagnetic and RF Spectrum](#6-electromagnetic-and-rf-spectrum)
- [7. Communications Terminology](#7-communications-terminology)
- [8. Isotropic and Anisotropic Radiation](#8-isotropic-and-anisotropic-radiation)
- [9. Effective Isotropic Radiated Power](#9-effective-isotropic-radiated-power)
- [10. Additional Telecom Equations](#10-additional-telecom-equations)
- [11. The Decibel](#11-the-decibel)
- [12. Link Budget](#12-link-budget)
- [13. Antenna Gain and Patterns](#13-antenna-gain-and-patterns)
- [14. Atmospheric Attenuation](#14-atmospheric-attenuation)
- [15. Trajectory and Field-of-View Impacts](#15-trajectory-and-field-of-view-impacts)
- [16. Mars Rover Telecom](#16-mars-rover-telecom)
- [17. RF Compatibility](#17-rf-compatibility)
- [18. Galileo HGA Failure Case Study](#18-galileo-hga-failure-case-study)
- [19. Modern Telecom Hardware](#19-modern-telecom-hardware)
- [20. Telecom Hardware Estimate](#20-telecom-hardware-estimate)
- [21. Telecom Design Steps](#21-telecom-design-steps)
- [22. Optical Communication](#22-optical-communication)
- [23. Additional Class Questions](#23-additional-class-questions)
- [Lecture Summary](#lecture-summary)

---

# 1. Telecom Overview

> **Source: Slides 2–4**

## Function

Provides communication to/from the spacecraft.

- Typically with the Earth, but can include other spacecraft.
- Command reception and detection
- Telemetry modulation & transmission
- Bandwidth selection & antenna pointing
- Carrier tracking modes and ranging
- Occasionally used for radio science
- Primary driver is typically spacecraft-Earth distance

## GRAIL Example

- S-band transponder
- Low-gain antenna (LGA)
- Misc. hardware
- Total = ~5 kg

## Common Components

- Radio/transponder
- Amplifier
- Antennas
  - High-gain (HGA)
  - Medium-gain (MGA)
  - Low-gain (LGA)

## Key Trades & Analyses

- Fixed vs. articulated antennas
- Data rate & volume analysis
- Link budget & antenna sizing
- Radio-band and power level
- Heritage from prior systems

## Key Parameters

- Mass, power, and cost
- Transmission power, data, & margin

---

## Communications Architecture

> **Source: Slide 3**

Communications is critical for nearly every spacecraft.

- Most likely subsystem to be redundant
- Direct uplink/downlink comm. with specific ground stations
- Relay communication, such as using the TDRS network or via MRO (from Mars)
- Significant increases in communication over the past 30 years (≥ 1 Gbps possible)

### Tracking & Data Relay Satellite (TDRS)

Space vehicles that use TDRS:

- ISS
- Hubble
- NASA LEOs
- Etc.

Most can also downlink directly.

**Figure description:** The slide compares **Direct Communications** with **TDRS Relay Communications**. Space vehicles can communicate directly with ground stations or relay communications through the Tracking & Data Relay Satellite network.

---

## Telecom Functions

> **Source: Slide 4**

### Command Reception and Detection

- Acquire, track, detect uplink data
- Forward command data to avionics

### Telemetry Modulation & Transmission

- Receive telemetry data from avionics
- Modulate downlink signal
  - Synchronize
  - Packetize
  - Encoding
  - Encryption
  - Etc.

### Additional Functions

- Perform antenna pointing
- Select desired antenna (or band)
  - In safe-mode, spacecraft will typically default to low gain antennas
- Carrier tracking modes
- Ranging

**Figure description:** Mars Reconnaissance Orbiter (MRO) is shown with its High Gain Antenna, Low Gain Antenna, and UHF antenna identified.

---

# 2. Telecom Hardware Overview

> **Source: Slide 5**

## Avionics Subsystem

The avionics subsystem serves as the interface to the telecom system. This often consists of an “ULDL” card that decodes and relays the uplink data to FSW and/or directly to hardware devices.

- Example: C&DH

## Radio/Transponder

An electronics box responsible for:

**Uplink:** Receiving the formatted bits from C&DH, converting them to an RF signal, and transmitting to the antennas.

**Downlink:** Receiving the RF signal from the antennas, converting them to bits, and relaying to the C&DH system.

- Example: SDST

## Amplifier

An RF power amplifier converts a low-power RF signal to a higher power RF signal that drives the spacecraft antennas.

- Example: TWTA

## Diplexer(s)

Passive devices that combine and/or separate uplink/downlink signals.

## Waveguide Transfer Switch(es)

Switches that route an RF signal to a selected device/antenna.

## Low Gain Antenna (LGA)

Typically, multiple dipole antennas that ensure ~360-deg coverage at a low data rate that is adequate for critical uplink/downlink.

## Medium Gain Antenna (MGA)

When used, this is typically a horn antenna that provides higher data rates than an LGA, but less rigorous pointing requirements than an HGA.

## High Gain Antenna (HGA)

Typically, a single parabolic dish that provides high data rate, but requires narrow pointing control.

**Figure description:** The OSIRIS-REx telecom block diagram shows the digital-signal interface to avionics and the RF-signal path through the radio/transponder, amplifier, diplexer, waveguide transfer switches, and HGA/MGA/LGA antennas. The slide also shows the OSIRIS-REx 2.1 m HGA.

### Slide Question

> What component in the diagram is not described? Speculate on its use and when/why it’s used.

---

# 3. MRO Waveguide Transfer Switch Anomaly

> **Source: Slide 6**

## Lesson Learned (#1796)

### Mission

- Mars Reconnaissance Orbiter (MRO) is a spacecraft designed to study the geology and climate of Mars, provide reconnaissance of future landing sites, and relay data from surface missions back to Earth. It was launched in August of 2005 and arrived in March of 2006.
- The spacecraft continues to operate far beyond its intended design life. Due to its critical role as a high-speed data-relay for ground missions, NASA intends to continue the mission as long as possible, at least through the late 2020s.

### Driving Event & Root Cause

- For the downlink, MRO uses a WTS to route a 100-W RF signal from one of the two power amplifiers to one of two radiating antennas.
- Five months after arrival, the WTS failed to actuate. The onboard software maintained the commanded downlink configuration by commanding a switch to the redundant X band amplifier. Telemetry indicates that the switch is stuck between its two nominal positions, causing the switch rotor to partially block the RF energy passing through the switch. This has resulted in a downlink RF power loss (~1 dB) and a temperature increase (~15 deg C) caused by absorption and dissipation of the reflected energy.
- The most likely root cause is the following series of events:
  1. Accumulation of conductive debris (flaked plating?) on the polyimide tape windows used for WTS venting
  2. RF breakdown of these surfaces resulting in high temperature decomposition of the tape
  3. Large amount of debris from tape entering the WTS and causing the switch to bind
  4. Reduced performance of RF signal by 1 dB (accommodated by 3 dB of margin)
- This process was exacerbated by the frequency of MRO’s use of the switch (720 times)

### Lessons Learned

- Avoid using polyimide tape windows for contamination control on WTS vents
- Many additional recommendations on analysis & design

**Source on slide:** JPL/NASA Lessons Learned

**Figure description:** The slide shows MRO, the failed Waveguide Switch S1 location, the approximately 1 dB RF loss, and photographs from anomaly-investigation testing of the tape and WTS.

---

# 4. Mission Telecom Examples

## Phoenix Telecom Subsystem — X-Band

> **Source: Slide 7**

### Mission Description

- NASA science mission to investigate the geologic history and biological potential of Martian arctic
- Launch in 2007, arrived May 2008, ended Nov. 2008

### Telecom System

- 2-way X-band for communication & ranging in Cruise
  - 2 SDST radios and 2 15-W SSPA amplifiers
  - 1 medium gain (MGA)
  - Separate low gain antennas (Rx & Tx)
  - 2100 bps (Earth) to 40 bps (Mars)
- 2-way UHF radio for EDL & Surface
  - 1 helix antenna (HGA) and 1 monopole (LGA)
  - 32 kbps (EDL) to 256 kbps (Surface)

**Source on slide:** “Phoenix Telecommunications”, DESCANSO Series, 2010

**Figure description:** The X-band block diagram shows redundant SDST radios, command detector units, SSPAs, RF switches/diplexers, and the MGA horn assembly. Hardware is color-coded by heritage and new development.

### Slide Question

> What component in the diagram is not described? Speculate on its use and when/why it’s used.

---

## Phoenix Telecom Subsystem — UHF

> **Source: Slide 8**

### Mission Description

- NASA science mission to investigate the geologic history and biological potential of Martian arctic
- Launch in 2007, arrived May 2008, ended Nov. 2008

### Telecom System

- 2-way X-band for communication & ranging in Cruise
  - 2 SDST radios and 2 15-W SSPA amplifiers
  - 1 medium gain (MGA)
  - Separate low gain antennas (Rx & Tx)
  - 2100 bps (Earth) to 40 bps (Mars)
- 2-way UHF radio for EDL & Surface
  - 1 helix antenna (HGA) and 1 monopole (LGA)
  - 32 kbps (EDL) to 256 kbps (Surface)

**Source on slide:** “Phoenix Telecommunications”, DESCANSO Series, 2010

**Figure description:** The UHF architecture shows the wraparound antenna and UHF monopole feeding UHF hardware and two transceivers. Hardware heritage is identified as MER heritage, MRO/ODY heritage, other heritage, or new development.

### Slide Question

> What component in the diagram is not described? Speculate on its use and when/why it’s used.

---

## Juno Telecom Subsystem

> **Source: Slide 9**

### Mission Description

- NASA science mission to understand the formation and evolution of Jupiter
- Launched in 2011, arrived 2016, extended to 2025

### Telecom System

- 2-way X-band for communication & ranging
  - 2 SDST radios and 2 TWTA amplifiers
  - 1,745 bps (launch), 100 bps (cruise), 18 kbps (HGA at Jupiter), 10 bps (safe)
- 2-way Ka-band for gravity science (single-string)
  - 1 Italian radio and 1 SSPA amplifier
- Five Antennas
  - 2.5 m HGA, MGA, and 3 LGAs

**Source on slide:** “Juno Telecommunications”, DESCANSO Series, 2012

**Figure description:** The Juno telecom architecture identifies the X/Ka HGA, forward and aft LGAs, toroidal pattern LGA, RF switches, waveguide/coax transitions, SDSTs, TWTAs, and Ka-band gravity-science hardware. Hardware is marked by heritage, modified heritage, and new development.

---

# 5. End-to-End Information System

## EEIS Overview

> **Source: Slide 10**

- EEIS stretches beyond the telecom subsystem to encompass all functions, data formats, and path losses from the initial selection and formatting of the data for transmission to the final reception and use of the data
  - These are the to/from paths between telecom and ground (uplink & downlink)

### Flight-Ground Interface Control Document (FG-ICD)

- This document describes the interfaces & data formats at each step in the process
- To maximize efficiency, data is transmitted in binary and thus needs to be converted at several steps along the full path

### Link Budget

- This is the corresponding analysis that captures all of the losses (L) and gains (G) between the source & receiver
- This budget determines the data rate (in bits per second, bps) at a given bit error rate (BER)
- It’s used across many industries to design communication systems

**Figure description:** The slide shows the end-to-end path from the Telecom Subsystem through Space Loss and Atmospheric Attenuation to the Ground Station.

---

## End-to-End Information System in Bits

> **Source: Slide 11**

The slide traces an image through the complete information path:

- Picture on Titan
- Binary data
- Flight Ground Interface Control Document (FG-ICD)
- Packet formatting
- BPSK modulated output wave
- Modulating wave
- Relay via Cassini spacecraft
- Received/decoded data
- Picture on Earth

**Figure description:** The image begins as a photograph on Titan, is represented in binary, packetized according to the FG-ICD, converted into a modulated RF waveform, transmitted through the communications path via Cassini, recovered into bits, and reconstructed as a picture on Earth.

---

# 6. Electromagnetic and RF Spectrum

## Electromagnetic Spectrum

> **Source: Slide 12**

The EM spectrum describes light in the form of frequencies and their respective wavelengths and photon energies.

The EM spectrum is used heavily in space, where its used or mitigated in the following applications:

- Radiation shielding
- Power generation (eg, solar arrays)
- Thermal absorption & radiation
- Science (eg, imaging, spectroscopy, radar)
- Communications

**Figure description:** The diagram compares atmospheric opacity across the electromagnetic spectrum and highlights the Radio Frequency (RF) Spectrum as the region used for radio communications.

---

## Radio Frequency Spectrum

> **Source: Slide 13**

### Key Relationship

```math
f = \frac{c}{\lambda}
```

where:

- **f** is frequency in Hz (cycles/sec)
- **c** is the speed of light (m/s)
- **λ** is wavelength (m)

As frequency increases:

- Throughput increases
- Antenna size decreases
- Spectrum band width increases
- Susceptibility to rain fading increases

| Spectrum | Advantages | Disadvantages | Notes |
|---|---|---|---|
| **Lower in Spectrum**<br>**L, S, C, X**<br>*(robust)* | • Frequently used with small omni-antennas<br>• Less susceptible to atmospheric effects (eg, rain, fog, snow) | • More power required<br>• Lower throughput<br>• Larger HGA size | • NASA/DoD use S- & X-bands<br>&nbsp;&nbsp;• Used for low or high rate data<br>• GPS, comm. satellites, & mobile phones use L-band<br>• TV broadcasting uses C-band |
| **Higher in Spectrum**<br>**Ku, K, Ka**<br>*(high-performance)* | • Lower power required<br>• Higher throughput<br>• Smaller HGA size | • More susceptible to atmospheric effects (eg, rain) | • Communications/NASA use Ka-band<br>&nbsp;&nbsp;• Used for high rate-data<br>• Satellite comm. & direct broadcast use Ku-band<br>• K-band avoided due to atmosphere |

**Figure description:** The RF-band diagram orders L, S, C, X, Ku, K, and Ka by wavelength and frequency. It emphasizes the trade between robust lower-frequency communication and higher-performance higher-frequency communication.

---

# 7. Communications Terminology

> **Source: Slide 14**

## Uplink, Downlink, Crosslink

- Communication up/down from the ground across via relay to other spacecraft

## Carrier

- Radio frequency (RF) source used to carry information
- Frequency:

```math
f = \frac{c}{\lambda}
```

- Typically in units of Hz; that is, cycles/second

## Modulation

- The process by which an input signal varies the characteristics of a carrier wave, including the amplitude, phase or frequency
- Spacecraft downlinks typically use phase modulation, where the amplitude/frequency remain the same and the phase (ie, signal level) is changed

## Demodulation

- The process for restoring the original input signal

## Bit Error Rate (BER)

- Frequency/probability of a bit error rate
- Typical requirement is 10⁻⁵ (ie, 1 in error in 100,000 bits)

**Figure description:** The slide compares amplitude, frequency, and phase modulation. It also shows a carrier wave and a modulating wave, with the modulating wave injecting data into the carrier. The slide notes that phase modulation varies the signal level very slightly.

---

# 8. Isotropic and Anisotropic Radiation

> **Source: Slide 15**

## Isotropic Radiation

Equal power radiated in all directions from the center of sphere with a point source (ie, equipotential electric field at all constant radii).

Surface area of a sphere:

```math
A = 4\pi r^2
```

Therefore, assuming no losses due to inefficiency, a 1 W source will gradually dissipate with:

```math
\frac{1}{r^2}
```

Or, flux density:

```math
\frac{P_t}{4\pi r^2}
```

## Anisotropic Radiation

Radiation where its intensity depends on the direction. Typically described via an antenna gain pattern.

If a transmitter has “gain”, then it transmits a signal in a given direction at an increased level of power than if it were isotropic.

```math
Gain = \frac{A_{\text{effective}}}{A_{\text{isotropic}}}
```

for a given section of the surface area (A).

**Figure description:** Isotropic radiation is shown as equal radiation in every direction from a point source. Anisotropic radiation concentrates energy in selected directions and is represented by an antenna gain pattern.

---

# 9. Effective Isotropic Radiated Power

> **Source: Slide 16**

Effective Isotropic Radiated Power (EIRP) is the resulting transmitted power after all gains & losses during transmission have been factored in, including:

- Antenna gains (Gtransmitted)
- Antenna pointing and/or circuit losses (Lantenna, Lcircuit)

Thus:

```math
EIRP = P_t G_t L_a L_c
```

where:

- **EIRP** and **Pt** are in Watts
- **G** and **L** are unitless factors

In other words, the resulting power is the original power times a series of factors (gains & losses).

Unfortunately, for communications, gains & losses typically vary by several orders of magnitude, such as:

- Gains: × 10–1,000,000
- Losses: × 1/10th to 1/1,000,000th

The result is that it’s far easier to work in decibels (dB).

**Figure description:** The EIRP figure compares an isotropic radiator with an actual directional radiator. The directional antenna concentrates the same peak power into a narrower beam, producing an equivalent isotropic radiated power.

---

# 10. Additional Telecom Equations

> **Source: Slide 17**

## Radiated Power

This equation converts transmitted power (Pt) to radiated power (Pr).

```math
P_r
=
\frac{A_r}{4\pi R^2} P_t G L_a
```

where:

- **R** = Range
- **Ar** = Receiving area
- **Pr** = Power received
- **Pt** = Power transmitted
- **La** = Transmission loss factor
- **G** = Transmission gain

## Telecom Link Equation

Eb/N0 is the final result that determines performance.

- **Eb** is energy per bit
- **N0** is noise power spectral density in Watts per hertz

```math
\frac{E_b}{N_0}
=
P_t L_t G_t
\left(\frac{\lambda^2}{4\pi R_g^2}\right)
L_m G_r L_r
\left(\frac{1}{R_t}\right)
\frac{1}{N_0}
```

where:

- **Pt** = transmit power
- **Lt** = transmit circuit loss
- **Gt** = transmit antenna gain
- **λ** = wavelength
- **Lm** = medium loss
- **Rg** = range
- **Gr** = receive gain
- **Lr** = receive circuit loss
- **Rt** = bit rate

---

# 11. The Decibel

> **Source: Slide 18**

## Background

Consider dB as just a method that is used to express ratios (ie, gains & losses).

dB converts factors (gain or loss) using a Log10 function:

```math
G_{\text{dB}} = 10\log_{10}(G)
```

The inverse of this is:

```math
G = 10^{G_{\text{dB}}/10}
```

## Example 1

10 W increases by a factor of 2:

```text
10 × 2 = 20 W
```

Factor of 2:

```math
10\log_{10}(2) = 3\text{ dB}
```

## Example 2

10 W decreases by a factor of 2:

```text
10 / 2 = 5 W
```

Factor of ½:

```math
10\log_{10}\left(\frac{1}{2}\right)
=
10\log_{10}(1)-10\log_{10}(2)
=
0\text{ dB}-3\text{ dB}
=
-3\text{ dB}
```

This is important because of the properties of log functions.

## Example 3

```text
10 W × 1/100 × 1,000 × 1/500 × 80,000 × 1/20,000 = 0.8 W
```

Whereas:

```text
10 W × (-20 dB + 30 dB - 27 dB + 49 dB - 43 dB) = 0.8 W
```

In other words, we can just add/subtract gains & losses by using dB.

```text
10 W × (-11 dB) = 0.8 W
```

```text
10 W × 0.08 = 0.8 W
```

where:

```math
0.08 = 10^{-11/10}
```

## Two Additional Conventions

Watts can be converted using:

```math
10\log_{10}(\text{Power in W})
```

Power can also be converted to milliWatts in dBm:

```math
10\log_{10}(\text{Power in W}\times1000)
```

```math
=
10\log_{10}(\text{Power in W})
+
10\log_{10}(1000)
```

```text
Power in dB + 30 = Power in dBm
```

---

## Questions from Prior Class

> **Source: Slide 19**

### How much power devoted to telecom?

- Transmitters are typically in the 10 to 100 W class
- Overall power is often 100 to 1,000 W, so 10–20% is probably a good assumption

### In telecommunication, what is a symbol?

- A symbol is a repeated wave pattern that represents a specific # of bits (eg, 1 bit in BPSK)

Examples shown:

- BPSK — 1 bit/symbol
- 8-PSK — 3 bits/symbol
- Phase Key Shifting
- Error Correction Codes

**Figure description:** The slide shows BPSK and 8-PSK examples, phase-key-shifting constellations, and an error-correction-code performance plot.

---

# 12. Link Budget

> **Source: Slide 20**

The link budget is the analysis that “sizes” the telecom system, but it is deeply intertwined with the entire EEIS architecture.

The following parameters are heavily traded very early in the design process to ensure a robust communication architecture.

## Telecom Subsystem

- Frequency Band (eg, L, S, C, X, Ku, K, Ka)
- Radio/Amplifier Power Input (eg, 1–200 W)
- Antenna Type (eg, dipole, parabolic) and sizing (eg, 1–3 m dish)
- Hardware efficiencies & losses (eg, radio, amplifier, circuit, antenna)
- Operations losses (eg, pointing loss)

## Space Loss & Atmospheric Attenuation

- Signal characteristics (eg, band, polarization, ellipticity, etc.) vs. losses

## Ground Station & Architecture

- Antenna network (eg, DSN) and size (eg, 34-m, 70-m)
- Pointing Loss (eg, 0.1 deg)

## Typical Products

- Data Rate (bps), margin (dB), and bit error rate (BER)

**Figure description:** The example link-budget spreadsheet is divided into received power, receiving downlink ratio, telecom/transmitter-point calculations, path calculations, and receiver calculations. It illustrates how gains, losses, transmitter properties, path effects, and receiver properties combine to determine link performance.

---

# 13. Antenna Gain and Patterns

## Antenna Gain

> **Source: Slide 21**

Antennas are generally characterized as:

- “Omni” = “low gain”
  - G ≤ 3 dB
- Directional = “medium gain”
  - 5 ≤ G ≤ 20 dB
- “high gain”
  - 20 dB ≤ G

Beam width (ϕ) = angle between -3 dB (half power) points relative to power on boresight axis.

Ideal (uniform) beam illuminating 1 deg² has a gain of:

```text
41,253 (46.2 dB)
```

Ideal:

```math
G\phi^2 = 4\pi\left(\frac{180}{\pi}\right)^2 = 41{,}253\ \text{deg}^2
```

Real:

```math
G\phi^2 = \eta_A 41{,}253\ \text{deg}^2
```

where:

- **ϕ** = “Field of View” (FOV)

**Figure description:** The slide shows representative dipole, helical, pyramidal, and parabolic-reflector antennas.

---

## A Typical Antenna Pattern

> **Source: Slide 22**

The antenna-pattern figure identifies:

- Boresight axis
- Main beam gain (G)
- -3 dB beamwidth
- 1st sidelobe
- Near-in sidelobes
- Far sidelobes
- Backlobes
- Cross-polarization region due to dish curvature
- 0 dB isotropic level
- Rear region around axis

**Figure description:** The main beam is centered on the boresight axis. The -3 dB beamwidth defines the half-power region. Sidelobes and backlobes represent lower-level radiation outside the main beam.

---

# 14. Atmospheric Attenuation

## Atmospheric Attenuation

> **Source: Slide 23**

- Peaks due to resonance of molecules
- Vibration frequency of Molecule = radiation frequency at peak
- Peaks at 22 and 185 GHz due to water
- Peaks at 60 and 120 GHz due to Oxygen
- Attenuation due to absorption and scattering from suspended particles

---

## Attenuation vs. Frequency

> **Source: Slide 24**

The slide identifies:

- < 0.1 GHz negligible
- > 5 GHz significant
- > 20 GHz severe
- Mostly due to water and oxygen
- Decreases with altitude
- Increases with lower terminal elevation angle
- Between peaks are called windows

**Figure description:** The graph plots theoretical one-way zenith attenuation in dB against frequency in GHz for several altitudes. Strong water and oxygen absorption lines produce attenuation peaks, while lower-attenuation regions between the peaks form communication windows.

---

# 15. Trajectory and Field-of-View Impacts

## Trajectory Impacts on Telecom

> **Source: Slide 25**

**Figure description:** Four plots show how the Earth-spacecraft geometry changes throughout a cruise trajectory. The plots include Earth range, Sun-Earth-probe angle, Earth-spacecraft-Sun angle, and related geometry versus time. The varying range and angular geometry directly affect telecom link performance, antenna pointing, and communication opportunities.

---

## Fields of View Impacts

> **Source: Slide 26**

- Interference with fields of view effect antenna patterns.
- Other items on nadir deck effect pattern. Objects are same order as the wavelength ~ .75m.

**Figure description:** The slide compares the MRO Flight UHF Antenna by itself with the antenna and radome mounted on the MRO nadir deck. Nearby spacecraft hardware can alter the antenna pattern because the objects are comparable in scale to the RF wavelength.

---

# 16. Mars Rover Telecom

> **Source: Slide 27**

## Typical Curiosity Data Rates

- 2 Mbps via RUHF
- 500 bps via RHGA
- 10 bps via RLGA

**Figure description:** Curiosity is shown with its RUHF, RLGA, and RHGA locations identified. The comparison demonstrates the major data-rate differences between the rover's UHF relay and direct-to-Earth high- and low-gain communication paths.

---

# 17. RF Compatibility

> **Source: Slide 28**

- All subsystems and instruments are required to avoid conducted and radiated emissions and susceptibilities.
- RF systems, communications and instruments, are intended to radiate and be susceptible at specific frequencies.
- Couplings between each element at each frequency and harmonics must be estimated and controlled.
- Filters must be added in the design.
- S/C system test must include complete self-compatibility test, including flight configuration, thermal blankets, and payload.

---

# 18. Galileo HGA Failure Case Study

## Galileo Mission and Near Mission Failure

> **Source: Slide 29**

### Galileo

- Launched in 1989 from the Space Shuttle Atlantis
- Jupiter Orbit Insertion (JOI) in 1995
- Controlled entry into Jupiter in 2003

### Scientific Discoveries

- Intense radiation environment
- Liquid ocean under Europa ice
- Io’s active volcanos
- Ganymead’s magnetic field

### Near Mission Failure

- In 1991, the operations team tried and failed to fully deploy the 4.8-m High Gain Antenna

**Figure description:** Galileo is shown with its large deployable HGA. Images of Europa and Io represent major science results from the mission.

---

## Trajectory Overview

> **Source: Slide 30**

**Figure description:** Galileo's trajectory to Jupiter includes launch, Venus flyby, two Earth flybys, asteroid encounters, probe release, Jupiter arrival, and the later orbital tour. The complex trajectory was used to build sufficient energy to reach Jupiter.

---

## Flight System Overview

> **Source: Slide 31**

The flight-system diagram identifies:

- High Gain Antenna
- Low Gain Antenna
- Telecommunications

**Figure description:** Galileo's major spacecraft elements are labeled, including the stowed/deployable HGA, LGA, propulsion, science instruments, probe relay antenna, magnetometer boom, and RTGs.

---

## Telecommunications Overview

> **Source: Slide 32**

The telecom architecture is divided into:

- S-/X-band Antenna (SXA) Subsystem
- Radio Frequency Subsystem (RFS)
- Modulation/Demodulation Subsystem (MDS)
- X- to S-band Downconverter

### Carrier Frequencies

- S-band Uplink: 2.1 GHz
- S-band Downlink: 2.3 GHz
- X-band uplink: 7.2 GHz
- X-band downlink: 8.4 GHz

**Figure description:** The detailed block diagram traces the Galileo telecom architecture through the antenna, RF, and modulation/demodulation subsystems.

---

## Component Terminology

> **Source: Slide 33**

- **Diplexer:** Routes two signals into one path based on frequency (typically reciprocal)
- **Switch:** Allows the spacecraft to switch between two RF paths (eg, LGA vs. HGA)
- **Filters:** Allow/reject certain frequencies. There are four types: high-pass, low-pass, band-pass, and band-reject
- **TWTA:** Traveling Wave Tube Amplifier is a specialized vacuum tube that is uses additional power (in W) to amplify RF signals
- **Down-converter:** Converts RF signals to a lower frequency range.
- **Hybrid Coupler:** Splits power evenly (3 dB) between two ports
- **Exciter:** Generates the modulated waveform that can be radiated to the antenna.
- **RF Oscillator:** Generates the carrier signal that is used for spacecraft communications. An ultra-stable oscillator (USO) is a highly stable version generally used for science.
- **Modulator:** Converts signals from digital to RF
- **Convolutional Code:** Type of error-correcting encoding that is used to increase the robustness of spacecraft communications.
  - Andrew Viterbi proposed the Viterbi algorithm to decode convolutionally encoded data.
  - Convolutional codes are being replaced by Turbo codes.

> These definitions are intended to be more readable, but slightly less accurate.

---

## LGA and HGA Signal Paths

> **Source: Slides 34–37**

The sequence of slides highlights the following paths through the Galileo telecom block diagram:

- LGA S-band Uplink Path
- HGA S-band Uplink Path
- Low-rate LGA S-band Downlink Path
- High-rate HGA X-band Downlink Path
  - Redundancy uses RCP/LCP polarization

The final comparison identifies:

- High-rate HGA X-band Downlink Path: **134 kbps**
- Low-rate LGA S-band Downlink Path: **< 40 bps**

**Figure description:** Colored paths are progressively overlaid on the Galileo telecom architecture to show how uplink and downlink signals travel through different antennas and electronics. The comparison demonstrates why loss of the HGA represented such a severe reduction in downlink capability.

---

## Redundancy

> **Source: Slide 38**

### Redundant Units

- 2 LGAs (1 not shown)
- 2 complete paths for low-rate telemetry
- All critical electrical uplink/downlink components are redundant

### Single-String

- USO
- HGA

**Figure description:** Dashed boxes identify redundant regions of the Galileo telecom architecture. The HGA and USO are identified as single-string elements.

---

# 19. Modern Telecom Hardware

## Since Galileo

> **Source: Slide 39**

### SDST

Unifies the following functions:

- Receiver
- Command detector
- Telemetry modulator
- Exciters

Note that encoding and compression is typically performed by the C&DH subsystem.

### SSPA or TWTA

- Solid State vs. Traveling Tube
- Uses power to amplify the signal
- Often range from 25 W to 100 W

### Result

- The above components greatly simplify modern telecom systems
- Typically, just combine these with:
  - Antennas
  - Diplexers & Switches (waveguide/coaxial)

**Figure description:** The slide shows a Small Deep Space Transponder (SDST) and a Solid State Power Amplifier (SSPA) as representative modern telecom hardware.

---

## Galileo Initial Anomaly

> **Source: Slide 40**

- In 1991, after the Venus flyby and beyond 1 AU, the team executed a sequence to deploy the high gain antenna
- While the telemetry showed that the motors operated at higher-than-expected power levels for 8 minutes, they were unable to deploy the antenna.
- 3 ribs were “stuck”
  - Can occur when there is insufficient lubricant

**Figure description:** The expected fully deployed HGA is compared with the actual partially deployed configuration. The diagram identifies the stowed ribs and the partially deployed rib geometry.

---

## Probable Root Cause

> **Source: Slide 41**

### Probable root cause

- Loss of lubricant occurred due to the vibration that the antenna experienced on the truck as it made multiple trips to/from KSC
  - Failed ribs were closest to the flatbed trailers that carried Galileo
  - The lubricants were not checked or replaced prior to launch

### Timeline

- Dec, 1985 — Originally shipped from JPL to KSC
- Jan, 1986 — Loss of Space Shuttle Challenger
- Late 1986 — Returned to JPL
- Mid, 1989 — Shipped to KSC
- Oct, 1989 — Launched on Space Shuttle Atlantis
- Early 1991 — HGA deployment failed

**Figure description:** A U.S. map illustrates the repeated transportation between JPL and KSC. A spacecraft transport photograph is also shown.

---

## Attempts to Unstick HGA

> **Source: Slide 42**

- Changing orientation towards/away from sun to change temperature
- Repeatedly turning on/off the motors would double the torque (13,000 attempts)
- Inducing a maximum spin rate of 10 rpm & hammering the motors
- Final attempts coincided with release of the probe, probe deflection maneuver, and JOI
- None were successful…
- At Jupiter, downlink rate would be 10 bps, which would effectively end the mission

---

## Transmission Improvements & Results

> **Source: Slide 43**

From 1993 to 1996, extensive new flight and ground software was developed and DSN stations were enhanced to increase the transmission rate.

### Improvements

1. Increased S-band signal to noise ratio (antenna arrays & ultra-low noise receivers)
2. Improved efficiency of radio modulation
3. Improved channel codes (ie, reduce Eb/No) so to minimize BER
4. Aggressively apply data compression techniques

### Result

- 1–3 improved the downlink rate from 10 bps to 160 bps
- 4 improve the rate to 1,000 bps
- These improvements allowed Galileo to meet 70% of its science goals

> Beyond Galileo, these changes both significantly improved NASA deep space communications and changed how the science community viewed data compression.

---

# 20. Telecom Hardware Estimate

> **Source: Slide 44**

## Primary Components — Part of Link Budget

### Radio / Transponder

- Find lowest mass, power, & cost system that meets requirements

### Power Amplifier

- Use a TWTA or SSPA (often depends on specific design and/or heritage)
- Otherwise, just based on lowest mass/cost/power system that provides desired RF power

### Antennas

- High Gain antenna for primary data uplink/downlink
- Medium gain antenna when high gain not required due to lower rate or nearer range
- Low Gain antenna for fault scenarios (~360-deg coverage)

## Additional Hardware

### Diplexers

- Routes different frequencies
- Uplink/downlink, S- vs. X-band
- 0.7 kg each (ballpark)

### Waveguide Transfer Switches

- Configures between different antennas
- Depends on design, but 1 per 1–2 antennas
- 1 kg each (ballpark)

### Coaxial Cable, Filters, etc.

- ~5% of telecom mass

**Figure description:** The OSIRIS-REx telecom subsystem block diagram is shown as a reference architecture for estimating radios/transponders, amplifiers, antennas, switches, diplexers, and supporting RF hardware.

---

# 21. Telecom Design Steps

> **Source: Slide 45**

## Review & Understand Design Information

- Mission Description and/or Concept of Operations
- System and Subsystem Requirements
  - ConOps, mission geometry, Earth-S/C range
  - Payload & engineering data requirements
  - Fault scenarios

## Create a Preliminary Design

- Identify the driving uplink/downlink scenarios
- Create link budgets for each
  - Optimize with respect to band, antenna types & sizes, RF power, ground station assumptions, etc.
- Create block diagram
- Create component mass list

## Review & Iterate (w/broader team)

- Revisit other options & trades

---

# 22. Optical Communication

## Questions from Last Week

> **Source: Slide 47**

### Telecom is a critical subsystem, but are there any spacecraft that might not need it or where it’s less important?

- Thoughts from the class?

### Are there any new innovations/improvements being made to the way s/c communicate either with other s/c or ground stations?

- Most significant is optical communication… (next chart)
- Additionally, there is a continuing drive towards higher bandwidths and higher power systems, which have resulted in an increasing amount of data

---

## Optical Communication

> **Source: Slide 48**

- Deep Space Optical Communications (DSOC) is a laser space communication system in development meant to improve communications performance 10 to 100 times over the current radio frequency technology without incurring increases in mass, volume or power.
- Mass 29 kg, power < 100 W, 0.2–200 Mbps

**Figure description:** The DSOC architecture shows an optical communications path between a spacecraft flight laser transceiver and Earth-based optical ground stations, including the Deep Space Network.

---

# 23. Additional Class Questions

## 3 dB Beamwidth

> **Source: Slide 49**

- 3 dB Beamwidth is the angle at which the signal is a half-power
- For example:

```math
dB = 10\log_{10}(\text{unitless factor})
```

The slide shows:

```text
3 dB = 10 Log10(0.5)
```

### For a Parabolic Antenna

```math
BW = \frac{70\lambda}{d}
```

where:

- **BW** = antenna beamwidth (deg)
- **λ** = wavelength (m)
- **d** = antenna diameter (m)

The antenna gain-pattern figures identify:

- Main Lobe
- Side Lobes
- Back Lobe
- Beamwidth

Magnitudes are in dB; ie, logarithmic scales.

---

## Telecom Block Diagrams and Polarization

> **Source: Slide 50**

### “When looking at a telecommunications block diagram, are the block always pieces of hardware?”

- For telecom & most subsystems, yes. For GN&C and Software, no.
- Note that block diagrams can be used in different ways (hardware, software, functional, organizational, etc.) Important to choose the right “architectural view or perspective” depending on the problem.

### “If switching between RCP and LCP may cause problems with receiving the signal on the ground, why do it?”

- In general, using polarization minimizes interference from other sources and expands the available bandwidth for communications.
- I believe it’s also used, on occasion, when uplinking/downlinking at the same time.

**Figure description:** The slide shows circular-polarization illustrations for electric and magnetic fields and the propagation of a rotating electromagnetic field.

---

## Simultaneous Transmit/Receive and Modulation

> **Source: Slide 51**

### “Can an antennas receive and send out information at the same time?”

- Yes. I believe there is a slight loss when simultaneously transmitting/receiving data
- Note that the diplexer is responsible for routing the appropriate signals (band & direction)

### “How is data modulation done and why is it important when downlinking?”

- Transmitting data via radio waves requires us to translate real data (ie, bits) into the RF signal. This is what modulation is (versus an electrical line where digital signals can be transmitted directly).

**Figure description:** A modulating wave is combined with a carrier wave to create the transmitted modulated RF signal.

---

## Telecom and C&DH Signal Flow

> **Source: Slide 52**

### “For clarification, does the [Telecom] subsystem receive RF signals from the uplink path, transform them into digital signals and then send these digital signals to the C&DH subsystem?”

- Yes — this is exactly how it works.

### “And then when the [Telecom] subsystem is sending signals on the downlink path back to earth, do these signals originally come from the C&DH subsystem?”

- Yes — they are either collected and/or generated by FSW, encoded, and then sent to telecom.

**Figure description:** The Galileo telecom block diagram is used again to show the relationship between RF signal paths and the digital C&DH interface.

---

# Lecture Summary

> **Source: Full Lecture**

The telecom subsystem provides the spacecraft's **uplink, downlink, ranging, antenna selection, and RF communication capability**, while the EEIS extends that architecture from the original data source through the spacecraft, transmission path, ground station, and final data use.

Key takeaways:

- **Telecom Hardware:** Radios/transponders, amplifiers, diplexers, switches, and HGA/MGA/LGA antennas form the core telecom architecture.
- **EEIS:** The full information path includes data formatting, modulation, RF transmission, path losses, ground reception, decoding, and final data use.
- **RF Bands:** Frequency affects throughput, antenna size, required power, and atmospheric susceptibility.
- **Link Budgets:** Telecom performance is sized by accounting for transmitter power, antenna gains, circuit losses, space loss, atmospheric attenuation, ground-station performance, data rate, BER, and margin.
- **Antenna Performance:** Gain and beamwidth determine how strongly and how narrowly an antenna directs RF energy.
- **Spacecraft Integration:** Trajectory, range, antenna FOV, spacecraft geometry, RF compatibility, pointing, redundancy, and fault scenarios all affect telecom performance.
- **Galileo:** The HGA failure demonstrates how a single mechanical deployment problem can drastically reduce communications performance and require major software, coding, ground-system, and data-compression changes.
- **Telecom Design:** The design process identifies driving uplink/downlink scenarios, creates link budgets, selects hardware, develops the block diagram and mass estimate, and iterates with the broader spacecraft team.