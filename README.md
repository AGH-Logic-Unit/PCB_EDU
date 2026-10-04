# Educational Board by AGH Logic Unit

An educational PCB board that demonstrates the architecture and operating principles of a processor in a highly simplified way. The project allows you to physically trace the data flow between memory, registers, and logic. All signals are controlled manually, and logic states are visualized in real time across the respective sections using LEDs.

<img width="1519" height="872" alt="PCB_EDU" src="https://github.com/user-attachments/assets/39488707-63c5-47f2-91b8-10c64edd81a2" />

## Functional Blocks

The system is divided into several sections:
* **Instruction Memory** - a set of LEDs reflecting the current state of the switches on the bottom panel (input data, selected register addresses, operation code).
* **Register File** - memory implemented as a 4x4 LED matrix. It represents 4 registers of 4 bits each. The LED arrangement allows direct observation of data distribution in the memory. By manipulating the inputs, you can also manually draw simple shapes on the matrix.
* **ALU** - an asynchronous, simplified arithmetic logic unit performing bitwise operations on the data fetched from the registers.
* **Data Memory** - output LEDs displaying the final result of the operation performed by the ALU.

## Interface and Controls

On the bottom edge of the board, there is a panel equipped with toggle switches and push buttons. 

Meaning of the individual signals:
* `DATA [3..0]` - sets the 4 data bits to be introduced into the system.
* `R SET [1..0]` - (Register Set) selects the address of one of the 4 registers where the value from the DATA lines will be written.
* `REG 0 [1..0]` - address of the first source register. Data from this register is routed to the first input of the ALU.
* `REG 1 [1..0]` - address of the second source register. Data from this register is routed to the second input of the ALU.
* `OP` - selects the type of logical operation performed by the ALU (AND or OR).
* `WE` - (Write Enable) a push button triggering the write process. Pressing it saves the current state of the DATA lines to the register indicated by R SET.
* `RST` - asynchronous reset button. Clears the contents of all registers (zeroes the matrix).
* `LED` - a switch used to demonstrate the Two's complement (U2) format.

## Basic Data Flow (Example)

1. Set a specific value on the `DATA` switches.
2. Use the `R SET` switch to indicate the register you want to write to (e.g., address 00).
3. Click `WE`, which immediately lights up the corresponding LEDs in the first row of the Register File block.
4. Change the `DATA` value, set `R SET` to the next register (e.g., 01), and write it again by pressing `WE`.
5. Route the saved data to the ALU: set `REG 0` to address 00 and `REG 1` to address 01.
6. Use the `OP` switch to decide whether an AND or OR operation should be performed on the given inputs.
7. The Data Memory section will display the operation's result.
