# UART DMA Memory-to-Peripheral Transfer Project

## Author
**Phạm Lê Ngọc Sơn**

## Overview
This project demonstrates the implementation of Memory-to-Peripheral Direct Memory Access (DMA) transfers using UART2 on the STM32F407 Discovery board. The application uses DMA to efficiently transfer data from memory to the UART peripheral without CPU intervention, allowing the processor to perform other tasks during the data transfer process.

## Hardware Requirements
- STM32F407 Discovery board
- USB-to-UART converter (for viewing the transmitted data)
- Jumper wires

## Project Structure
```
UART2_TX_DMA_M2P_Project/
├── Core/                     # Core application code
│   ├── Inc/                  # Header files
│   │   ├── main.h           # Main application header
│   │   ├── stm32f4xx_hal_conf.h  # HAL configuration
│   │   └── stm32f4xx_it.h   # Interrupt handlers header
│   └── Src/                  # Source files
│       ├── main.c           # Main application code
│       ├── stm32f4xx_hal_msp.c  # HAL MSP initialization
│       ├── stm32f4xx_it.c   # Interrupt handlers
│       └── system_stm32f4xx.c  # System configuration
├── Drivers/                  # STM32 HAL drivers
├── MDK-ARM/                  # Keil MDK-ARM project files
│   ├── data_stream.c        # Data to be transmitted
│   └── ...                  # Other Keil project files
└── UART2_TX_DMA_M2P.ioc     # STM32CubeMX configuration file
```

## Functionality
1. The project initializes STM32F407's UART2 and configures DMA for memory-to-peripheral transfer.
2. When the user button (Blue button on the STM32F4 Discovery board) is pressed, it triggers an interrupt.
3. In the interrupt handler, a DMA transfer is initiated to send a predefined message from memory to UART2.
4. The message is transmitted without CPU intervention, demonstrating efficient data transfer.

## Pin Configuration
- PA2: USART2_TX - Connected to the RX pin of a USB-to-UART converter
- PA3: USART2_RX - Connected to the TX pin of a USB-to-UART converter
- PA0: User button (EXTI0) to trigger the DMA transfer

## DMA Configuration
- DMA1, Stream 6, Channel 4 is used for USART2 TX
- Memory-to-peripheral direction
- Memory and peripheral sizes: Byte (8-bits)
- Memory increment mode: Enabled
- Peripheral increment mode: Disabled
- Transfer complete interrupt: Enabled

## How to Use
1. Connect the STM32F407 Discovery board to your computer using a USB cable.
2. Connect PA2 (USART2_TX) to the RX pin of a USB-to-UART converter.
3. Connect PA3 (USART2_RX) to the TX pin of a USB-to-UART converter.
4. Connect the USB-to-UART converter to your computer.
5. Open a serial terminal application (such as Tera Term, PuTTY, or CoolTerm).
6. Configure the serial port with the following settings:
   - Baud rate: 115200
   - Data bits: 8
   - Stop bits: 1
   - Parity: None
   - Flow control: None
7. Press the blue user button on the STM32F407 Discovery board.
8. Observe the message transmitted in your serial terminal application.

## Development Environment
- STM32CubeMX: For initial project configuration and code generation
- Keil MDK-ARM: For development, compilation, and debugging

## Acknowledgements
Thanks to STMicroelectronics for providing the STM32 HAL libraries and documentation that made this project possible.