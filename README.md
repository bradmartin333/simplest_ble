# How to use [SimpleBLE](https://github.com/OpenBluetoothToolbox/SimpleBLE) on ![windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)

Following these steps, you will be able to build a C++ app on Windows that runs the [notify example from the SimpleBLE repo](https://github.com/OpenBluetoothToolbox/SimpleBLE/tree/main/examples/simpleble/cpp/notify).

### Options

**Included**  
🟢 vcpkg (cleanest) - install vcpkg following [these instructions](https://vcpkg.io/en/getting-started)  
🔵 git - you will need a working [installation of git](https://git-scm.com/download/win)  

**Not-included**  
🔴 [SimpleBLE release package](https://github.com/OpenBluetoothToolbox/SimpleBLE/releases) - never get it to work on Windows, so if someone knows how to, please share!  
🟡 installing to Program Files - it is easy enough to [install following the instructions](https://simpleble.readthedocs.io/en/latest/simpleble/usage.html#building-and-installing-simpleble-source), but was never able to get CMake to work with this method (share if you know how!)  

In the current state of this repo, it is configured for the vcpkg option. So, if you can already build C++ apps with CMake on Windows and have vcpkg installed, you can clone and skip to the [end](#build-and-run). If not, these instructions will set you up for that.

### Target Audience 🫵

- You have installed Visual Studio before
- You enjoy VSCode extensions
- You want to use SimpleBLE right now

## Setup PC

Linux is much more forgiving than Windows when it comes to C++. For instance, if you have workplace firewall that won't allow for the full download of "Visual Studio Desktop development with C++", then these instructions won't work for you. Also, admin permissions, environment variables and library paths.

### ![CMake](https://img.shields.io/badge/CMake-%23008FBA.svg?style=for-the-badge&logo=cmake&logoColor=white)

1. Open powershell and run `winget install -e --id Kitware.CMake` and follow the prompts

### ![Visual Studio](https://img.shields.io/badge/Visual%20Studio-5C2D91.svg?style=for-the-badge&logo=visual-studio&logoColor=white)

1. Download the [Visual Studio 2022 Installer](https://visualstudio.microsoft.com/downloads/)
1. Once in the "Workloads" section of the installer, select "Desktop development with C++" and install the defaults
1. *TODO* determine if necessary to add `C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\` to Environment Variables PATH

### ![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)

While it is possible to do this in Visual Studio 2022, it is much simpler in VSCode.

1. Download the [Visual Studio Code Installer](https://code.visualstudio.com/download)
1. Once installed, install the suggested C/C++ extensions (3 total) and CMake extensions (2 total)
1. *TODO* determine if necessary to -> Ctrl+Shift+P -> `CMake: Configure` in VSCode

## Create Project

1. Create a project directory and open it in VSCode
1. Copy the following files from this repo to the root of the project directory:
    - CMakeLists.txt - choose the .txt from this repo for the option (vcpkg or git) that you chose and remove the suffix (Modified from [this](https://github.com/OpenBluetoothToolbox/SimpleBLE/blob/main/examples/simpleble/cpp/notify/CMakeLists.txt))
    - main.cpp (Modified from [this](https://github.com/OpenBluetoothToolbox/SimpleBLE/blob/main/examples/simpleble/cpp/notify/notify.cpp))
1. Create the following directories at the root of the project directory:
    - common
    - lib (Only for git option)
1. Into `common`, copy the 2 files from this repo's `common` directory (Which were copied from [here](https://github.com/OpenBluetoothToolbox/SimpleBLE/tree/main/examples/simpleble/cpp/common))

## 🟢 vcpkg option: Install SimpleBLE

1. Open a shell in your vcpkg directory (Where you cloned it)
1. `./vcpkg install simpleble`

## 🔵 git option: Clone SimpleBLE

Not all files/dirs are needed here, but it can be cleaned up later. You will want to delete the `.git` directory inside the cloned repo, though.

1. Open a shell at the project root in VSCode (Ctrl+J) and `cd lib`
1. `git clone https://github.com/OpenBluetoothToolbox/SimpleBLE.git`

## Build and Run

1. Open a shell at the project root
1. `mkdir build`
1. `cd build`
1. `cmake ..`
1. `msbuild .\test_app.vcxproj /property:Configuration=Release`
1. `.\Release\test_app.exe`
1. Tinker and make the app you desire!

**Notes**  

- Build with `cmake .. -DCMAKE_TOOLCHAIN_FILE=F:/vcpkg/scripts/buildsystems/vcpkg.cmake\` to include necessary libs for a Debug build
