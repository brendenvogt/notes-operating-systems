# FreeRTOS
## Overview
- Operating System: What is it?
- Basic features
- CMSIS_OS API vs FreeRTOS API
- FreeRTOS and STM32CubeMX
- Configuration
- Memory allocation
- Scheduler
- Tasks
- Intertask Communication
  - Queues (Messages, mail)
  - Semaphores (binary, counting)
  - Signals
- Resource Management
- Mutexes
- Software Timers
- Advanced Topics
  - Hooks
  - Stack Overflow Protection
  - Gatekeeper task
- Debugging
- Low Power Support (tickless mode)
- Footprint

## Tasks
``` c++
for (;;) 
{
    /* Task code */
}
```
- What is a task? 
    - It is a unit of runnable code that can either run indefinitely or have an ending point.
- C function
- Should be formatted as an infinite loop 
- Has its own part of the stack and priority
- Has a state:
    - RUNNING
    - BLOCKED
    - SUSPENDED
    - READY
- Created and deleted by calling API functions

## Scheduler
- A scheduler is an algorithm determining which task to execute.
    - It selects one of the tasks being ready to be executed (in READY state)
    - There are a few mechanisms controlling access to CPU for tasks (timeslice, preemption, idle)
- In FreeRTOS round-robin scheduling algorithm is implemented
- Round-robin can be used 
    - Can use a few types of interrupting strategies
        - preemption multitasking
        - cooperation multitasking

