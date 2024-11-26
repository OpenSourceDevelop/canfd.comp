# CAN-FD HAL Component for LinuxCNC (MCP2518 over SPI)

The `canfd.comp` module enables communication with the MCP2518 CAN-FD controller via SPI in a LinuxCNC environment. It uses the SPI interface on the Raspberry Pi for direct communication with the MCP2518, supporting both standard CAN and CAN-FD frames.

---

## Features

- **CAN-FD Support**: Communicates with MCP2518 using CAN-FD.
- **Standard CAN Support**: Backward-compatible with standard CAN.
- **Configurable SPI Interface**: Uses Raspberry Pi SPI pins for communication.
- **Data Handling**: Send and receive data with up to 64 bytes per frame.
- **Dynamic Configuration**: Adjustable through HAL pins and parameters.

---

## Prerequisites

1. **SPI Interface on Raspberry Pi**:
   - Ensure the SPI interface is enabled using `raspi-config` or by modifying `/boot/config.txt`:
     ```bash
     sudo raspi-config
     # Navigate to: Interface Options -> SPI -> Enable
     ```
   - Or manually edit `/boot/config.txt`:
     ```bash
     dtparam=spi=on
     ```

2. **MCP2518 Wiring**:
   - Connect the MCP2518 to the Raspberry Pi SPI pins:
     - `MISO` → GPIO 9 (SPI0 MISO)
     - `MOSI` → GPIO 10 (SPI0 MOSI)
     - `SCLK` → GPIO 11 (SPI0 SCLK)
     - `CS` → GPIO 8 (SPI0 CE0)
     - `INT` → Any GPIO pin (for interrupts)

3. **Install SPI Tools**:
   - Install `spidev` and `can-utils`:
     ```bash
     sudo apt install python3-spidev can-utils
     ```

---

## Installation

To compile and install the component:
```bash
halcompile --install canfd.comp
