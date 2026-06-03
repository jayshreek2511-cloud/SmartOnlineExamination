# Team Division and Module Plan

## Team size
4 members

## Goal
Each member builds a clear part of the same application so that the project can be integrated at the end.

---

## Member 1 - UI and Layout

### Role
Build the visual structure of the portal.

### Tasks
- create the page layout
- add title and header
- create summary cards
- build the request table
- create buttons and sections
- make the page look like a real portal

### Outputs
- `index.html`
- `style.css`
- portal shell layout

### Needs from others
- request data format from Member 2
- result format from Member 3 and Member 4

---

## Member 2 - Request Generator and Data Model

### Role
Create the student request data and input logic.

### Tasks
- define the request object
- generate sample student requests
- accept manual input
- validate request fields
- send queue data to the scheduler

### Outputs
- `models.py` or equivalent
- request generator logic
- input validation logic

### Needs from others
- UI form structure from Member 1
- scheduler output contract from Member 3

---

## Member 3 - Scheduling Engine

### Role
Implement the OS logic.

### Tasks
- build baseline sequential mode
- build Round Robin scheduler
- rotate the queue
- update remaining time
- calculate completion details

### Outputs
- `scheduler.py`
- algorithm log
- queue execution data

### Needs from others
- fixed request object from Member 2
- quantum value from UI or settings

---

## Member 4 - Statistics and Visualization

### Role
Convert the algorithm result into meaningful outputs.

### Tasks
- calculate waiting time
- calculate turnaround time
- calculate averages
- build Gantt chart
- create comparison view
- create final summary panel

### Outputs
- `statistics.py`
- chart logic
- comparison dashboard

### Needs from others
- execution log and completion times from Member 3

---

## Integration order
1. Member 1 builds UI shell.
2. Member 2 connects request generation.
3. Member 3 connects scheduling logic.
4. Member 4 connects metrics and charts.
5. All members test the integrated app together.

---

## Collaboration rule
No one should invent a different structure for the request object or output format.
Everyone must use the shared guardrails file.
