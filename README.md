# UART Transmitter

### Team members

* David Hromas

### Table of contents

* Project objectives
* Hardware description
* VHDL modules description and simulations
* TOP module description and simulations
* Video
* References

<a name="objectives"></a>

## Project objectives

The goal of this project is to build a transmitter that sends data in the 7O1 format (7 data bits, odd parity, 1 stop bit) at a rate of 4800 Baud using the UART interface. The data word is configured using the switches on the board.

<a name="hardware"></a>

## Hardware description
![your figure](https://github.com/davidhro/DE1_projekt_2/blob/main/pictures/nexys-a7-callout.png)


The project uses the Nexys A7-50T board from Digilent.
The data word is set using the switches (18). Data output goes through one of the Pmod ports (14). One of the push buttons (13) is used for reset. The clock signal is provided by the internal crystal oscillator with a frequency of 100 MHz.

<a name="modules"></a>

## VHDL modules description and simulations

### parity_generator
The module performs an XOR operation on all input bits, and its output is the parity bit. It operates in odd parity mode, i.e. it generates the value 1 if the data word contains an even number of bits set to 1, and the value 0 if the data word contains an odd number of bits set to 1.

### clock_enable
The module adjusts the clock signal rate.

### cnt_up
The module ensures the required data transfer speed (together with the clock_enable module) and helps to send the data to the output bit by bit.

### UART_TX
The module arranges the bits into a vector and sends the individual bits serially. It assembles the bits (start bit, 7 data bits, one parity bit and one stop bit) into the specified format and sends them to the output one by one. The word starts with the start bit. The data bits are ordered LSB->MSB, followed by the parity bit and the stop bit.

### Simulation of all modules (selected signals)
![your figure](https://github.com/davidhro/DE1_projekt_2/blob/main/pictures/pictures/UART_TX_waveforms.png)
<a name="top"></a>

## TOP module description and simulations

![your figure](https://github.com/davidhro/DE1_projekt_2/blob/main/pictures/pictures/top.png)

The TOP module schematic, drawn using Vivado.

<a name="references"></a>

## References

1. https://github.com/tomas-fryza/digital-electronics-1
2. https://www.nandland.com/articles/what-is-a-uart-rs232-serial.html
3. https://forum.digikey.com/t/parity-generator-vhdl/12591
4. https://digilent.com/reference/programmable-logic/nexys-a7/reference-manual?redirect=1
