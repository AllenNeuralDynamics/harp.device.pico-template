## Setting up the Build Environment


## Pre-requisites
Install CMake.

### Install Submodules
This project uses the [Harp Core RP2040](https://github.com/AllenNeuralDynamics/harp.core.rp2040) library as a submodule.
Install it with:
````
git submodule update --init
````

### Install Pico SDK
This project uses the [Pico SDK](https://github.com/raspberrypi/pico-sdk/tree/master).
The SDK needs to be downloaded and installed to a known folder on your PC.
Note that the PICO SDK also contains submodules (including TinyUSB), so you must ensure that they are also fetched with:
````
git clone git clone git@github.com:raspberrypi/pico-sdk.git
git submodule update --init --recursive
````

### Point to Pico SDK
Optional: define the `PICO_SDK_PATH` environment variable to point to the location where the pico-sdk was downloaded. i.e:
````
PICO_SDK_PATH=/home/username/projects/pico-sdk
````
On Linux, you can define it in your `.bashrc` file.
On Windows, you can define it via System Properties ([tutorial](https://www.computerhope.com/issues/ch000549.htm)).

Confirm that the environment variable is applied to your system by opening a terminal (Powershell on Windows) and
entering (with the `$` sign)
```bash
$PICO_SDK_PATH
```
to confirm that the path was defined correctly.
(Windows may require a restart for the environment variable to take effect.)

## Compiling the Firmware

### Without an IDE
From within this folder, create a new folder called *build*, enter it, and invoke cmake with:
````
mkdir build
cd build
cmake ..
````
If you did not define the `PICO_SDK_PATH` as an environment variable, you must pass it in here like so:
````
mkdir build
cd build
cmake -DPICO_SDK_PATH=/path/to/pico-sdk ..
````
After this point, you can invoke the auto-generated Makefile with `make`

## Flashing the Firmware
Press-and-hold the Pico's BOOTSEL button and power it up (i.e: plug it into usb).
At this point you do one of the following:
* drag-and-drop the created **\*.uf2** file into the mass storage device that appears on your pc.
* flash with [picotool](https://github.com/raspberrypi/picotool)
