# Pico Coffee Machine

This project aims to add a PID controller (and other features) to an `Elektra Cappuccina` coffee machine
(and possibly any other single heater manual coffee machine) using a Raspberry Pi Pico.

The project is based on [ArduinoCoffeeMachine](https://github.com/ilcardella/ArduinoCoffeeMachine) which uses an Arduino Nano.
Both projects are based on [lib_coffee_machine](https://github.com/ilcardella/lib_coffee_machine) which is a C++ library providing an abstraction of a generic coffee machine.

Please refer to the [ArduinoCoffeeMachine documentation](https://arduinocoffeemachine.readthedocs.io/en/latest/?badge=latest) for a detailed explanation of the design and components used.

The SSD1306 display is driven using the [pico-ssd1306](https://github.com/Harbys/pico-ssd1306) library. All credits for that code goes to its creator.

## Getting Started

The project is configured to build targeting the RP2040 platform which is at the core of the Raspberry PI Pico board.

### Build

The `Makefile` at the project root directory provides targets to create the build docker image and to build the code itself:

```
$ make docker
$ make build
```

The build process runs inside a Docker container allowing isolation and easier dependencies management.

## PCB

Schematics and PCB gerber files can be found in the `pcb` folder. The folder contains:
- .zip archive containing gerber files for the PCB
- .png showing the schematics and the PCB mask
- .json file to open and edit the project in EasyEDA

## INTRODUCTION

To add a PID controller to the coffee machine we’ll need to replace the existing thermostats that control the heater. There are 2 thermostats to allow the operation of the machine heating water to brew temperature and also steam temperature. Unfortunately these thermostats do not allow a fine control of the water temperature, being a simple on/off switch without any logic behind. The result is that they don’t keep the water/steam temperature stable enough to allow consistency of the brewed coffee.

