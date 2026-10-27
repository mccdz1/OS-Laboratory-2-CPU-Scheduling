# BCA151 Operating Systems Laboratory
## Lab Activity 2: CPU Scheduling Algorithms Simulator

This repository contains the Python implementation and experimental evaluation of five fundamental CPU scheduling algorithms for **BCA151 Operating Systems Laboratory Activity 2**.

---

## 📌 Implemented Algorithms
1. **First-Come, First-Served (FCFS)** — Non-preemptive scheduling based strictly on arrival time with PID tie-breaking.
2. **Shortest Job First (SJF)** — Non-preemptive scheduling prioritizing processes with the smallest burst time.
3. **Priority Scheduling** — Non-preemptive scheduling where lower numerical values represent higher process priority.
4. **Round Robin (RR)** — Preemptive scheduling utilizing a circular queue with a configurable time quantum ($q = 2\text{ ms}$).
5. **Shortest Remaining Time First (SRTF)** — Preemptive SJF that dynamically preempts running processes upon arrival of shorter tasks.

---

## 📊 Datasets

### 1. Standard Dataset
*(Used for FCFS, SJF, Priority Scheduling, and Round Robin)*
| Process | Arrival Time (AT) | Burst Time (BT) | Priority |
| :---: | :---: | :---: | :---: |
| **P1** | 0 ms | 8 ms | 2 |
| **P2** | 0 ms | 4 ms | 1 (Highest) |
| **P3** | 0 ms | 2 ms | 4 (Lowest) |
| **P4** | 0 ms | 6 ms | 3 |

### 2. Separate SRTF Dataset
*(Used to demonstrate preemption meaningfully with staggered arrival times)*
| Process | Arrival Time (AT) | Burst Time (BT) | Priority |
| :---: | :---: | :---: | :---: |
| **P1** | 0 ms | 8 ms | 2 |
| **P2** | 1 ms | 4 ms | 1 |
| **P3** | 2 ms | 2 ms | 4 |
| **P4** | 3 ms | 1 ms | 3 |

---

## 🚀 How to Run the Simulator

### In GitHub Codespaces or Terminal
1. Open the repository in **GitHub Codespaces** or your local terminal.
2. Execute the simulator script:
   ```bash
   python3 cpu_scheduling.py
   ```
   *(Or on Windows PowerShell: `python cpu_scheduling.py`)*

---

## 📈 Reference Output & Verification

| Algorithm | Execution Order | Average Waiting Time ($WT$) | Average Turnaround Time ($TAT$) | Average Response Time ($RT$) |
| :--- | :--- | :---: | :---: | :---: |
| **FCFS** | $P_1 \to P_2 \to P_3 \to P_4$ | 8.50 ms | 13.50 ms | 8.50 ms |
| **Non-Preemptive SJF** | $P_3 \to P_2 \to P_4 \to P_1$ | 5.00 ms | 10.00 ms | 5.00 ms |
| **Non-Preemptive Priority** | $P_2 \to P_1 \to P_4 \to P_3$ | 8.50 ms | 13.50 ms | 8.50 ms |
| **Round Robin ($q = 2\text{ ms}$)** | $P_1 \to P_2 \to P_3 \to P_4 \to P_1 \dots$ | 9.00 ms | 14.00 ms | 3.00 ms |
| **SRTF (Preemptive)** | $P_1 \to P_2 \to P_3 \to P_4 \to P_2 \to P_1$ | 2.75 ms | 6.50 ms | 0.25 ms |

---

## 📐 Formulas Used
* **Turnaround Time ($TAT$)**: $\text{Completion Time (CT)} - \text{Arrival Time (AT)}$
* **Waiting Time ($WT$)**: $\text{Turnaround Time (TAT)} - \text{Burst Time (BT)}$
* **Response Time ($RT$)**: $\text{First CPU Start Time} - \text{Arrival Time (AT)}$
