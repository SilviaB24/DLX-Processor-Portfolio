# 32-bit DLX RISC Processor (RTL-to-GDSII)

This repository documents the end-to-end ASIC implementation of a **5-stage pipelined RISC processor**, developed from RTL specifications down to the final physical layout (GDSII).

The project focuses on the **Physical Design** flow, achieving timing closure and optimizing for area/power using industry-standard EDA tools.

## 📸 Final Layout Visualization (Cadence Innovus)
The physical implementation was split into the main functional blocks to optimize placement and routing.

| **Datapath (DP)** | **Control Unit (CU)** |
| :---: | :---: |
| ![Datapath Layout](images/dlx_dp_gif.png) | ![Control Unit Layout](images/dlx_cu_gif.png) |
| *Layout of the 5-stage Datapath* | *Layout of the Hardwired Control Unit* |


## 🛠️ Design Flow & EDA Stack
The implementation followed a rigorous ASIC flow:

1.  **RTL Design & Verification:**
    * **Language:** VHDL (Structural & Behavioral).
    * **Architecture:** 5-Stage Pipeline (Fetch, Decode, Execute, Memory, Write-Back).
    * **Hazards:** Handled via Forwarding Unit and Hazard Detection Unit (Stalling).
    * **Tool:** Siemens QuestaSim.
2.  **Logic Synthesis:**
    * **Constraints:** Optimized for Timing (WNS) and Area.
    * **Tool:** Synopsys Design Compiler.
3.  **Physical Design (P&R):**
    * **Steps:** Floorplanning, Power Ring/Stripe planning, Placement, Clock Tree Synthesis (CTS), Routing, DRC/LVS.
    * **Tool:** Cadence Innovus.

## 📊 Key Metrics & Results
Achieved full timing closure with positive slack under the target clock frequency.

| Metric | Value | Notes |
| :--- | :--- | :--- |
| **Technology Node** | 45nm (Nangate Open Cell Library) |
| **Frequency** | 307.69 MHz |
| **Worst Negative Slack (WNS)** | **0.917 ns** | **TIMING MET** (Setup Clean) |
| **Pipeline Stages** | 5 | With Forwarding logic |

## 📄 Documentation
Detailed analysis of the datapath, control unit FSM, and physical constraints can be found in the technical report.

* [**View Full Technical Report (PDF)**](DLX_Complete_Report.pdf)
* [**View Presentation Slides (PDF)**](DLX_Presentation.pdf)

---
> *Note: Due to academic policy regarding the "Microelectronic Systems" course at Politecnico di Torino, the raw VHDL source code is not publicly available in this repository. This portfolio demonstrates the design methodology, flow proficiency, and final physical results.*