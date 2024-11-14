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
## Repository
* If the project has a corresponding Allen Institute SIPE project number, prepend the repository description with: `{SIPE Project Number}:`.
* add the tag `Harp`

## Hardware
* Remove all unused hardware folder starter projects.
* 🔧 Design your hardware.
* In the PCBA silkscreen, add:
  * SIPE part number with full hardware semantic version appended in the format: `{SIPE Project Number}-E-{hw major}-{hw minor}-{hw patch}`. Version number fields range from 1-999 and include leading zeros.
  * [QR code](https://www.the-qrcode-generator.com/) linking to the Github repository.

## Firmware
* Update the *Manufacturer* and *Description* USB descriptors in the CMakeLists.txt
* 📝 Write your firmware.

# Github Release Conventions
Releases specify any vetted changes to the hardware or firmware.

Each release specifies:
* semantic versions of changed elements: hardware or firmware.
* SIPE part number (or part numbers if multiple are compatible)

Each hardware release includes:
* STEP file of the PCB named with the SIPE part number
* Gerber files (with logos removed) of the PCBA
* Position files for component placement
* Bill-of-Materials for the PCBA

Each hardware release specifies:
* compatible SIPE part number(s)

> [!NOTE]
> SIPE part numbers only encode hardware semantic version major number, so multiple minor/patch hardware releases may point to the same SIPE part number.

Each firmware release specifies:
* firmware semantic version
* compatible hardware (SIPE part number or part number range).

Each firmware release includes:
* compiled binary file (**\*.uf2**) of the firmware.

## Release Title
The release title is specified as follows:

`hw{hw major}.{hw minor}.{hw patch}-fw{fw major}.{fw minor}.{fw patch}`

> [!NOTE]
> After Oct 2024, hardware major fields on all future releases will be equivalent to the major version number of the SIPE part number. See the [SIPE PCBA part numbering standard](https://alleninstitute.sharepoint.com/:w:/s/Instrumentation/EYsRN8q4jHJDmG5DNf-gaM0Bq418YMXollFxtB9d_NZ6pg?e=joLAvU) for more details.

The above field spec enables automation utilities to find the latest firmware version and automatically update compatible hardware. Since releases can include changes to some, but not other fields, unchanged fields are omitted. (i.e: firmware-only changes would be titled `fw{fw major}.{fw minor}.{fw patch}`.)
