# Avionics: C&DH and FSW

**Course:** ASTE-331a — Spacecraft Systems Engineering  
**Lecture:** 04 — Avionics: C&DH and FSW  
**Instructors:** Jim Chase, Danielle Marsh  
**Source:** `331_04_Avionics_20251003.pdf`

---

## Lecture Overview

This lecture introduces spacecraft avionics, with emphasis on Command & Data Handling (C&DH) hardware and Flight Software (FSW). It covers the hardware and software architectures that provide spacecraft command and control, internal data handling, time management, autonomy, fault management, uplink/command processing, downlink/data management, and interfaces to spacecraft devices.

The lecture is organized into three major parts:

1. Avionics hardware and software architectures and examples.
2. Avionics functions and spacecraft software simulation.
3. The avionics design process, verification, and case studies.

The lecture also supports two course activities: spacecraft simulation verification, in which students develop a FSW procedure to test spacecraft commands and telemetry, and avionics design, in which students select avionics hardware for different mission needs.

---

## Table of Contents

- [1. Avionics Overview](#1-avionics-overview)
- [2. Avionics Hardware Architecture](#2-avionics-hardware-architecture)
- [3. Flight Software Architecture](#3-flight-software-architecture)
- [4. Avionics Mission Examples](#4-avionics-mission-examples)
- [5. Processing](#5-processing)
- [6. Intercommunications](#6-intercommunications)
- [7. Uplink and Command Management](#7-uplink-and-command-management)
- [8. Downlink and Data Management](#8-downlink-and-data-management)
- [9. Time Management](#9-time-management)
- [10. Autonomy and Fault Management](#10-autonomy-and-fault-management)
- [11. Avionics Design Process](#11-avionics-design-process)
- [12. MSL Sol 200 Anomaly](#12-msl-sol-200-anomaly)
- [13. Spacecraft Simulation Software](#13-spacecraft-simulation-software)
- [14. Command and Telemetry](#14-command-and-telemetry)
- [15. Software Boot and Reset](#15-software-boot-and-reset)
- [16. Verification Test Procedures](#16-verification-test-procedures)
- [17. C&DH and FSW Downlink Verification Example](#17-cdh-and-fsw-downlink-verification-example)
- [18. Typical Test and Spacecraft Data](#18-typical-test-and-spacecraft-data)

---

# 1. Avionics Overview

> **Source: Slides 2–5**

## Lecture Structure

> **Source: Slides 2–3**

### Part 1

Avionics hardware and software architectures and examples.

### Part 2

Avionics functions and spacecraft software simulation.

### Part 3

Avionics design process and case studies.

The lecture roadmap identifies the following topics:

- Introduction
  - Overview
  - Hardware overview
  - FSW overview
  - Examples
- Functions
  - Processing
  - Intercommunications
  - Uplink/command
  - Downlink/data
  - Time management
  - Autonomy and fault management
- Design process
- Case studies

---

### Avionics Function

> **Source: Slide 4**

Avionics provides:

- Spacecraft command and control
- Internal data handling
- Fault management
- FSW with boot/reset functionality

The slide describes avionics as:

**The brains of the spacecraft.**

### Primary Drivers

- Time-critical activities
  - Orbit insertion
  - Landing
  - Other critical events
- Environment
  - Thermal
  - Radiation
- Number, interface type, complexity, and data production of spacecraft devices
  - ACS
  - Payload
  - Other subsystem hardware
- Fault-tolerance requirements
  - Including required spacecraft "up-time"

Avionics may also be called the **Flight Computer**.

### GRAIL Example

- RAD750 processor
- Interface cards
- Converters
- Backplane
- Chassis assembly
- Total mass approximately 5 kg

### Common Components

A flight-computer electronics box/chassis may contain:

- Processor
- Payload interface cards
- Data interface cards
- Memory
- Power converters

Depending on system complexity, these functions may be contained in:

- One electronics box
- Multiple electronics boxes

An independent electronics device may monitor flight-computer health. The lecture informally calls this a **"lizard brain."**

### Key Trades and Analyses

- Hardware vs. software implementation of functions
  - Timing
  - Configurability
  - Other considerations
- Interface types
  - MIL-STD-1553
  - LVDS
  - RS-422
  - etc.
- Onboard memory storage
- CPU utilization
- Radiation shielding
- Heritage
- Redundancy
- Cross-strapping

### Key Parameters

- Mass
- Power
- Cost

---

## Acronyms and Terminology

> **Source: Slide 5**

| Term | Definition |
|---|---|
| Backplane | Circuit board that connects boards of a computer and enables communication between them. cPCI is a common backplane. |
| Chassis | Structural enclosure that houses electronics. |
| Command | Instruction sent to the spacecraft that is processed to tell it what to do. |
| Downlink | Sending data from the spacecraft to the ground. |
| EEPROM | Electrically Erasable Programmable Read Only Memory; non-volatile memory that can be written more than once. |
| Flight Computer (FC) | Main spacecraft control electronics; the "brains" of the spacecraft. |
| Flight Software (FSW) | Code residing within the flight computer that executes most spacecraft control, including ACS, power control, thermal control, etc. |
| PROM | Programmable Read Only Memory; non-volatile memory that can only be written once. |
| RAM | Random Access Memory; volatile memory for temporary, fast read/write data storage. |
| Remote Engineering Unit (REU) | "Lizard brain" avionics hardware that monitors the health of the main flight computer. The term is JPL-specific. |
| Single Board Computer (SBC) | Hosts the processor and FSW. |
| Surom | Firmware on the processor used to boot and configure the flight computer. |
| NAND Memory | Non-volatile flash memory with high density. |
| NOR Memory | Non-volatile flash memory with low density. |
| Nonvolatile Memory (NVM) | Memory that retains data after a power cycle; often used for long-term storage. |
| Parameter | A settable state used by spacecraft logic, such as wait times or error thresholds. |
| Sequence | A file of commands uploaded to the spacecraft that can execute in order and include logic such as conditional checks. |
| System Modes | Overall spacecraft configurations with defined hardware states, such as nominal mode and safe mode. |
| Telemetry | Data collected from spacecraft devices and sent to the ground for interpretation; may include housekeeping or science data. |
| Uplink | Sending commands from the ground to the spacecraft. |
| Volatile Memory | Memory that loses data after a power cycle; often used for real-time task execution requiring fast access. |

---

# 2. Avionics Hardware Architecture

> **Source: Slides 6–8**

## Hardware Overview

> **Source: Slide 6**

Avionics hardware contains the chassis and circuit-board cards required to interface with spacecraft devices and execute avionics functions.

### Processing

Executes functions required for spacecraft operation.

### Device Intercommunication

Sends commands and receives data from devices such as:

- ACS hardware
- Instruments
- Other spacecraft devices

### Uplink and Sequence/Command Management

Receives and decodes commands and files sent from the ground.

### Downlink and Data/Telemetry Management

- Stores data collected by devices
- Formats data
- Sends data to the ground

### Time Management

- Maintains spacecraft clock
- Distributes time to devices

### Autonomous Behaviors

Includes management of:

- Modes
- Attitude determination and control
- Power
- Thermal
- Other autonomous spacecraft functions

### Fault Management

Detects and responds to off-nominal events such as:

- Low battery state of charge
- Loss of communications

### Distributed Processing

The flight computer hosts the central processor, but individual boards can contain their own microcontrollers or FPGAs for local interface/control logic.

### Robustness and Fault Tolerance

Key architecture choices include:

- Single-string vs. redundant
- Block-swapped vs. cross-strapped
- Cold-spare vs. warm-spare operation
- Independent "lizard brain" health monitoring

**Figure description:** The slide compares cross-strapped and block-swapped architectures. Cross-strapping allows redundant computers to access redundant external devices through alternate paths. Block swapping pairs each computer side with its corresponding device side.

---

## Flight Computer Hardware Architecture

> **Source: Slide 7**

The representative flight computer contains:

### Power Supply

Provides:

- 3.3 V
- 5 V
- ±12 V
- Power-on reset (POR)

### SBC / Processor Card

Contains:

- EEPROM with Surom
- RAM containing executing FSW

### Relay / Driver Card

Contains:

- Relays
- Drivers

The generic "driver card" may more specifically be:

- Propulsion interface card
- Motor interface card
- Other device-specific driver card

### Serial Interface Card

Provides point-to-point interfaces to devices such as:

- Instruments
- Star trackers
- Other spacecraft devices

The generic serial card may be specialized as:

- Payload interface card
- GN&C interface card
- Other interface card

### Telecom Interface Card

Interfaces with the telecom radio and can provide the 1553 bus-controller function.

### Non-Volatile Memory Card

Contains:

- NOR
- NAND
- RAM

### Backplane

Connects the internal avionics cards.

### Remote Engineering Unit

Contains PROM and independently monitors flight-computer health.

### External Interfaces

The diagram distinguishes:

- Data interfaces
- Power interfaces
- RF interfaces
- Avionics devices
- Non-avionics devices

External devices include:

- Instruments
- IMUs
- Star trackers
- Telecom radio
- Power-switching card

**Figure description:** The flight computer is shown as a chassis containing vertically stacked cards connected through a backplane. A shared data bus such as 1553 connects the computer to the REU, instruments, spacecraft devices, and telecom system. Dedicated serial links connect other instruments and devices.

---

## Hardware Roles

> **Source: Slide 8**

| Avionics Hardware | Role | Related Functions |
|---|---|---|
| Power supply | Receives primary bus power, typically 31 V; provides secondary conversion and distribution for flight computer | Housekeeping |
| SBC / Processor card | Hosts CPU and FSW; provides boot/initialization; provides spacecraft clock | Processing, intercommunications, uplink/command, downlink/data, time, autonomy, fault management |
| Relay / Driver card | Hardware relays independent of FSW; drivers for propulsion, motors, sensors, etc. | Processing, intercommunications |
| Serial interface card | Point-to-point interface between flight computer and spacecraft devices | Device intercommunications |
| Telecom interface card | Uplink/downlink interface to telecom radio; command decoding; data encoding; may act as 1553 bus controller | Intercommunications, uplink/command, downlink/data |
| NVM card | Bulk housekeeping/payload storage; redundant FSW image storage | Downlink/data, fault management |
| Remote Engineering Unit | Independent flight-computer health checking and redundancy management | Fault management |

---

# 3. Flight Software Architecture

> **Source: Slides 9–12**

## Flight Software Functions

> **Source: Slide 9**

FSW provides:

- Boot and initialization
- Device intercommunications
- Uplink and sequence/command management
- Downlink and data/telemetry management
- Autonomous behaviors
- FSW update
- Time management
- Fault management

### Command Paths

Commands may be:

- Sequenced
- Real-time

A sequence can include logic such as:

```text
CMD1
WAIT for TLM
CMD2
...
```

### Data Path

Raw data may include:

- Raw science data
- Raw engineering data

The data are then:

```text
Raw Data
   ↓
Formatted Data
   ↓
Packetized Data
   ↓
Downlink
```

### Autonomous Behaviors

Example system modes:

```text
Nominal Mode
    ↕
Standby Mode
    ↕
Safe Mode
```

### Fault Management

Error monitors trigger responses, which may lead to mode transitions.

---

## Software Architecture Layers

> **Source: Slide 10**

A FSW architecture is a high-level graphical model or abstraction of a FSW system.

It provides:

- Decomposition into components with interfaces
- Reflection of FSW requirements
  - Functions
  - Activities
  - Behaviors
  - Interfaces
  - Interactions

Systems engineers and FSW engineers use the architecture as the basis for:

- System function partitioning and allocation
- Trade studies
- Design decisions
- Implementation decisions
- Verification and validation decisions

### Hardware Layer

Includes:

- Backplane
- Internal data bus
- Processor
- Cards
- Device drivers
- Controllers

### Functional Layer

Basic functional building blocks such as:

- Device management
- Time management
- Command management
- Telemetry management

### Activity Layer

Core spacecraft activities that may be autonomous or ground initiated:

- Attitude control
- Power control
- Thermal control
- Ground communications

### Behavior Layer

High-level, cross-cutting coordination:

- System modes
- Fault management

### Services

Key hardware/software services include:

- Real-time operating system
- Boot and initialization
- FSW upload
- Memory access

---

## Flight Software Architecture Example

> **Source: Slide 11**

### Behavior Layer

- Mode management
- Fault management

### Activity Layer

- Communications management
- Power management
- ACS
- Thermal control

### Functional Layer

Examples include:

- Timekeeping
- Parameter manager
- Command manager
- Telemetry manager
- NOR memory manager
- NAND memory manager
- Battery manager
- Power-converter manager
- Power-switch manager
- Sun-sensor manager
- Reaction-wheel-assembly manager
- IMU manager
- Star-tracker manager
- Thruster manager
- Heater manager
- Sensor manager
- Magnetometer manager
- Camera manager

### Hardware Layer

- Backplane
- Processor
- Telecom interface card
- Serial interface card
- NVM card
- Device controllers and drivers

### Services

- Memory access
- FSW upload
- Boot and initialization
- Real-time operating system

The slide notes:

**mgr = manager**

---

## FSW Boot and Image Management

> **Source: Slide 12**

FSW contains the logic/code necessary to execute avionics functions.

### Boot and Initialization

FSW must come online in a reliable and repeatable manner.

- Multiple FSW images are stored in NOR memory on the NVM card.
- This provides robustness against corruption.
- Surom on the SBC selects a FSW image from NOR.
- The selected image is loaded into SBC RAM for execution.

### In-Flight FSW Configuration

FSW can generally be changed in flight using:

- A patch
- A complete reimage

For a new FSW image:

1. Ground uploads the new image to NVM RAM.
2. Surom checks NVM RAM during FSW loading.
3. If an image exists there, it can be selected and loaded.

FSW resides both:

- On the flight computer
- On peripheral devices such as payloads

**Figure description:** The NVM card contains several FSW images in NOR, spacecraft data in NAND, and an FSW image update area in RAM. Surom in EEPROM on the SBC selects an image and loads it into processor RAM for execution.

---

# 4. Avionics Mission Examples

> **Source: Slides 13–14**

## Solar Probe

> **Source: Slide 13**

Key avionics design drivers:

- Flagship mission
  - Drives overall redundancy
- Tight pointing constraints due to thermal environment
  - Drives very fast recovery time
  - Drives triple-redundant processors
- Several instruments and spacecraft devices
  - Drives interface-card sizing
  - Drives memory sizing
- Severe thermal and radiation environment
  - Drives chassis design
  - Drives shielding
  - Drives test program

**Figure description:** The spacecraft system block diagram shows avionics connected throughout the spacecraft to GN&C, instruments, propulsion, cooling, telecom, EPS, mechanical, and thermal hardware. The diagram illustrates the highly integrated role of avionics.

---

## Psyche

> **Source: Slide 14**

Key avionics design drivers:

- Class B mission
  - Drives overall redundancy
- Tight pointing constraints for:
  - Electric-propulsion thrusting
  - Science instruments
  - Drives recovery time
- Split avionics design between JPL and Maxar, formerly SSL
  - Drives centralized processing with additional hardware
  - Includes Attitude Control Electronics (ACE) and router hardware
- Maxar avionics heritage
  - Drives new interfaces to JPL hardware
  - Drives operational strategy, including fault recovery

**Figure description:** The architecture separates JPL C&DH from the SSL SEP chassis. The JPL flight computer connects over 1553 and RS-485 links to star tracker, inertial-reference unit, ACE, smart battery tray, router, power-processing unit, power-control unit, and other distributed hardware. Redundant units are omitted from the simplified diagram.

---

# 5. Processing

> **Source: Slides 15–18**

Slide 15 begins **Part 2: Avionics Functions**.

## Processing Function

> **Source: Slide 16**

### Role

- Host flight software
- Provide overall command and control
- Provide boot and initialization

### Hardware

SBC / processor card:

- Hosts CPU
- Hosts FSW
- Provides boot and initialization

Some missions use additional interface hardware, such as the router in the Psyche architecture.

### Software

- Surom executes boot and initialization.
- Primary FSW executes most spacecraft-control functions:
  - Attitude control
  - Power management
  - Thermal management
  - System modes
  - Fault management

### Key Trades

- Performance vs. reliability
- Simplicity vs. robustness
- Redundancy architecture
- Cold-spare vs. warm-spare operation

---

## Types of Flight Computers and Processors

> **Source: Slide 17**

| Processor Type | Pros | Cons | Example Hardware | Example Mission |
|---|---|---|---|---|
| CPU | Versatile; handles multiple applications and tasks | May not be optimized for real-time operations; can be less fault tolerant | BAE Systems RAD750 | Mars Science Laboratory / Curiosity |
| Real-Time Processor | Deterministic, timely task execution | May have limited flexibility; integration can be complex | VxWorks-based processors; RTEMS-based processors such as RAD750 and LEON-3 | Juno |
| Multi-core Processor | High processing power; parallel task handling | Higher power; increased software complexity | Space-grade multi-core processors | JWST |
| ASIC | Compact; efficient for specific tasks | Limited flexibility; custom design can be costly/time-consuming | Space Systems/Loral ASICs; Qualcomm Snapdragon listed as example hardware | JUICE |
| FPGA | Highly flexible/customizable; parallel processing | Complex design/programming; can be costly | Xilinx Virtex-5/6/7; Altera/Intel Stratix and Arria | Hubble Space Telescope |

---

## RAD750

> **Source: Slide 18**

The RAD750 was manufactured by BAE Systems under contract from Lockheed Martin and JPL to support Deep Impact in 2005.

The slide identifies it as a NASA standard for approximately two decades.

Characteristics:

- Available in different form factors
  - 3U
  - 6U
  - Custom
- Designed to be radiation tolerant

### Mission-Specific Adaptation

Processors can be adapted for:

- Radiation hardening
  - Can be costly
  - Can reduce performance
- Fault tolerance
  - Adds complexity
  - May use block redundancy, such as 2× RAD750
  - May use internal redundancy, such as triple-modular redundancy
- Payload processing
  - Limited to payload-specific operations
  - Most science instruments contain internal processors

**Figure description:** A RAD750 3U cPCI Single Board Computer is labeled with RAD750 CPU, oscillator, EEPROM/SUROM boot-code devices, SDRAM for FSW, and power PCI circuitry.

---

# 6. Intercommunications

> **Source: Slides 19–22**

## Intercommunications Function

> **Source: Slide 19**

### Role

Provide data exchange among spacecraft subsystems and devices.

### Hardware

**Relay / Driver Card**
- Hardware relays independent of FSW
- Can reset flight computer
- Can select FSW image
- Drivers for:
  - Propulsion hardware
  - Motor-control hardware
  - Sensors

**Serial Data Interface Card**
- Point-to-point device interfaces

**Telecom Interface Card**
- Interface to telecom radio
- Can provide 1553 bus controller

### Software

- Interface initialization
- Data formatting
- Data constraints
- Data distribution

### Key Trades

- Point-to-point vs. data-bus architecture
- Physical layer
- Protocol selection

---

## Point-to-Point and Data-Bus Interfaces

> **Source: Slide 20**

### Point-to-Point

A direct, dedicated link between two devices.

Use when:

- Only a few devices need direct communication
- A device requires a robust dedicated interface

Advantages:

- Simple
- Non-interfering
- Can support very high rate

Disadvantages:

- Limited scalability
- Limited flexibility

Examples:

- RS-422
- RS-485
- SpaceWire
- Ethernet

### Data Bus

A shared network allowing multiple devices, often called **Remote Terminals (RTs)**, to communicate.

A bus controller arbitrates data flow.

Advantages:

- Scalable
- Flexible
- Supports dynamic reconfiguration
- May contain built-in error detection

Disadvantages:

- More complex
- Devices can interfere with one another
- Example failure: "babbling"

Examples:

- 1553
- CAN
- Ethernet

---

## Data Interface Specification

> **Source: Slide 21**

### Physical Layer

Defines hardware and electrical specifications.

Includes:

- Signal type
  - Electrical
  - Optical
- Transmission medium
  - Copper
  - Fiber
  - Wireless
- Data rate
  - Example: 1 Mbps, 10 Gbps
- Electrical specifications
  - Voltage
  - Current
  - Impedance matching

Examples:

- RS-422
- RS-485
- LVDS

### Protocol Layer

Defines structure, format, and communication management.

Includes:

- Data framing
- Error detection and correction
- Flow control
- Addressing
- Protocol rules for starting/stopping and managing exchanges

Examples:

- UART
- SpaceWire

**Figure description:** Instruments A and B each exchange telemetry, command, and a 1-Hz timing signal with dedicated serial-interface cards. The signal labels distinguish protocol and physical-layer choices, such as UART over LVDS.

---

## Ethernet vs. 1553

> **Source: Slide 22**

The lecture notes that JPL tends to rely heavily on high-heritage serial interfaces or 1553, while newer commercial space organizations may use more Ethernet.

### 1553 — Federated Bus

- Common multi-drop data bus
- Up to approximately 1 Mbps
- Standard interface
- Deterministic
- Fixed-format messages
- Limited scalability
- Highly reliable
- Built-in error correction

### Ethernet — Star Bus

- Discrete interfaces between systems and a central processor
- Data rates up to tens of Gbps
- Custom interface for each device
- Flexible frames/packets
- Highly scalable
- May be susceptible to network collisions

**Figure description:** The 1553 architecture is drawn as a shared vertical bus with several components attached. Ethernet is drawn as a star topology with the flight computer in the center and individual links to each component.

---

# 7. Uplink and Command Management

> **Source: Slides 23–24**

## Overview

> **Source: Slide 23**

### Role

- Provide communication from ground operators to spacecraft.
- Validate uplink products:
  - Real-time commands
  - Files
  - Sequences
- Decode and execute commands.

### Hardware

Telecom interface card:

- Interfaces with telecom radio
- May provide 1553 bus-controller function

### Software

- Command validation
- Command decoding
- Command execution
- File/sequence validation
- File/sequence storage

### Key Trades

- Software commands vs. hardware commands
- Real-time vs. sequenced commands

---

## Types of Commands

> **Source: Slide 24**

Commands are instructions sent to the spacecraft that it processes and responds to.

### Software Commands

Most commands are interpreted and executed by FSW.

Example:

```text
CMD_PWR_ON_IMU
```

which powers on the IMU.

Software commands may be:

**Real-time**
- Individual commands
- Operator in the loop

**Sequenced**
- File of commands
- Can execute at specific times
- Can contain logic and conditional checks
- Does not require an operator in the loop

Example sequence:

```text
CMD_PWR_ON_IMAGER
WAIT until TLM_IMAGER_STATE = ON
CMD_COLLECT_IMAGE
WAIT 300s
CMD_PWR_OFF_IMAGER
```

### Hardware Commands

Less common.

- Bypass FSW
- Executed directly by hardware
- Useful when FSW is hung

Example:

```text
HDW_SYS_RESET
```

### Command Formatting

Actual flight commands are binary.

The **Command & Telemetry Dictionary (C&TD)** defines the meaning of the bits.

Typical C&TD fields:

- Command stem
- Op code
- Arguments
- Restricted modes
- FSW module
- Description

Example command representation:

```text
008 CMD_PWR_ON_IMU (STRING)
```

where the slide identifies:

- `008` as the op code
- `CMD_PWR_ON_IMU` as the command stem
- `STRING` as the argument type, with A or B as possible values in the example

---

# 8. Downlink and Data Management

> **Source: Slides 25–27**

## Overview

> **Source: Slide 25**

### Role

- Collect data from subsystem devices
- Process data for onboard use
- Store data for future downlink
- Packetize data for ground downlink

### Hardware

**NVM Card**
- Bulk housekeeping-data storage
- Payload-data storage
- Redundant FSW-image storage

**Telecom Interface Card**
- Interface to telecom radio

### Software

- Telemetry generation and collection
- Data storage
- Data formatting
- Data transmission

### Key Trades

- Volatile vs. non-volatile memory
- NAND vs. NOR
- Parameter management

---

## Types of Data and Telemetry

> **Source: Slide 26**

### Engineering, Housekeeping, and Accountability (EHA)

Channelized telemetry provided at regular intervals for spacecraft devices.

General format:

```text
[subsystem]-[ID]: Description
```

Example:

```text
PWR_IMU_A_STATE = [ON/OFF]
```

This gives the power state of IMU A.

Onboard EHA is continuously updated, but downlink occurs periodically, for example every:

**5–30 seconds**

EHA may be categorized as:

**Housekeeping Data**
- General subsystem health/status
- Onboard fault management
- Ground trending

**Mission Data**
- Payload science data
- Imagery
- Spectrometer data
- etc.

### Event Records (EVRs)

Event records are similar to logs/text messages and record events at specific times.

The lecture notes that EVRs are not common across the entire industry; some organizations instead rely on EHA.

Format:

```text
Time, Event Description
```

Examples:

```text
0000145, Command successfully executed: CMD_CDH_NOOP
0000147, Command successfully executed: CMD_CDH_EHA_RATE
0000148, EHA Rate set to 5 seconds
```

Like commands, flight telemetry is transmitted as bits/codes and translated into readable descriptions on the ground.

---

## Types of Memory

> **Source: Slide 27**

### Volatile Memory

Pros:

- Fast
- Many write cycles

Cons:

- Requires constant power

Applications:

- Real-time task execution
- Temporary storage/caching
- FSW execution
- Parameters that change based on conditions

Hierarchy shown:

```text
Volatile
├── RAM
│   ├── DRAM
│   │   └── SDRAM
│   └── SRAM
└── Other
    ├── Buffers
    └── Registers
```

The slide associates:

- DRAM with high-speed applications
- SRAM with large amounts of memory
- SDRAM with increased performance and complexity

### Non-Volatile Memory

Pros:

- Only requires power during writes

Cons:

- Slower
- Fewer write cycles

Applications:

- Long-term storage
- Redundant FSW images
- Science data
- Default parameters

Hierarchy shown:

```text
Non-Volatile
├── ROM
│   ├── PROM
│   └── EEPROM
└── Flash
    ├── NAND
    └── NOR
```

**PROM**
- Programmable once
- Typically used for "lizard brain" logic

**EEPROM**
- Reprogrammable
- More limited write cycles than flash
- Typically used for boot code

**NAND**
- High-density block storage
- Slow read / fast write
- Susceptible to radiation
- Typically used for science-data storage

**NOR**
- Individual memory access
- Fast read / slow write
- Typically used for FSW-image storage

---

# 9. Time Management

> **Source: Slide 28**

## Role

- Manage time within FSW and across spacecraft devices.
- Correlate spacecraft clocks with ground time.

### Hardware

**Processor Card**
- Time correlation
- Monitors for time jumps

**Telecom Interface Card**
- Typically stores SCLK

**Serial Interface Card**
- Broadcasts STM

**Remote Engineering Unit**
- Typically stores MCLK

### Software

- Seed SCLK with MCLK if FSW resets
- Distribute STM to devices

### Key Trades

- Clock precision
- Clock stability
- Device timing needs
- Time-broadcast strategy

### Clock Terminology

**MCLK — Mission Clock**
- Used for internal timing
- Seeds SCLK
- Stored separately from flight computer

**SCLK — Spacecraft Clock**
- Used for onboard event execution
- Stored in flight computer

**STM — Spacecraft Time Message**
- Broadcasts time to devices

---

# 10. Autonomy and Fault Management

> **Source: Slides 29–31**

## Overview

> **Source: Slide 29**

Autonomy and fault-management functions execute onboard FSW behaviors independently of ground operators for:

- Nominal operation
- Off-nominal operation

### Hardware

**Processor Card**
- Hosts CPU
- Hosts FSW

**Remote Engineering Unit**
- Independent health checking
- Redundancy management
- Can swap computers if loss of computer signal is detected

### Software

- Attitude determination and control
- Communications management
- Power management
- Thermal management
- System modes
- Fault management

### Key Trade

Real-time commanding vs.:

- Sequencing
- Onboard autonomy
- Autonomous behaviors

---

## Autonomous Behaviors

> **Source: Slide 30**

### Communications Management

Executes pre-planned communication windows, including:

- Turning toward Earth
- Configuring radio

### Attitude Determination and Control

- Determines spacecraft attitude
- Executes turns
- Executes delta-v maneuvers
- Maintains attitude
- Manages momentum

### Thermal Management

- Monitors device temperatures
- Turns heaters on/off

### Power Management

- Turns devices on/off
- Charges battery

### System Modes

Defines spacecraft states for:

- Nominal operations
- Faulted operations

Example:

```text
Nominal Mode
    ↕
Standby Mode
    ↕
Safe Mode
```

---

## Fault Management

> **Source: Slide 31**

Error monitors look for off-nominal conditions such as:

- Devices too hot or too cold
- Battery state of charge too low
- Attitude-control error too high
- Other failures

An error monitor includes:

- Condition
- Comparison
- Threshold
- Persistence

Generic form:

```text
IF [condition] [>, <, =] [threshold] for [persistence]
```

Example:

```text
IF TLM_PRIME_IMU_TEMP > 30 for 10 SECONDS
```

The condition typically requires a FSW update to change.

Threshold and persistence are typically parameters that can be modified by ground command.

### Responses

Responses correct the detected problem.

Examples:

- Power off faulty device
- Swap to redundant device
- Transition to safe mode

Example response:

```text
CMD_IMU_PRIME [OFF]
CMD_IMU_BACKUP [ON]
CMD_SAFE_MODE
```

### Safe Mode

Typical safe-mode configuration:

- All non-critical devices off
  - e.g. science instruments
- Basic ACS state
  - Typically IMU and Sun sensors only
- Low-gain antenna communications
  - Wide beamwidth for robust Earth communications
- Safe attitude
  - Typically solar arrays pointed at Sun

Response actions may consist of a series of steps.

The spacecraft must be shown to remain safe even during faults such as:

- Computer faults/swaps
- Temporary loss of attitude control
- Temporary loss of thermal control

---

# 11. Avionics Design Process

> **Source: Slides 32–39**

Slide 32 begins **Part 3: Design Process**.

## Overall Process

> **Source: Slide 33**

The avionics development flow is:

```text
Define Avionics Subsystem Requirements
                ↓
Define Avionics Architecture
                ↓
       Design Avionics Subsystem
          ↙              ↘
Select Avionics       Develop FSW
   Hardware              Code
          ↘              ↙
Build, Integrate, and Test
      Avionics Subsystem
                ↓
Deliver Avionics Subsystem
     to Spacecraft ATLO
                ↓
Operate Spacecraft with
    Avionics Subsystem
```

Approximate project phases:

| Phase | Avionics Activity |
|---|---|
| Phase A | Requirements and architecture |
| Phase B/C | Hardware selection and FSW development |
| Phase D | Build, integrate, test, deliver |
| Phase E | Operate |

Circular arrows on the diagram emphasize iteration.

---

## Requirements

> **Source: Slide 34**

Develop L4 avionics subsystem requirements in response to L3 flight-system requirements.

Examples:

> The avionics subsystem shall be single fault tolerant.

Drives:
- Redundancy

> The avionics subsystem shall tolerate the Jovian radiation environment.

Drives:
- Radiation-hardened hardware

> The avionics subsystem shall provide 100 Gb of data storage.

Drives:
- NVM card

> The avionics subsystem shall accommodate an imager and a spectrometer.

Drives:
- Interface card(s)

---

## Architecture

> **Source: Slide 35**

Perform key architecture trades and sizing analyses:

- Redundancy
- Processor type
- Serial vs. bus interface
- Interface-throughput sizing
- Memory sizing
- Ground-commanded vs. autonomous functions

---

## Design

> **Source: Slide 36**

### Hardware Selection

Select:

- Chassis
  - 3U
  - 6U
  - etc.
- Processor and other cards
  - Heritage vs. custom
- Harness

### FSW Design

Develop:

- Device drivers
- Function modules
- Activity modules
- Behavior modules
- Services
- FSW interfaces
- Boot and initialization

---

## Build and Test

> **Source: Slide 37**

- Fabricate or procure circuit boards/cards.
- Assemble avionics components and chassis.
- Perform qualification testing:
  - Mechanical
  - Thermal
- Load FSW.
- Perform integrated hardware/software functional testing.

---

## Deliver

> **Source: Slide 38**

- Deliver avionics subsystem engineering models into testbeds for system-level V&V.
- Deliver flight models into ATLO.
- Integrate with the rest of the flight hardware.
- Execute:
  - Functional tests
  - Environmental tests
  - Other verification
- Identify and resolve hardware/software issues.
- Rework as needed.

---

## Operate

> **Source: Slide 39**

During launch, cruise, and science operations:

- Operate avionics hardware and software.
- Trend hardware parameters:
  - Temperatures
  - Voltages
- Perform FSW updates as needed.

---

# 12. MSL Sol 200 Anomaly

> **Source: Slide 40**

Six months after landing on Mars, uncorrectable errors in MSL's NAND flash memory caused several FSW tasks to hang.

This prevented the prime computer from turning off for its normal recharge session.

If unresolved, the rover could have fully discharged its battery—a **brown-out**—within a few days, which would have been unrecoverable.

### Why the Watchdog Did Not Catch It

Normally, a watchdog timer detects unresponsive FSW.

In this anomaly:

- Some FSW tasks were hung.
- Enough other tasks remained responsive to reset the watchdog timer.
- The rover therefore did not automatically detect the problem.

### Recovery

Ground operators sent a **hardware command** that:

- Bypassed FSW
- Swapped computer sides
- Restored functionality using the backup computer

### Design Features Enabling Recovery

- Ability to generate telemetry and debug FSW without a NAND-based file system
- Ability to transfer critical telemetry between prime and backup computers
- Storage location readable without the faulty computer's FSW
- Hardware commands capable of swapping computers independently of FSW
- NAND segmented across multiple chips/boards for redundancy

---

# 13. Spacecraft Simulation Software

> **Source: Slides 41–42**

Slide 41 introduces **Spacecraft Simulation Software**.

## Basic Python Simulation Structure

> **Source: Slide 42**

### Spacecraft Configuration File

Contains settings controlling the spacecraft:

- Clock time
  - Simulation rate relative to actual time
- Processing time in Hz
  - Cycles per second
- Telemetry update interval
- Spacecraft moment of inertia
- Propellant load

### Simulation Configuration File

Contains environment settings.

May eventually include:

- Orbital ephemeris
- Sun position
- Ground-station position
- Other environmental information

### Simulation Script

- Reads configuration files
- Initializes spacecraft states
- Runs processing loop
- Executes commands
- Updates state values
- Generates telemetry
- Repeats indefinitely

### User Input

Sends commands.

Example:

```text
> Run_SC_Sim.py TestRun-1
SC Sim is running. Enter commands:

> CDH_NOOP
>
```

**NOOP = No Operation**, often used to verify interface/aliveness.

### Command/Event Log

Logs spacecraft actions.

Example:

```text
Wall Clock Time, SC Time (s), Event Description
20220204-133000, 0000000, Simulation started
20220204-133001, 0000001, SC configuration file read
20220204-133002, 0000002, Sim configuration file read
20220204-133200, 0000120, CDH_NOOP received
```

### Telemetry Log

Receives updated telemetry at regular intervals.

Example with 5-second telemetry:

```text
Wall Clock Time, SC Time (s), Channel, Value, units
20220204-133010, 0000010, CDH-0001, 0,
20220204-133015, 0000015, CDH-0001, 0,
20220204-133020, 0000020, CDH-0001, 0,
...
20220204-133155, 0000115, CDH-0001, 0,
20220204-133200, 0000120, CDH-0001, 1,
20220204-133205, 0000125, CDH-0001, 1,
...
```

The simulation uses flight-software logic intended to be identical in behavior to the modeled FSW.

---

# 14. Command and Telemetry

> **Source: Slide 43**

## Commands

Two types:

### Software Commands

Interpreted and executed by FSW.

### Hardware Commands

Bypass software and execute directly in hardware.

Example:

```text
HDW_SYS_RESET
```

### Class Command Format

For the class, binary translation is not required.

Format:

```text
[subsystem]_[command mnemonic],[argument 1],[argument 2],...
```

Examples:

```text
CDH_NOOP
CDH_EHA_RATE,5
```

`CDH_NOOP` executes no operation.

`CDH_EHA_RATE,5` sets the EHA rate to 5 seconds.

---

## Event Records

Format:

```text
Time, Event Description
```

Examples:

```text
0000145, Command successfully executed: CDH_NOOP
0000147, Command successfully executed: CDH_EHA_RATE
0000148, EHA Rate set to 5 seconds
```

For the class:

- No downlink-bit translation is required.
- Commands should produce a success or failure EVR.
- Additional EVRs should describe resulting state changes.

---

## EHA

Channelized telemetry provided at regular intervals.

Format:

```text
[subsystem]-[ID]: Description
```

Example:

```text
CDH-0001: Successful command execution counter
```

The counter increments each time a command executes.

Onboard status is continuously updated, while EHA is downlinked periodically, for example every 5–30 seconds.

---

# 15. Software Boot and Reset

> **Source: Slide 44**

## Overview

Except in rare cases, software is always running onboard.

A possible exception is hibernation, such as overnight on Mars, where a hardware timer automatically boots the software.

Fault monitors, including watchdogs, monitor execution and may trigger a hardware software reset.

## Boot and Reset Scenarios

### Testing

The most common boot scenario occurs during testing.

Desired result:

- Nominal/test configuration

### Initial Flight Boot

Prior to launch:

- Configure spacecraft for launch.
- May use two steps:
  1. Boot into test.
  2. Configure for launch.

### Anomaly-Induced Reset

Configures the spacecraft into a safe mode that protects hardware.

## Architecture

Reset behavior can use:

- Hard-coded responses
- Configurable tables
- Sequences
- Multiple possible states/modes

The lecture emphasizes that many architectures are possible.

## Example: FSW Reset During Testing

During initial boot:

1. Execute spacecraft configuration file.
2. Configure minimum functionality.
3. Use minimum default settings.
4. Keep devices powered off except the flight computer.

Good scripting practice is to clear or reinforce variable parameters so the same file can also reset software.

During a commanded or autonomous reset:

1. Reset software.
2. Run the SC configuration file.
3. Trip the FSW Reset fault monitor.
4. If monitor is disabled, do nothing further.
5. If enabled, run the fault response.
6. Run the safe-mode configuration file.

### Expected Telemetry

**EVRs**
- FSW reset
- Fault-monitor trip
- Fault-monitor response
- Configuration-file execution
- Activities within configuration file
- Additional hard-coded activities

**EHA**
- Spacecraft state changes, e.g. Test → Safe
- FSW reset counter increments
- Fault-monitor counter increments
- Fault-response counter increments

## Example Spacecraft Commands

### Successful Command Examples

| Subsystem | Command | Description | Expected Response |
|---|---|---|---|
| **C&DH** | `CDH_NOOP` | This command does No Operation (ie, nothing), which is often used to check whether there is a valid command path to the spacecraft. | **EVR:** Command successfully executed<br>**EHA:** CDH-001 Successful command counter (+1) |
| **C&DH** | `CDH_EHA_RATE,[x]` | Sets the telemetry (EHA) rate for how often packets are received. Valid arguments are 5 to 1,000 sec. | **EVR:** EHA rate updated to x sec<br>**EHA:** CDH-002 EHA Rate = x |
| **C&DH** | `HWD_SYS_RESET` | Resets flight software | See description in separate chart (Boot/Reset) |
| **C&DH** | `CDH_UPLOSS_TIMER,[x]` | Resets the uploss timer to x seconds from the present time. Note that if no commands are received within this period of time, the spacecraft will go into safe mode. | **EVR:** Uploss timer set to x sec<br>**EHA:** CDH-003 Uploss timer = x (should be counting down to 0) |
| **C&DH** | `CDH_MODE,[mode]` | Sets the spacecraft mode by running an onboard configuration file that sets and/or reinforces the devices states for the relevant mode | **EVR:** Spacecraft mode to set [mode]<br>**EHA:** CDH-004 Spacecraft Mode = [mode] |
| **Power** | `PWR_DEVICE_STATE,[device],[state]` | Changes state of a device. Note that this should likely be consistent with the power modes table with respect to both devices, states, and resulting power (W) values. | **EVR:** [device] state changed to [state]<br>**EHA:** PWR-000x: [Device] State = [state]<br>PWR-000y: [Device] Current = [current in W] |

---

### Example Spacecraft Command Failures

| Subsystem | Command | Description | Expected Response | Comments |
|---|---|---|---|---|
| **C&DH** | `[any unrecognized command stem]` | Any unrecognized command stem will fail onboard command validation | **EVR:** Command validation failed<br>**EHA:** Invalid command counter (+1) | |
| **C&DH** | `[any argument that exceeds allowed range or otherwise fails]` | For example, if `"CDH_EHA_RATE,1"` is sent, this should fail to execute. | **EVR:** Command execution failed<br>**EHA:** Failed command counter (+1) | |

---

# 16. Verification Test Procedures

> **Source: Slides 47–49**

## Verification Test Procedure

> **Source: Slide 47**

The lecture introduces a real THEMIS probe-instrument Limited Performance Test for TVAC as an example of a verification procedure.

---

## Typical Verification Procedure Outline

> **Source: Slide 48**

### Cover Page

- Project
- Test name
- Procedure number
- Version

### Usage Log

Table containing:

- Date
- Activity description
- Session/report number
- Test conductor

### Signatures

- Names
- Titles
- Signatures of preparer and approvers

### Revisions and Changes

- Revision number
- Description
- Date

### Table of Contents

### Introduction

- Objective
- Scope
- Hazardous operations
- Venue

### Requirements

**Personnel**
- Two-person minimum / buddy system when hardware is used

**Required Equipment**
- Support equipment
  - GSE rack
  - Ground-system workstation
- Special equipment
  - Breakout boxes
  - Oscilloscopes

**Applicable Documents**
- Functional descriptions
- Interface control documents
- ESD procedures
- Safety documents

### Special Instructions

**Safety**
- General safety
- Hardware safety
- Applicable safety concerns such as ESD

**Environmental Constraints**
- Example humidity:

```text
30–70%
```

- Temperature requirements

**Special Considerations**
- Additional notes

### Preparation

**Hardware Configuration**
- Hardware
- Serial number/version
- Comments

**Software Configuration**
- Software
- Version
- Comments

**Test Equipment Configuration**
- Instrument
- Model
- Serial number
- Comments

### Functional Procedure

- Test setup
- Test 1
  - Test Case A
  - Test Case B
  - etc.
- Test n
- Shutdown

### Appendix

- References
- Printouts/files used

### Additional Notes

- Procedures are often scripted, e.g. in Python, especially for regression testing.
- Boilerplate sections are commonly reused but must be tailored.
- Unnecessary sections may be removed or marked N/A for software-only tests.

---

## Functional Portion of a Test Procedure

> **Source: Slide 49**

Each functional test generally includes:

- Description
- Test-case list
- Requirements and/or verification items being verified
- Initial setup
- Step-by-step test cases
- Shutdown procedure

### Coverage

Test cases must verify the full intended functionality.

For a telecom-transmission-rate requirement, coverage may include:

- Every allowed rate
  - 10 bps
  - 2,000 bps
  - 50 kbps
  - 2 Mbps
  - etc.
- Encoding against the flight-ground ICD
- Other configurations
  - Long frames
  - Short frames
- Adequate criteria
  - Timing
  - Data format

### Step Specificity

Each step should identify:

- **Who** performs the action
- **What** action is performed
- **How** the action is performed
  - User interface
  - Instrument
  - Other required information

---

# 17. C&DH and FSW Downlink Verification Example

> **Source: Slides 50–52**

## Downlink Verification Test

> **Source: Slides 50–51**

### Test 1: Downlink Configurations

Verifies C&DH ULDL board configurations for:

- Rates
- Encoding
- Frame lengths
- X-band radios
- UHF radios
- Prime and redundant radios

The testbed test using FSW and engineering models is more comprehensive than the telecom functional test later performed in ATLO.

Test cases:

- A: SDST-A configurations for each data rate
- B: SDST-B configurations for each data rate
- C–F:
  - UHF-A
  - UHF-B
  - Mode changes
  - Off-nominal configurations

### Requirements

The procedure includes a requirements table with:

- Requirement number
- Text
- Status
- Comments

Vague requirements may be decomposed into verification items used to sell off the requirement.

### Test Case A: SDST-A Downlink Configurations

Representative procedure:

```text
5-01 TA  Disable TZ radio interface in simulation SW
         SSE → uldl tz_interface off

5-02 TA  Enable SDST-A
         SSE → uldl sdsta_interface on

5-03 TA  Verify GSE downlink is configured for SDST-A
         SSE-0101: ULDL_SDSTA_ONOFF      (1 = On)
         SSE-0102: ULDL_SDSTB_ONOFF      (0)
         SSE-0103: ULDL_UHFA_ONOFF       (0)
         SSE-0104: ULDL_UHFB_ONOFF       (0)
         SSE-0105: ULDL_TZ_ONOFF         (0)
         SSE-0114: ULDL_Downlink_Source  (0 = SDSTA)

5-04 TA  Send FSW command to change downlink configuration
         GDS → CDH_DL_SET_TX_CONFIG,LONG_SDSTA_50K

5-05 TA  Wait 1 minute
         Includes maximum expected synchronization delay
         Goal: ≥100 frames
         Minimum threshold: 3 frames for 10 bps

5-06 TA  Verify frame-accountability configuration
         TZ Downlink Configuration
         Ant Downlink Configuration
         LV Downlink Configuration

5-07 TA  Verify spacecraft telemetry
         CDH-1010: DL_DATA_RATE
         CDH-1011: DL_FRAME_LENGTH
         CDH-1012: DL_FRAMES_SENT
         CDH-1013: DL_FRAMES_DROPPED
         CDH-1014: DL_FRAME_COUNT

5-08 TA  Post-process using gds_get_frames
         Verify TZ, antenna, and LV downlink rates
```

The test is repeated for each rate on each relevant antenna.

### Annotated Procedure

Slide 51 identifies:

- **TA** = Test Analyst
- **SSE** = user interface for Software Simulation Environment
- **GDS** = user interface for Ground Data System
- Commands are written exactly as required.
- SSE provides channelized telemetry.
- Spacecraft FSW provides the telemetry the software is actually sending.
- Ground verification checks:
  - Frames
  - Timing
  - Formatting
  - Other received characteristics

---

## As-Run Test

> **Source: Slide 52**

The as-run example is:

**Session Report #129, June 19, 2022**

Recorded results include:

- Initial interface-state checks passed.
- Command execution steps passed.
- Expected frame-accountability configuration did **not** match:
  - Expected LONG
  - Observed SHORT
- The issue was written up as:

**Anomaly #577**

The test result was:

**Not Passed**

Other recorded values included:

- Data rate: 50,000 bps
- Frame length: 1,000 bytes
- Frames sent: 1,254
- Frames dropped: 0
- Sequential frame count: YES
- Antenna downlink rate: 50,000 bps

The example demonstrates that a verification procedure is not merely a script—it records objective evidence and identifies anomalies when actual behavior differs from expected behavior.

---

# 18. Typical Test and Spacecraft Data

> **Source: Slide 53**

## Test Files

- Original signed procedure
- As-run procedure
- Files used during the test
  - Command sequences
  - Other inputs
- Session report

## Software Simulation Environment

Data depends on the simulated hardware/software.

It may resemble spacecraft telemetry, including channelized EHA.

## Spacecraft Telemetry

When the Ground Data System unpacks telemetry, it can add fields such as:

- Session ID
- Testbed
- Record Type
- Received Time / Earth Return Time (ERT)

ERT is typically represented in an ISO-8601-style format.

For EHA, an alarm state may also be added to identify values exceeding:

- Caution thresholds
- Warning thresholds

### EHA Fields

Common EHA fields include:

- Channel ID
- Channel name
- Module
- DN
- EU
- SCLK
- SCET

**DN — Design Number**
- Raw value received from spacecraft

**EU — Enumerated Number**
- Converted value meaningful to users
- Example: raw `0` may map to `Off`

**SCLK — Spacecraft Clock**
- Unix-time-like spacecraft event timestamp
- Seconds since midnight January 1, 1970, including subseconds

**SCET — Spacecraft Event Time**
- SCLK converted to a more conventional ISO-8601-style format

### EVR Fields

- EVR name
- Message
- EVR type
  - Diagnostic
  - Warning
  - etc.
- Sequence ID
  - Helps identify missing EVRs
- SCLK
- SCET

### Spacecraft Files

Custom files may also be downlinked:

- Engineering parameter tables
- Science data
- Images

Hardware and simulated models often have the ability to generate test files.

---

# Lecture Summary

> **Source: Slides 1–53**

Avionics provides the spacecraft's central command, control, data-handling, timing, autonomy, and fault-management capability.

A representative avionics architecture contains:

- Flight-computer chassis
- Power supply
- SBC / processor card
- Relay / driver cards
- Serial interface cards
- Telecom interface card
- Non-volatile memory
- Backplane
- Independent health-monitoring hardware

Flight software is organized around functions and behaviors such as:

- Boot and initialization
- Device intercommunication
- Command management
- Telemetry/data management
- Time management
- Autonomous spacecraft activities
- System modes
- Fault management
- FSW update

The architecture can be viewed as layers:

```text
Behavior Layer
      ↓
Activity Layer
      ↓
Functional Layer
      ↓
Hardware Layer

Services span the architecture.
```

The primary avionics functions introduced are:

| Function | Purpose |
|---|---|
| Processing | Execute FSW and overall spacecraft command/control |
| Intercommunications | Exchange data among spacecraft devices |
| Uplink / Command | Receive, validate, decode, and execute ground commands |
| Downlink / Data | Collect, store, format, packetize, and transmit telemetry/data |
| Time Management | Maintain and distribute spacecraft time |
| Autonomy | Execute onboard behaviors without continuous ground control |
| Fault Management | Detect off-nominal conditions and execute recovery responses |

Fault tolerance is a major design driver. Relevant architecture choices include:

- Single-string vs. redundant
- Block-swapped vs. cross-strapped
- Cold spare vs. warm spare
- Independent health monitoring
- Hardware commands that bypass FSW
- Multiple FSW images
- Redundant memory and processing paths

The MSL Sol 200 anomaly demonstrates why these features matter. NAND errors caused FSW tasks to hang without triggering the watchdog, but the rover was recoverable because operators could bypass FSW and command a hardware computer-side swap.

The avionics development process proceeds from requirements and architecture through hardware/FSW design, build, integration, verification, delivery to ATLO, and flight operation.

Verification procedures provide structured evidence that requirements are satisfied. A good test procedure specifies:

- What is being verified
- Test configuration
- Personnel and equipment
- Exact commands/actions
- Expected telemetry
- Pass/fail criteria
- Recorded results
- Anomalies

The as-run downlink-verification example demonstrates that verification must compare actual spacecraft behavior against expected behavior and formally record deviations rather than assuming success.

The spacecraft simulation portion connects these avionics concepts directly to software implementation through:

- Configuration files
- Processing loops
- Commands
- EVRs
- EHA telemetry
- Logs
- FSW behavior
- Verification procedures
