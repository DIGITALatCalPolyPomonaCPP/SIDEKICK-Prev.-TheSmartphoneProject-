# SIDEKICK — The Smartphone Project

SIDEKICK was a student-led effort at **DIGITAL @ Cal Poly Pomona** to explore a smartphone as a complete, cross-disciplinary product rather than a single circuit board. The project centered on an FPGA-based main board and grew into parallel electrical, sensing, haptics, mechanical, and thermal workstreams owned by different student contributors.

This repository consolidates the project's previously distributed engineering record. It is an archival snapshot of the original repositories—not a claim that every subsystem reached production readiness or that the files form a buildable final phone.

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

The [`documentation/`](documentation/) directory preserves project-level proposals and narrative records alongside the subsystem engineering files. It currently includes the 13-page Learn Through Discovery Projects Hatchery proposal, *Smartphone Education: Building a Modular Student-Designed Smartphone*, covering the project's educational rationale, technical phases, team structure, goals, and milestone budget.

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

## About DIGITAL

DIGITAL is a cross-disciplinary student product-development organization at Cal Poly Pomona. SIDEKICK reflects the core challenge of integrated product work: many specialized teams contributing to one coherent system.
