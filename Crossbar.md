# SPI Crossbar

## Block Diagram

In the original VERA, SPI access was arbitrated by a simple mux and bus switch with the mux connection determined by the FPGA configuration
done (CDONE) signal. ESPIcial required a more complex system where the ESP32 could also communicate on the SPI busses for updating the
configuration firmware and writing files to the SD card. The following block diagram describes the logical connection between components and
related key signals on the SPI busses:

![SPI Crossbar Logical Connection Diagram](assets/VESPI_SPI.png)

This design requires the ESP32 microcontroller to participate in the FPGA configuration reset process. `FPGA_CFG` and `FPGA_SD` are tri-stateable 4-bit bus switches used to select where the FPGA's SPI bus is directed. Only one of FPGA SPI bus switch should be enabled at a time.

## FPGA Reset

The basic reset sequence for the FPGA is as follows:

1. ESP32 drives `FPGA_RESET_N` low. This places the FPGA into the reset state.
2. ESP32 drives FPGA_SD_EN and SPI_BUS_EN low (disabled state)
3. ESP32 releases its own SPI controller on CFG_SPI and switches those pins to the input (high impedance state). This ensures that there will not be bus contention between the ESP32 and the FPGA during configuration.
4. ESP32 drives `FPGA_CFG_EN` high (enable state). This connects the FPGA's SPI bus to the Flash configuration memory.
5. ESP32 releases `FPGA_RESET_N`
6. ESP32 monitors `FPGA_CDONE` waiting for it to go high. This should happen within 250ms of `FPGA_RESET_N` being released.
7. ESP32 disconnects any internal SPI controller (FSPI/VSPI) connected to the `SD_SPI` bus and sets those pins to output (high impedance).
8. ESP32 drives `FPGA_CFG_EN` low and `FPGA_SD_EN` high so that FPGA SPI bus activity is now directed toward the micro SD socket.

## Writing Flash from ESP32

The configuration memory stored on the SPI flash IC can be updated from the ESP32. The sequence for performing this operation is:

1. Ensure `FPGA_CFG_EN` is low so that the FPGA will not interfere with the update process.
2. Ensure `SPI_BUS_EN` is low so that the update activity is not incorrectly sent to the FPGA.
3. Connect one of the ESP32 SPI state machines to the CFG_SPI bus.
4. Perform the update process according to SPI flash datasheet.
5. (optional) perform an FPGA Reset

## Accessing the micro SD socket from ESP32

The ESP32 with a WiFi connection could act as an efficient way to transfer files to a computer using ESPIcial without physically moving the micro SD card between computers. To achieve this ESP32 has a second set of SPI signals connected to the micro SD SPI bus. The ESP32 should ensure that the FPGA is disconnected from the micro SD socket by driving `FPGA_SD_EN` low during the time that it is accessing the micro SD card.

## Driving video from ESP32

Note: the SPI slave state machine that must run on the FPGA is not yet implemented. This work is ongoing.

The ESP32 can also act as the micrcontroller driving the display. In this way, ESPIcial could operate as a single board computer with retro video output. This is accomplished by enabling `SPI_BUS_EN`. Separate chip select (SS#) pins are provided so that the SPI flash does not incorrectly interpret traffic directed at the FPGA as being intended for it.

[TODO: provide mapping of FPGA SPI slave pins]
