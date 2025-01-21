# Traffic Light Design for Two Roads

## Objective

The task is to design a solution for a real-world problem: the traffic light system for two intersecting roads. The design should be based on a Finite State Machine (FSM) that controls the traffic lights at the intersection of a highway and a farm road.

## The Task

Design a traffic light controller for the highway and farm road intersection. The traffic light controller outputs four 2-bit signals:

- **Highway Signal 1 (Highway TL1)**
- **Highway Signal 2 (Highway TL2)**
- **Farm Signal 1 (Farm TL1)**
- **Farm Signal 2 (Farm TL2)**

These outputs represent the states of the traffic lights on each road. The following encoding is used for both signals:

- **00**: Green
- **01**: Yellow (when changing from green)
- **10**: Red
- **11**: Red-Yellow (when changing from red)

You can also consider the four outputs as 3-bit signals.

## State Table

Below is the table showing the states of the traffic light system with their corresponding output signals and delay time.

| State | Highway TL1 | Highway TL2 | Farm TL1 | Farm TL2 | Delay (Seconds) |
|-------|-------------|-------------|----------|----------|-----------------|
| S0    | Red         | Red         | Red      | Red      | 1               |
| S1    | Red-Yellow  | Red-Yellow  | Red      | Red      | 2               |
| S2    | Green       | Green       | Red      | Red      | 30              |
| S3    | Green       | Yellow      | Red      | Red      | 2               |
| S4    | Green       | Red         | Red      | Red      | 10              |
| S5    | Yellow      | Red         | Red      | Red      | 2               |
| S6    | Red         | Red         | Red      | Red      | 1               |
| S7    | Red         | Red         | Red-Yellow| Red-Yellow | 2             |
| S8    | Red         | Red         | Green    | Green    | 15              |
| S9    | Red         | Red         | Green    | Yellow   | 2               |
| S10   | Red         | Red         | Green    | Red      | 5               |
| S11   | Red         | Red         | Yellow   | Red-Yellow | 2             |
| S12   | Red         | Red         | Red      | Green    | 10              |
| S13   | Red         | Red         | Red      | Yellow   | 2               |
| S14   | Red         | Red         | Red      | Red      | 1               |
| S15   | Red         | Red-Yellow  | Red      | Red      | 2               |
| S16   | Red         | Green       | Red      | Red      | 15              |
| S17   | Red         | Yellow      | Red      | Red      | 3               |

## Description of Signals

### Inputs
- **Rst**: Resets the design to state 0 and counter to 0.
- **Go**: Defaults to 1 for state transitions. When forced to 0, it freezes the counter.
- **clk**: Synchronous clock signal.

## System Description

The system operates as a finite state machine, where the state transitions are determined by the input signals (**Rst**, **Go**, **clk**). Each state has a corresponding output for the traffic light signals, and a delay is specified for each state.

## Testbench

After designing the system, you need to build a simple testbench that implements tests for all states to ensure that the design works as expected.

## Format of the Report

The project should be submitted in the form of a formal report with the following sections:

1. **Brief Introduction and Background**: Overview of the project and its importance.
2. **Design Philosophy**: Explanation of the design approach, including FSM states and transition logic.
3. **Results**: Summary of simulation results, including outputs for all states.
4. **Conclusion and Future Works**: Final thoughts on the design and potential improvements.
