# Backend and Scheduler Specification

## Purpose
This module contains the operating system logic.

## Core objects
### Request
A student request that behaves like a process.

Fields:
- id
- student_name
- request_type
- arrival_time
- burst_time
- remaining_time
- start_time
- completion_time
- waiting_time
- turnaround_time

## Sequential baseline
This mode processes each request fully before moving to the next.

Use it to show the problem:
- later requests wait longer
- fairness is poor

## Round Robin
Rules:
- each request receives a fixed quantum
- if remaining time is greater than quantum, reduce it
- place it at the end of the queue
- continue until all requests complete

## Statistics formulas
### Waiting time
`waiting_time = turnaround_time - burst_time`

### Turnaround time
`turnaround_time = completion_time - arrival_time`

### Response time
`response_time = first_start_time - arrival_time`

## Output
Return:
- execution log
- Gantt timeline
- completion details
- averages

## Implementation note
Keep the scheduling logic independent from the user interface.
That makes integration easier and testing cleaner.
