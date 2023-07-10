# ESPIcial Pin Mappings

## ESP32 Pin Mapping

| GPIO Pin | Dir     | Name | Function |
| -------- | ------- | ---- | ---- |
| 0        | In      | Boot0 | Boot select (connected to BOOT0 button and serial DTR/RTS update circuit) |
| 1        | Inout   | SCL | I2C Clock |
| 2        | Out     | LED | Built-in LED |
| 3        | Out     | BUS_IRQ_N | Connected to the IRQ# pin on the parallel bus connector |
| 4        | TBD     | USER0 | Unused, available to user at GPIO header |
| 5        | TBD     | USER1 | Unused, available to user at GPIO header |
| 6        | TBD     | USER2 | Unused, available to user at GPIO header |
| 7        | TBD     | USER3 | Unused, available to user at GPIO header |
| 8        | Inout   | SDA | I2C Data |
| 9        | Out,HiZ | SD_SPI_SS | Micro SD SPI interface, chip select signal |
| 10       | Out,HiZ | SD_SPI_MOSI | Micro SD SPI interface, host data output |
| 11       | Out,HiZ | SD_SPI_SCK | Micro SD SPI interface, Clock |
| 12       | In      | SD_SPI_MISO | Micro SD SPI interface, micro SD data output |
| 13       | Out     | FPGA_CFG_EN | FPGA SPI Configuration bus switch enable |
| 14       | In      | FPGA_CDONE | FPGA Configuration completed signal |
| 15       | Out     | XTAL_32K_P | RTC Crystal oscillator positive/output pin |
| 16       | In      | XTAL_32K_N | RTC Crystal oscillator negative/input pin |
| 17       | TBD     | USER4 | Unused, available to user at GPIO header |
| 18       | TBD     | USER5 | Unused, available to user at GPIO header |
| 19       | Inout   | USB_D_N | USB differential pair data signal, negative side |
| 20       | Inout   | USB_D_P | USB differential pair data signal, positive side |
| 21       | Out,HiZ | SPI_BUS_EN | ESP32 to FPGA SPI Bus switch enable (enabled when 1) |
| 22       | N/A     | NC | Not connected |
| 23       | N/A     | NC | Not connected |
| 24       | N/A     | NC | Not connected |
| 25       | N/A     | NC | Not connected |
| 26       | N/A     | NC | Not connected |
| 27       | N/A     | NC | Not connected |
| 28       | N/A     | NC | Not connected |
| 29       | N/A     | NC | Not connected |
| 30       | N/A     | NC | Not connected |
| 31       | N/A     | NC | Not connected |
| 32       | N/A     | NC | Not connected |
| 33       | N/A     | NC | Not connected |
| 34       | N/A     | NC | Not connected |
| 35       | In      | CFG_SPI_MISO | Configuration Flash SPI bus, flash IC data output |
| 36       | Out,HiZ | CFG_SPI_SCK | Configuration Flash SPI bus clock |
| 37       | Out,HiZ | CFG_SPI_MOSI | Configuration Flash SPI bus, host data output
| 38       | Out,HiZ | CFG_SPI_SS | CS# of FPGA Configuration Flash ROM |
| 39       | In      | MTCK | JTAG Clock |
| 40       | In      | MTDO | JTAG Data output |
| 41       | In      | MTDI | JTAG Data input |
| 42       | In      | MTMS | JTAG chip select |
| 43       | Out     | PRG_RXD | ESP32 to Host serial data |
| 44       | In      | PRG_TXD | Host to ESP32 serial data |
| 45       | Out,HiZ | SPI_BUS_CS | CS# connected to FPGA SPI Bus switch for ESP32->FPGA communication |
| 46       | Out     | FPGA_SD_EN | Bus switch enable for FPGA->micro SD socket SPI bus |
| 47       | In      | FPGA_CRESET_N | Pin connected to RESET# signal on the 8-bit parallel bus interface, also goes to the FPGA |
| 48       | Out     | FPGA_RESET | FPGA Reset signal, does not drive CRESET_N |

