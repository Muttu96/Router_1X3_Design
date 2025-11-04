📌 Project Overview

The Router 1x3 manages data packets through a modular architecture consisting of multiple submodules such as FIFO Buffers, Register, FSM Controller, and Synchronizer.
It ensures smooth data transfer, reliable flow control, and high-speed communication without packet loss or corruption.

The router also includes parity checking for error detection and a finite state machine (FSM) for controlling data flow and timing across the design.

🧩 Submodule Descriptions
1️⃣ FIFO Buffers (fifo0, fifo1, fifo2)

Each output port has a dedicated FIFO buffer to store packets temporarily before transmission.

Purpose: Prevent data loss and manage flow control during varying data rates.

Operation:

Write to FIFO when valid data arrives.

Read from FIFO when the output port is ready.

Capacity: 8 packets (Depth = 8).

2️⃣ Register

Purpose: Holds the currently received packet for address decoding and parity check.

Operation: Loads valid packets from the input and enables decoding by the FSM.

3️⃣ Finite State Machine (FSM) Controller

Purpose: Controls the router’s operation across states — idle, receiving, decoding, FIFO write, and output wait.

Operation: Transitions depend on input validity, FIFO status, and control signals.

Benefit: Ensures ordered and reliable packet processing.

4️⃣ Synchronizer

Purpose: Synchronizes asynchronous signals from external domains to the router’s internal clock.

Operation: Uses flip-flops to stabilize asynchronous transitions, preventing metastability.

⚙️ Additional Features

Parity Checker: Detects corrupted packets and flags errors before forwarding.

Signal-Based Flow Control: Uses write and read enable signals for reliable data transfer between modules.

Soft Reset Mechanism: Automatically triggers reset when output data remains unread for a defined number of cycles.

🛠️ Tools Used

Xilinx Vivado – RTL design and simulation

QuestaSim / ModelSim – Functional simulation and waveform analysis

EDA Playground – Rapid design validation and testbench testing


💡 Learning Outcome

This project strengthened understanding of packet-based router architecture, data synchronization, and finite state machine control.
It demonstrates how FIFO buffering, error checking, and flow control work together in digital communication systems to ensure high performance and data integrity.

📍 Author: Muttu B Naik
📧 Email: muttunaik5096@gmail.com

🔗 LinkedIn: https://www.linkedin.com/in/muttunaik5096
