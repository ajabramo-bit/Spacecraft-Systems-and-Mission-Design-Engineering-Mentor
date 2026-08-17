# ASTE 421 — Mission Design

**Term:** Spring  
**Instructors:** Jim Chase, Danielle Marsh  
**TAs:** Arianna A, Sarah G, Brian P, Jonathan H, Sandra H, Mia C, Elizabeth B <br>
**Meeting Time/Location:** Fridays, 1:00–4:40 PM  

---

## About This Course

ASTE 421 builds on the spacecraft systems-engineering foundation developed in **ASTE 331 — Spacecraft Systems Engineering**.

While ASTE 331 focuses primarily on the design, analysis, integration, and operation of individual spacecraft subsystems, ASTE 421 expands that perspective to the **mission level**.

The course applies systems-engineering principles to the development of complete space-mission concepts, including the relationships between:

- Mission objectives
- Science and stakeholder requirements
- Mission architecture
- Concept of Operations (ConOps)
- Orbital mechanics and trajectory design
- Spacecraft design
- Payload design
- Launch systems
- Ground systems
- Mission operations
- Cost
- Schedule
- Risk
- Verification and validation
- System-level trades

The goal is to understand how these elements interact to produce a complete, feasible, and defensible mission design.

Concepts introduced in **ASTE 331** should therefore be treated as foundational material for ASTE 421.

---

## Purpose of This Page

This page is the course-content reference and navigation hub for **ASTE 421**.

It is designed to live alongside the course's slides, homework, notes, and ASTE 331 materials in a shared **ASTE 331/421 GitHub repository**.

The repository is intended to give students one organized place to:

- access course materials by **course, week, and topic**;
- follow the sequence of material from **ASTE 331 into ASTE 421**;
- connect mission-level decisions back to the relevant spacecraft-subsystem concepts from ASTE 331;
- find the original lecture slide associated with a concept;
- ask questions in **GitHub Discussions** using a precise course, lecture, and slide reference; and
- give connected tools such as **Claude or Codex** enough structure to point students back to the relevant course material.

The lecture reference files therefore favor **course navigation, detailed explanations, and source traceability** over reproducing the visual layout of the original PowerPoint decks.

---

## How to Use This Repo

Each ASTE 421 lecture will be organized into its own folder containing:

- **Lecture Reference** — a detailed Markdown walkthrough of the lecture;
- **Original Slides** — the source PDF provided for the lecture; and
- additional course materials when applicable.

The Markdown lecture references will reorganize the original slides by **concept** while preserving slide-source references throughout.

Within each lecture reference, you will find:

- a **lecture overview** describing the major ideas covered;
- a **table of contents** for quickly navigating the lecture;
- detailed explanations of the original lecture material;
- recreated **tables, equations, and technical relationships**;
- descriptions of important **figures, diagrams, mission architectures, and trades**; and
- **slide-source markers** identifying where each concept appears in the original lecture.

The original PDF remains the authoritative visual source. The Markdown files are intended to make the material easier to navigate, search, reference, and discuss.

---

## Weekly Content

> **Note:** Lecture references will be added as ASTE 421 course content is organized and converted.

| Week | Topic | Lecture Reference |
|---:|---|---|
| 1 | <Topic> | *Lecture reference coming soon* |
| 2 | <Topic> | *Lecture reference coming soon* |
| 3 | <Topic> | *Lecture reference coming soon* |
| 4 | <Topic> | *Lecture reference coming soon* |
| 5 | <Topic> | *Lecture reference coming soon* |
| 6 | <Topic> | *Lecture reference coming soon* |
| 7 | <Topic> | *Lecture reference coming soon* |
| 8 | <Topic> | *Lecture reference coming soon* |
| 9 | <Topic> | *Lecture reference coming soon* |
| 10 | <Topic> | *Lecture reference coming soon* |
| 11 | <Topic> | *Lecture reference coming soon* |
| 12 | <Topic> | *Lecture reference coming soon* |
| 13 | <Topic> | *Lecture reference coming soon* |
| 14 | <Topic> | *Lecture reference coming soon* |
| 15 | <Topic> | *Lecture reference coming soon* |

---

## Connecting ASTE 421 to ASTE 331

ASTE 421 builds directly on the subsystem knowledge developed in ASTE 331.

When a mission-level design decision depends on a spacecraft subsystem, the ASTE 331 lecture references can be used as supporting material.

| Mission-Design Question | Relevant ASTE 331 Material |
|---|---|
| How much Delta-V can the spacecraft provide? | [Propulsion](../ASTE-331/02-Propulsion/02-Propulsion.md) |
| Can the spacecraft achieve the required pointing and stability? | [Attitude Control Systems](../ASTE-331/03-ACS/03-ACS.md) |
| Can the spacecraft autonomously execute the mission? | [Avionics](../ASTE-331/04-Avionics/04-Avionics.md) |
| Can the mission return the required amount of data? | [Telecom](../ASTE-331/05-Telecom/05-Telecom.md) |
| Can the spacecraft generate and store enough electrical power? | [Power](../ASTE-331/06-Power/06-Power.md) |
| Can the spacecraft survive launch and support the required configuration? | [Mechanical](../ASTE-331/07-Mechanical/07-Mechanical.md) |
| Can spacecraft hardware remain within allowable temperatures? | [Thermal](../ASTE-331/08-Thermal/08-Thermal.md) |
| How do subsystem requirements flow from mission objectives? | [Space Systems Intro](../ASTE-331/01-Space-Systems-Intro/01-Space-Systems-Intro.md) |

> **Note:** The relative paths above assume the ASTE 331 and ASTE 421 course folders are siblings within the same repository. Update these paths if the final repository structure differs.

---

## From Spacecraft Design to Mission Design

ASTE 331 and ASTE 421 are intended to form a connected sequence.

```text
ASTE 331
Spacecraft Systems Engineering
        |
        |  Propulsion
        |  ACS
        |  Avionics
        |  Telecom
        |  Power
        |  Mechanical
        |  Thermal
        |
        v
Spacecraft-Level Understanding
        |
        |  Requirements
        |  Interfaces
        |  Constraints
        |  Margins
        |  Trades
        |  Verification
        |
        v
ASTE 421
Mission Design
        |
        |  Mission Objectives
        |  Mission Requirements
        |  Mission Architecture
        |  ConOps
        |  Trajectory
        |  Payload
        |  Spacecraft
        |  Launch
        |  Ground System
        |  Operations
        |  Cost / Schedule / Risk
        |
        v
Integrated Mission Concept
```

A mission architecture developed in ASTE 421 ultimately creates requirements that must be satisfied by the spacecraft and its subsystems.

Likewise, subsystem limitations identified in ASTE 331 can constrain the mission architecture.

The relationship therefore works in **both directions**.

---

## Finding Material

Once the ASTE 421 lecture references are available, this section can be used to quickly identify where a mission-design concept is discussed.

| Looking for... | Start Here |
|---|---|
| Mission objectives and stakeholder needs | *Lecture reference coming soon* |
| Requirements development and flowdown | *Lecture reference coming soon* |
| Mission architecture | *Lecture reference coming soon* |
| Concept of Operations (ConOps) | *Lecture reference coming soon* |
| Orbital mechanics or trajectory design | *Lecture reference coming soon* |
| Payload and science requirements | *Lecture reference coming soon* |
| Spacecraft-level design | *Lecture reference coming soon* |
| Launch system | *Lecture reference coming soon* |
| Ground system and mission operations | *Lecture reference coming soon* |
| Cost and schedule | *Lecture reference coming soon* |
| Risk and margins | *Lecture reference coming soon* |
| Verification and validation | *Lecture reference coming soon* |
| Mission-level trade studies | *Lecture reference coming soon* |

This table should be updated as lecture topics and filenames are finalized.

---

## Slide Source References

The ASTE 421 lecture reference files will use the same source-traceability convention as ASTE 331.

Sections will include source markers such as:

> **Source: Slide 12**

or:

> **Source: Slides 20–27**

The original source PDF will also be identified near the top of each Markdown file.

For example:

```text
Source: <421_Lecture_Source_File.pdf>
```

Together, the PDF filename and slide marker provide a precise reference to the original course material.

This allows a student to move between:

```text
Concept
   ↓
Markdown Lecture Reference
   ↓
Original Lecture
   ↓
Exact Slide(s)
```

---

## How to Cite a Slide When Asking a Question

When asking a question about ASTE 421 course material, include:

1. the **course**;
2. the **lecture/topic**;
3. the **source PDF**; and
4. the **slide number or range**.

For example:

> In ASTE 421 `<Lecture Topic>`, slide `<X>` of `<source-file.pdf>`, how does this requirement affect the mission architecture?

For a question involving several slides:

> In ASTE 421 `<Lecture Topic>`, slides `<X–Y>` of `<source-file.pdf>`, how does this trade affect the spacecraft and trajectory design?

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

For course-content questions, use [GitHub Discussions](../../discussions).

When possible, include the lecture and slide reference described above.

A useful Discussion title might look like:

```text
[ASTE 421][Mission Architecture][Slide 12] Architecture Trade Question
```

The question itself could begin with:

```text
Course: ASTE 421
Lecture: <Lecture Number — Topic>
Source: <source-file.pdf>
Slide: <X>
```

Then describe the specific:

- concept;
- requirement;
- trade;
- architecture;
- equation;
- figure; or
- design decision

that is unclear.

This format makes questions easier to:

- answer;
- search;
- reference later; and
- reuse when another student has the same question.

For **grading, accommodations, or personal matters**, contact the course staff through the appropriate private course channel rather than GitHub Discussions.

---

## Using Claude, Codex, and Other Connected Tools

The ASTE 421 lecture references will be intentionally structured so connected tools can identify both the relevant concept and its original source.

For example:

```text
Using the ASTE 421 course materials in this repository, explain the
mission-architecture trade discussed in Lecture <X> and tell me which
slide(s) I should review.
```

For questions involving ASTE 331 subsystem material:

```text
Using the ASTE 331 and ASTE 421 materials in this repository, explain
how this mission-level requirement flows down into spacecraft subsystem
requirements.

Reference the relevant lectures and slide numbers from both courses.
```

For a cross-course design question:

```text
How would increasing the required science-data return affect the
mission architecture?

Identify the relevant ASTE 421 material and connect it to the ASTE 331
Telecom and Power lectures.
```

A useful response should point back to the relevant course material and original slide references rather than treating the repository as an unsourced textbook.

---

## Cross-Course Questions

Some of the most useful questions will involve both courses.

For example:

```text
Mission Objective
      ↓
ASTE 421 Mission Requirement
      ↓
Mission Architecture / ConOps
      ↓
Spacecraft Requirement
      ↓
ASTE 331 Subsystem Requirement
      ↓
Hardware / Software Design
```

A question might therefore begin in ASTE 421 but require reviewing ASTE 331.

Examples include:

- How does trajectory Delta-V affect propulsion sizing?
- How does science-data volume affect telecom and power?
- How does observation geometry affect ACS and thermal design?
- How does mission duration affect redundancy and avionics?
- How does launch-vehicle selection affect mechanical design?
- How do payload temperature requirements affect thermal architecture?
- How do mission operations affect battery sizing?
- How does spacecraft-Earth range affect telecom architecture?

The shared repository is intended to make these connections easier to trace.

---

## Repository Conventions

To keep ASTE 331 and ASTE 421 consistent, searchable, and useful for both students and connected tools:

- course materials are organized by **course, lecture, and topic**;
- each lecture is contained in its own folder;
- lecture folders contain the **Markdown lecture reference** and **original source PDF**;
- original source PDFs are identified by their **exact filenames**;
- lecture content is organized by **concept rather than forcing one Markdown section per slide**;
- original slide numbers are preserved using **source markers**;
- equations are written using **GitHub-compatible math formatting**;
- Markdown titles and headings use **plain text only**;
- tables are recreated in Markdown when practical;
- important figures, diagrams, architectures, and trades are described in text; and
- source traceability is preserved so students can return to the original lecture material.

---

## Course Materials and Attribution

The materials in this repository are provided for use in ASTE 331/421 and should be used in accordance with the course's policies and permissions.

The Markdown lecture references are organized from the original course materials and retain slide-level source references so students can trace information back to the appropriate lecture and original source.

The Markdown files are intended to supplement the original course materials by improving:

- navigation;
- searchability;
- accessibility;
- cross-course connections;
- question tracking; and
- source traceability.

They are not intended to replace the original lecture slides.

---

## Questions?

Use [GitHub Discussions](../../discussions) for course-content questions.

When asking about lecture material, include the **course, lecture, source PDF, and slide number** whenever possible.

For questions that cross between ASTE 331 and ASTE 421, include references from **both courses** when possible.

For grading or personal matters, contact the course staff through the appropriate private course channel.