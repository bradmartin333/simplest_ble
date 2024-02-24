# How to use [SimpleBLE](https://github.com/OpenBluetoothToolbox/SimpleBLE) on Windows

Following these steps, you will be able to build a C++ app on Windows that runs the [notify example from the SimpleBLE repo](https://github.com/OpenBluetoothToolbox/SimpleBLE/tree/main/examples/simpleble/cpp/notify).

### Target Audience

- You have installed Visual Studio before
- You enjoy VSCode extensions
- You want to use SimpleBLE right now

## Setup PC

Linux is much more forgiving than Windows when it comes to C++. For instance, if you have workplace firewall that won't allow for the full download of "Visual Studio Desktop development with C++", then these instructions won't work for you. Also, admin permissions. Things like that...

### CMake

1. Open powershell and run `winget install -e --id Kitware.CMake` and follow the prompts

### Visual Studio 2022

1. Download the [Visual Studio 2022 Installer](https://visualstudio.microsoft.com/downloads/)
1. Once in the "Workloads" section of the installer, select "Desktop development with C++" and install the defaults

### Visual Studio Code

While it is possible to do this in Visual Studio 2022, it is much simpler in VSCode.

1. Download the [Visual Studio Code Installer](https://code.visualstudio.com/download)
1. Once installed, install the suggested C/C++ extensions (3 total) and CMake extensions (2 total)
1. *TODO* determine if necessary to -> Ctrl+Shift+P -> `CMake: Configure` in VSCode

## Create Project

1. Create a project directory and open it in VSCode
1. Copy the following files from this repo to the root of the project directory:
    - CMakeLists.txt (Modified from [this](https://github.com/OpenBluetoothToolbox/SimpleBLE/blob/main/examples/simpleble/cpp/notify/CMakeLists.txt))
    - main.cpp (Modified from [this](https://github.com/OpenBluetoothToolbox/SimpleBLE/blob/main/examples/simpleble/cpp/notify/notify.cpp))
1. Create the following directories at the root of the project directory:
    - common
    - lib
1. Into `common`, copy the 2 files from this repo's `common` directory (Which were copied from [here](https://github.com/OpenBluetoothToolbox/SimpleBLE/tree/main/examples/simpleble/cpp/common))

## Clone SimpleBLE

Not all files/dirs are needed here, but it can be cleaned up later. You will want to delete the `.git` directory inside the cloned repo, though.

1. Open a shell in VSCode (Ctrl+J) and `cd lib`
1. `git clone https://github.com/OpenBluetoothToolbox/SimpleBLE.git`

## Build and Run

1. Open a shell at the project root
1. `mkdir build`
1. `cd build`
1. `cmake ..`
1. `msbuild .\test_app.vcxproj`
1. `.\Debug\test_app.exe`
1. Tinker and make the app you desire!
