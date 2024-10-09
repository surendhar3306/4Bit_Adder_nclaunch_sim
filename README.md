# EXP1: 4 Bit Adder functionality verification
# Aim: 
To write a verilog code for 4bit adder and verify the functionality using Test bench.

 Write Verilog Code

 Verify the Functionality using Test-bench.

# Tool Required:
Functional Simulation: nclaunch Simulator (nclaunch)

# 4-bit Adder Design:
To construct a 4-bit adder, need to chain together four 1-bit full adders. Each full adder computes the sum and carry for one bit of the two numbers. The carry-out from one adder feeds into the carry-in of the next adder in the sequence. This process adds the two 4-bit numbers bit by bit, with the carry propagating through each stage, resulting in a final sum and carry-out at the end.

To design a 1-bit full adder, the first step is to create a truth table that represents all possible combinations of the inputs (A, B, and CIN) and the corresponding outputs (Sum(S) and COUT).

![image](https://github.com/user-attachments/assets/ce099a52-d3d1-4c26-b36c-ac58ecef5eac)

Here’s the truth table for a 1-bit full adder:

![image](https://github.com/user-attachments/assets/e577e0d9-1a1a-49f4-bbf6-0efd13329d32)
# Fig 1 : Diagram and truth table of full adder
# Logic Expressions:
1.Sum (S): S=A⊕B⊕CIN
   Where ⊕ represents XOR.
   
2.Carry out (COUT):COUT=(A&B) 

3.Carry in(CIN): (A^B)
![image](https://github.com/user-attachments/assets/e79e7281-180b-40cb-99b2-46dbedbb9aca)

# Fig 2:Diagram of 4 Bit Adder

# Creating Source Codes
 In the Terminal, type gedit .v (ex: gedit 4bitadder.v).

 A Blank Document opens up into which the following source code can be typed down.

Note : File name should be with HDL Extension

# a) Verify the Functionality
 Three Codes shall be written for implementation of 4-bit Adder as follows,

• fa.v → Single Bit 3-Input Full Adder [Sub-Module / Function]

• fa_4bit.v → Top Module for Adding 4-bit Inputs.

• fa_4bit_test.v → Test bench

*/Program to design 4 bit adder by instantiating 1 bit Full adder.also add test bench program / Developed by: Register Number/

# Functional Simulation:
 Invoke the cadence environment by type the below commands

 tcsh (Invokes C-Shell)

 source /cadence/install/cshrc (mention the path of the tools)
  (The path of cshrc could vary depending on the installation destination)
 After this you can see the window like below
![image](https://github.com/user-attachments/assets/286f9237-311c-414b-a723-29b518f8b817)
# Fig 3:Invoke the Cadence Environment
 To Launch Simulation tool
•	linux:/> nclaunch -new& // “-new” option is used for invoking NCVERILOG for the first time for any design
or

•	linux:/> nclaunch& // On subsequent calls to NCVERILOG
 It will invoke the nclaunch window for functional simulation we can compile,elaborate and simulate it using Multiple Step .
![image](https://github.com/user-attachments/assets/3638af14-bc68-4fb9-b6b2-fbc9bc0d76e1)
# Fig 4:Setting Multi-step simulation
 Select Multiple Step and then select “Create cds.lib File” .

 Click the cds.lib file and save the file by clicking on Save option
![image](https://github.com/user-attachments/assets/779344c4-7e56-4d02-aca7-9d83f01f7c4c)
# Fig 5:cds.lib file Creation
 Save cds.lib file and select the correct option for cds.lib file format based on the HDL Language and Libraries used.

 Select “Don’t include any libraries (verilog design)” from “New cds.lib file” and click on “OK” as in below figure .

• We are simulating verilog design without using any libraries

• A Click “OK” in the “nclaunch: Open Design Directory” window as shown in below figure

![image](https://github.com/user-attachments/assets/7b261dfb-fcac-4c21-bfba-f894d4807fe0)
# Fig 6: Selection of Don’t include any libraries
 A ‘NCLaunch window’ appears as shown in figure below

 Left side you can see the HDL files. Right side of the window has worklib and snapshots directories listed.

 Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation .

 To perform the function simulation, the following three steps are involved Compilation, Elaboration and Simulation.

# Fig 7: Nclaunch Window

![image](https://github.com/user-attachments/assets/f39120cf-1b50-441c-acbb-4ee14f726b06)
# Step 1: Compilation:– Process to check the correct Verilog language syntax and usage
 Inputs: Supplied are Verilog design and test bench codes

 Outputs: Compiled database created in mapped library if successful, generates report else error reported in log file

 Steps for compilation:

Create work/library directory (most of the latest simulation tools creates automatically)
Map the work to library created (most of the latest simulation tools creates automatically)
Run the compile command with compile options i.e Cadence IES command for compile: ncverilog +access+rwc -compile fa.v
Left side select the file and in Tools : launch verilog compiler with current selection will get enable. Click it to compile the code

Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation

# Fig 8: Compiled database in worklib
 After compilation it will come under worklib you can see in right side window

 Select the test bench and compile it. It will come under worklib. Under Worklib you can see the module and test-bench.

 The cds.lib file is an ASCII text file. It defines which libraries are accessible and where they are located. It contains statements that map logical library names to their physical directory paths. For this Design, you will define a library called “worklib”

![image](https://github.com/user-attachments/assets/8253b3d5-87a0-4f59-abce-da6be08dc5e6)
# Step 2: Elaboration:– To check the port connections in hierarchical design
 Inputs: Top level design / test bench Verilog codes

 Outputs: Elaborate database updated in mapped library if successful, generates report else error reported in log file

 Steps for elaboration – Run the elaboration command with elaborate options

1.It builds the module hierarchy
2.Binds modules to module instances
3.Computes parameter values
4.Checks for hierarchical names conflicts
5.It also establishes net connectivity and prepares all of this for simulation
 After elaboration the file will come under snapshot. Select the test bench and elaborate it.

# Fig 9: Elaboration Launch Option

![image](https://github.com/user-attachments/assets/73428c80-5f6f-4a7e-a6fd-4c85963664b3)
# Step 3: Simulation: – Simulate with the given test vectors over a period of time to observe the output behaviour.
 Inputs: Compiled and Elaborated top level module name

 Outputs: Simulation log file, waveforms for debugging

 Simulation allow to dump design and test bench signals into a waveform

 Steps for simulation – Run the simulation command with simulator options

# Fig 10: Design Browser window for simulation

![image](https://github.com/user-attachments/assets/200edba7-a4b3-4bb6-afef-50cacc152b7b)

# Fig 11: Launching Simulation Waveform WindowSimulation Waveform Window

![image](https://github.com/user-attachments/assets/8dfbde8a-aa11-4aa8-9410-3ee763bd1d09)

# Fig 12: Simulation Waveform Window

![image](https://github.com/user-attachments/assets/edce38e3-34e8-4d20-8fbe-3bc628003d2a)

