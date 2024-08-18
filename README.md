# Automatic-Vending-Machine
Automatic Vending Machine - Verilog Project

![Automatic_Vending_Machine](/automatic_vending_machine_ui.png)
## Overview
This repository contains the design code, testbench code, and UI image for an automatic vending machine implemented using Verilog. The vending machine accepts two types of inputs: 5 Rs and 10 Rs, and provides the appropriate change or delivers the product based on the amount inserted.

## Contents
- <b>Design Code:</b> The Verilog code for the vending machine logic.
- <b>Testbench Code:</b> The Verilog testbench to simulate and verify the functionality of the vending machine.
- <b>UI Image:</b> An image illustrating the user interface of the vending machine.
- <b>Project Information:</b> A detailed document (Project_details) that explains the state transitions and operation of the vending machine.

## Project Details
### Vending Machine Operation
The vending machine in this project is designed to vend a product costing 15 Rs. The machine operates based on the amount inserted by the user, and it has three primary states:

- <b>State 0 (s0):</b> 0 Rs in the Vending Machine
- <b>State 1 (s1):</b> 5 Rs in the Vending Machine
- <b>State 2 (s2):</b> 10 Rs in the Vending Machine
### State Transitions

- <b>State 0 (s0):</b>
    - If no money is added: Stay in s0, OUTPUT = 0, CHANGE = 0.
    - If 5 Rs is added: Move to s1, OUTPUT = 0, CHANGE = 0.
    - If 10 Rs is added: Move to s2, OUTPUT = 0, CHANGE = 0.

- <b>State 1 (s1):</b>
    - If no money is added: Return 5 Rs as change (incomplete transaction), Move to s0, OUTPUT = 0, CHANGE = 5 Rs (01).
    - If 5 Rs is added: Move to s2, OUTPUT = 0, CHANGE = 0.
    - If 10 Rs is added: Deliver the product, Move to s0, OUTPUT = 1, CHANGE = 0.

- <b>State 2 (s2):</b>
    - If no money is added: Return 10 Rs as change (incomplete transaction), Move to s0, OUTPUT = 0, CHANGE = 10 Rs (10).
    - If 5 Rs is added: Deliver the product, Move to s0, OUTPUT = 1, CHANGE = 0.
    - If 10 Rs is added: Deliver the product and return 5 Rs as change, Move to s0, OUTPUT = 1, CHANGE = 5 Rs (01).
This state transition logic ensures that the vending machine either provides the product or returns the appropriate change based on the user's input.

### Inputs
- <b>clk:</b> Clock signal.
- <b>rst:</b> Reset signal (active high).
- <b>in:</b> 2-bit input where 01 represents 5 Rs and 10 represents 10 Rs.

### Outputs
- <b>out:</b> Product delivery signal. 1 means the product is delivered.
- <b>change:</b> 2-bit output indicating the change returned (if any).

## How to Run the Code

- <b>Clone the Repository:</b>
    - Copy code<br>
`git clone https://github.com/vaibhavgupta03/Automatic-Vending-Machine.git`<br>
`cd vending-machine-verilog`

- <b>Open the Project:</b>
    - Open the Verilog files in your preferred IDE (e.g., ModelSim, Vivado).

- <b>Simulate the Design:</b>
    - Load the design file vending_machine_thala.v and the testbench file vending_machine_tb.v.
    - Run the simulation to observe the vending machine's behavior for different input sequences.

- <b>View the UI:</b>
    - Open the vending_machine_ui.png file to see the conceptual user interface of the vending machine.

- <b>Review Project Information:</b>
    - The file Project_details contains a detailed explanation of the state transitions and the overall operation of the vending machine.

## Code Explanation
### Design Code (vending_machine.v)
This module represents the core logic of the vending machine. The state machine manages transitions based on the inputs provided:

 - <b>State 0 (s0):</b> Represents the initial state where no money is inserted.
 - <b>State 1 (s1):</b> Represents the state where 5 Rs is inserted.
 - <b>State 2 (s2):</b> Represents the state where 10 Rs is inserted.

The `always` block handles the state transitions and output logic. The `case` statement determines the next state and outputs based on the current state and input.

## Testbench Code
The testbench code simulates different scenarios to verify the correctness of the vending machine design. It provides various input sequences and checks the outputs to ensure that the vending machine behaves as expected.