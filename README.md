# Circular-Linked-List-Simulaation

# Delivery Pipeline Simulation Using Circular Linked List (C Language)

This repository contains a complete event-driven simulation of an **order delivery pipeline** implemented using a **Circular Linked List (CLL)**.  
The system models multiple lifecycle stages of each order — from placement to final delivery — while supporting express/normal priority ordering, cancellations, and statistical analysis.

The program simulates order movement through these stages:

- **PLACED → PACKED → DISPATCHED → OUT_FOR_DELIVERY → DELIVERED**

All active orders are stored inside a **Circular Linked List**, enabling continuous rotation through processing without needing array-based queues.

---

### **1. Circular Linked List Implementation**
The code defines two main structures:

- `Order` — Represents an individual order (ID, express flag, stage, arrival time, next pointer)
- `Ring` — Represents the circular linked list of active orders

Operations implemented:
- Insert at tail (normal orders)
- Insert after head (express orders get priority)
- Remove node with pointer adjustment
- Maintain head pointer & ring size

---

##  Simulation Model

### **Event Types**
The simulation processes:
- **Order Arrivals** (user-defined arrival times)
- **Stage Transitions** (using exponential service times)
- **Random Cancellations**
- **Delivery Completion**
- **Periodic Queue Sampling**

Arrival times and express flags are entered by the user and internally sorted to create proper event sequences.

### **Service Time Model**
Each stage uses an exponential service time:

| Stage        | Service Rate |
|--------------|--------------|
| PLACED       | `RATE_PLACED`  
| PACKED       | `RATE_PACKED`  
| DISPATCHED   | `RATE_DISPATCH`  
| OUT_FOR_DELIVERY | `RATE_OUTFOR`  

Random generation uses:
```c
double expo(double mean);

