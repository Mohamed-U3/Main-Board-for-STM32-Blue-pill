# Main Board for STM32 Blue Pill

A custom PCB main board designed to extend JST cables for STM32F103C8T6 Blue Pill microcontroller board. This board provides organized connections for displays, sensors, buttons, and communication modules with proper ESD protection.

## 📋 Overview

This project is a breakout/expansion board for the STM32 Blue Pill that simplifies connections to various peripherals through organized connectors. The board features dedicated interfaces for TFT displays, laser range finders, sensors, and a 10-button.

### Key Features

- **Compact Design**: 60mm × 40mm PCB size
- **ESD Protection**: Built-in protection diodes for all I/O pins
- **Multiple Interfaces**: SPI, UART communication support
- **Organized Connectors**: Dedicated connectors for different peripheral types
- **Buttons**: Support for 10 buttons with internal pull-up configuration
- **Programming Interface**: SWD debugging/programming connector

## 🔌 Connectors & Pin Assignments

### J1 - TFT Display Connector (8 pins)

Standard SPI TFT display interface with power and control signals.

```
Pin | Signal | STM32 Pin | Description
----|--------|-----------|-------------
1   | BLK    | 3.3V      | Backlight control (always on)
2   | DC     | PA1       | Data/Command select
3   | RES    | PA2       | Reset signal
4   | CS     | PA4       | Chip Select
5   | CLK    | PA5       | SPI Clock (SPI1_SCK)
6   | MOSI   | PA7       | SPI Data Out (SPI1_MOSI)
7   | VCC    | 3.3V      | Power supply
8   | GND    | GND       | Ground
```

### J2 - LRF (Laser Range Finder) Connector (6 pins)

UART interface for laser distance measurement modules.

```
Pin | Signal | STM32 Pin | Description
----|--------|-----------|-------------
1   | VCC    | VIN       | Power supply (5V tolerant)
2   | GND    | GND       | Ground
3   | Rx     | PA10      | UART Receive (USART1_RX)
4   | Tx     | PA9       | UART Transmit (USART1_TX)
5   | En     | 3.3V      | Enable signal
6   | GND    | GND       | Additional ground connection
```

### J3 - Button Connector 1 (6 pins)

First set of button inputs with internal pull-up resistors.

```
Pin | Signal | STM32 Pin | Description
----|--------|-----------|-------------
1   | GND    | GND       | Common ground
2   | BTN1   | PB4       | Button 1 input
3   | BTN2   | PA15      | Button 2 input
4   | BTN3   | PA12      | Button 3 input
5   | BTN4   | PA8       | Button 4 input
5   | BTN5   | PB15      | Button 5 input
```

### J4 - Button Connector 2 (6 pins)

Second set of button inputs with internal pull-up resistors.

```
Pin | Signal | STM32 Pin | Description
----|--------|-----------|-------------
1   | GND    | GND       | Common ground
2   | BTN6   | PB5       | Button 6 input
3   | BTN7   | PB6       | Button 7 input
4   | BTN8   | PB7       | Button 8 input
5   | BTN9   | PB8       | Button 9 input
5   | BTN10  | PB9       | Button 10 input
```

### J5 - Sensor Connector (5 pins)

SPI interface for various sensors (IMU, compass, temperature, etc.).

```
Pin | Signal | STM32 Pin | Description
----|--------|-----------|-------------
1   | VCC    | 3.3V      | Power supply
2   | CS     | PB12      | Chip Select (SPI2_NSS)
3   | CLK    | PB13      | SPI Clock (SPI2_SCK)
4   | MISO   | PB14      | SPI Data In (SPI2_MISO)
5   | GND    | GND       | Ground
```

### J6 - SWD Connector (4 pins)

SWD interface for Programming & debbugging.

```
Pin | Signal | STM32 Pin | Description
----|--------|-----------|-------------
1   | VCC    | 3.3V      | Power supply
2   | SWDIO  | SWDIO     | Serial Wire Debug Input Output data
3   | SWDCLK | SWDCLK    | Serial Wire Debug Clock
4   | GND    | GND       | Ground
```

### J7 - Power Connector (2 pins)

Power input for the system

```
Pin | Signal | STM32 Pin | Description
----|--------|-----------|-------------
1   | VCC    | 5V        | System Power supply
2   | GND    | GND       | Ground
```

### J8 - Brightness SW Connector (4 pins)

Switch to select the Brightness of the TFT

```
Pin | Signal | STM32 Pin | Description
----|--------|-----------|-------------
1   | Level1 | PB0       | Brightness Level 1
2   | Level2 | PB1       | Brightness Level 2
3   | Level3 | PB10      | Brightness Level 3
4   | Level4 | PB11      | Brightness Level 4
```

### U1 - STM32 Blue Pill Socket

Standard 40-pin socket for STM32F103C8T6 Blue Pill board with organized breakout connections.

## 🔒 ESD Protection

The board includes comprehensive ESD protection for all I/O connections:

- **LESD8D3.3N3T5G** diodes for 3.3V signal protection
- **CESD5V0D3** diodes for 5V tolerant pins
- Protection on all connector pins to prevent damage from static discharge

## 🎯 Button Configuration

All 10 buttons are configured for **internal pull-up** operation:

| Button | STM32 Pin | GPIO Mode       | Notes                        |
| ------ | --------- | --------------- | ---------------------------- |
| 1      | PA8       | Input + Pull-up | TIM1_CH1 alternate function  |
| 2      | PA12      | Input + Pull-up | USB_DP alternate function    |
| 3      | PA15      | Input + Pull-up | SPI3_NSS alternate function  |
| 4      | PB4       | Input + Pull-up | SPI3_MISO alternate function |
| 5      | PB5       | Input + Pull-up | SPI3_MOSI alternate function |
| 6      | PB6       | Input + Pull-up | I2C1_SCL, TIM4_CH1 alternate |
| 7      | PB7       | Input + Pull-up | I2C1_SDA, TIM4_CH2 alternate |
| 8      | PB8       | Input + Pull-up | TIM4_CH3 alternate function  |
| 9      | PB9       | Input + Pull-up | TIM4_CH4 alternate function  |
| 10     | PB15      | Input + Pull-up | SPI2_MOSI alternate function |

## 📐 PCB Specifications

- **Dimensions**: 60mm × 40mm
- **Layers**: 2-layer PCB design
- **Design Tool**: KiCad EDA v9.0.3
- **Mounting**: Multiple mounting holes for secure installation
- **Copper Weight**: Standard 1oz copper thickness
- **Via Size**: Standard 0.4mm drill, 0.7mm pad
- **Minimum Track Width**: 0.4mm

## 📁 Repository Contents

```
├── D98.kicad_pcb              	# PCB layout file
├── D98.kicad_sch              	# Schematic file  
├── D98.kicad_pro              	# KiCad project file
├── bom/                       	# Bill of Materials
│   └── bom.csv               	# Component list with part numbers
├── production/                	# Manufacturing files
│   ├── gerbers/              	# Gerber files for PCB fab
│   ├── drill/                	# NC drill files
│   └── pick_and_place/       	# Assembly files
├── 3D output/                 	# 3D renderings (Step files)
└── fabrication-toolkit-options.json
```

## 🚀 Getting Started

### Prerequisites

- STM32F103C8T6 Blue Pill development board
- KiCad EDA software (for viewing/editing design files)
- ST-Link V2 programmer or compatible SWD interface
- Peripheral modules (TFT display, sensors, laser range finder)

### Hardware Assembly

1. **Install Blue Pill**: Solder the Blue Pill board into the U1 socket
2. **ESD Protection**: Install all ESD protection diodes (refer to schematic)
3. **Connectors**: Solder pin headers or JST connectors for J1-J6
4. **Programming Interface**: Install SWD connector (U2)
5. **Testing**: Verify all connections with multimeter before power-on

### Software Setup

1. Install STM32CubeIDE or PlatformIO with STM32 support
2. Configure GPIO pins according to the pin assignment table
3. Enable internal pull-ups for button pins in your initialization code
4. Set up SPI1 for TFT display communication
5. Configure SPI2 for sensor communication
6. Set up USART1 for laser range finder communication

## 🔧 Usage Examples

### TFT Display Connection

```c
// SPI1 configuration for TFT
// PA5 - SPI1_SCK (Clock)
// PA7 - SPI1_MOSI (Data)
// PA4 - CS (Chip Select)
// PA1 - DC (Data/Command)
// PA2 - RES (Reset)
```

### Sensor Interface

```c
// SPI2 configuration for sensors
// PB13 - SPI2_SCK (Clock)
// PB14 - SPI2_MISO (Data In)
// PB12 - SPI2_NSS/CS (Chip Select)
```

### UART Communication

```c
// USART1 configuration for LRF
// PA9  - USART1_TX (Transmit)
// PA10 - USART1_RX (Receive)
// Baud rate: 9600-115200 (module dependent)
```

### Button Reading

```c
// Configure buttons with internal pull-up
// Active LOW logic (pressed = 0, released = 1)
// Debouncing recommended in software
```

## ⚡ Power Requirements

- **Input Voltage**: 5V via USB or external supply
- **Logic Level**: 3.3V (regulated by Blue Pill)
- **Current Consumption**:
  - MCU: ~10mA (active)
  - TFT Display: 20-100mA (depending on size and backlight)
  - Sensors: 1-10mA each
  - LRF Module: 50-200mA (measurement dependent)

## 🛠️ Troubleshooting

### Common Issues

1. **No Display Output**: Check SPI connections and power supply
2. **Button Not Responding**: Verify internal pull-up configuration
3. **Sensor Communication Failure**: Check SPI2 pin assignments
4. **Programming Issues**: Ensure SWD connections are correct

### Debug Tips

- Use multimeter to verify 3.3V power rail
- Check continuity of all connector pins
- Verify Blue Pill is properly seated in socket
- Monitor current consumption to detect short circuits

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Mohamed Yousry Ragab**

- **GitHub**: [@Mohamed-U3](https://github.com/Mohamed-U3)
- **LinkedIn**: [mohamed-u3](https://www.linkedin.com/in/mohamed-u3/)
- **Email**: Contact via GitHub profile
- **Specialization**: Embedded Systems & PCB Design

## 🤝 Contributing

Contributions are welcome! Please feel free to submit:

- Bug reports and feature requests via [Issues](https://github.com/Mohamed-U3/Main-Board-for-STM32-Blue-pill/issues)
- Code improvements via Pull Requests
- Documentation enhancements
- Hardware testing feedback

### Development Guidelines

1. Follow KiCad design rules and conventions
2. Test all changes on actual hardware
3. Update documentation for any pin assignment changes
4. Maintain backward compatibility when possible

## 🔗 Related Projects

- [StopWatch_STM32F103](https://github.com/Mohamed-U3/StopWatch_STM32F103) - Stopwatch project using STM32F103
- *More STM32 projects coming soon...*

## 📊 Version History

- **v1.0** - Initial release with basic functionality
- **v1.1** - Added ESD protection and improved routing
- **v1.2** - Updated connector layout and pin assignments

## 📞 Support

For technical support:

1. Check the [Issues](https://github.com/Mohamed-U3/Main-Board-for-STM32-Blue-pill/issues) page
2. Review the troubleshooting section above
3. Create a new issue with detailed description and photos if needed

---

*This README reflects the D98 PCB design with corrected pin assignments. Always verify connections against the actual schematic before assembly.*
