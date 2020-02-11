# Operating Systems
## OS Domains
- Hardware Resources
- Specific Operating Systems
- Disk I/O
- Disk Scheduling
- File Systems
- CPU Features
- Kernel Architectures
- Interrupts and I/O
- Interrupt Controllers
- Interrupt Handling
- Memory Resources
- Dynamic Memory Allocation
- Kernel Memory Allocation
- Paging
- Page Tables
- Memory Protection
- Virtual Memory
- Page Replacement

## OS Tiers
- T4 Application Layer
  - Aggregations of System Applications
- T3 Application Interface Layer (GCC, Core Utilities, Bash)
  - Compilation
  - System Applications
- T2 Library Layer 
  - Under this purview
    - C Library
    - Kernel APIs
    - Other Libraries
- T1 Hardware Kernel (Interface, Abstraction, Arbitration)
  - I/O Interfacing
  - Drivers and Modules
  - Sockets
  - Protocols
  - File System
  - Memory Management
  - Processes
  - Device Files
- T0 Hardware Layer
  - Under this purview 
    - Decide your GPIO Layout
    - Decide your Communication Interfaces

## Kernel
The kernel is the single most important part of the operating system. 
- Manages Access to the CPU
- Manages Access to Memory
- Manages Access to Disk
- Manages Access to Storage
  - Interrupts
  - Termination
  - Spawning
- Manages Access to Devices
  - Network


## Disk I/O

# Building an Operating System
- Boot instructions need to be available on the boot sector of storage for a boot loader to load.
- Boot loader is in charge of loading the first initial start up instructions into ram. 