# Telecommunications and the End-to-End Information System

**Course:** ASTE-331a — Spacecraft Systems Engineering  
**Lecture:** 05 — Telecommunications (Telecom) and the End-to-End Information System (EEIS)  
**Instructors:** Jim Chase, Danielle Marsh    
**Source:** `331_05_Telecom_20251024.pdf`

---

## Table of Contents

- [1. Telecom Overview](#1-telecom-overview)
- [2. Telecom Hardware](#2-telecom-hardware)
- [3. Mission Telecom Examples](#3-mission-telecom-examples)
- [4. End-to-End Information System](#4-end-to-end-information-system)
- [5. Electromagnetic and RF Spectrum](#5-electromagnetic-and-rf-spectrum)
- [6. Communications Definitions](#6-communications-definitions)
- [7. Radiation, Gain, and EIRP](#7-radiation-gain-and-eirp)
- [8. Telecom Link Equations](#8-telecom-link-equations)
- [9. Decibels](#9-decibels)
- [10. Link Budget](#10-link-budget)
- [11. Antenna Gain and Patterns](#11-antenna-gain-and-patterns)
- [12. Atmospheric Attenuation](#12-atmospheric-attenuation)
- [13. Trajectory and Field-of-View Effects](#13-trajectory-and-field-of-view-effects)
- [14. Mars Rover Communications](#14-mars-rover-communications)
- [15. RF Compatibility](#15-rf-compatibility)
- [16. Galileo High-Gain-Antenna Failure](#16-galileo-high-gain-antenna-failure)
- [17. Modern Telecom Hardware](#17-modern-telecom-hardware)
- [18. Telecom Hardware Estimation](#18-telecom-hardware-estimation)
- [19. Telecom Design Process](#19-telecom-design-process)
- [20. Optical Communications](#20-optical-communications)
- [21. Additional Class Questions](#21-additional-class-questions)
- [22. Lecture Summary](#22-lecture-summary)

---

# 1. Telecom Overview

> **Source: Slides 2–4**

Telecommunications provides communication to and from the spacecraft, typically with Earth but sometimes with other spacecraft. Primary functions include command reception and detection, telemetry modulation and transmission, bandwidth selection, antenna pointing, carrier tracking, ranging, and occasional radio-science use. The primary driver is typically spacecraft-Earth distance.

## Common Components

- Radio/transponder
- Amplifier
- High-gain antenna (HGA)
- Medium-gain antenna (MGA)
- Low-gain antenna (LGA)

## Key Trades

- Fixed vs. articulated antennas
- Data rate and data volume
- Link budget and antenna sizing
- Radio band and power
- Heritage
- Mass, power, cost, transmission power, data performance, and margin

The GRAIL example uses an S-band transponder, LGA, and miscellaneous hardware totaling approximately 5 kg.

Communications is critical for nearly every spacecraft and is one of the subsystems most likely to be redundant. Architectures include direct ground communication and relay communication through systems such as TDRS or Mars orbiters.

### Detailed Functions

**Command reception**
- Acquire and track uplink
- Detect uplink data
- Forward commands to avionics

**Telemetry**
- Receive data from avionics
- Synchronize, packetize, encode, encrypt, and modulate the downlink

**Antenna management**
- Point antennas
- Select antenna/band
- Safe mode typically defaults to LGA

---

# 2. Telecom Hardware

> **Source: Slide 5**

## Avionics Subsystem

C&DH serves as the digital interface to telecom. A ULDL card can decode uplink data and relay it to FSW or directly to hardware.

## Radio / Transponder

Example: SDST.

The transponder converts between digital spacecraft information and RF.

```text
C&DH ↔ Radio/Transponder ↔ Amplifier ↔ Diplexer ↔ RF Switch ↔ Antenna
```

## Amplifier

An RF power amplifier increases low-power RF to a level capable of driving the antenna. Example: TWTA.

## Diplexer

A passive device that combines or separates uplink/downlink signals based on frequency.

## Waveguide Transfer Switch

Routes RF to a selected device or antenna.

## Antennas

**HGA**
- Usually parabolic
- High data rate
- Narrow pointing requirement

**MGA**
- Often a horn
- Intermediate data rate and pointing requirement

**LGA**
- Broad, approximately 360-degree coverage
- Low data rate
- Critical/fault communications

The OSIRIS-REx diagram shows redundant SDSTs, TWTAs, diplexers and switches connected to HGA, MGA and LGAs.

---

# 3. Mission Telecom Examples

> **Source: Slides 6–9**

## MRO Waveguide Transfer Switch Anomaly

MRO uses a WTS to route a 100-W RF downlink from one of two amplifiers to one of two antennas. Five months after Mars arrival, a WTS failed to actuate and became stuck between positions.

Effects:
- Approximately 1 dB RF loss
- Approximately 15 °C temperature increase
- FSW maintained configuration by switching to the redundant X-band amplifier

Probable sequence:
1. Conductive debris accumulated on polyimide-tape vent windows.
2. RF breakdown decomposed the tape.
3. Debris entered the WTS.
4. The switch bound.
5. RF performance decreased by approximately 1 dB.

The approximately 3-dB system margin accommodated the loss. Frequent use—about 720 actuations—exacerbated the process.

**Lesson:** avoid polyimide-tape windows for contamination control on WTS vents.

## Phoenix

Mission to investigate the Martian arctic.

**X-band cruise**
- Two SDST radios
- Two 15-W SSPAs
- One MGA
- Separate Rx and Tx LGAs
- About 2100 bps near Earth to 40 bps near Mars

**UHF EDL/surface**
- Helix and monopole antennas
- About 32 kbps during EDL to 256 kbps on surface

## Juno

- Two-way X-band communications/ranging
- Two SDSTs and two TWTAs
- 1,745 bps launch
- 100 bps cruise
- 18 kbps HGA at Jupiter
- 10 bps safe mode
- Separate single-string Ka-band gravity-science link
- 2.5-m HGA, MGA, and three LGAs

---

# 4. End-to-End Information System

> **Source: Slides 10–11**

EEIS includes all functions, formats, conversions, gains, and losses from initial data selection to final reception and use.

```text
Source Data
↓
Formatting / Packetization
↓
Encoding
↓
RF Modulation
↓
Spacecraft Telecom
↓
Space Propagation
↓
Atmosphere
↓
Ground Station
↓
Demodulation / Decoding
↓
Recovered Data
```

## Flight-Ground Interface Control Document

The FG-ICD defines interfaces and data formats throughout the flight-ground path. Data is transmitted efficiently in binary and converted at multiple stages.

The Titan-image example visually traces an image through binary data, packet structure, modulation, relay via Cassini, ground reception, and image reconstruction.

## Link Budget

The link budget captures all gains and losses between source and receiver and determines achievable data rate for a specified BER.

---

# 5. Electromagnetic and RF Spectrum

> **Source: Slides 12–13**

The EM spectrum describes radiation in terms of frequency, wavelength, and photon energy. Space applications include radiation, power generation, thermal control, science, radar, and communications.

```math
f = \frac{c}{\lambda}
```

where `f` is frequency, `c` is speed of light, and `λ` is wavelength.

Common RF bands progress approximately:

```text
L → S → C → X → Ku → K → Ka
```

Higher frequency generally provides:
- Higher throughput
- Smaller HGA
- More available spectrum
- Greater susceptibility to atmospheric/rain effects

Lower-frequency L/S/C/X bands are generally more robust. NASA/DoD commonly use S and X. Ka supports high-rate NASA communications. K is avoided because of atmospheric attenuation.

---

# 6. Communications Definitions

> **Source: Slides 14 and 19**

- **Uplink:** ground to spacecraft
- **Downlink:** spacecraft to ground
- **Crosslink:** spacecraft-to-spacecraft or relay communication
- **Carrier:** RF source carrying information
- **Modulation:** varies amplitude, phase, or frequency of a carrier according to information
- **Demodulation:** restores the original information
- **BER:** probability/frequency of bit errors

Representative requirement:

```math
BER = 10^{-5}
```

approximately one erroneous bit in 100,000.

A **symbol** is a repeated wave pattern representing bits:
- BPSK: 1 bit/symbol
- 8-PSK: 3 bits/symbol

Typical transmitter power is roughly 10–100 W. The lecture suggests 10–20% of total spacecraft power as a rough telecom assumption.

---

# 7. Radiation, Gain, and EIRP

> **Source: Slides 15–16**

For isotropic radiation:

```math
A = 4\pi r^2
```

and flux density is:

```math
S = \frac{P_t}{4\pi r^2}
```

so power density decreases with inverse square of range.

Directional radiation is anisotropic and characterized by an antenna gain pattern.

Conceptually:

```math
G = \frac{A_{effective}}{A_{isotropic}}
```

## EIRP

Effective Isotropic Radiated Power includes transmit power, antenna gain, and transmission-side losses:

```math
EIRP = P_t G_t L_a L_c
```

Communications gains/losses span many orders of magnitude, motivating logarithmic dB notation.

---

# 8. Telecom Link Equations

> **Source: Slide 17**

Received power:

```math
P_r = \frac{A_r}{4\pi R^2} P_t L_a
```

The central link-performance metric is:

```math
\frac{E_b}{N_0}
```

where `E_b` is energy per bit and `N_0` is noise power spectral density.

The lecture presents:

```math
\frac{E_b}{N_0}
=
P_t L_t G_t
\left(\frac{\lambda^2}{4\pi R_g^2}\right)
L_m G_r L_r
\left(\frac{1}{R_t}\right)
\frac{1}{N_0}
```

Parameters include transmit power, circuit losses, antenna gains, wavelength, medium loss, range, receive gain, bit rate, and noise.

---

# 9. Decibels

> **Source: Slide 18**

```math
G_{dB} = 10\log_{10}(G)
```

Inverse:

```math
G = 10^{G_{dB}/10}
```

A factor of two gain is approximately +3 dB; a factor of one-half is approximately -3 dB.

The key benefit is that multiplicative gains and losses become additive/subtractive dB terms.

For the lecture's example, a net -11 dB corresponds to:

```math
10^{-11/10} \approx 0.08
```

so 10 W becomes approximately 0.8 W.

For milliwatt reference:

```math
P_{dBm} = 10\log_{10}(1000P_W)
```

---

# 10. Link Budget

> **Source: Slide 20**

The link budget sizes the telecom system and is tightly coupled to the EEIS.

## Telecom Inputs

- Frequency band
- Radio/amplifier power
- Antenna type and size
- Hardware efficiency/losses
- Pointing loss

## Path Inputs

- Range
- Band
- Polarization
- Ellipticity
- Space loss
- Atmospheric attenuation

## Ground Inputs

- Network such as DSN
- 34-m or 70-m antenna
- Pointing loss

## Outputs

- Data rate
- Margin
- BER

The slide's spreadsheet organizes calculations into transmitter, path, receiver, total received power, and resulting downlink rate.

---

# 11. Antenna Gain and Patterns

> **Source: Slides 21–22 and 49**

Approximate gain categories:

```math
G < 3\ dB
```

for low gain,

```math
5\ dB \le G \le 20\ dB
```

for medium gain, and

```math
G \ge 20\ dB
```

for high gain.

Beamwidth is the angle between the -3-dB half-power points around boresight.

A typical antenna pattern contains:
- Main beam
- Boresight
- First sidelobe
- Near-in sidelobes
- Far sidelobes
- Backlobes
- Cross-polarization regions

For a parabolic antenna:

```math
BW = \frac{70\lambda}{d}
```

where `BW` is beamwidth in degrees, `λ` is wavelength in meters, and `d` is antenna diameter.

Larger diameter or shorter wavelength gives narrower beamwidth and generally higher gain, but tighter pointing requirements.

---

# 12. Atmospheric Attenuation

> **Source: Slides 23–24**

Atmospheric attenuation peaks occur because of molecular resonance.

Water peaks:
- ~22 GHz
- ~185 GHz

Oxygen peaks:
- ~60 GHz
- ~120 GHz

Attenuation is caused by absorption and scattering.

The lecture summarizes:
- <0.1 GHz: negligible
- >5 GHz: significant
- >20 GHz: severe
- Decreases with altitude
- Increases at lower terminal elevation angle
- Low-attenuation regions between peaks are called windows

---

# 13. Trajectory and Field-of-View Effects

> **Source: Slides 25–26**

Trajectory affects telecom because spacecraft-Earth range changes dramatically over a mission. Cassini plots illustrate variations in range and Earth-spacecraft-Sun angle during gravity assists and cruise.

These changes affect:
- Free-space loss
- Data rate
- Required gain
- Required transmit power
- Ground station
- Antenna pointing

Spacecraft hardware can also distort antenna patterns. The MRO UHF example shows that neighboring nadir-deck hardware, with dimensions comparable to the roughly 0.75-m wavelength, affects antenna performance.

---

# 14. Mars Rover Communications

> **Source: Slide 27**

Representative Curiosity rates:

| Link | Rate |
|---|---:|
| RUHF | 2 Mbps |
| RHGA | 500 bps |
| RLGA | 10 bps |

This shows the large performance difference between relay, direct high-gain, and low-gain fault communications.

---

# 15. RF Compatibility

> **Source: Slide 28**

Spacecraft subsystems must avoid unacceptable conducted/radiated emissions and susceptibility.

RF communications and instruments intentionally radiate at selected frequencies, so coupling at operating frequencies and harmonics must be estimated and controlled.

Design implications:
- Add filters where required
- Evaluate subsystem interactions
- Perform complete spacecraft self-compatibility testing
- Test flight configuration including thermal blankets and payload

---

# 16. Galileo High-Gain-Antenna Failure

> **Source: Slides 29–43**

Galileo launched in 1989, entered Jupiter orbit in 1995, and was intentionally entered into Jupiter in 2003.

Its science included Jupiter's radiation environment, Europa's subsurface ocean evidence, Io volcanism, and Ganymede's magnetic field.

In 1991, the 4.8-m HGA failed to fully deploy.

## Telecom Architecture

Major sections:
- S-/X-band Antenna subsystem
- Radio Frequency Subsystem
- Modulation/Demodulation Subsystem
- X-to-S downconverter

Carrier frequencies:

| Link | Frequency |
|---|---:|
| S uplink | 2.1 GHz |
| S downlink | 2.3 GHz |
| X uplink | 7.2 GHz |
| X downlink | 8.4 GHz |

## Component Terminology

- **Diplexer:** routes signals by frequency
- **Switch:** selects RF paths
- **Filter:** passes/rejects frequency regions
- **TWTA:** traveling-wave-tube RF amplifier
- **Downconverter:** converts RF to lower frequency
- **Hybrid coupler:** splits power evenly, about 3 dB
- **Exciter:** generates modulated waveform
- **RF oscillator:** carrier source
- **USO:** ultra-stable oscillator used for highly stable reference/science
- **Modulator:** converts digital information into RF modulation
- **Convolutional code:** error-correcting code; Viterbi algorithm used for decoding

## Signal Paths

LGA S-band uplink and HGA S-band uplink feed receiver/command chains.

The intended high-rate HGA X-band downlink supported approximately:

```text
134 kbps
```

The low-rate LGA S-band downlink supported:

```text
< 40 bps
```

Redundancy used RCP/LCP polarization.

## Redundancy

Redundant:
- Two LGAs
- Two low-rate telemetry paths
- Critical electrical uplink/downlink components

Single-string:
- USO
- HGA

## Initial Failure

After the Venus flyby and beyond 1 AU, deployment was commanded.

- Motors operated about 8 minutes
- Power was higher than expected
- Three ribs remained stuck
- HGA remained partially deployed

## Probable Root Cause

The lecture identifies lubricant loss due to transportation vibration during repeated JPL/KSC truck trips.

- Failed ribs were closest to the flatbed trailers
- Lubricants were not checked/replaced before launch

Timeline:
- Dec. 1985: JPL → KSC
- Jan. 1986: Challenger loss
- Late 1986: returned to JPL
- Mid-1989: shipped to KSC
- Oct. 1989: launched
- Early 1991: HGA deployment failure

## Recovery Attempts

- Thermal cycling by changing Sun orientation
- Repeated motor cycling, about 13,000 attempts
- Spin up to 10 rpm
- Hammering motors
- Attempts during probe release, deflection maneuver, and JOI

None deployed the HGA.

At Jupiter the fallback rate would have been roughly 10 bps, effectively threatening the mission.

## EEIS Recovery

From 1993–1996, flight/ground software and DSN were improved:

1. Better S-band SNR using antenna arrays and ultra-low-noise receivers
2. More efficient modulation
3. Better channel coding / lower required `E_b/N_0`
4. Aggressive compression

Results:
- 10 bps → 160 bps from link improvements
- Effective science return to roughly 1,000 bps with compression
- Approximately 70% of science goals achieved

This case demonstrates that mission recovery can come from improving the complete end-to-end information system rather than only the failed spacecraft hardware.

---

# 17. Modern Telecom Hardware

> **Source: Slide 39**

Modern SDST hardware combines:
- Receiver
- Command detector
- Telemetry modulator
- Exciters

C&DH typically performs encoding and compression.

SSPAs or TWTAs provide RF amplification, commonly in the 25–100 W range.

A modern system can therefore be simplified to:

```text
C&DH
↓
SDST
↓
SSPA / TWTA
↓
Diplexer / RF Switches
↓
Antenna
```

---

# 18. Telecom Hardware Estimation

> **Source: Slide 44**

## Primary Components

**Radio/transponder**
- Lowest mass/power/cost unit meeting requirements

**Power amplifier**
- TWTA or SSPA
- Selection depends on heritage and required RF power

**HGA**
- Primary high-rate uplink/downlink

**MGA**
- Moderate-rate/nearer-range operation

**LGA**
- Fault scenarios and wide coverage

## Additional Hardware

**Diplexers**
- Route frequencies and uplink/downlink
- Ballpark: 0.7 kg each

**Waveguide transfer switches**
- Configure antenna paths
- Roughly one per 1–2 antennas
- Ballpark: 1 kg each

**Coax, filters, etc.**
- Ballpark: ~5% of telecom mass

---

# 19. Telecom Design Process

> **Source: Slide 45**

## Review Design Information

- Mission description / ConOps
- System/subsystem requirements
- Mission geometry
- Earth-spacecraft range
- Payload and engineering data
- Fault scenarios

## Preliminary Design

- Identify driving uplink/downlink cases
- Create link budget for each
- Optimize band, antenna type/size, RF power, ground assumptions
- Create block diagram
- Create component mass list

## Review and Iterate

Work with the broader team and revisit options and trades.

---

# 20. Optical Communications

> **Source: Slides 47–48**

The lecture identifies optical communication as a major innovation.

Deep Space Optical Communications (DSOC) is described as a laser communication system intended to improve performance approximately:

```text
10–100×
```

over RF without corresponding increases in mass, volume, or power.

Representative lecture values:
- Mass: 29 kg
- Power: <100 W
- Data rate: 0.2–200 Mbps

The DSOC diagram shows a flight laser transceiver communicating with ground laser transmitter/receiver facilities and DSN infrastructure.

---

# 21. Additional Class Questions

> **Source: Slides 49–52**

## 3-dB Beamwidth

The 3-dB beamwidth is the half-power angular width.

```math
dB = 10\log_{10}(factor)
```

For a parabolic antenna:

```math
BW = \frac{70\lambda}{d}
```

## Are Telecom Blocks Always Hardware?

For telecom and most subsystems, usually yes. But block diagrams can represent hardware, software, functions, organizations, or other architectural views.

## Why RCP and LCP?

Polarization can minimize interference and expand available communications bandwidth. The lecture also notes possible use during simultaneous uplink/downlink.

## Can an Antenna Transmit and Receive Simultaneously?

Yes. The lecture notes a possible slight loss, with diplexers routing the appropriate band and direction.

## Why Modulate?

Digital data must be translated into an RF carrier for wireless transmission. Modulation performs this conversion; demodulation recovers the information.

## Telecom-C&DH Interface

Uplink:

```text
RF → Telecom → Digital Data → C&DH / FSW
```

Downlink:

```text
C&DH / FSW → Encoded Data → Telecom → RF → Earth
```

---

# 22. Lecture Summary

> **Source: Slides 1–52**

Telecom provides the spacecraft communication path to Earth and other spacecraft.

A representative modern chain is:

```text
C&DH
↕
Radio / Transponder
↕
Power Amplifier
↕
Diplexer / RF Switching
↕
Antenna
```

The broader EEIS extends from source-data generation through formatting, encoding, modulation, propagation, atmospheric loss, ground reception, decoding, and final data use.

The link budget is the principal sizing analysis. It combines:
- Transmitter power
- Circuit losses
- Antenna gain
- Wavelength
- Range
- Medium loss
- Receiver gain
- Noise
- Bit rate
- BER
- Margin

The central quality metric is:

```math
\frac{E_b}{N_0}
```

Decibels simplify the analysis of multiplicative gains and losses:

```math
G_{dB} = 10\log_{10}(G)
```

High-gain antennas concentrate energy and improve link performance, but narrow the beam and tighten pointing requirements.

Atmospheric attenuation becomes increasingly important at high frequencies, especially around water and oxygen absorption lines.

Trajectory, spacecraft geometry, antenna field of view, RF compatibility, redundancy, ground-station capability, and fault modes all affect telecom architecture.

The Galileo HGA failure demonstrates the importance of designing the entire EEIS. Although the single-string HGA failed, improvements in DSN reception, modulation, coding, compression, flight software, and ground software increased the effective science return from an otherwise mission-ending low-rate link and enabled approximately 70% of Galileo's science goals.

Telecom design is therefore an iterative systems-engineering process:

```text
Mission Requirements
↓
Geometry and Data Needs
↓
Driving Communication Scenarios
↓
Link Budgets
↓
Band / Power / Antenna / Ground Trades
↓
Telecom Architecture
↓
Hardware and Mass Estimate
↓
System Review and Iteration
```

Optical communications such as DSOC represent a future direction with the potential for roughly 10–100× communications-performance improvement over conventional RF technology.
