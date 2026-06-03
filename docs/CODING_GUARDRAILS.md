# Coding Guardrails for All Members and Coding Agents

This file is the single source of truth for the project. Every teammate and coding agent must follow it.

## 1. Project goal
Build a small web application that simulates an online examination server and demonstrates CPU scheduling.

The application must compare:
- a naive sequential mode
- Round Robin scheduling

## 2. Do not change the core concept
The app is a scheduling simulator inside an exam portal theme.

Do not turn it into:
- a full exam website
- a login/authentication system
- a database-heavy product
- a generic dashboard with no OS explanation

## 3. Shared business meaning
The same terms must be used everywhere.

| Concept | Meaning |
|---|---|
| Student request | Process |
| Server CPU | CPU |
| Request list | Ready queue |
| Time quantum | Time slice |
| Burst time | CPU time needed |
| Waiting time | Time spent in queue |
| Turnaround time | Total time to finish |

## 4. Shared data model
Every module must use the same request object.

Required fields:
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

Do not rename these fields in different modules.

## 5. Shared output contract
The scheduler must return a structure that contains:
- final request list
- execution log
- gantt timeline
- average waiting time
- average turnaround time
- comparison mode name

## 6. UI rules
The interface should look like a real portal:
- top title bar
- summary cards
- request table
- action buttons
- live queue area
- execution log
- results panel
- comparison chart

Do not make the UI plain or empty.

## 7. Algorithm rules
Round Robin must:
- use a fixed quantum
- rotate unfinished requests to the end of the queue
- update remaining time after each slice
- stop only when all requests finish

Sequential mode must:
- process requests one by one
- not use quantum rotation
- act as the baseline comparison

## 8. Integration rules
Use the same request structure from start to finish.

Frontend must send:
- student_name
- request_type
- arrival_time
- burst_time

Backend must respond with:
- scheduling results
- statistics
- timeline

Do not build isolated modules that cannot be connected later.

## 9. Naming rules
Use clear names like:
- request
- queue
- scheduler
- execution_log
- gantt_chart
- waiting_time
- turnaround_time

Avoid unclear names like:
- x1
- data2
- tempStuff
- test123

## 10. Styling rules
Use simple, clean, academic styling:
- readable fonts
- consistent spacing
- clear buttons
- visible table headers
- no unnecessary animations
- no clutter

## 11. Programming rules
Each module must be small and testable.
Write comments for:
- scheduling steps
- calculations
- integration points

Avoid mixing UI code and scheduling logic in the same place.

## 12. Testing rules
Test with:
- 3 requests
- 5 requests
- 10 requests
- same burst times
- different burst times
- different quantum values

Check that:
- waiting time is correct
- turnaround time is correct
- the queue rotates correctly
- the output matches the timeline

## 13. Demo rules
During presentation, show:
1. generated requests
2. sequential baseline
3. Round Robin execution
4. comparison results
5. final conclusion

## 14. Definition of done
The project is complete only when:
- the UI works
- requests can be generated
- both modes run correctly
- statistics are shown
- integration is successful
- the whole app runs from one start screen

## 15. Forbidden shortcuts
Do not:
- hardcode final outputs
- skip the queue logic
- fake the statistics
- hide the baseline comparison
- submit modules that never connect

## 16. Final reminder
Keep the project simple, consistent, and integrated.
Every member must use this file as the common rulebook.
