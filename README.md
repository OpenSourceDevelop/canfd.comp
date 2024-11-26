# CAN-FD HAL Component for LinuxCNC (MCP2518FD on Raspberry Pi)

The `canfd.comp` module enables communication with the MCP2518FD CAN-FD controller via SPI on a Raspberry Pi. It integrates CAN-FD support into LinuxCNC, allowing for high-speed communication with peripherals like motor controllers, sensors, and other industrial devices.

---

## Features

- **CAN-FD Support**: Communicates with the MCP2518FD over SPI, supporting CAN-FD frames with up to 64 bytes of data.
- **Standard CAN Compatibility**: Backward-compatible with standard CAN.
- **Interrupt-Based Processing**: Uses GPIO interrupts for efficient handling of received messages.
- **Configurable Parameters**: Allows configuration of baud rate, SPI settings, and interrupt GPIO pin.
- **Dynamic Data Handling**: Handles sending and receiving of CAN messages dynamically through HAL pins.

---

## Requirements

1. **Raspberry Pi with SPI Enabled**:
   - Enable the SPI interface on the Raspberry Pi via `raspi-config`:
     ```bash
     sudo raspi-config
     # Navigate to: Interface Options -> SPI -> Enable
     ```
   - Alternatively, add the following line to `/boot/config.txt`:
     ```bash
     dtparam=spi=on
     ```

2. **MCP2518FD Wiring**:
   - Connect the MCP2518FD to the Raspberry Pi as follows:
     - `MISO` → GPIO 9 (SPI0 MISO)
     - `MOSI` → GPIO 10 (SPI0 MOSI)
     - `SCLK` → GPIO 11 (SPI0 SCLK)
     - `CS` → GPIO 8 (SPI0 CE0)
     - `INT` → GPIO 25 (default, configurable in the module)

3. **Install Dependencies**:
   - Install the required tools and libraries for SPI and CAN:
     ```bash
     sudo apt update
     sudo apt install can-utils python3-spidev
     ```

---

## Installation

Compile and install the component:
```bash
halcompile --install canfd.comp
