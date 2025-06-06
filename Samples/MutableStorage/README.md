---
page_type: sample
languages:
- c
products:
- azure
- azure-sphere
name: Azure Sphere – Mutable storage
urlFragment: MutableStorage
extendedZipContent:
- path: HardwareDefinitions
  target: HardwareDefinitions
- path: .clang-format
  target: .clang-format
- path: BUILD_INSTRUCTIONS.md
  target: BUILD_INSTRUCTIONS.md
- path: Samples/SECURITY.md
  target: SECURITY.md
- path: Samples/troubleshooting.md
  target: troubleshooting.md
description: "Demonstrates how to manage storage on an Azure Sphere device."
---

# Sample: Mutable storage

This sample application illustrates how to manage [storage](https://learn.microsoft.com/azure-sphere/app-development/storage) on an Azure Sphere device.

When you press button A, the sample opens a persistent data file on the device, increments the value in it, and closes the file. When you press button B, the sample deletes the file. The file persists if the application exits or is updated. However, if you delete the application by using the `az sphere device sideload delete` command, the file is deleted as well.

**Note:** This sample writes data to and erases data from the flash. Be aware that repeatedly updating the flash eventually wears it out and makes it invalid.

The sample uses the following Azure Sphere libraries.

| Library   | Purpose  |
|-----------|----------|
| [eventloop](https://learn.microsoft.com/azure-sphere/reference/applibs-reference/applibs-eventloop/eventloop-overview) | Invokes handlers for timer events. |
| [gpio](https://learn.microsoft.com/azure-sphere/reference/applibs-reference/applibs-gpio/gpio-overview) | Enables use of buttons and LEDs. |
| [log](https://learn.microsoft.com/azure-sphere/reference/applibs-reference/applibs-log/log-overview) | Displays messages in the **Device Output** window during debugging. |
| [storage](https://learn.microsoft.com/azure-sphere/reference/applibs-reference/applibs-storage/storage-overview) | Manages persistent user data. |

## Contents

| File/folder           | Description |
|-----------------------|-------------|
| `app_manifest.json`   | Application manifest file, which describes the resources. |
| `CMakeLists.txt`      | CMake configuration file, which Contains the project information and is required for all builds. |
| `CMakePresets.json`   | CMake presets file, which contains the information to configure the CMake project. |
| `launch.vs.json`      | JSON file that tells Visual Studio how to deploy and debug the application. |
| `LICENSE.txt`         | The license for this sample application. |
| `main.c`              | Main C source code file. |
| `README.md`           | This README file. |
| `.vscode`             | Folder containing the JSON files that configure Visual Studio Code for deploying and debugging the application. |
| `HardwareDefinitions` | Folder containing the hardware definition files for various Azure Sphere boards. |

## Prerequisites

The sample requires the following hardware:

- An [Azure Sphere development board](https://aka.ms/azurespheredevkits) that supports the [Sample Appliance](../../HardwareDefinitions) hardware requirements.

   **Note:** By default, the sample targets the [Reference Development Board](https://learn.microsoft.com/azure-sphere/hardware/mt3620-reference-board-design) design, which is implemented by the Seeed Studios MT3620 Development Board. To build the sample for different Azure Sphere hardware, change the value of the TARGET_HARDWARE variable in the `CMakeLists.txt` file. For detailed instructions, see the [Hardware Definitions README](../../HardwareDefinitions/README.md) file.

## Setup

1. Ensure that your Azure Sphere device is connected to your computer, and your computer is connected to the internet.
1. Ensure that you have Azure Sphere SDK version 24.03 or above. At the command prompt, run `az sphere show-sdk-version` to check. Upgrade the Azure Sphere SDK for [Windows](https://learn.microsoft.com/azure-sphere/install/install-sdk) or [Linux](https://learn.microsoft.com/azure-sphere/install/install-sdk-linux) as needed.
1. Ensure that the [Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli) is installed. At a minimum, the Azure CLI version must be 2.45.0 or later.
1. Install the [Azure Sphere extension](https://learn.microsoft.com/azure-sphere/reference/cli/overview?view=azure-sphere-integrated).
1. Clone the [Azure Sphere samples](https://github.com/Azure/azure-sphere-samples) repository and find the *MutableStorage* sample in the *MutableStorage* folder or download the zip file from the [Microsoft samples browser](https://learn.microsoft.com/samples/azure/azure-sphere-samples/mutablestorage/).
1. Connect your Azure Sphere device to your computer by USB.
1. Enable application development, if you have not already done so, by entering the `az sphere device enable-development` command in the [command prompt](https://learn.microsoft.com/azure-sphere/reference/cli/overview?view=azure-sphere-integrated).

## Build and run the sample

To build and run this sample, follow the instructions in [Build a sample application](../../BUILD_INSTRUCTIONS.md).

### Test the sample

When the application starts:

1. Press button A to open and write to a file.
1. Press the button repeatedly to increment the value in the file.
1. Press button B to delete the file.

## Further reference
You may also be interested in the following related projects on the [Azure Sphere Gallery](https://github.com/Azure/azure-sphere-gallery):

- [MutableStorageKVP](https://github.com/Azure/azure-sphere-gallery/blob/main/MutableStorageKVP) | Provides a set of functions that expose Key/Value pair functions (write, read, delete) over Azure Sphere Mutable Storage.
- [LittleFs_RemoteDisk](https://github.com/Azure/azure-sphere-gallery/tree/main/LittleFs_RemoteDisk) | A project that shows how to add LittleFs to an Azure Sphere project, uses Curl to talk to remote storage.
- [LittleFs_SDCard](https://github.com/Azure/azure-sphere-gallery/tree/main/LittleFs_SDCard) | A project that combines LittleFs with SD Card support, and PC utilities to read the SD Card and extract files/folders.

## Next steps

- For an overview of Azure Sphere, see [What is Azure Sphere](https://learn.microsoft.com/azure-sphere/product-overview/what-is-azure-sphere).
- To learn more about Azure Sphere application development, see [Overview of Azure Sphere applications](https://learn.microsoft.com/azure-sphere/app-development/applications-overview).
- To learn more about memory usage by high-level applications, see [Understand memory use](https://learn.microsoft.com/azure-sphere/app-development/application-memory-usage).
