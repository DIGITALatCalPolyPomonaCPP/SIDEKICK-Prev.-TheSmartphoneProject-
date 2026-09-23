# SIDEKICK — The Smartphone Project

**SIDEKICK, previously named TheSmartphoneProject, is DIGITAL @ Cal Poly Pomona's flagship systems-engineering project: a student-designed modular smartphone built around an FPGA-based computing platform.** It treats the phone as one integrated product spanning programmable logic, circuit design, embedded software, operating systems, sensing, user interaction, mechanical design, and thermal engineering.

<p align="center">
  <a href="https://photos.app.goo.gl/fKSVxjnxUvrLaF7E6">
    <img src="documentation/media/sidekick-fpga-mainboard-prototype.jpg" alt="SIDEKICK FPGA smartphone mainboard prototype" width="620">
  </a>
</p>

<p align="center"><em>FPGA smartphone mainboard prototype. <a href="https://photos.app.goo.gl/fKSVxjnxUvrLaF7E6">View the project photo album.</a></em></p>

**Repository status:** This is an archival engineering snapshot. It consolidates original design files, subsystem iterations, planning documents, curricula, and project updates that were previously distributed across multiple repositories and contributor archives. It does not claim that every subsystem reached production readiness or that the files currently assemble into a finished phone.

## Executive summary

Technology has always evolved. What has changed is the pace at which innovation reshapes the world around us. Entire industries can now emerge, mature, and reinvent themselves within the span of a student's undergraduate education. Artificial intelligence is reshaping knowledge-based work, robotics is moving from laboratories into homes and industry, and manufacturing is becoming increasingly autonomous.

**The technologies that will define our students' careers have not all been invented yet.**

Industry has responded by becoming increasingly interdisciplinary. The products that define modern society are rarely conceived, developed, or delivered through engineering alone. They emerge from engineering, business, operations, manufacturing, research, and design working toward a common objective.

DIGITAL @ Cal Poly Pomona was created in response to this shift. It does not replace traditional engineering education or the student organizations that apply it through competitions, research, and hands-on work. DIGITAL bridges the space between them by organizing around the process through which ideas become projects. Members investigate unfamiliar problems, research existing solutions, define requirements, evaluate trade-offs, establish scope, build prototypes, test assumptions, document decisions, and communicate across disciplines.

Few products demonstrate the importance of this process more clearly than the smartphone. Its significance comes not simply from replacing the telephone, but from integrating computing, communications, embedded systems, software, industrial design, manufacturing, supply-chain logistics, product management, and business strategy at global scale. SIDEKICK turns that integration challenge into an educational platform: students can specialize in one subsystem while learning how their decisions affect the complete product.

The projects will change. The technologies will change. What remains constant is the framework through which students learn to transform ideas into reality. Ultimately, the true product of DIGITAL is not the prototype; it is the people who leave the organization prepared to help define what comes next.

## Project definition

The project aims to engineer a working, custom-built mobile-device prototype whose central processing and hardware-control functions are implemented with field-programmable logic. Inspired by modern mobile architecture and open-source hardware, the team uses tools including KiCad, SolidWorks, ANSYS, AMD Vivado, and OrCAD to expose parts of the system that are normally hidden inside closed silicon and proprietary product stacks.

The intended phone should be comfortable to hold, intuitive to navigate, responsive under real use, and efficient enough for sustained daily operation. Success is therefore broader than a booting circuit board: the project pairs user evaluation of ergonomics, navigation, and responsiveness with engineering measurements such as clock speed, bus bandwidth, screen-on time, battery discharge, component efficiency, data integrity, latency, and thermal behavior.

As an educational platform, the phone gives students a way to follow a complete system from physical circuits and programmable logic through hardware interfaces, drivers, the operating system, and the user experience. The objective is not only a device, but a reusable foundation for learning, experimentation, repairability, and later product iterations.

## Planned operational architecture

The system concept separates the FPGA motherboard from modular peripheral hardware. Custom logic moves device data through controller and buffering stages into an AXI-based system fabric, where software drivers expose it to the operating system and user interface.

```mermaid
flowchart LR
    A[Peripheral daughterboard<br/>sensors and actuators] --> B[Custom SPI and GPIO logic]
    B --> C[Hardware FIFO buffers]
    C --> D[AXI interconnect and<br/>memory-mapped registers]
    E[FPGA processing core<br/>and programmable logic] --> B
    E --> D
    D --> F[OS kernel and drivers]
    F --> G[Touch UI, telemetry,<br/>audio and haptic feedback]
```

Representative system flows include:

- **Boot and biometric unlock:** power-rail bring-up, FPGA bitstream loading, kernel and driver initialization, fingerprint transfer, authentication, haptic confirmation, and UI unlock.
- **Continuous sensor telemetry:** IMU, temperature, ambient-light, and microphone sampling; serial-to-parallel conversion; cross-clock FIFO buffering; AXI transfer; and UI updates.

The current systems plan treats a peripheral-to-memory latency below 15 ms, lossless sensor-packet handling at the target sampling load, and passive heat routing away from user touchpoints as design requirements. These are project targets documented in the planning workspace, not certifications of the archived hardware.

## Development approach

The project follows a systems-engineering cycle:

1. define the product, user experience, and measurable requirements;
2. decompose the phone into coordinated electrical, computing, software, mechanical, and thermal workstreams;
3. select components and tools, establish interfaces, and procure hardware;
4. design and prototype subsystems independently;
5. integrate through defined buses, connectors, drivers, and mechanical boundaries;
6. test electrical, performance, power, thermal, usability, and integration risks; and
7. evaluate readiness, document results, and carry lessons into the next iteration.

The public [TheSmartphoneProject workspace](https://successful-twill-84f.notion.site/TheSmartphoneProject-3e3169473d7780c18205ee25701566bf) contains the living planning record, including the product definition, requirements, work breakdown, use-case material, sequence diagrams, activity diagrams, team plans, and subsystem task tracking. Some linked workspace records may have separate access controls.

## System overview

| Subsystem | Scope | Contents |
| --- | --- | --- |
| [FPGA main board and peripheral board](subsystems/fpga-mainboard/) | Central Zynq/FPGA architecture, power, RF/transceiver, USB, connectors, display peripheral board | KiCad source, fabrication outputs, 3D renders, manufacturing notes |
| [Haptics](subsystems/haptics/) | Tactile-feedback motor-driver board | KiCad project archive |
| [Fingerprint sensor](subsystems/fingerprint-sensor/) | Fingerprint-sensor interface board | KiCad project archive |
| [Flashlight](subsystems/flashlight/) | LM3644-based flashlight/LED driver | KiCad revisions and symbol/footprint library |
| [Mechanical and thermal](subsystems/mechanical-thermal/) | Phone enclosure, frame, assembly, and thermal/mechanical exploration | STEP, STL, SolidWorks, PDF, and archived CAD models |
| [Ambient-light sensor](subsystems/ambient-light-sensor/) | VCNL4030X01-based sensing board and additional light-sensor iterations | KiCad project archives and STEP model |
| [IMU](subsystems/imu/) | ICM-20948 inertial-sensing board and supporting power/level shifting | Seven chronological KiCad project archives |
| [Real-time clock](subsystems/real-time-clock/) | RV-3028-C8-based RTC board | KiCad source, component library, renders, schematics, and prototype outputs |
| [STM32 controller](subsystems/stm32-controller/) | STM32G431-based control and support electronics | KiCad design, component models/libraries, and STM32CubeIDE firmware project |
| [Heat sensor](subsystems/heat-sensor/) | Temperature/heat-sensing circuit exploration | KiCad schematic project archive |

## Project documentation

The [`documentation/`](documentation/) directory preserves the project record alongside the subsystem engineering files. It includes Hatchery proposals and phase updates, DIGITAL curriculum and mini-project decks, the project budget and bill-of-materials workbook, and organizational records. These originals are grouped by purpose and accompanied by checksums and provenance notes.

## Repository organization

Each subsystem has:

- a short README explaining what is present;
- a `PROVENANCE.md` with the original repository, branch, imported commit, and contributors; and
- a `source/` directory containing an unchanged snapshot of the files tracked at that commit.

The snapshots intentionally retain original filenames, archive structure, and intermediate revisions. This avoids silently selecting a “final” design where the source repository did not designate one.

## Opening the design files

Most electronics work is stored as KiCad projects, either directly or inside ZIP archives. Mechanical work includes STEP, STL, SolidWorks (`.SLDPRT`), and PDF files. Some archives contain KiCad automatic backups in addition to the latest project files.

Treat all outputs as historical engineering artifacts. Review schematics, footprints, stackups, component availability, electrical rules, and manufacturing requirements before fabrication.

## Project history and attribution

The initial source material was maintained across seven repositories under individual contributors and the DIGITAL organization. Additional project archives supplied directly by the project maintainer are recorded separately, without inferring authorship or repository history. See [CONTRIBUTORS.md](CONTRIBUTORS.md) for the contributor index and each subsystem's `PROVENANCE.md` for source details.

No authorship is transferred by this consolidation. Original Git history remains available through the linked source repositories and the immutable commit identifiers recorded here.

## Licensing

Licensing is **per subsystem**, not repository-wide. The FPGA/main-board snapshot includes its original GNU GPL v3 license. No explicit license file was present in the other source repositories at the recorded commits. See [LICENSES.md](LICENSES.md) before reusing or redistributing any material.

## About DIGITAL @ Cal Poly Pomona

DIGITAL is intentionally broader than one device, competition, technology, or discipline. Each initiative follows a shared project lifecycle: assess purpose and feasibility; define scope, requirements, risks, roles, and resources; execute and integrate through clear interfaces; document decisions continuously; and conclude with reflection, knowledge transfer, and a deliberate decision about what follows.

Systems engineering is the organization's foundation. It connects the complete product architecture with the technical and operational teams needed to deliver it, while allowing members to develop depth in hardware, software, mechanical design, thermal engineering, product design, business, or operations. SIDEKICK is DIGITAL's flagship reference implementation—not its fixed endpoint—and provides a concrete system through which this model can be tested and improved.

DIGITAL measures success beyond commercial readiness. Clear design decisions, robust interfaces, useful documentation, transferable skills, and member growth are outcomes in their own right. Read the archived [DIGITAL project proposal for Maximizing Engineering Potential](documentation/organization/DIGITAL_CPP_Project_Proposal_MEP.docx) for the organization's mission, values, project lifecycle, and structure.
