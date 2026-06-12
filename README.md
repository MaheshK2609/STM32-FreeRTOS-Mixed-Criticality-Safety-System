# STM32 FreeRTOS Mixed-Criticality Smart Vehicle Safety System
Overview

This project implements a Mixed-Criticality Real-Time Vehicle Safety System on the STM32F4 Nucleo board using FreeRTOS (CMSIS-RTOS v2).

The system continuously monitors obstacles using an IR sensor and guarantees deterministic safety response through priority-based scheduling. Under high CPU load conditions, the system automatically enters Critical Mode and suspends non-essential tasks to preserve safety-critical functionality.

Features
Priority-based FreeRTOS scheduling
Mixed-Criticality task management
Dynamic task creation using osThreadNew()
Runtime task suspension using osThreadSuspend()
Event Flag based inter-task communication
Mutex protected UART logging
CPU load monitoring using Idle Hook
Stress test task for overload simulation
Obstacle detection and emergency braking
Critical mode activation above 80% CPU utilization

Hardware Used
Component	Purpose
STM32F4 Nucleo	Main Controller
IR Sensor	Obstacle Detection
DC Motor	Vehicle Motion
Buzzer	Alert System
User Button (PC13)	Stress Task Trigger
UART2	Debug Output

Task Architecture
Task	Priority	Period
BreakTask	High	50 ms
IRSensorTask	AboveNormal	50 ms
MonitorTask	Normal2	1000 ms
LoggingTask	Low7	1000 ms
StressTask	AboveNormal	Runtime

These tasks were implemented using CMSIS-RTOS v2 APIs.

- Preemptive Scheduling
- Rate Monotonic Scheduling (RMS)
- Event Flags
- Mutexes
- Dynamic Task Creation
- ISR-to-Task Communication
- CPU Load Monitoring
- Mixed-Criticality Scheduling
- Deterministic Timing

These concepts are explicitly implemented and documented in the project.

Critical Mode Operation

When CPU load exceeds 80%:
- LoggingTask is suspended
- LED status indication replaces UART logging
- Safety-critical tasks continue executing
- Obstacle detection remains active
- Braking response remains within 50 ms

This adaptive behavior ensures system reliability under overload conditions.

Key Learning Outcomes
- FreeRTOS Task Scheduling
- Real-Time Embedded System Design
- Inter-Task Communication
- STM32 Peripheral Programming
- Mixed-Criticality Systems
- Embedded Performance Optimization
- Safety-Critical Firmware Design
