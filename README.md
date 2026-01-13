# Operation Skywatch – OS Scheduler Simulation

## 📌 Course Information

**Course:** Operating Systems (CS-2006)
**Assignment:** Assignment 02 – Processes, Threads & Synchronization
**Project Title:** Operation Skywatch – The Air Traffic Scheduler

---

## 🛰️ Project Overview

Operation Skywatch is a **C/C++ based Operating Systems simulation** that models an **Air Traffic Control (ATC) scheduler** using core OS concepts. The project demonstrates how **processes, threads, synchronization, inter-process communication (IPC), and scheduling algorithms** work together in a real-time system.

The simulation implements a **three-level Multi-Level Feedback Queue (MLFQ)** scheduler with:

* **Queue 1:** Shortest Remaining Time First (SRTF)
* **Queue 2:** Round Robin (RR)
* **Queue 3:** First Come First Served (FCFS)

Jets are simulated as processes competing for a shared runway resource, while the ATC tower manages scheduling, preemption, and synchronization.

---

## 🎯 Learning Objectives

This project was designed to practically demonstrate:

* Process creation using `fork()`
* Multithreading using `pthread`
* Mutexes and condition variables
* Preemptive and non-preemptive scheduling
* Inter-process communication using pipes
* Starvation prevention using aging
* Real-time scheduling decisions
* Concurrent system design and synchronization

---

## 🧩 System Architecture

### Main Components

* **ATC Tower (Main Process):**

  * Manages MLFQ scheduling
  * Controls runway access
  * Handles IPC with jets and generator

* **Jet Generator (Child Process):**

  * Randomly generates jet processes
  * Sends arrival information to ATC via pipe

* **Jet Processes:**

  * Each jet is a separate process
  * Contains internal threads (fuel monitoring, status updates)
  * Communicates with ATC using pipes

* **ATC Display Thread:**

  * Displays real-time queue status and runway usage

---

## ⚙️ Scheduling Policies

### Queue 1 – Emergency Queue (SRTF)

* Highest priority
* Preemptive scheduling
* Jets with the lowest remaining fuel are prioritized
* Emergency jets from lower queues are promoted here

### Queue 2 – Standard Operations (Round Robin)

* Medium priority
* Time quantum based scheduling
* Jets exceeding quantum are demoted to Queue 3

### Queue 3 – Standby / Refueling (FCFS)

* Lowest priority
* Aging mechanism prevents starvation
* Long-waiting jets are promoted back to Queue 2

---

## 🔁 Inter-Process Communication

* Pipes are used for communication between:

  * ATC Tower ↔ Jet Generator
  * ATC Tower ↔ Individual Jet Processes
* Mutexes protect shared resources
* Condition variables ensure correct execution order

---

## 🖥️ Interactive Console Commands

The simulation supports real-time interaction:

| Command                          | Description                        |
| -------------------------------- | ---------------------------------- |
| `force_emergency <PID>`          | Immediately moves a jet to Queue 1 |
| `new_jet <TYPE>`                 | Generates a new jet                |
| `change_quantum <Q_NUM> <VALUE>` | Updates time quantum               |
| `boost_priority <PID>`           | Promotes a jet                     |
| `pause_sim / resume_sim`         | Pauses or resumes simulation       |
| `status`                         | Displays current queues            |
| `exit`                           | Gracefully terminates simulation   |

---

## 📁 Project Structure

```
22i-XXXX_ChronoArena/
│── main.cpp
│── scheduler.cpp
│── drone.cpp
│── utils.h
│── rollno_skywatch_log.txt
│── rollno_Report.pdf
│── ReadMe.txt
```

---

## 🛠️ Compilation & Execution

### Compile

```bash
g++ main.cpp scheduler.cpp drone.cpp -o skywatch -pthread
```

### Run

```bash
./skywatch
```

---

## 📊 Outputs

* **Live Radar Display:** Real-time runway and queue status
* **Log File:** Context switches, scheduling events, emergencies
* **Monitoring Output:** CPU usage, waiting time, turnaround time
* **Final Report:** Performance metrics and screenshots

---

## 🔐 Determinism & Roll Number Seed

Randomization (arrival time, fuel, I/O waits) is seeded using the **student roll number**, ensuring:

* Unique output per student
* Reproducibility during demo

Each jet logs its activity with a **UAV tag containing the roll number**.

---

## 🧠 Key Takeaways

* Reinforced understanding of **concurrency and synchronization**
* Hands-on experience with **real OS scheduling policies**
* Improved confidence in **explaining and modifying live systems**

---

## 👤 Author

**Name:** Laiba Nasir
**Course:** BS Computer Science
**Project:** CS-2006 Assignment 02 – Operation Skywatch

---

> ⚠️ This project was developed strictly following academic integrity guidelines. The logic, structure, and implementation are original and intended for educational purpos

