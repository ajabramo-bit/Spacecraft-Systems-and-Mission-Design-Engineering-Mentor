# Telecommunications (Telecom) and the End-to-End Information System (EEIS)

**Course:** ASTE-331a — Spacecraft Systems Engineering  
**Lecture:** 05 — Telecommunications (Telecom) and the End-to-End Information System (EEIS)  
**Instructors:** Jim Chase, Danielle Marsh    
**Source:** `331_05_Telecom_20251024.pdf`

---

## Lecture Overview

This lecture covers the spacecraft telecommunications subsystem and the End-to-End Information System (EEIS), including telecom functions and hardware, uplink/downlink paths, RF bands, modulation, radiation and antenna gain, EIRP, link equations, decibels, link budgets, antenna patterns, atmospheric attenuation, trajectory and field-of-view impacts, RF compatibility, the Galileo HGA failure case study, telecom hardware estimation, design steps, and optical communication.

The content below is intentionally kept as close to the original slide wording as possible, with slide-source markers throughout for traceability.

---

## Table of Contents

- [1. Telecom Overview](#1-telecom-overview)
- [2. Telecom Hardware and Mission Examples](#2-telecom-hardware-and-mission-examples)
- [3. End-to-End Information System (EEIS)](#3-end-to-end-information-system-eeis)
- [4. Electromagnetic and RF Spectrum](#4-electromagnetic-and-rf-spectrum)
- [5. Communications Definitions and Radiation](#5-communications-definitions-and-radiation)
- [6. EIRP, Link Equations, and Decibels](#6-eirp-link-equations-and-decibels)
- [7. Link Budget and Antenna Performance](#7-link-budget-and-antenna-performance)
- [8. Atmospheric, Trajectory, FOV, and RF Compatibility Effects](#8-atmospheric-trajectory-fov-and-rf-compatibility-effects)
- [9. Galileo HGA Failure Case Study](#9-galileo-hga-failure-case-study)
- [10. Telecom Hardware Estimate and Design Steps](#10-telecom-hardware-estimate-and-design-steps)
- [11. Optical Communication and Class Questions](#11-optical-communication-and-class-questions)
- [Lecture Summary](#lecture-summary)


---

# 1. Telecom Overview


## Telecom Overview (1 of 3)

> **Source: Slide 2**

- Function
  - Provides communication to/from the spacecraft.
Typically with the Earth, but can include other
spacecraft.
- 
Command reception and detection
- 
Telemetry modulation & transmission
- 
Bandwidth selection & antenna pointing
- 
Carrier tracking modes and ranging
  - Occasionally used for radio science
  - Primary driver is typically spacecraft-Earth distance
10/24/2025
2
- GRAIL Example
  - S-band transponder
  - Low-gain antenna (LGA)
  - Misc. hardware
  - Total = ~5 kg
- Common Components
  - Radio/transponder
  - Amplifier
  - Antennas
- 
High-gain (HGA)
- 
Medium-gain (MGA)
- 
Low-gain (LGA)
- Key Trades & Analyses
  - Fixed vs. articulated antennas
  - Data rate & volume analysis
  - Link budget & antenna sizing
  - Radio-band and power level
  - Heritage from prior systems
- Key Parameters
  - Mass, power, and cost
  - Transmission power, data, & margin

## •

> **Source: Slide 3**

Communications is critical for nearly every spacecraft
  - Most likely subsystem to be redundant
  - Direct uplink/downlink comm. with specific ground stations
  - Relay communication, such as using the TDRS network or via MRO (from Mars)
  - Significant increases in communication over the past 30 years (≥ 1 Gbps possible)
10/24/2025
3
Tracking & Data Relay
Satellite (TDRS)
Space Vehicles that use TDRS
- 
ISS, Hubble, NASA LEOs, etc.
- 
Most can also downlink directly…
Direct
Communications
TDRS Relay
Communications
Telecom Overview (2 of 3)

## 10/24/2025

> **Source: Slide 4**

4
Mars Reconnaissance
Orbiter (MRO)
Telecom Overview (3 of 3)
- Functions
  - Command reception and detection
- 
Acquire, track, detect uplink data
- 
Forward command data to avionics
  - Telemetry modulation & transmission
- 
Receive telemetry data from avionics
- 
Modulate downlink signal (synchronize, packetize, encoding, encryption, etc.)
  - Perform antenna pointing
  - Select desired antenna (or band)
- 
In safe-mode, spacecraft will typically default to low gain antennas
  - Carrier tracking modes
  - Ranging

---

# 2. Telecom Hardware and Mission Examples


## 10/24/2025

> **Source: Slide 5**

5
Telecom Hardware Overview
High Gain Antenna (HGA)
Typically, a single parabolic dish that provides high
data rate, but requires narrow pointing control.
Medium Gain Antenna (MGA)
When used, this is typically a horn antenna that
provides higher data rates than an LGA, but less
rigorous pointing requirements than an HGA.
Low Gain Antenna (LGA)
Typically, multiple dipole antennas that ensure
~360-deg coverage at a low data rate that is
adequate for critical uplink/downlink.
Radio/Transponder
An electronics box responsible for:
Uplink: Receiving the formatted bits from C&DH, converting
them to an RF signal, and transmitting to the antennas.
Downlink: Receiving the RF signal from the antennas,
converting them to bits, and relaying to the C&DH system.
[eg, SDST]
Amplifier
An RF power amplifier converts a low-power RF
signal to a higher power RF signal that drives the
spacecraft antennas.
[eg, TWTA]
Diplexer(s)
Passive devices that combine and/or separate
uplink/downlink signals.
DPXR
Avionics Subsystem
The avionics subsystem serves as the interface to the telecom
system. This often consists of an “ULDL” card that decodes and
relays the uplink data to FSW and/or directly to hardware devices.
[eg, C&DH]
Waveguide Transfer Switch(es)
Switches that route an RF signal to a selected
device/antenna.
OSIRIS-REx Telecom Block Diagram
OSIRIS-REx 2.1 m HGA
WTS
RF Signal
Digital Signal
What component in the diagram is not described?
Speculate on its use and when/why it’s used.

## Lesson Learned (#1796)

> **Source: Slide 6**

MRO Waveguide Transfer Switch (WTS) Anomaly
Mission
- 
Mars Reconnaissance Orbiter (MRO) is a spacecraft designed to study the geology and climate
of Mars, provide reconnaissance of future landing sites, and relay data from surface missions
back to Earth. It was launched in August of 2005 and arrived in March of 2006.
- 
The spacecraft continues to operate far beyond its intended design life. Due to its critical role
as a high-speed data-relay for ground missions, NASA intends to continue the mission as long
as possible, at least through the late 2020s.
Driving Event & Root Cause
- 
For the downlink, MRO uses a WTS to route a 100-W RF signal from one of the two power
amplifiers to one of two radiating antennas.
- 
Five months after arrival, the WTS failed to actuate. The onboard software maintained the
commanded downlink configuration by commanding a switch to the redundant X band
amplifier. Telemetry indicates that the switch is stuck between its two nominal positions,
causing the switch rotor to partially block the RF energy passing through the switch. This has
resulted in a downlink RF power loss (~1 dB) and a temperature increase (~15 deg C) caused
by absorption and dissipation of the reflected energy.
- 
The most likely root cause is the following series of events:
1.
Accumulation of conductive debris (flaked plating?) on the polyimide tape windows used for WTS venting
2.
RF breakdown of these surfaces resulting in high temperature decomposition of the tape
3.
Large amount of debris from tape entering the WTS and causing the switch to bind
4.
Reduced performance of RF signal by 1 dB (accommodated by 3 dB of margin)
- 
This process was exacerbated by the frequency of MRO’s use of the switch (720 times)
Lessons Learned
- 
Avoid using polyimide tape windows for contamination control on WTS vents
- 
Many additional recommendations on analysis & design
Source: JPL/NASA Lessons Learned
- 
https://llis.nasa.gov/lesson/1796
10/24/2025
6
3
4
1
2
1 db RF loss
Tape & WTS pictures show testing
that was completed as part of the
anomaly investigation

## Phoenix Telecom Subsystem (X-Band)

> **Source: Slide 7**

10/24/2025
7
Source: “Phoenix Telecommunications”, DESCANSO Series, 2010
Mission Description
- NASA science mission to investigate the geologic
history and biological potential of Martian arctic
- Launch in 2007, arrived May 2008, ended Nov. 2008
Telecom System
- 2-way X-band for communication & ranging in Cruise
- 2 SDST radios and 2 15-W SSPA amplifiers
- 1 medium gain (MGA)
- Separate low gain antennas (Rx & Tx)
- 2100 bps (Earth) to 40 bps (Mars)
- 2-way UHF radio for EDL & Surface
- 1 helix antenna (HGA) and 1 monopole (LGA)
- 32 kbps (EDL) to 256 kbps (Surface)
What component in the diagram is not described?
Speculate on its use and when/why it’s used.

## Phoenix Telecom Subsystem (UHF)

> **Source: Slide 8**

10/24/2025
8
Source: “Phoenix
Telecommunications”,
DESCANSO Series, 2010
Mission Description
- NASA science mission to investigate the geologic
history and biological potential of Martian arctic
- Launch in 2007, arrived May 2008, ended Nov. 2008
Telecom System
- 2-way X-band for communication & ranging in Cruise
- 2 SDST radios and 2 15-W SSPA amplifiers
- 1 medium gain (MGA)
- Separate low gain antennas (Rx & Tx)
- 2100 bps (Earth) to 40 bps (Mars)
- 2-way UHF radio for EDL & Surface
- 1 helix antenna (HGA) and 1 monopole (LGA)
- 32 kbps (EDL) to 256 kbps (Surface)
What component in the diagram is not described?
Speculate on its use and when/why it’s used.

## Juno Telecom Subsystem

> **Source: Slide 9**

10/24/2025
9
Mission Description
- 
NASA science mission to understand the
formation and evolution of Jupiter
- 
Launched in 2011, arrived 2016, extended to 2025
Telecom System
- 
2-way X-band for communication & ranging
- 2 SDST radios and 2 TWTA amplifiers
- 1,745 bps (launch), 100 bps (cruise), 18 kbps
(HGA at Jupiter), 10 bps (safe)
- 
2-way Ka-band for gravity science (single-string)
- 1 Italian radio and 1 SSPA amplifier
- 
Five Antennas
- 2.5 m HGA, MGA, and 3 LGAs
Source: “Juno Telecommunications”, DESCANSO Series, 2012

---

# 3. End-to-End Information System (EEIS)


## End-to-End Information System (EEIS) Overview

> **Source: Slide 10**

- 
EEIS stretches beyond the telecom subsystem to encompass all functions, data formats, and path losses from
the initial selection and formatting of the data for transmission to the final reception and use of the data
  - These are the to/from paths between telecom and ground (uplink & downlink)
- 
Flight-Ground Interface Control Document (FG-ICD)
  - This document describes the interfaces & data formats at each step in the process
  - To maximize efficiency, data is transmitted in binary and thus needs to be converted at several steps along the full path
- 
Link Budget
  - This is the corresponding analysis that captures all of the losses (L) and gains (G) between the source & receiver
  - This budget determines the data rate (in bits per second, bps) at a given bit error rate (BER)
  - It’s used across many industries to design communication systems
10/24/2025
10
Telecom Subsystem
Space Loss
Atmospheric Attenuation
Ground Station

## End-to-End Information System (in bits)

> **Source: Slide 11**

10/24/2025
12
Picture on Titan
Picture on Earth
(relay via
Cassini s/c)
Flight Ground Interface Control Document (FG-ICD)

---

# 4. Electromagnetic and RF Spectrum


## Electromagnetic (EM) Spectrum

> **Source: Slide 12**

10/24/2025
13
Radio Frequency (RF) Spectrum
The EM spectrum
describes light in the form
of frequencies and their
respective wavelengths
and photon energies.
The EM spectrum is used
heavily in space, where its
used or mitigated in the
following applications:
- Radiation shielding
- Power generation (eg,
solar arrays)
- Thermal absorption &
radiation
- Science (eg, imaging,
spectroscopy, radar)
- Communications

## Radio Frequency (RF) Spectrum

> **Source: Slide 13**

10/24/2025
14
30 cm
7.5 mm
Wavelength (λ):
Frequency (GHz):
RF Bands:
15 cm
1.2 cm
Advantages
Disadvantages
Notes
Lower in
Spectrum
L, S, C, X
- Frequently used with
small omni-antennas
- Less susceptible to
atmospheric effects (eg,
rain, fog, snow)
- More power required
- Lower throughput
- Larger HGA size
- NASA/DoD use S- & X-bands
- Used for low or high rate data
- GPS, comm. satellites, & mobile phones
use L-band
- TV broadcasting uses C-band
Higher in
Spectrum
Ku, K, Ka
- Lower power required
- Higher throughput
- Smaller HGA size
- More susceptible to
atmospheric effects
(eg, rain)
- Communications/NASA use Ka-band
- Used for high rate-data
- Satellite comm. & direct broadcast use Ku-
band
- K-band avoided due to atmosphere
Key Relationship: f = c / λ
Where: f is frequency in Hz (cycles/sec)
c is the speed of light (m/s)
λ is wavelength (m)
K-above
Ka
X, C, S, L
K-under
Ku
K
(robust)
(high-
performance)

---

# 5. Communications Definitions and Radiation


## A Few Definitions…

> **Source: Slide 14**

- Uplink, Downlink, Crosslink
  - Communication up/down from the ground across via relay to other spacecraft
- Carrier
  - Radio frequency (RF) source used to carry information
  - Frequency: f = c / λ (typically in units of Hz; that is, cycles/second)
- Modulation
  - The process by which an input signal varies the characteristics of a carrier wave, including the
amplitude, phase or frequency
  - Spacecraft downlinks typically use phase modulation, where the amplitude/frequency remain the
same and the phase (ie, signal level) is changed
- Demodulation
  - The process for restoring the original input signal
- Bit Error Rate (BER)
  - Frequency/probability of a bit error rate
  - Typical requirement is 10^-5 (ie, 1 in error in 100,000 bits)
10/24/2025
15
Phase modulation varies the
signal level (very slightly)
Modulating Wave
(injects your data)
Carrier
(carries your data)

## Isotropic & Anisotropic Radiation

> **Source: Slide 15**

10/24/2025
16
Equal power radiated in all directions
from the center of sphere with a
point source (ie, equipotential electric
field at all constant radii).
Radiation where its intensity
depends on the direction. Typically
described via an antenna gain
pattern.
Isotropic Radiation
Anisotropic Radiation
Surface area of a sphere = 4 π r2
Therefore, assuming no losses due to inefficiency, a 1
W source will gradually dissipate with 1/r2.
Or, flux density (in Watts) = Pt / (4 π r2)
If a transmitter has ‘gain’, then it transmits a signal in a given
direction at an increased level of power than if it were
isotropic. That is:
Gain = Aeffective / Aisotropic
…for a given section of the surface area (A).

---

# 6. EIRP, Link Equations, and Decibels


## Effective Isotropic Radiated power (EIRP)

> **Source: Slide 16**

- Effective Isotropic Radiated Power (EIRP) is the resulting
transmitted power after all gains & losses during
transmission have been factored in, including:
  - Antenna gains (Gtransmitted)
  - Antenna pointing and/or circuit losses (Lantenna, Lcircuit)
- Thus EIRP = Pt Gt La Lc
  - Where EIRP & Pt are in Watts and G & L are unitless factors
  - In other words, the resulting power is the original power times a
series of factors (gains & losses)
- Unfortunately, for communications, gains & losses typically
vary by several orders of magnitude, such as:
  - Gains: x 10-1,000,0000
  - Losses x 1/10th to 1/1,000,000th
- The result is that it’s far easier to work in decibels (dB)
10/24/2025
17

## Additional Equations

> **Source: Slide 17**

Telecom Link Equation
- Eb/N0 is the final result that determines
performance. Eb is energy per bit, N0 is noise
power spectral density in Watts per hertz
- Eb/N0 = PtLtGt ( ) LmGrLr ( ) / N0
- 
Where:
Pt = transmit power
Lt = transmit circuit loss
Gt = transmit antenna gain
lambda = wavelength
Lm = medium loss
Rg = range
Gr = receive gain
Lr = receive circuit loss
Rt = bit rate
5/18/18
SEA-18
4 Rg
2
2
1
Rt
Where…
R = Range
Ar = Receiving area
Pr = Power received
Pt = Power transmitted
La = Transmission loss factor
G = Transmission
Radiated Power
- This equation converts transmitted power
(Pt) to radiated power (Pr)

## The decibel (dB)

> **Source: Slide 18**

- Background
  - Consider dB as just a method that is used to express ratios (ie, gains & losses).
- 
dB converts factors (gain or loss) using a Log10 function; that is, 10 x Log10 (G) = G (in dB)
- 
The inverse of this is: Gain = 10 (Gain (in dB) / 10)
  - Examples:
- 
Example 1: 10 W increases by a factor of 2, 10 x 2 = 20 W
  - 
Factor of 2 = 10 x Log10 (2) = 3 dB
- 
Example 2: 10 W decreases by a factor of 2, 10 / 2 = 5 W
  - 
Factor of ½ = 10 x Log10 (½) = 10 x Log10 (1) – 10 x Log10 (2) = 0 dB – 3 dB = -3dB
  - This is important because of the properties of log functions
- 
Example 3: 10 W x 1/100 x 1,000 x 1/500 x 80,000 x 1/20,000 = 0.8 W
  - 
Where as:
10 W x (-20 dB + 30 dB – 27 dB + 49 dB – 43 dB) = 0.8 W → In other words, we can just add/subtract gains & losses by using dB
10 W x (-11 dB) = 0.8 W
10 W x 0.08 = 0.8 W, where 0.08 = 10^(-11/10)
- Two additional conventions
  - Watts can be converted to dBi:
10 x Log10 (Power in W) = Power in dBi
  - You can convert to milliWatts as well (in dBm):
10 x Log10 (Power in W x 1000) =
10 x Log10 (Power in W) + 10 x Log10 (1000) =
Power in dBi + 30 = Power in dBm
10/24/2025
19

## Questions from Prior Class

> **Source: Slide 19**

10/24/2025
20
- How much power devoted to telecom?
  - Transmitters are typically in the 10 to 100 W class
  - Overall power is often 100 to 1,000 W, so 10-20% is probably a good assumption
- In telecommunication, what is a symbol?
  - A symbol is a repeated wave pattern that represents a specific # of bits (eg, 1 bit in BPSK)
BPSK (1 bit/symbol)
8-PSK (3 bits/symbol)
Phase Key Shifting
Error Correction Codes

---

# 7. Link Budget and Antenna Performance


## Link Budget Overview

> **Source: Slide 20**

- The link budget is the analysis that ‘sizes’ the telecom system, but it
is deeply intertwined with the entire EEIS architecture
  - The following parameters are heavily traded very early in the design
process to ensure a robust communication architecture
- Telecom Subsystem
  - Frequency Band (eg, L, S, C, X, Ku, K, Ka)
  - Radio/Amplifier Power Input (eg, 1-200 W)
  - Antenna Type (eg, dipole, parabolic) and sizing (eg, 1-3 m dish)
  - Hardware efficiencies & losses (eg, radio, amplifier, circuit, antenna)
  - Operations losses (eg, pointing loss)
- Space Loss & Atmospheric Attenuation
  - Signal characteristics (eg, band, polarization, ellipticity, etc.) vs. losses
- Ground Station & Architecture
  - Antenna network (eg, DSN) and size (eg, 34-m, 70-m)
  - Pointing Loss (eg, 0.1 deg)
- Typical Products
  - Data Rate (bps), margin (dB), and bit error rate (BER)
10/24/2025
21

## Antenna Gain

> **Source: Slide 21**

10/24/2025
23

## A Typical Antenna Pattern

> **Source: Slide 22**

10/24/2025
24

---

# 8. Atmospheric, Trajectory, FOV, and RF Compatibility Effects


## Atmospheric Attenuation

> **Source: Slide 23**

10/24/2025
25

## Attenuation vs. Frequency

> **Source: Slide 24**

10/24/2025
26

## Trajectory Impacts on Telecom

> **Source: Slide 25**

10/24/2025
27

## Fields of View (FOV) Impacts…

> **Source: Slide 26**

10/24/2025
28
- 
Interference with fields of view effect antenna patterns.
- 
Other items on nadir deck effect pattern. Objects are same order as the wavelength ~
.75m.
MRO Flight UHF Antenna
Antenna with radome mounted on MRO nadir deck.

## Mars Rovers

> **Source: Slide 27**

- Typical Curiosity Data Rates
  - 2 Mbps via RUHF
  - 500 bps via RHGA
  - 10 bps via RLGA
10/24/2025
29
RUHF
RLGA
RHGA

## RF Compatibility

> **Source: Slide 28**

- All subsystems and instruments are required to avoid conducted and radiated emissions and susceptibilities.
- RF systems, communications and instruments, are intended to radiate and be susceptible at specific
frequencies.
- Couplings between each element at each frequency and harmonics must be estimated and controlled.
- Filters must be added in the design.
- S/C system test must include complete self-compatibility test, including flight configuration, thermal blankets,
and payload.
10/24/2025
30

---

# 9. Galileo HGA Failure Case Study


## Case Study

> **Source: Slide 29**

Galileo HGA Failure
10/24/2025
31
- 
Galileo
  - 
Launched in 1989 from the Space Shuttle Atlantis
  - 
Jupiter Orbit Insertion (JOI) in 1995
  - 
Controlled entry into Jupiter in 2003
- 
Scientific Discoveries
  - 
Intense radiation environment
  - 
Liquid ocean under Europa ice
  - 
Io’s active volcanos
  - 
Ganymead’s magnetic field
- 
Near Mission Failure….
  - 
In 1991, the operations team tried and failed to fully
deploy the 4.8-m High Gain Antenna
Europa
Io

## 10/24/2025

> **Source: Slide 30**

32
Galileo HGA Failure
Trajectory Overview

## 10/24/2025

> **Source: Slide 31**

33
Galileo HGA Failure
Flight System Overview
High Gain Antenna
Low Gain Antenna
Telecommunications

## 10/24/2025

> **Source: Slide 32**

34
Galileo HGA Failure
Telecommunications Overview
Radio Frequency Subsystem (RFS)
Modulation/Demodulation Subsystem (MDS)
S-/X-band Antenna (SXA) Subsystem
X- to S-band Downconverter
Carrier Frequencies
S-band Uplink: 2.1 GHz
S-band Downlink: 2.3 GHz
X-band uplink: 7.2 GHz
X-band downlink: 8.4 GHz

## 10/24/2025

> **Source: Slide 33**

35
Galileo HGA Failure
Component Terminology
- 
Diplexer: Routes two signals into one path based on frequency (typically reciprocal)
- 
Switch: Allows the spacecraft to switch between two RF paths (eg, LGA vs. HGA)
- 
Filters: Allow/reject certain frequencies. There are four types: high-pass, low-pass, band-pass, and band-reject
- 
TWTA: Traveling Wave Tube Amplifier is a specialized vacuum tube that is uses additional power (in W) to amplify RF signals
- 
Down-converter: Converts RF signals to a lower frequency range.
- 
Hybrid Coupler: Splits power evenly (3 dB) between two ports
- 
Exciter: Generates the modulated waveform that can be radiated to the antenna.
- 
RF Oscillator: Generates the carrier signal that is used for spacecraft communications. An ultra-stable oscillator (USO) is a highly stable
version generally used for science.
- 
Modulator: Converts signals from digital to RF
- 
Convolutional Code: Type of error-correcting encoding that is used to increase the robustness of spacecraft communications. Notes:
(1)Andrew Viterbi proposed the Viterbi algorithm to decode convolutionally encoded data. (2) Convolutional codes are being replaced by
Turbo codes.
(These definitions are intended to be more readable, but slightly less accurate.)

## 10/24/2025

> **Source: Slide 34**

36
Galileo HGA Failure
Telecommunications Overview
Radio Frequency Subsystem (RFS)
Modulation/Demodulation Subsystem (MDS)
S-/X-band Antenna (SXA) Subsystem
X- to S-band Downconverter
LGA vs. HGA
LGA S-band
Uplink Path

## 10/24/2025

> **Source: Slide 35**

37
Galileo HGA Failure
Telecommunications Overview
Radio Frequency Subsystem (RFS)
Modulation/Demodulation Subsystem (MDS)
S-/X-band Antenna (SXA) Subsystem
X- to S-band Downconverter
LGA vs. HGA
LGA S-band
Uplink Path
HGA S-band
Uplink Path
Low-rate LGA S-band
Downlink Path

## 10/24/2025

> **Source: Slide 36**

38
Galileo HGA Failure
Telecommunications Overview
Radio Frequency Subsystem (RFS)
Modulation/Demodulation Subsystem (MDS)
S-/X-band Antenna (SXA) Subsystem
X- to S-band Downconverter
LGA vs. HGA
LGA S-band
Uplink Path
HGA S-band
Uplink Path
High-rate HGA X-band
Downlink Path
(redundancy uses RCP/LCP
polarization)

## 10/24/2025

> **Source: Slide 37**

39
Galileo HGA Failure
Telecommunications Overview
Radio Frequency Subsystem (RFS)
Modulation/Demodulation Subsystem (MDS)
S-/X-band Antenna (SXA) Subsystem
X- to S-band Downconverter
LGA vs. HGA
LGA S-band
Uplink Path
HGA S-band
Uplink Path
High-rate HGA X-band
Downlink Path (134
kbps)
(redundancy uses RCP/LCP
polarization)
Low-rate LGA S-band
Downlink Path (< 40 bps)

## 10/24/2025

> **Source: Slide 38**

40
Galileo HGA Failure
Redundancy
Radio Frequency Subsystem (RFS)
Modulation/Demodulation Subsystem (MDS)
S-/X-band Antenna (SXA) Subsystem
X- to S-band Downconverter
LGA vs. HGA
Redundant Units
- 2 LGAs (1 not shown)
- 2 complete paths for
low-rate telemetry
- All critical electrical
uplink/downlink
components are
redundant
Single-String
- USO
- HGA

## Aside…

> **Source: Slide 39**

Since Galileo…
- 
SDST
  - Unifies the following functions
- 
Receiver
- 
Command detector
- 
Telemetry modulator
- 
Exciters
  - Note that encoding and compression is typically performed by the C&DH
subsystem
- 
SSPA or TWTA
  - Solid State vs. Traveling Tube
  - Uses power to amplify the signal
  - Often range from 25 W to 100 W
- Result
  - The above components greatly simplify modern telecom systems
  - Typically, just combine these with
- 
Antennas
- 
Diplexers & Switches (waveguide/coaxial)
10/24/2025
41
Small Deep Space Transponder (SDST)
Solid State Power Amplifier (SSPA)

## Galileo HGA Failure

> **Source: Slide 40**

Initially Anomaly…
- 
In 1991, after the Venus flyby and beyond 1 AU, the team executed a sequence to deploy the high gain antenna
- 
While the telemetry showed that the motors operated at higher-than-expected power levels for 8 minutes, they were unable to deploy
the antenna.
- 
3 ribs were ‘stuck’
(Can occur when there is insufficient lubricant)
10/24/2025
42
Expected State (fully deployed)
Actual State
(partially deployed)

## • Probable root cause…

> **Source: Slide 41**

  - Loss of lubricant occurred due to the vibration that the antenna experienced on the truck as it made multiple trips
to/from KSC
- 
Failed ribs were closest to the flatbed trailers that carried Galileo
- 
The lubricants were not checked or replaced prior to launch
10/24/2025
43
Galileo HGA Failure
Why?
Timeline
- 
Dec, 1985- Originally shipped from JPL to KSC
- 
Jan, 1986-
Loss of Space Shuttle Challenger
- 
Late 1986- Returned to JPL
- 
Mid, 1989- Shipped to KSC
- 
Oct, 1989-
Launched on Space Shuttle Atlantis
- 
Early 1991- HGA deployment failed
(Picture from Phoenix S/C)

## • Attempts to Unstick the HGA

> **Source: Slide 42**

  - Changing orientation towards/away from sun to change temperature
  - Repeatedly turning on/off the motors would double the torque (13,000 attempts)
  - Inducing a maximum spin rate of 10 rpm & hammering the motors
  - Final attempts coincided with release of the probe, probe deflection maneuver, and JOI
  - None were successful…
  - At Jupiter, downlink rate would be 10 bps, which would effectively end the mission
10/24/2025
44
Galileo HGA Failure
Attempts to Unstick HGA

## Galileo HGA Failure

> **Source: Slide 43**

Transmission Improvements & Results
- From 1993 to 1996, extensive new flight and ground software was developed and DSN stations were enhanced to increase
the transmission rate
- Improvements
1.
Increased S-band signal to noise ratio (antenna arrays & ultra-low noise receivers)
2.
Improved efficiency of radio modulation
3.
Improved channel codes (ie, reduce Eb/No) so to minimize BER
4.
Aggressively apply data compression techniques
- Result
  - 1-3 improved the downlink rate from 10 bps to 160 bps
  - 4 improve the rate to 1,000 bps
  - These improvements allowed Galileo to meet 70% of its science goals
10/24/2025
45
Beyond Galileo, these changes both significantly improved NASA deep space communications and changed how the
science community viewed data compression.

---

# 10. Telecom Hardware Estimate and Design Steps


## Telecom Hardware Estimate

> **Source: Slide 44**

- Primary Components (part of link budget)
  - Radio / Transponder, find lowest mass, power, & cost system that meets requirements
  - Power Amplifier
- 
Use a TWTA or SSPA (often depends on specific design and/or heritage)
- 
Otherwise, just based on lowest mass/cost/power system that provides desired RF power
  - Antennas
- 
High Gain antenna for primary data uplink/downlink
- 
Medium gain antenna when high gain not required due to lower rate or nearer range
- 
Low Gain antenna for fault scenarios (~360-deg coverage)
- Additional Hardware
  - Diplexers
- 
Routes different frequencies
- 
Uplink/downlink, S- vs. X-band
- 
0.7 kg each (ballpark)
  - Waveguide Transfer Switches
- 
Configures between different antennas
- 
Depends on design, but 1 per 1-2 antennas
- 
1 kg each (ballpark)
  - Coaxial Cable, Filters, etc.
- 
~5% of telecom mass
10/24/2025
46
OSIRIS-Rex Telecom Subsystem

## Telecom Design Steps

> **Source: Slide 45**

- Review & Understand Design Information
  - Mission Description and/or Concept of Operations
  - System and Subsystem Requirements
- 
ConOps, mission geometry, Earth-S/C range
- 
Payload & engineering data requirements
- 
Fault scenarios
- Create a Preliminary Design
  - Identify the driving uplink/downlink scenarios
  - Create link budgets for each
- 
Optimize with respect to band, antenna types & sizes, RF power, ground station assumptions, etc.
  - Create block diagram
  - Create component mass list
- Review & Iterate (w/broader team)
  - Revisit other options & trades
10/24/2025
47

---

# 11. Optical Communication and Class Questions


## QUESTIONS

> **Source: Slide 46**

10/24/2025
48

## Questions from Last Week

> **Source: Slide 47**

- 
Telecom is a critical subsystem, but are there any spacecraft that might not need it or where it’s less important?
  - Thoughts from the class?
- 
Are there any new innovations/improvements being made to the way s/c communicate either with other s/c or ground stations?
  - Most significant is optical communication… (next chart)
  - Additionally, there is a continuing drive towards higher bandwidths and higher power systems, which have resulted in an increasing amount of data
10/24/2025
49

## Optical Communication

> **Source: Slide 48**

- 
Deep Space Optical Communications (DSOC) is a laser space communication system in development meant to improve
communications performance 10 to 100 times over the current radio frequency technology without incurring increases in mass,
volume or power.
- 
Mass 29 kg, power < 100 W, 0.2-200 Mbps
10/24/2025
50

## Questions from Class (3 of 3)

> **Source: Slide 49**

10/24/2025
51
- 
3 dB Beamwidth is the angle at which the signal is a half-power
  - For example:
dB = 10 Log10 (unitless factor)
3 dB = 10 Log10 (0.5)
- 
For a parabolic antenna
Main Lobe
Side Lobes
Back Lobe
beamwidth
Antenna Gain Patterns
(magnitudes are in dB; ie, logarithmic scales)
BW = 70l
d
where BW = antenna beamwidth (deg)
l = wavelength (m)
d = antenna diameter (m)
Useful Source
https://www.phys.hawaii.edu/~anita/new/papers/militaryHandbook/antennas.pdf

## Questions from Class (4 of 9)

> **Source: Slide 50**

- 
“When looking at a telecommunications block diagram, are the block always pieces of hardware?”
  - For telecom & most subsystems, yes. For, GN&C and Software, no.
  - Note that block diagrams can be used in different ways (hardware, software, functional, organizational, etc.) Important to choose the right “architectural
view or perspective” depending on the problem.
- 
“If switching between RCP and LCP may cause problems with receiving the signal on the ground, why do it?”
  - In general, using polarization minimizes interference from other sources and expands the available bandwidth for communications.
  - I believe it’s also used, on occasion, when uplinking/downlinking at the same time
10/24/2025
52

## Questions from Class (5 of 9)

> **Source: Slide 51**

- 
“Can an antennas receive and send out information at the same time?”
  - Yes. I believe there is a slight loss when simultaneously transmitting/receiving data
  - Note that the diplexer is responsible for routing the appropriate signals (band & direction)
10/24/2025
53
- 
“How is data modulation done and why is it important when
downlinking?”
  - 
Transmitting data via radio waves requires us to translate real data (ie, bits)
into the RF signal. This is what modulation is (versus an electrical line where
digital signals can be transmitted directly).

## Questions from Class (8 of 9)

> **Source: Slide 52**

- 
“For clarification, does the [Telecom] subsystem receive RF signals from the uplink path, transform them into digital signals and then send
these digital signals to the C&DH subsystem?”
  - Yes – this is exactly how it works.
- 
“And then when the [Telecom] subsystem is sending signals on the downlink path back to earth, do these signals originally come from the
C&DH subsystem?”
  - Yes – they are either collected and/or generated by FSW, encoded, and then sent to telecom
10/24/2025
54

---

# Lecture Summary

> **Source: Full Lecture**

The telecom subsystem provides communication to/from the spacecraft and supports command reception, telemetry transmission, antenna selection and pointing, carrier tracking, and ranging. The lecture connects spacecraft telecom hardware to the broader End-to-End Information System (EEIS), including the complete data path between spacecraft and ground.

Key takeaways:

- **Telecom hardware:** Radios/transponders, amplifiers, diplexers, waveguide transfer switches, and high-, medium-, and low-gain antennas form the core telecom architecture.
- **EEIS:** Communications design extends beyond spacecraft hardware to data formatting, path losses, ground stations, and the Flight-Ground Interface Control Document.
- **RF spectrum:** Frequency band affects antenna size, throughput, required power, and susceptibility to atmospheric effects.
- **Link performance:** EIRP, antenna gain, path loss, atmospheric attenuation, receiver performance, data rate, BER, and margin are combined through the link budget.
- **Spacecraft integration:** Trajectory, antenna field of view, spacecraft geometry, RF compatibility, redundancy, and fault scenarios directly affect telecom design.
- **Galileo HGA failure:** The case study shows how an antenna-deployment failure forced major flight-software, ground-system, coding, modulation, and compression improvements to preserve mission science return.
- **Design process:** Telecom design begins with mission geometry, data requirements, and fault scenarios, then develops driving uplink/downlink link budgets, hardware architecture, and a component mass estimate before iteration with the broader spacecraft team.
- **Optical communication:** DSOC demonstrates the potential for major communications-performance improvements beyond traditional RF systems.
