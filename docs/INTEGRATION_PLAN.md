# Integration Plan

This document explains how the separate parts should connect.

## Flow
1. User opens portal.
2. User generates requests.
3. Requests are stored in the shared request list.
4. User clicks Baseline or Round Robin.
5. Backend runs the chosen scheduler.
6. Backend returns execution details.
7. Frontend renders the table, log, and chart.
8. Frontend shows final comparison results.

## Required API-style data flow
Even if the app is small, use a clean structure like this:

### Input
```json
{
  "requests": [
    {
      "id": "S1",
      "student_name": "Student 1",
      "request_type": "Login",
      "arrival_time": 0,
      "burst_time": 4
    }
  ],
  "quantum": 2,
  "mode": "round_robin"
}
```

### Output
```json
{
  "mode": "round_robin",
  "execution_log": [],
  "timeline": [],
  "statistics": {
    "average_waiting_time": 0,
    "average_turnaround_time": 0
  },
  "requests": []
}
```

## Integration checkpoints
- checkpoint 1: UI renders correctly
- checkpoint 2: request generation works
- checkpoint 3: sequential mode works
- checkpoint 4: Round Robin works
- checkpoint 5: charts render
- checkpoint 6: final demo works end-to-end

## Common problems to avoid
- different field names in different files
- hardcoded charts that do not match data
- scheduler logic that the UI cannot read
- missing quantum input
- incomplete final results

## Final acceptance test
The application is accepted only if a user can:
- open the portal
- generate requests
- run both modes
- see correct outputs
- compare results
- understand why Round Robin is better
