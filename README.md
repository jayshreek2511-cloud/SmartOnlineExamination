# Smart Online Examination Request Scheduler

An Operating Systems lab project that models a real-world online examination 
server as a CPU scheduling problem. Instead of building a full exam platform, 
this application focuses on the OS concept behind the scene — how a server 
decides which student request to process, for how long, and in what order.

---

## What This Project Does

During an online exam, hundreds of students send requests simultaneously — 
login, load questions, save answers, submit papers. The server cannot handle 
all of them at once. This project simulates how an OS scheduler manages that 
problem fairly and efficiently.

Two scheduling modes are compared side by side:

- **FCFS (First Come First Serve)** — requests are processed one by one in 
  arrival order. Simple, but unfair. Later requests wait too long.
- **Round Robin** — each request gets a fixed time quantum. Unfinished 
  requests rotate to the end of the queue. Every request makes progress. 
  Waiting time is reduced.

---

## Features

- Generate random student requests with customizable count
- Run FCFS baseline and observe poor waiting times
- Run Round Robin with adjustable time quantum
- Live Ready Queue panel showing rotation in real time
- Timestamped Execution Log with color-coded events
- Gantt Chart showing the full execution timeline
- Performance Comparison table — avg waiting time, turnaround time, 
  CPU utilization, throughput
- Waiting Time bar chart comparing both algorithms per student
- Reset and re-run for repeated demonstration

---

## OS Concepts Demonstrated

| Concept | How It Appears in This Project |
|---|---|
| Process | Each student request |
| CPU | The exam server processor |
| Ready Queue | List of requests waiting to run |
| Burst Time | CPU time needed per request |
| Time Quantum | Fixed slice given to each request in RR |
| Waiting Time | Time spent in queue before execution |
| Turnaround Time | Total time from arrival to completion |
| Context Switch | Moving from one request to the next |

---

## Tech Stack

- HTML — page structure
- CSS — portal styling and layout
- JavaScript — scheduling logic, DOM updates, chart rendering
- Chart.js — bar chart for waiting time comparison

No frameworks. No build tools. Open index.html and it runs.

---

## How to Run

1. Clone the repository
2. Open index.html in any browser
3. Click Generate Requests
4. Click Run FCFS to see the baseline
5. Click Reset
6. Click Run Round Robin to see the improvement
7. Compare results in the dashboard

---


