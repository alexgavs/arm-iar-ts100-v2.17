# arm-iar-ts100-v2.17

TS100 soldering station firmware — IAR Embedded Workbench project for the STM32F103-based Miniware TS100.

## What it does
Firmware for the TS100 portable soldering iron (STM32F103 MCU). The codebase covers the device's hardware abstraction, OLED UI, USB mass-storage / bot interface (so the iron appears as a virtual disk for configuration), I2C accelerometer (`MMA8652FC`), internal/external flash handling, FAT12 filesystem, and the main control loop.

Source headers identify it as **S100 APP version 2.11** by e-Design Co., Ltd. (2015), retained here at v2.17 for reference / modification.

## Stack
- Language: C, with ARM startup assembly
- Toolchain: IAR Embedded Workbench for ARM (`App.eww`, `App.ewp`, `App.ewd`)
- Target MCU: STM32F103 (Cortex-M3); linker script `STM32F103_APP.icf`
- Output: `Exe/APP.hex` / `Exe/APP.out`

## Build / Run
Open `App.eww` in IAR Embedded Workbench for ARM, then Project → Rebuild All. The resulting `APP.hex` can be flashed to the TS100 via its DFU bootloader (hold the front button while connecting USB).

## Layout
- `Src/` — C sources (`Main.c`, `Bios.c`, `CTRL.c`, `UI.c`, `Oled.c`, `Disk.c`, `Flash.c`, USB stack, `MMA8652FC.c`, startup `.s` files, etc.)
- `Inc/` — headers (`HARDWARE.h`, `S100V0_1.h`, USB descriptors, `APP_Version.h`, …)
- `Exe/` — prebuilt `APP.hex` / `APP.out`
- `App.eww`, `App.ewp`, `App.ewd` — IAR workspace / project
- `STM32F103_APP.icf` — IAR linker config
- `settings/` — IAR debugger session files

## Status
Archived in spirit (last touched 2017). Vendor firmware port; modifications visible as `*.orig` files alongside edited sources.
