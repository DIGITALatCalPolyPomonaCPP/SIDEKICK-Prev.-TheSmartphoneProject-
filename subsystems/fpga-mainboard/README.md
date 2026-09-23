# FPGA main board and peripheral board

This subsystem contains the central FPGA-based phone hardware from the original SIDEKICK repository.

- `source/hardware/` contains the Zynq/FPGA main-board KiCad design, including power management, processing-system and programmable-logic configuration, DDR, RF/transceiver, USB, and board-to-board connector sheets.
- `source/hardware/gerber/` contains fabrication outputs and manufacturing requirements.
- `source/Peripheral-Board-master/` contains the display/peripheral-board KiCad design, component models, libraries, and chronological backups.
- `source/repo_desc/` contains board renders, copper-layer images, and a schematic PDF.

The source snapshot retains its original [GNU GPL v3 license](source/LICENSE). See [PROVENANCE.md](PROVENANCE.md) for the exact origin.
