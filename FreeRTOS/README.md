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
``` cpp
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

## Inter-Task Communication
How to exchange data between tasks, and how to control a shared resource
- Queues
  - Allows to pass more info between the task.
- Semaphores
  - Guard a resource with a limited amount of access.
- Direct to task notifications
  - 
- Mutexes
  - 
- Event Groups

### Queues
#### Queue Create
``` cpp
osMessageQId osMessageCreate( const osMessageQDef_t *queue_def, osThreadId thread_id);
```
- `osMessageQId` is the queue handle returned by the function
- `osMessageCreate` is the create queue function

#### Queue Put
``` cpp
osStatus osMessagePut( osMessageQId queue_id, uint32_t info, uint32_t millisec);
```
- `osMessageQId queue_id` is the queue handle for the data to be placed
- `uint32_t info` is the data to send
- `uint32_t millisec` is the amount of time to wait before timeout.
  
#### Queue Receive
``` cpp
osEvent osMessageGet( osMessageQId queue_id, uint32_t millisec);
```
- `osEvent` is the structure with status and with receive item
- `osMessageQId queue_id` is the queue handle
- `uint32_t millis` is the receiving timeout
  
#### The `osEvent` Structure
``` cpp
typedef struct {
    osStatus status;
    union { 
        uint32_t v;             // message as 32-bit value
        void *p;                // message or mail as void pointer
        int32_t signal;         //signal flags
    } value;                    // event value definition
    union {
        osMailQId mail_id;      //mail id obtained by /ref osMailCreate
        osMessageQId message_id;//message id obtained by /ref osMessageCreate
    } def;                      // event definition
} osEvent;
```
- `osEventName.value.v` if the value is 32Bit message(or 8 or 16bit)
- `osEventName.value.p` if the 

#### Delete the Queue
``` cpp
osStatus osMessageDelete( osMessageQId queue_id);
```
- `osMessageQId queue_id` is the queue handle

#### Peek at an item on the Queue
``` cpp
osEvent osMessagePeek( osMessageQId queueId, uint32_t millisec);
```

#### Get the number of messages stored in a queue
``` cpp
uint32_t osMessageWaitingPeek( osMessageQId queue_id);
```
- `uint32_t` is the number of the messages stored in the queue
- `osMEssageQId queue_id` is the queue handle

#### Get the number of available spaces in the queue
``` cpp
uint32_t osMessageAvailableSpace( osMessageQId queue_id);
```
- `uint32_t` is the number of available spaces left in the queue
- `osMEssageQId queue_id` is the queue handle

