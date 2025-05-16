===========================================================================================
Modified Nano-processor Instruction Manual
===========================================================================================
Team No.	  : 	- 03
Team Members  : 	- Gunathilake M.H.S.
			- Abeynayake D.C.
			- Kodithuwakku K.S.
			- Wanigasooriya K.W.M.R.S.B.
-------------------------------------------------------------------------------------------

Table of Contents:
 1. Introduction
 2. System Requirements
 3. Installation Instructions
 4. Functionality Overview
 5. Usage Instruction
 6. Troubleshooting
 7. Appendix
 8. Feedback

-------------------------------------------------------------------------------------------

1. Introduction:
   Welcome to the instruction manual for the modified nano-processor with additional 
   featuresproject. This document provides guidance on setting up and using the designed 
   microprocessor functionalities.


2. System Requirements:
   - Basys3 FPGA board
   - Vivado Design Suite (version 2018.1 or later)


3. Installation Instructions:
   - Open Vivado and create a new project.
   - Import the provided VHDL files for the nanoprocessor component.
   - Configure the project settings and generate the bitstream.
   - Connect the Basys3 FPGA board to your computer via the USB cable.
   - Program the FPGA board with the generated bitstream.


4. Functionality Overview:
   - The nano-processor is capable of executing a variety of instructions. 
   - Upon initiation, processor starts to execute the instructions stored in the ROM 
     sequentially according to clock signal.
   - There are several outputs that displays the results of each executed instruction. 


5. Usage Instruction:

   Important: 
   - Register 0 is hardcoded to value 0 for the entire time.
   - Negative numbers are represented using 2's complement.
   - Current processor is a 4-bit processor. Therefore, the The arithmetic 
     operations have limited range (-8 to +7) to show correct value.

   Inputs:    
   - PIN U18  push button is used to reset the program counter and the register bank.
   - The user is recommended to reset the system before running the application. 

   Outputs:
   - LEDs
   	-- PIN U16, PIN E19, PIN U19, and PIN V19 LEDs are used to display the value 
         stored in Register 7

      -- PIN N3 is the Sign flag and turn ON if the result of AU is negative.
   	-- PIN P1 is the Zero flag and turn ON if the output value of the AU unit is zero.
   	-- PIN L1 is the Overflow flag and turn ON if the output of AU exceeds the reserved range.
      
      -- PIN W18 is the Equal flag of Comparator Unit.
      -- PIN U15 is the Greater flag of Comparator Unit.
      -- PIN U14 is the smaller flag of Comparator Unit. 

   - 7-segment display
      -- The last (right most) two 7-segment display units display the value in the Register 7
         in correct decimal representation of positive and negative numbers. If the result is 
         negative, minus sign is displayed in front of the numerical magnitude value.

   Guide to use the Machine code:
   - The machine code takes the following format.
     [Instruction (3 bits)][Register A (3 bits)][Register B (3 bits)][Value (4 bits)]

     -- Instruction (3 bits): Specifies the operation to be performed.
     -- Register A (3 bits) : The register that will be updated or selected for the instruction.
     -- Register B (3 bits) : The register that will not be updated but may be used for the instruction.
     -- Value (4 bits)      : A user-provided value, if applicable.   

     -- Instruction Set:
   		- Addition (000)
     		  000[RegA][RegB][----] : Adds the values of Register A and Register B, 
              and stores the result in Register A, overwriting its previous value.

   		- Negation (001)
     		  001[RegA][0000][----] : Negates the value of Register A. Register B must be 0 (0000). 
     		  The result is stored in Register A, overwriting its previous value.

   		- Move (010)
     		  010[RegA][----][Value]: Moves the provided 4-bit Value into Register A, 
     		  overwriting its previous value.

   		- Jump if Zero (011)
     		  011[RegA][----][Address]: If the value in Register A is zero, jumps to the instruction 
              at the specified Address.

		- Compare (100)
		  100[RegA][RegB][----]	: Compare the values in Register A and Register B. Currently it 
              display if the values are equal or Register A value is greater than or less than Register B
	        in the corresponding LEDs.	

   Instruction to use:
   - After programmiing the FPGA board, press the Reset button (PIN U18).
   - Then the processor is reset and starts to execute the instructions from 0th ROM.
   - If you want to reset at a particular occasion, press, Reset button (PIN U18).


6. Troubleshooting:
   - If the nanoprocessor does not execute programs correctly, verify the program code and 
     memory configuration.


7. Appendix:
   - For additional information, refer to the project documentation, lab rport.
   - For technical support or further assistance, please contact "himala.22@cse.mrt.ac.lk".


8. Feedback:
    We value your feedback! Please send any suggestions, bug reports, or comments to 
    "ravinduw.22@cse.mrt.ac.lk".

===========================================================================================