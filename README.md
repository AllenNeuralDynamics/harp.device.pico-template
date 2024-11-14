# harp.device.pico-template

An RP2040-based Harp hardware/firmware project template.

## Features
* predefined *.gitignore* file to remove extraneous KiCAD (hardware) files.
### Hardware
* Schematic template for a generic Harp Device including:
  * ground-isolated Full Speed USB communication
  * 3.5mm audio jack for Harp-protocol time synchronization
* Basic PCB Layout with size hints for various existing enclosures
  * DC Barrel Jack (2.1 x 5.5mm, positive center)
  * USBC
  * 3.5mm audio jack for Harp synchronization signal
  * Ground lug
### Firmware
* basic "hello-world" project with corresponding file structure
* populated CMakeLists.txt for compliation
* placeholder USB descriptors for Manufacturer and Description fields (in the CMakeLists.txt)
* compilation [instructions](./firmware/README.md)
* harp protocol core library included as a submodule [harp.core.rp2040](https://github.com/AllenNeuralDynamics/harp.core.rp2040)

# Using this template
## Hardware
* Remove all unused hardware folder starter projects.
* 🔧 Design your hardware.
## Firmware
* Update the *Manufacturer* and *Description* USB descriptors in the CMakeLists.txt
* 📝 Write your firmware.

# Github Release Conventions
Releases specify any vetted changes to the hardware, firmware, software interface, or Harp protocol.

Each release specifies:
* semantic version of the entire project
* SIPE part number (or part numbers if multiple are compatible)

Each hardware release includes:
* STEP file of the PCB named with the SIPE part number
* Gerber files (with logos removed) of the PCBA
* Position files for component placement
* Bill-of-Materials for the PCBA

Each hardware release specifies:
* compatible SIPE part number(s)

> [!NOTE]
> SIPE part numbers only encode semantic version major changes, so multiple minor/patch hardware releases may point to the same SIPE part number. 

Each firmware release specifies:
* compatible hardware:
  * SIPE part number(s)

Each firmware release includes:
* compiled binary file (**\*.uf2**) of the firmware.

## Release Title
The release title is specified as follows:

`pcb{major}.{minor}-fw{major}.{minor}-harp{protocol-major}.{protocol-minor}`

> [!NOTE]
> The `major` and `minor` fields are the *semantic version* project fields. These will likely always be the same following adoption of the [SIPE PCBA part numbering standard](https://alleninstitute.sharepoint.com/:w:/s/Instrumentation/EYsRN8q4jHJDmG5DNf-gaM0Bq418YMXollFxtB9d_NZ6pg?e=joLAvU) (~Nov 2024).

The above field specification enables automation utilities to find the latest firmware version and automatically update compatible hardware.

Since releases can include changes to some, but not other fields, unchanged fields are omitted.
| Change                | Release Title                                             | Note                                                                                                                       |
|-----------------------|-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| hardware-only         | `pcb{major}.{minor}`                                      |                                                                                                                            |
| firmware-only         | `fw{major}.{minor}`                                       |                                                                                                                            |
| hardware and firmware | `pcb{major}.{minor}-fw{major}.{minor}`                    |                                                                                                                            |
| Harp protocol only    | `fw{major}.{minor}-harp{protocol-major}.{protocol-minor}` | This is inherently a firmware change also. Must bump project patch number, but may  or may not bump major or minor numbers |
