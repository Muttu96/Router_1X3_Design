# Router_1X3

## 📌 Project Overview

This project implements a **1x3 Router** in Verilog designed for packet-based data communication. The router receives data packets at a single input port, identifies the destination address from the packet, and forwards the packet to one of three output ports. The router architecture uses multiple submodules to ensure efficient, reliable, and synchronized data handling.

The Router 1x3 handles data packets by reading the input stream, decoding the destination address, buffering the packets in FIFOs associated with each output port, and forwarding the packets when the downstream modules are ready. It uses parity checking for error detection and a finite state machine (FSM) to control the packet processing flow.


## Submodule Descriptions

### 1. FIFO Buffers (fifo0, fifo1, fifo2)

Each output port has its own FIFO buffer to temporarily store packets before transmission. These buffers manage data rate mismatches between input and output ports, prevent data loss during high traffic, and enable smooth flow control.

* **Purpose:** Temporarily store valid data packets addressed to their respective ports.
* **Operation:** Packets are written into the FIFO when they arrive and are validated. Packets are read out when the corresponding output port signals readiness.
* **Size:** Each FIFO has a capacity of 8 packets (depth 8).

### 2. Register

The Register module stores the currently received packet during the decoding phase.

* **Purpose:** Holds the incoming packet data temporarily for processing and address decoding.
* **Operation:** Loads packet data on the input when the packet is valid, enabling the FSM and other logic to inspect packet fields.

### 3. Finite State Machine (FSM) Controller

The FSM governs the entire packet processing flow, coordinating between data input, address decoding, FIFO writing, and output signaling.

* **Purpose:** Controls the router’s behavior in different states such as idle, receiving, decoding, writing to FIFO, and waiting for output read.
* **Operation:** Transitions between states based on input signals, packet validity, and FIFO status signals.
* **Benefits:** Ensures orderly processing and prevents data loss or corruption.

### 4. Synchronizer

The Synchronizer handles the timing coordination between asynchronous signals from different clock domains or external modules.

* **Purpose:** Eliminates metastability issues by synchronizing incoming asynchronous signals to the router’s clock domain.
* **Operation:** Uses flip-flops to stabilize signals, ensuring reliable signal transitions within the router.


## Additional Features

* **Parity Checker:** The router includes a parity check mechanism to detect errors in incoming packets. Packets failing the parity check are discarded, ensuring only valid data is forwarded.
* **Signal-based Flow Control:** Write and read enable signals control packet data transfer into and out of FIFOs, ensuring data integrity and proper timing.


## Summary

This 1x3 Router design integrates FIFO buffers, registers, FSM control, and synchronization mechanisms to provide a robust packet routing system. The modular design makes it easy to scale or adapt for larger router architectures. This project is an excellent example of combining finite state machines with data buffering and synchronization techniques for digital communication hardware design.

