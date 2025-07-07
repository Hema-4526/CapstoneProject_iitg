# CapstoneProject_iitg

# 🚗 Dynamic Pricing for Urban Parking Lots

**Capstone Project – Summer Analytics 2025**  
Hosted by Consulting & Analytics Club × Pathway

---

## 📌 Overview

Urban parking spaces are a limited and highly demanded resource. Fixed pricing strategies often lead to inefficiencies such as over-utilization or underutilization of parking lots. This project aims to implement **real-time dynamic pricing models** using data-driven techniques, demand-based logic, and competition-based adjustments to optimize the pricing of 14 urban parking lots.

---

## 🧠 Problem Statement

To build a real-time pricing engine that updates the parking prices based on:
- Historical occupancy patterns
- Queue length
- Nearby traffic congestion
- Special events
- Vehicle type
- Competitor pricing (optional)

---

## 🔧 Tech Stack

| Layer         | Technology                     |
|--------------|---------------------------------|
| Language      | Python                         |
| Libraries     | Pandas, NumPy, Bokeh           |
| Streaming     | Pathway                        |
| IDE           | Google Colab                   |
| Visualization | Bokeh                          |
| Version Control | Git, GitHub                  |

---

## 📊 Models Implemented

### ✅ Model 1: Baseline Linear Pricing  
Price increases linearly based on occupancy level.

Formula:  
Price_{t+1} = Price_t + α × (Occupancy / Capacity)

---

### ✅ Model 2: Demand-Based Pricing  
Demand is calculated based on multiple real-time parameters:
Demand = α × (Occupancy / Capacity) + β × QueueLength − γ × TrafficScore + δ × IsSpecialDay + ε × VehicleTypeWeight
Price_t = BasePrice × (1 + λ × NormalizedDemand)

---

### ✅ Model 3: Competitive Pricing (Optional)  
Uses spatial information (latitude, longitude) to adjust price based on competitor lots nearby.

- Increases price if nearby lots are expensive.
- Decreases price or reroutes vehicles if nearby lots are cheaper and own lot is full.

---

## 📈 Real-Time Streaming with Pathway

- Simulates streaming data ingestion of parking records using **Pathway**.
- Processes data incrementally and generates real-time pricing.
- Outputs results to CSV (`live_prices.csv`) and Bokeh plots.

---

## 🧱 Project Architecture

flowchart TD
    A[CSV Data (dataset.csv)] --> B[Pathway Streaming Engine]
    B --> C[Feature Engineering]
    C --> D[Model 1 / Model 2 / Model 3]
    D --> E[Real-Time Pricing Engine]
    E --> F[Output CSV + Bokeh Visualization]
    
📂 Folder Structure

dynamic-parking-pricing/
│
├── dataset.csv
├── dynamic_pricing.ipynb        # Main Colab notebook
├── live_prices.csv              # Output from pricing engine
├── README.md                    # This file
└── visualizations/              # Saved Bokeh plots
📑 How Pricing Works
Feature	Role in Pricing
Occupancy	Higher → Higher price
Queue Length	Longer → Higher price
Traffic Level	More traffic → Higher price
Special Day	Event/Holiday → Higher price
Vehicle Type	Car > Truck > Bike (weighted)
Nearby Lots	If cheaper → decrease price / reroute

📎 Assumptions
Base price is set at $10.
Price is capped between 0.5x and 2x of base.
Vehicle weights:
Car: 1.0
Truck: 1.3
Bike: 0.6

📘 How to Run
Open the Colab notebook dynamic_pricing.ipynb.
Ensure the dataset is loaded (dataset.csv).
Run all cells in order.
View outputs in live_prices.csv and real-time Bokeh plots.


👨‍💻 Contributors
Hema Sudabathula
Capstone Project – Summer Analytics 2025

🏁 Final Note
This project demonstrates how real-time dynamic pricing strategies can be built using simple Python logic and streaming frameworks. It simulates a smart-city solution that optimizes parking lot utilization in urban areas using data.


