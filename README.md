An RP2040-based Harp Hardware/Firmware project template.

## Features
* Schematic template for an isolated full speed USB Harp Device with an audio jack
* basic PCB Layout with size hints for various existing enclosures
  * DC Barrel Jack (2.1 x 5.5mm, positive center)
  * USBC
  * 3.5mm audio jack for Harp synchronization signal
  * Ground lug
* firmware template using the [harp.core.rp2040](https://github.com/AllenNeuralDynamics/harp.core.rp2040) library as a submodule

## Wiring Diagram

*TODO: Wiring Diagram Here*

# Release Conventions
Releases specify any vetted changes to the hardware, firmware, software interface, or Harp protocol.

Each release specifies:
* semantic version of the entire project

Each hardware release includes:

Each hardware release specifies:

Each firmware release specifies:

Each firmware release includes:

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
