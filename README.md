"# SPI_Master_Core" 

# 🔗 APB-Based SPI Master Core

## 📌 Overview

This project implements an **APB (Advanced Peripheral Bus) based SPI (Serial Peripheral Interface) Master Core** using RTL design in Verilog. The design enables efficient communication between an APB master (like a microcontroller) and SPI-compatible peripheral devices.

The SPI core supports **full-duplex synchronous communication**, configurable clock modes, and seamless integration with AMBA APB protocol systems. 


## 🚀 Key Features

* APB3 compliant slave interface for easy SoC integration
* Full-duplex SPI communication (simultaneous transmit & receive)
* Configurable SPI modes (CPOL & CPHA support)
* Master and Slave operation support
* Programmable baud rate generator
* Low power operation modes (Run, Wait, Stop) 
* Double-buffered data handling


## 🧱 Architecture

The SPI core is divided into the following major blocks:

1. **APB Slave Interface**

   * Handles communication with APB master
   * Supports read/write transactions

2. **Baud Rate Generator**

   * Generates SPI clock (SCLK) from APB clock
   * Uses programmable divisor logic

3. **SPI Slave Select Generator**

   * Controls SS (Slave Select) signal
   * Manages transaction boundaries

4. **Shift Register (Shifter)**

   * Handles serial-to-parallel and parallel-to-serial conversion

👉 The *block diagram (page 8 of the document)* shows interaction between APB interface, shifter, and clock generator. 


## 🔌 SPI Interface Signals

* **MOSI** – Master Output, Slave Input
* **MISO** – Master Input, Slave Output
* **SCK** – Serial Clock
* **SS** – Slave Select

These signals enable synchronous communication between master and slave devices. 


## 🧠 APB Protocol Basics

* Uses **Setup and Access phases** for each transfer
* Minimum of **2 clock cycles per transaction**
* Key signals:

  * `PADDR`, `PWDATA`, `PRDATA`
  * `PSEL`, `PENABLE`, `PWRITE`
  * `PREADY`, `PSLVERR` 


## ⚙️ Register Map

| Address | Register Name          | Access |   |
| ------- | ---------------------- | ------ | - |
| 0       | SPI Control Register 1 | RW     |   |
| 1       | SPI Control Register 2 | RW     |   |
| 2       | SPI Baud Rate Register | RW     |   |
| 3       | SPI Status Register    | RO     |   |
| 5       | SPI Data Register      | RW     |   |


## 🔁 Data Transfer Flow

1. Data written into SPI Data Register via APB
2. SS signal goes LOW (start of communication)
3. SCLK generated based on CPOL & CPHA
4. Data transmitted via MOSI and received via MISO
5. SS goes HIGH (end of communication) 


## 🛠️ Tools & Technologies

* Verilog HDL (RTL Design)
* Simulation using Verilog Testbench
* Linting & Synthesis tools
* AMBA APB Protocol


## 🧪 Verification

* Verilog-based testbench used for functional validation
* Different SPI modes and baud rates tested
* Data integrity verified through simulation


## 📈 Applications

* Embedded systems
* Sensor interfacing
* Communication modules
* Microcontroller peripheral communication


## 🔮 Future Enhancements

* UVM-based verification environment
* Support for multi-slave SPI
* DMA integration for high-speed transfer
* AXI/APB bridge extension

## Conclusion

This project successfully demonstrates the design and implementation of an **APB-based SPI Master Core** using RTL in Verilog. It ensures reliable, high-speed communication between APB and SPI domains with configurable features like clock modes and baud rate. The modular architecture makes it scalable and easy to integrate into SoC designs. Overall, it provides a strong foundation for further enhancements in design and verification.
