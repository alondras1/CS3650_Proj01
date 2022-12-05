## CS3650_Proj01 : Single Cycle Preowned Processor 

# Notes
https://docs.google.com/document/d/1ThHZGP7AFoKlbOJ6b8oWPkdn_OdW3jxgtyNy645WAok/edit

# Installation 
- (Mac) using homebrew worked best to download icarus verilog via Terminal 
- $ /bin/bash -c “$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" /bin/bash
- $ install icarus-verilog
- [Installation tutorial](https://www.youtube.com/watch?v=jUYkYoYr8hs)
(Mac) for GTKWave the provided link for mac worked just fine. For M1, security settings do have to be configured for the app to properly launch. 

# ALU 
- Takes 3 inputs (the two values to be operated on SrcA, SrcB and the alu control value produced by the previous module)
- Produces 2 outputs (ALUResult and zero)
- Depending on the alucontrol input a different operation will be selected 
- handles setting the zero variable
- The output is the result for the Case module 

# ALU_Control_Unit
- Takes 2 inputs (function is 6 bits, Operation is 2 bits)
- Creates 1 output (ALU Control)
- using a case statement, depending on the alu_op input given, the alu_control will output the corresponding alu_control  
- 3-bit output that is sent to ALU.v

# Control_Unit
- This module handles sending which reg to read or write to, which register will be the destination, whether or not the branching is involved, whether or not jumping is involved
- It will only take one input (which operation to perform)
- Based on the input, the case statement will decide which instruction it is reading and how to assign which values to the different registers. 
- clk input hadles updating all the state elements on the same clock edge

# Data_Memory 
- This module takes in the clock cycle and what to reset to 
- The following three inputs are the address to write to, the data to write. We were not sure what WE meant 
- This will output the reg data of what was read
- The module will read data from a file. #500 is the mode to write 
- The data that will be stored will be stored will be stored on the positive clock edge 

# Imm_Sign_Extend 
- This module will take a number and compute an immediate sign extension 

# Instr_Memory 
- This module will read from the memfile.dat. Those are the 18 machine codes 
- The assign line holds the entire machine instruction. 

# MEM_Data.txt
- This will display the address being written to and where that address is located.

# Memfile.dat
- This outputs the various states of the registers in a sequential pattern based on the change in the different wires.
- Useful for debugging purposes, and also for when a waveform isn’t necessary to be generated or read.

# MIPS_Single_Cycle.v
- This serves as the core implementation for the running of the program; the instances of the other control modules are contained within this module.
- Interfaces with the majority of the datalines and registers through wire implementation.

# MIPS_wave.vcd 
- This is the output file that the GTKwave executable can interpret and generate waveforms from.

# PC_Counter.v 
- This assigns the program counter based on inputs like the low clock signal, and requires a sign immediate input.
- The next PC address is set to the current counter plus an addition of 4 on a 32 bit interface.

# Reg_File.v
- Contains register data that is used to write to for data values.
- The inputs include regWrite, which is used to enable the writing to a register, as well as the input for the data to be written. Additionally, the data address is separated and is input in three different inputs busses.

# tb_MIPS_Single_Cycle.v
- Serves as the initiator for the test values, is responsible for tracking the values in the testbench, as well as writing the results of the waveform to a file to be recompiled for waveform analysis.
- The clock cycles, as well as the amount of time that passes, are controlled externally from the main processor implementation by this test bench. A count is also calculated and set on the falling edge of the clock cycle using an “always” block.

# tb_MIPS_Single_Cycle.vvp 
- Compiled version of the testbench file. This keeps the results in a format that can be further converted by the vvp executable into a .vcd (or in macs, a .ltk file) for graphing by a waveform viewer, such as GTKwave.


# References 
https://github.com/Hola39e/MIPS_Multi_Implementation
https://www.fpga4student.com/2017/01/verilog-code-for-single-cycle-MIPS-processor.html



