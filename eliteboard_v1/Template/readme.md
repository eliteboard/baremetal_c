# Eliteboard C-Project Template
This template contains all files required for setting up a new C project for the Eliteboard.<br>
Make sure to check the repository out with the `--recurse-submodules` option to also get periph_drivers.

## Prerequisites
See *Manual installation of the development environment* section [here](https://gitlab.nthfs.jku.at/eliteboard/vscode_c_examples). 

## Usage
1. Copy the contents of this folder to you new project's directory.
2. Rename `template.ioc` to `<project-name>.ioc`, according to your new project's name.
3. Open `<project-name>.ioc` in [STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html#get-software).
4. *If required*, adapt the project settings within STM32CubeMX.<br>
   By default, most peripherals are enabled and routed to pins, LwIP and FatFs are enabled and the clock tree is properly set-up.
5. In STM32CubeMX, click `Generate code`.<br>
   This will copy all required dependencies to you project folder and generate a Makefile and a `main.c`.[^1]
6. Open `.vscode\launch.json` and adapt `configurations.executable` and `configurations.<your-os>.BMPGDBSerialPort` according to the project name and your attached Eliteboard's BMP-COM-Port.
7. Open your new project's folder in VSCode.

## Notes
- In Windows it might be necessary to create a folder `build` within your project directory.
- To include own header and source files, as well as precompiled static libraries you have to add them to the Makefile manually. Add additional include paths to `configurations.includePath` as well in `.vscode\c_cpp_properties.json`.

[^1]: To change settings later, repeat steps 4 and 5. If this leads to compiler errors, make sure that `C_SOURCES` and `C_INCLUDES` sections in the Makefile do **not** end with a duplicated line separated by a *newline without backslash*.
