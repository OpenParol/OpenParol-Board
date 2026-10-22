# OpenParol Control Board

OpenParol-Board is an open-source controller for a 6-DOF robotic arm. It features six TMC5160T Pro drivers and a section containing two galvanically isolated CAN-FD buses, which can be used for communication with external (or future) modules and controllers. It also includes an isolated I/O section for connecting limit switches (both mechanical and NPN inductive types), as well as two galvanically isolated outputs and inputs (one of which supports an MCU interrupt).

> [!IMPORTANT]
> This is merely a hobby project; under no circumstances is it a professional project intended for industrial use!

> [!IMPORTANT]
> The current design is a development version and has not yet been tested. It is therefore best to wait for the official release.

---
<br>

<span style="font-size: 1.25em; font-weight: 600; letter-spacing: 0.7px;">🌟 Design compatible with and tested on the PAROL6 arm by [@PCrnjak](https://github.com/PCrnjak). Thank you for such a wonderful project!</span>

## Overview

The board is built around an **STM32G474VET6** microcontroller and is designed
to provide:

- six **TMC5160T** stepper-motor driver channels;
- isolated CAN interfaces using **ISO1042DWV** transceivers;
- galvanic isolation and isolated power rails for selected interfaces;
- USB-C 2.0 connectivity;
- an ARM JTAG/SWD debug connector;
- status indicators, test points, configuration jumpers, and pluggable
  motor/power connectors.

The exact electrical behavior, pin assignments, component values, and
connection details are defined by the KiCad source files and should be taken
from the schematic rather than inferred from this overview.

<span style="font-size: 1.25em; font-weight: 600; letter-spacing: 0.7px;">If you are interested in the software, check out the other repositories [here](https://github.com/orgs/OpenParol/repositories)</span>

## Requirements

- [Latest KiCad](https://www.kicad.org/) version or a compatible version that can open
  the project files;
- the repository cloned with its directory structure preserved, so that the
  project can resolve its custom libraries and 3D models.

## Development workflow

When modifying the design:

1. Make schematic changes first.
2. Annotate and update the PCB from the schematic.
3. Verify footprints, pin assignments, clearances, and isolation boundaries.
4. Review the 3D model placement and board constraints.
5. Run ERC and DRC.
6. Export manufacturing files only from a tagged or otherwise clearly
   identified revision.

Custom symbols and footprints are stored in `Board/libraries/`. Their library
paths are configured by `Board/sym-lib-table` and `Board/fp-lib-table`; avoid
moving these files without updating the corresponding KiCad configuration.

## Contributing

Contributions are more than welcome. Before submitting a change:

- keep schematic and PCB changes synchronized;
- include or update custom library data when a new footprint or symbol is
  required;
- preserve the existing project-relative library paths;
- run ERC and DRC and describe any intentional exceptions;
- explain the changes that have been made.

## License

Unless stated otherwise for a particular third-party asset, this project is
provided under the **GNU General Public License v3.0**. See [LICENSE](LICENSE)
for the complete license text.

Third-party component datasheets, manufacturer models, and other external
assets may be subject to their own terms. Verify their licensing and
redistribution conditions before using them outside this repository.
