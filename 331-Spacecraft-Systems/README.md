# ASTE 331 — Spacecraft Systems Engineering

**Term:** Fall  
**Instructors:** Jim Chase, Danielle Marsh  
**TAs:** Arianna A, Sarah G, Brian P, Jonathan H, Sandra H, Mia C, Elizabeth B <br>
**Meeting Time/Location:** Fridays, 1:00–4:40 PM  

---

## About This Course

ASTE 331 introduces the fundamentals of spacecraft systems engineering and the design, integration, and operation of the major spacecraft subsystems.

Topics include:

- Spacecraft systems engineering fundamentals
- Propulsion
- Attitude Control Systems (ACS)
- Avionics
- Telecommunications
- Electrical power
- Mechanical systems
- Thermal control

The course emphasizes how these subsystems interact as parts of a single spacecraft rather than treating them as completely independent systems.

Concepts from ASTE 331 carry directly into **ASTE 421 — Mission Design** in the spring, where students apply systems-level thinking to complete mission architectures.

---

## Purpose of This Page

This page is the course-content reference and navigation hub for **ASTE 331**.

It is designed to live alongside the course's slides, homework, and notes in a shared **ASTE 331/421 GitHub repository**.

The repository is intended to give students one organized place to:

- access course materials by **course, week, and subsystem**;
- follow the sequence of material from **ASTE 331 into ASTE 421**;
- find the original lecture slide associated with a concept;
- ask questions in **GitHub Discussions** using a precise course, lecture, and slide reference; and
- give connected tools such as **Claude or Codex** enough structure to point students back to the relevant course material.

The lecture reference files therefore favor **course navigation, detailed explanations, and source traceability** over reproducing the visual layout of the original PowerPoint decks.

---

## How to Use This Repo

Each lecture is organized into its own folder containing:

- **Lecture Reference** — a detailed Markdown walkthrough of the lecture;
- **Original Slides** — the source PDF provided for the lecture; and
- additional course materials when applicable.

The Markdown lecture references reorganize the original slides by **concept** while preserving slide-source references throughout.

Within each lecture reference, you will find:

- a **lecture overview** describing the major ideas covered;
- a **table of contents** for quickly navigating the lecture;
- detailed explanations of the original lecture material;
- recreated **tables, equations, and technical relationships**;
- descriptions of important **figures, diagrams, and spacecraft architectures**; and
- **slide-source markers** identifying where each concept appears in the original lecture.

The original PDF remains the authoritative visual source. The Markdown files are intended to make the material easier to navigate, search, reference, and discuss.

---

## Weekly Content

| Week | Topic | Lecture Reference |
|---:|---|---|
| 1 | Space Systems Intro | [01-Space-Systems-Intro.md](01-Space-Systems-Intro/01-Space-Systems-Intro.md) |
| 2 | Propulsion | [02-Propulsion.md](02-Propulsion/02-Propulsion.md) |
| 3 | Attitude Control Systems (ACS) | [03-ACS.md](03-ACS/03-ACS.md) |
| 4 | Avionics | [04-Avionics.md](04-Avionics/04-Avionics.md) |
| 5 | Telecom | [05-Telecom.md](05-Telecom/05-Telecom.md) |
| 6 | Power | [06-Power.md](06-Power/06-Power.md) |
| 7 | Mechanical | [07-Mechanical.md](07-Mechanical/07-Mechanical.md) |
| 8 | Thermal | [08-Thermal.md](08-Thermal/08-Thermal.md) |

---

## Finding Material

If you are looking for a particular concept, start with the lecture most closely associated with that subsystem.

| Looking for... | Start Here |
|---|---|
| Spacecraft architecture, requirements, systems engineering, or subsystem organization | [Week 1 — Space Systems Intro](01-Space-Systems-Intro/01-Space-Systems-Intro.md) |
| Delta-V, propellant, thrusters, tanks, or propulsion schematics | [Week 2 — Propulsion](02-Propulsion/02-Propulsion.md) |
| Reaction wheels, star trackers, pointing, disturbances, or spacecraft attitude | [Week 3 — ACS](03-ACS/03-ACS.md) |
| Flight computers, FSW, commands, telemetry, memory, or fault management | [Week 4 — Avionics](04-Avionics/04-Avionics.md) |
| Antennas, link budgets, RF, data rates, EEIS, or the DSN | [Week 5 — Telecom](05-Telecom/05-Telecom.md) |
| Solar arrays, batteries, power buses, regulation, or power distribution | [Week 6 — Power](06-Power/06-Power.md) |
| Spacecraft structures, mechanisms, launch loads, vibration, or structural analysis | [Week 7 — Mechanical](07-Mechanical/07-Mechanical.md) |
| Heat transfer, MLI, radiators, heaters, thermal balance, or TVAC | [Week 8 — Thermal](08-Thermal/08-Thermal.md) |

Because spacecraft subsystems are interconnected, many concepts appear in more than one lecture.

For example:

- reaction-control thrusters involve both **Propulsion** and **ACS**;
- antenna pointing involves both **Telecom** and **ACS**;
- heater power involves both **Thermal** and **Power**;
- electronics heat dissipation involves **Avionics**, **Power**, and **Thermal**;
- launch loads and spacecraft mass properties involve both **Mechanical** and **ACS**.

When a topic crosses subsystem boundaries, reviewing the relevant sections from multiple lectures can provide a more complete picture.

---

## Slide Source References

The lecture reference files are designed so that individual concepts can be traced back to the original lecture slides.

Sections use source markers such as:

> **Source: Slide 7**

or:

> **Source: Slides 19–25**

The original source PDF is also identified near the top of each Markdown file.

For example:

```text
Source: 331_02_Propulsion_20250905.pdf
```

Together, the PDF filename and slide marker provide a precise reference to the original course material.

This is especially useful when:

- reviewing a concept before an exam;
- comparing the Markdown explanation with the professor's original figure or diagram;
- asking a question in GitHub Discussions; or
- asking a connected tool to locate and explain a specific part of the course.

---

## How to Cite a Slide When Asking a Question

When asking a question about course material, include:

1. the **course**;
2. the **lecture/topic**;
3. the **source PDF**; and
4. the **slide number or range**.

For example:

> In ASTE 331 Propulsion, slide 7 of `331_02_Propulsion_20250905.pdf`, how does the rocket equation relate wet mass, dry mass, and specific impulse?

For a question involving several slides:

> In ASTE 331 ACS, slides 19–25 of `331_03_ACS_20250926.pdf`, how do the different disturbance torques affect ACS actuator sizing?

Providing this information makes it much easier for:

- classmates;
- instructors and TAs;
- GitHub Discussions;
- Claude;
- Codex; and
- other connected tools

to locate the exact material associated with the question.

---

## Asking Questions

For course-content questions, use [Piazza](https://piazza.com/class/mp5es26r4qwau).

When possible, include the lecture and slide reference described above.

A useful Discussion title might look like:

```text
[ASTE 331][Propulsion][Slide 7] Rocket Equation and Wet Mass
```

The question itself could begin with:

```text
Course: ASTE 331
Lecture: 02 — Propulsion
Source: 331_02_Propulsion_20250905.pdf
Slide: 7
```

Then describe the specific concept, equation, figure, or step that is unclear.

This format makes questions easier to:

- answer;
- search;
- reference later; and
- reuse when another student has the same question.

For **grading, accommodations, or personal matters**, contact the course staff through the appropriate private course channel rather than Piazza.

---

## Using Claude, Codex, and Other Connected Tools

The lecture files are intentionally structured so connected tools can identify both the relevant concept and its original source.

When asking a connected tool about course material, provide as much context as possible.

For example:

```text
Using the ASTE 331 course materials in this repository, explain the
gravity-gradient torque discussion in Lecture 03 (ACS), and tell me
which slide(s) I should review.
```

A useful response should point back to the relevant lecture and original slide reference rather than treating the repository as an unsourced textbook.

For questions involving multiple subsystems, ask the tool to identify each relevant lecture.

For example:

```text
How does spacecraft attitude affect both telecom antenna pointing
and thermal radiator performance?

Reference the relevant ASTE 331 lectures and slide numbers.
```

You can also ask questions by source directly:

```text
Using 331_06_Power_20251107.pdf and the corresponding Power lecture
reference, explain how solar-array sizing changes with distance
from the Sun.
```

---

## ASTE 331 to ASTE 421

ASTE 331 establishes the spacecraft-subsystem foundation used in **ASTE 421 — Mission Design**.

```text
ASTE 331
Spacecraft Systems Engineering
        |
        |  Subsystem knowledge
        |  Requirements
        |  Interfaces
        |  Trades
        |  Verification
        v
ASTE 421
Mission Design
        |
        |  Mission architecture
        |  Mission-level trades
        |  Integrated spacecraft design
        v
Complete Mission Concept
```

Keeping both courses in the same repository makes it easier to trace a mission-design decision in ASTE 421 back to the subsystem concepts introduced in ASTE 331.

---

## Repository Conventions

To keep the repository consistent, searchable, and useful for both students and connected tools:

- course materials are organized by **course, lecture, and subsystem**;
- each ASTE 331 lecture is contained in its own folder;
- lecture folders contain the **Markdown lecture reference** and **original source PDF**;
- original source PDFs are identified by their **exact filenames**;
- lecture content is organized by **concept rather than forcing one Markdown section per slide**;
- original slide numbers are preserved using **source markers**;
- equations are written using **GitHub-compatible math formatting**;
- Markdown titles and headings use **plain text only**;
- tables are recreated in Markdown when practical;
- important figures and diagrams are described in text; and
- source traceability is preserved so students can return to the original lecture material.

---

## Course Materials and Attribution

The materials in this repository are provided for use in ASTE 331/421 and should be used in accordance with the course's policies and permissions.

The Markdown lecture references are organized from the original course materials and retain slide-level source references so students can trace information back to the appropriate lecture and original source.

The Markdown files are intended to supplement the original course materials by improving:

- navigation;
- searchability;
- accessibility;
- question tracking; and
- source traceability.

They are not intended to replace the original lecture slides.

---

## Questions?

Use [GitHub Discussions](../../discussions) for course-content questions.

When asking about lecture material, include the **course, lecture, source PDF, and slide number** whenever possible.

For grading or personal matters, contact the course staff through the appropriate private course channel.