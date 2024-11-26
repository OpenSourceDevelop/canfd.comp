# CAN-FD HAL Component for LinuxCNC

The `MCP2518.comp` module enables communication with CAN-FD (Controller Area Network - Flexible Data-Rate) devices in a LinuxCNC environment. It uses the Linux SocketCAN interface for sending and receiving CAN-FD frames, making it suitable for integration with devices such as motor controllers, sensors, and other automation peripherals.

---

## Features

- **CAN-FD Support**: Communicates with CAN-FD-capable devices.
- **Standard CAN Support**: Backward-compatible with standard CAN.
- **Configurable Baud Rate**: Supports custom CAN bus bitrates.
- **Data Handling**: Send and receive data with up to 64 bytes per frame.
- **Dynamic Configuration**: Adjustable through HAL pins and parameters.
- **Fault Tolerance**: Handles common communication errors gracefully.

---

## Installation

To compile and install the component:
```bash
halcompile --install MCP2518.comp
