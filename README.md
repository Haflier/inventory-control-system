# Inventory Control System Simulation using Arena

> **A Discrete-Event Simulation of an (s, S) Inventory Policy with Parameter Optimization using Rockwell Arena**

![Arena](screenshots/arena_model.png)

---

## Overview

This project presents a **Discrete Event Simulation (DES)** of a single-item inventory control system developed using **Rockwell Arena Simulation**. The objective is to analyze and optimize an **(s, S) inventory replenishment policy** under stochastic customer demand.

The simulation models customer arrivals, random demand sizes, inventory replenishment, supplier lead times, holding costs, ordering costs, lost sales, and revenue generation. Arena's **Process Analyzer (PAN)** is used to perform sensitivity analysis and determine the optimal inventory policy parameters that maximize profit while minimizing total operating cost.

---

## Features

* Discrete Event Simulation using Arena
* (s, S) Inventory Control Policy
* Random customer arrivals
* Random customer demand
* Supplier lead time
* Lost sales tracking
* Partial order fulfillment
* Automatic inventory replenishment
* Daily holding cost calculation
* Financial performance monitoring
* Process Analyzer optimization
* Interactive simulation dashboard

---

## Problem Description

A retail store sells a single product with uncertain customer demand.

Customers arrive according to a stochastic process and request a random number of units. If sufficient inventory exists, the demand is completely satisfied. Otherwise, all available inventory is sold and the remaining demand is recorded as **Lost Sales**.

Whenever the inventory level falls below a predefined reorder point **s**, a replenishment order is automatically placed.

The ordered quantity is:

`OrderSize = S - Inventory`

where

* **Inventory** = Current Inventory
* **s** = Reorder Point
* **S** = Order-up-to Level
* **OrderSize** = amount of order

The order arrives after a supplier lead time **L**.

The simulation evaluates the operational and financial performance of this inventory policy over a one-year planning horizon.

---

# Inventory Policy

The simulation implements the classical continuous review inventory policy.

If

`Inventory < s`

then

`OrderSize = S-Inventory`

Otherwise,

No order is placed.

---

# Initial Parameters

| Parameter                 | Value            |
| ------------------------- | ---------------- |
| Selling Price (r)         | 5                |
| Purchase Cost (c)         | 3                |
| Initial Inventory         | 50 units         |
| Order-up-to Level (S)     | 60               |
| Reorder Point (s)         | 24               |
| Lead Time (L)             | 1 day            |
| Holding Cost              | 0.1 per unit/day |
| Customer Arrival Rate (λ) | 2                |
| Simulation Length         | 365 days         |

---

# Stochastic Assumptions

### Customer Arrivals

Customer arrivals follow a **Poisson process**

**Arrival Process:** `N(t) ~ Poisson(λ)`

where

**Arrival Rate:** `λ = 2`

---

### Demand Size

Each customer's demand is randomly generated using

**Demand Distribution:** `Uniform(8, 23)`

---

### Supplier Lead Time

The replenishment lead time is assumed to be deterministic

**Lead Time:** `L = 1 day`

---

# Event Scheduling Logic

The simulation operates using the Event Scheduling approach.

The primary events are:

1. Customer Arrival
2. Demand Generation
3. Inventory Availability Check
4. Complete Sale
5. Partial Sale
6. Lost Sale
7. Inventory Reorder
8. Order Arrival
9. Daily Holding Cost Calculation
10. End of Simulation

---

# Arena Model

The Arena model contains the following major modules:

* Create
* Assign
* Decide
* Separate
* Delay
* Dispose

The model manages customer arrivals, inventory transactions, replenishment orders, and financial updates while continuously recording system performance.

---

# Performance Metrics

The following Key Performance Indicators (KPIs) are collected throughout the simulation.

* Inventory Level
* Total Earn
* Budget
* Holding Cost
* Ordering Cost
* Total Cost
* Lost Sales
* Partial Sales
* Number of Orders
* Order Size
* Profit

---

# Simulation Dashboard

The simulation includes an interactive dashboard displaying:

* Real-time inventory level
* Inventory history
* Budget trend
* Cost vs. Revenue
* Lost sales counter

This visualization enables immediate monitoring of system behavior during execution.

---

# Process Analyzer Experiments

Arena Process Analyzer was used to perform sensitivity analysis on the inventory policy.

The following parameters were varied:

* Reorder Point (s)
* Order-up-to Level (S)
* Supplier Lead Time (L)

For each scenario, the following outputs were evaluated:

* Total Revenue
* Total Cost
* Budget
* Lost Sales
* Holding Cost
* Ordering Cost

---

# Optimization Results

## Effect of Order-up-to Level (S)

Increasing **S** generally reduced lost sales by maintaining higher inventory availability.

However, excessively large inventory levels significantly increased holding costs.

Simulation results indicated that the best overall performance occurred approximately within

`S ≈ 51`

with

`s ≈ 22`

providing the highest net profit under the modeled assumptions.

---

## Effect of Lead Time

Lead time had a strong influence on system performance.

As lead time increased:

* Lost sales increased.
* Total revenue decreased.
* Total inventory declined.
* Profit decreased.
* Customer service level deteriorated.

Reducing supplier lead time produced substantial improvements in overall inventory performance.

---

# Results

The simulation successfully demonstrates the trade-off between:

* Inventory holding cost
* Ordering cost
* Customer service level
* Lost sales
* Profitability

The experiments show that selecting appropriate values for **s** and **S** is critical to achieving an optimal balance between inventory investment and customer satisfaction.

---

# Repository Structure

```text
inventory-control-arena/

│
├── ArenaModel/
│   ├── Inventory.doe
│   ├── Inventory.mdb
│   ├── Inventory.opw
│   └── Inventory.out
│
├── screenshots/
│   ├── arena_model.png
│   ├── dashboard.jpg
│   ├── process_analyzer_S.jpg
│   └── process_analyzer_L.jpg
│
├── docs/
│   ├── Project_Report.pdf
│
│
├── README.md
└── LICENSE
```

---

# Technologies Used

* Rockwell Arena Simulation
* Arena Process Analyzer (PAN)
* Discrete Event Simulation (DES)
* Event Scheduling Method
* Inventory Theory
* Operations Research
* Draw.io (Flowchart)

---

# Screenshots

| Arena Model                      | Dashboard                      |
| -------------------------------- | ------------------------------ |
| ![](screenshots/flowchart.png) | ![](screenshots/arena_model.jpg) |

| Parameter Optimization                  | Lead Time Analysis                      |
| --------------------------------------- | --------------------------------------- |
| ![](screenshots/process_analyzer_S.jpg) | ![](screenshots/process_analyzer_L.jpg) |

---

# Project Highlights

* Developed a complete **Discrete Event Simulation** using Rockwell Arena.
* Implemented an **(s, S)** inventory control policy.
* Modeled stochastic customer arrivals and demand.
* Evaluated financial and operational KPIs.
* Performed simulation-based optimization using Arena Process Analyzer.
* Identified near-optimal inventory policy parameters through sensitivity analysis.
