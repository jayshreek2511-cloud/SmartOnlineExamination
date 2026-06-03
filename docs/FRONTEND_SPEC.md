# Frontend and UI Specification

## Purpose
Create a portal-like interface that looks realistic and is easy to present.

## Layout sections
### Header
- project title
- subtitle
- small description

### Summary cards
- active students
- queue length
- current mode
- time quantum

### Controls
- generate requests
- run baseline
- run Round Robin
- reset

### Main table
Columns:
- request ID
- student name
- request type
- arrival time
- burst time
- remaining time
- status

### Live panels
- ready queue
- execution log
- Gantt chart
- statistics panel

## UI style
Use:
- simple colors
- clean spacing
- clear table borders
- readable fonts
- button states for actions

## UI behavior
- show generated requests immediately
- update queue during execution
- show final statistics after algorithm run
- allow reset for repeated demo

## Important design rule
The UI should look like a real online examination dashboard, but the purpose is to visualize scheduling, not to implement real exam functionality.
