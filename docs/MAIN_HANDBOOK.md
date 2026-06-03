# Smart Online Examination Request Scheduler
## Operating System Case Study and Implementation Handbook

### Project Idea
This project models a real online examination server that receives many student requests at the same time. Instead of building a full exam platform, the application focuses on the OS problem behind the scene: **CPU scheduling**.

We compare two ways of handling requests:

1. **Without scheduling** - requests are handled in the order they arrive, which can lead to long waiting time.
2. **Round Robin scheduling** - each request gets a fixed time quantum, so all requests progress fairly.

The real-world story is an online exam portal, but the actual OS solution is a **scheduler simulator**.

---

## 1. Problem Statement

During an online examination, many students perform actions such as login, loading questions, saving answers, and submitting papers. These actions reach the server simultaneously. A server has limited CPU time, so it cannot serve every request at once.

The OS challenge is to decide:
- which request should run first,
- how long it should run,
- and when it should be paused and moved to the end of the queue.

That is a classic CPU scheduling problem.

---

## 2. Why This is an OS Project

This project is related to Operating System concepts because it directly uses:

- CPU Scheduling
- Process Management
- Ready Queue
- Context Switching
- Time Quantum
- Waiting Time
- Turnaround Time
- Fair Resource Sharing

Each student request is treated as a process. The scheduler acts like the OS scheduler. The CPU is the server processor.

---

## 3. What the Application Should Look Like

The application should feel like a small real exam portal, not like a plain console program.

### Main screen
The user should see:
- a title like **Online Examination Portal**
- a summary bar showing:
  - active students
  - queue length
  - current mode
- buttons:
  - Generate Requests
  - Run Without Scheduling
  - Run FCFS
  - Run Round Robin
  - Reset
- a table showing student requests
- a queue area showing which requests are waiting
- a live execution panel
- a results panel with waiting time and turnaround time
- a comparison chart

### What makes it look legit
- clean layout
- consistent colors
- cards or panels for each section
- table with rows for requests
- live log area
- Gantt chart or timeline
- summary dashboard at the end

The goal is to present a realistic backend scheduling demo inside a simple web app.

---

## 4. Core Story of the Application

The portal does not need to be a full exam platform. It only needs to simulate the request flow of one.

Example request types:
- Login
- Load Question Paper
- Save Answer
- Auto Save
- Submit Exam
- Fetch Score Status

Each request gets:
- student ID
- request type
- arrival time
- burst time
- remaining time

Burst time means the CPU time needed to process that request.

---

## 5. How the Two Modes Work

### Mode A: Without Scheduling
This is the baseline. The application processes requests one by one in strict arrival order.

What happens:
- the first request gets all CPU time until it finishes
- the second request waits
- the third request waits
- and so on

This mode usually produces higher waiting time for later requests.

### Mode B: Round Robin Scheduling
The application gives each request a fixed time slice called the time quantum.

What happens:
- each request gets a small CPU slice
- unfinished requests go back to the end of the queue
- every request makes progress
- no request is ignored for too long

This mode is fair and is the main OS solution.

---

## 6. Example Input

| Student | Request Type | Burst Time |
|---|---:|---:|
| S1 | Login | 4 |
| S2 | Save Answer | 7 |
| S3 | Submit Exam | 2 |
| S4 | Fetch Question | 6 |

If time quantum = 2, then Round Robin will rotate through all requests in small turns.

---

## 7. Example Output to Show the Instructor

### Without scheduling
- S1 finishes first
- S2 waits longer
- S3 waits longer
- S4 waits longer

### With Round Robin
- all requests get turns
- the queue rotates
- each request progresses fairly
- average waiting time is usually reduced

The application should display:
- execution order
- waiting time
- turnaround time
- average waiting time
- average turnaround time

---

## 8. Important OS Terms in Simple Language

### Process
A process is a request being handled by the server.

### Ready Queue
The list of requests waiting to use the CPU.

### Burst Time
How long a request needs the CPU.

### Time Quantum
The maximum time a request can use the CPU in one turn.

### Waiting Time
How long a request spends waiting before it gets CPU time.

### Turnaround Time
Total time from request arrival to completion.

### Context Switching
When the scheduler stops one request and starts another.

---

## 9. Suggested Tech Stack

The project can be built using simple web technologies:

- HTML
- CSS
- JavaScript
- Python for backend logic

### Practical stack options
Option 1:
- Frontend: HTML, CSS, JavaScript
- Backend: Python Flask

Option 2:
- Frontend: HTML, CSS, JavaScript
- Backend: Python FastAPI or Flask

For a classroom project, Flask is simple and easy to integrate.

---

## 10. Recommended Application Architecture

### Frontend
Handles:
- request form
- buttons
- tables
- timeline
- charts
- summary dashboard

### Backend
Handles:
- request generation
- scheduling algorithm
- statistics calculation
- returning results as JSON

### Shared data model
Every part of the app should use the same request structure:

```json
{
  "id": "S1",
  "type": "Login",
  "arrival_time": 0,
  "burst_time": 4,
  "remaining_time": 4,
  "completion_time": null
}
```

---

## 11. Step-by-Step Implementation Plan

### Step 1: Build the UI shell
Create the page layout with:
- title
- control buttons
- request table
- queue display
- log panel
- result panel

### Step 2: Build request generation
Create fake or user-entered student requests and show them in a table.

### Step 3: Build the queue
Store generated requests in an array or queue structure.

### Step 4: Build the baseline mode
Simulate processing without scheduling so the instructor can see the problem clearly.

### Step 5: Build the Round Robin engine
Implement time quantum rotation and queue re-entry for unfinished requests.

### Step 6: Build statistics
Compute waiting time and turnaround time for each request.

### Step 7: Build visualization
Show a Gantt chart or execution strip.

### Step 8: Build comparison
Show FCFS/naive mode vs Round Robin side by side.

### Step 9: Test and polish
Use different inputs and check whether the output stays correct.

---

## 12. What Each Member Should Do

The team has 4 members, so the work should be split in a way that allows clean integration.

### Member 1 - UI and page layout
Responsibilities:
- design the homepage
- create the portal look and feel
- build cards, tables, headers, and buttons
- create the live status panel
- make the app look like a real portal

Deliverables:
- HTML structure
- CSS styling
- responsive layout
- portal branding section

### Member 2 - Request generation and data model
Responsibilities:
- define the request/process object
- generate sample student requests
- manage add/edit/delete request actions
- validate user input

Deliverables:
- request model
- sample data generator
- form submission handling
- queue input logic

### Member 3 - Scheduling engine
Responsibilities:
- implement the baseline sequential mode
- implement Round Robin scheduling
- update remaining time
- compute completion times
- keep the scheduling output correct

Deliverables:
- scheduler module
- queue rotation logic
- algorithm execution log
- JSON results returned to frontend

### Member 4 - Statistics and visualization
Responsibilities:
- calculate waiting time
- calculate turnaround time
- generate Gantt chart/timeline
- render comparison dashboard
- format final summary for demo

Deliverables:
- metrics module
- charts
- result tables
- comparison view
- final conclusion section

---

## 13. Order of Integration

The project should be built in this order so that everyone can integrate smoothly.

### Integration order
1. Member 1 creates the base UI layout.
2. Member 2 connects request generation to the UI.
3. Member 3 connects the scheduling engine to the generated requests.
4. Member 4 connects statistics and charts to the scheduler output.
5. Final integration testing is done on the full flow.

### Why this order matters
If the UI is built first, everyone knows where their module will connect.
If the data model is fixed early, all members can code consistently.
If the scheduler contract is fixed early, there will be fewer integration errors.

---

## 14. How the Final Demonstration Should Work

### Demo flow
1. Open the application.
2. Generate 10 or more student requests.
3. Show the queue and the portal style UI.
4. Run the baseline mode.
5. Observe long waiting time in the output.
6. Reset and run Round Robin.
7. Observe the rotating queue.
8. Show reduced waiting time and fair progress.
9. Display final comparison results.

This gives the instructor both:
- the real-world case study
- the OS solution
- the implementation evidence

---

## 15. Final Evaluation Points

The instructor should be able to see:

- a real-world problem
- a correct OS concept
- a working algorithm
- a readable UI
- a comparison between two methods
- clear results
- teamwork and integration

That is what makes this project strong.

---

## 16. Expected Conclusion

This project proves that an online examination portal can be modeled as an OS scheduling problem. Requests are handled fairly using Round Robin. The demo shows why a simple sequential approach is weaker and how scheduling improves responsiveness and fairness.

---

## 17. Suggested File Structure

```text
project/
  app/
    __init__.py
    routes.py
    scheduler.py
    statistics.py
    models.py
  templates/
    index.html
  static/
    css/
      style.css
    js/
      app.js
  docs/
    PROJECT_BRIEF.md
    CODING_GUARDRAILS.md
    TEAM_DIVISION.md
    INTEGRATION_PLAN.md
```

---

## 18. Final Note
Keep the project simple, visual, and consistent. The aim is not to build a full exam platform. The aim is to show how OS scheduling solves a realistic resource-sharing problem.
