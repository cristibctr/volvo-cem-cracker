# Building and Uploading

This project can be built with the Arduino IDE using either a Teensy 4.x or an STM32F411 "black pill" board.

## Requirements

- **Arduino IDE** (1.8.x or newer)
- **Board packages**
  - PJRC Teensy (for Teensy boards)
  - STM32 MCU based boards (by STMicroelectronics) for the F411
- **Libraries**
  - `LiquidCrystal`
  - `FlexCAN_T4` (Teensy only)
  - `STM32_CAN` (install via Library Manager for STM32). This library replaces
    the old "STM32duino CAN" package and is maintained by Pasi Kemppainen.

## Steps

1. Open the Arduino IDE and install the required board support using **Tools → Board → Boards Manager…**
2. For the black pill, select **Generic STM32F4 series → BlackPill F411CE** from the board list.
3. Use **Tools → Manage Libraries…** to install the **CAN bus Library for Arduino STM32** (`STM32_CAN`) if it is not already present.
4. Create a file named `hal_conf_extra.h` next to the sketch with the following
   line to enable CAN support (this repository already ships with such a file,
   just make sure it lives in the same folder as the `.ino`):
   ```
   #define HAL_CAN_MODULE_ENABLED
   ```
5. Connect your board and select the appropriate upload method (for the black pill usually `STM32CubeProgrammer (DFU)` or `Serial`).
6. Open `volvo-cem-cracker.ino`, choose the correct board and port, then click **Upload**.

The sketch uses `Serial` for the console and `Serial2` as the K-line port when building for STM32. Adjust the wiring accordingly.
