# ESP32-PICO-D4 / ESP-IDF / VS Code template app

This is a template application to be used with:

+ [Espressif ESP32-PICO-D4 chip](https://www.espressif.com/en/producttype/esp32-pico-d4)
+ [Espressif IoT Development Framework](https://github.com/espressif/esp-idf)
+ [Visual Studio Code IDE](https://code.visualstudio.com)

## Table of contents
- [ESP32-PICO-D4 / ESP-IDF / VS Code template app](#esp32-pico-d4--esp-idf--vs-code-template-app)
  - [Table of contents](#table-of-contents)
  - [Getting Started](#getting-started)
    - [Software Prerequisites](#software-prerequisites)
    - [Hardware Prerequisites](#hardware-prerequisites)
      - [ESP32-PICO-KIT](#esp32-pico-kit)
  - [Tools installation](#tools-installation)
    - [Install Espressif toolchain](#install-espressif-toolchain)
    - [Install Visual Studio Code](#install-visual-studio-code)
    - [Install required VS Code addins](#install-required-vs-code-addins)
  - [Project setup and build](#project-setup-and-build)
    - [Clone this GitHub repository](#clone-this-github-repository)
    - [Open this project in VS Code](#open-this-project-in-vs-code)
    - [Adjust project directory settings to your tool installation paths](#adjust-project-directory-settings-to-your-tool-installation-paths)
    - [Modify ESP-IDF project configuration](#modify-esp-idf-project-configuration)
    - [Build the application](#build-the-application)
    - [Deploy the application on target](#deploy-the-application-on-target)
  - [License](#license)

## Getting Started

The following instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Software Prerequisites

You will need to install these packages on your PC:

|Tool|Version|Link|Platforms|Comment|
|-|-|-|-|-|
|ESP toolchain|2.2|[Installation instructions](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/#installation-step-by-step)|Windows/Linux/Mac OS||
|ESP-IDF|3.3.1|[ESP-IDF files](https://github.com/espressif/esp-idf/releases/tag/v3.3.1)|Platform independent|This version is highly recommended, download via git clone|
|VS Code|14.1|https://code.visualstudio.com/|Windows/Linux/Mac OS||

You may also check Espressifs [Get Started Guide](https://docs.espressif.com/projects/esp-idf/en/v3.3.1/get-started/index.html) for further reference (The link references ESP-IDF version 3.3.1 which is used for this project).

> Remark: This project is using the CMAKE build system. GNU make is not supported since the Espressif toolchain will not support this make tool in the future.

### Hardware Prerequisites

This project is based on an Espressif ESP-PICO-D4 chip. Supported hardware includes:

1. Espressif board ESP32-PICO-KIT

#### ESP32-PICO-KIT

The ESP32-PICO-Kit is an evaluation board featuring an ESP-PICO-D4 chip including WIFI/BT frontend, a voltage regulator and a USB interface for flashing/monitoring. It features a Micro USB port for connecting to a host PC.

Detailed information about the ESP32-PICO-KIT hardware can be found here: Official [ESP32-PICO-KIT V4 / V4.1 Getting Started Guide](https://docs.espressif.com/projects/esp-idf/en/v3.3.1/get-started/get-started-pico-kit.html) from Espressif.

> REMARK: This project is tested with ESP PICO KIT HW V4.0 but should also work with V4.1.

## Tools installation

Perform the following steps to install all tools and perform needed adaption for your environment:
1. Install Espressif toolchain
2. Install Visual Studio Code
3. Install recommended VS Code addins

### Install Espressif toolchain

The easiest way to install ESP-IDF’s prerequisites is to download the ESP-IDF Tools installer from this URL: [ESP-IDF tools setup V2.2](https://dl.espressif.com/dl/esp-idf-tools-setup-2.2.exe).

The installer includes the cross-compilers, OpenOCD, cmake and Ninja build tool. The installer can also download and run installers for Python 3.7 and Git For Windows if they are not already installed on the computer. The installer also offers to download one of the ESP-IDF release versions.

> Remark: This project was tested with ESP-IDF Release 3.3.1 so it is highly recommended to download this version.

You can also download the required tools and components separately and perform a manual configuration of paths etc. 

Detailed information about this step can be found here: [ESP IDF get started](https://docs.espressif.com/projects/esp-idf/en/v3.3.1/get-started/index.html).

### Install Visual Studio Code

Download and install the free VS Code IDE from here: [VS Code homepage](https://code.visualstudio.com/).

### Install required VS Code addins

1. Open Extensions view in VS Code (in sidebar or by pressing CTRL+SHIFT+X)
2. Search for _ms-vscode.cpptools_
3. Press "install" button
4. Wait for installation to complete

## Project setup and build

After installation of all tools, you can now proceed to setting up the project and building/deploying oit on the ESP32-PICO-D4 target by following these steps:

1. Clone this GitHub repository
2. Open this project in VS Code
3. Adjust project directory settings to your tool installation paths
4. Modify ESP-IDF project configuration
5. Build the application
6. Deploy the application on target

### Clone this GitHub repository

To clone this repository, open a command prompt and type:

```
git clone https://github.com/slot-tronic/esp32-pico-d4-idf-vscode
```

The repository will then be cloned into your local git repositories folder.

Detailed information about this step can be found here [Cloning a repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository).

### Open this project in VS Code

1. Open the VS Code IDE
2. Go to Menu "File" -> "Open folder..."
3. Select the root folder of this repository and confirm.

### Adjust project directory settings to your tool installation paths

1. Open the file [c_cpp_properties.json](.vscode/c_cpp_properties.json) in this repository
2. Go to the section "env"
3. Change the variable "IDF_PATH" to your ESP-IDF installation path
4. Change the variable ""COMPILER_PATH" to your gcc compiler path

```json
...

"env": {
        "IDF_PATH": "<your_ESP-IDF_path_goes_here>",
        "COMPILER_PATH": "<your_gcc-compiler_path_goes_here>"
    },

...
```

### Modify ESP-IDF project configuration

1. Press CTRL+SHIFT+B to open the build target list
2. Select build target **"menuconfig"**
3. Change your settings as preferred
4. Save settings and exit the configurator
5. Rebuild and deploy your application as described in the following sections

**Remark:** This template project contains a [sdkconfig.defaults](sdkconfig.defaults) file. This file overrides some project specific settings in order to allow easy later updates of the ESP-IDF framework. In case you want to change settings listed in sdkconfig.defaults, you have to remove them from this file in order to become effective.

### Build the application

1. Press CTRL+SHIFT+B to open the build target list
2. Select the build target "**build**"
3. Wait for flash procedure to complete

### Deploy the application on target

Perform the following steps to deploy this project on an Espressif ESP-PICO-KIT board:

1. Connect the Espressif ESP32-PICO-KIT board to your PC via USB
2. Press ALT+CTRL+B to open the build target list
3. Select the build target "**flash**"
4. Wait for flash procedure to complete
5. Connect to the ESP32-PICO-KIT console with a monitor program and check output

Other targets with a ESP32-PICO-D4 should work in a similar way but were not tested.

## License

*Code in this repository is in the Public Domain (or CC0 licensed, at your option.)
Unless required by applicable law or agreed to in writing, this
software is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
CONDITIONS OF ANY KIND, either express or implied.*
