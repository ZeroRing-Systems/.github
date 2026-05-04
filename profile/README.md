# ⚡ ZeroRing-Systems

Welcome to the official organization profile for **Project ZeroRing**, an experimental systems architecture R&D initiative. 

### 🪐 The Mission
We are engineering a highly experimental **Cloud-Backed WebAssembly (WASM) Operating System**. 

The goal of this architecture is to bridge bare-metal systems programming with modern web infrastructure. We are tricking the browser's V8 execution engine into acting as a bare-metal CPU and RAM, while offloading all hardware-level system calls (file I/O, networking) to a persistent C++ cloud backend.

### 🏗️ Core Architecture
The ecosystem is strictly decoupled into distinct operational boundaries:

* **[`ZeroKernel`](https://github.com/ZeroRing-Systems/ZeroKernel):** The brain. A pure, freestanding C++ OS kernel. It is compiled entirely to WebAssembly and contains zero browser-specific dependencies or standard library calls.
* **[`ZeroRing-Cloud`](https://github.com/ZeroRing-Systems/ZeroRing-Cloud):** The hardware abstraction. This repository houses both the frontend JavaScript interop bridge (acting as the BIOS/Display) and the C++ WebSocket server (acting as the Hard Drive and Network).

### 🛠️ Tech Stack
* **Kernel Engine:** Pure C++ (Compiled via Emscripten)
* **Backend Server:** C++ (Boost.Beast) / WebSockets
* **Virtual File System:** PostgreSQL 
* **Build System:** CMake

> *"The kernel must never know whether it is running in a browser or on real hardware. That decision lives entirely in the Hardware Abstraction Layer."*
