
---

## Day 3: Dynamic Simulation, Case Studies & Advanced Analysis

**Objective:** To understand and perform dynamic simulations, interpret results, and apply the software to analyze real-world pipeline scenarios.

---

### **Module 5: Batch Dynamic Simulation (Chapter 5)**

This module focuses on setting up and running dynamic simulations that run automatically without user intervention during the calculation process.

*   **5.1 Creating Dynamic Scripts**
    *   **Purpose of Batch Dynamic Simulation:** "The characteristic of batch dynamic simulation is that it does not require manual intervention during the running process, and the computer runs at the fastest possible speed. Intermediate results cannot be seen during the simulation."
    *   **Prerequisite:** A network model must have an initial state. The most common initial state is the result of a steady-state calculation. Results from previous dynamic simulations can also serve as initial states for subsequent ones. Any model must undergo a steady-state simulation before its first dynamic simulation run.
    *   **Creating a Dynamic Script:**
        *   Click the `Simulation > Transient Scenario` button. A blank script table with only a header row will appear.
        *   **Inserting Rows:** Right-click the header row and select `insert row` to add a new row for defining changes.
        *   **Selecting Components and Setpoints:**
            *   A dialog box appears to select the component type (`Device Type`), component name (`Device Name`), and the specific parameter to change (`Device Setpoint`).
            *   **Example:** Selecting `Delivery` as Device Type, `05部队` as Device Name, and `Max Flow` as Device Setpoint.
        *   **Defining Time-Based Changes:**
            *   After selecting the component and setpoint, a new row is added to the script table. This row sets the selected parameter as a setpoint, and the steady-state calculation result becomes the initial value at time zero.
            *   **Time Table:** To define *when* these changes occur, columns representing time intervals are added. This is done by right-clicking the initial value column and selecting `Insert Column` or `Insert Column Range`.
            *   **Rescheduling Ramp Time:** If the timing of a change needs adjustment, right-click the time column or the relevant cell and select `Reschedule Ramp Time`.
            *   **Inputting Values:** Time intervals are defined by start time, end time, and time step. Empty cells in the time table represent values that remain constant until the next defined change.
            *   **Saving the Script:** After inputting all necessary changes and time points, save the script.

*   **5.2 Setting Trends and Reports ( 45)**
    *   **Purpose:** Dynamic simulations generate large amounts of data. It's essential to specify which trends to monitor and the frequency of reports.
    *   **5.2.1 Specifying Trends:**
        *   Double-click a network component in the dialog box, then click the `Trend` tab.
        *   Select the desired trends from the list.
        *   To apply the same trends to all components of the same type, click `Apply to All` before clicking `OK`.
        *   Repeat for all components requiring trend monitoring.
    *   **5.2.2 Specifying Report Frequency:**
        *   Access the `Simulation > Option` dialog.
        *   **Report Tab:** This tab controls the parameters for output reports. Default settings are usually sufficient for most cases.
        *   **Dynamic Simulation Reporting:** For dynamic simulations, specify the report frequency:
            *   `No transient reports`: No dynamic simulation reports are generated.
            *   `Interval time between reports`: Reports are generated at specified time intervals (entered in the adjacent text box).
            *   `List of report time`: Reports are generated at specific times listed in the text box.
        *   **Control Tab**
            *   This tab relates to the control parameters of the simulation. It's recommended not to modify these unless familiar with the software.
            *   **Trend Control:** Options for controlling trend reporting frequency:
                *   `None`: No trend reports.
                *   `Print`: Reports generated based on the `Simulation > Report` settings.
                *   `Maxmum`: Trend reports generated at every time step.
                *   `Minimum`: Reports generated at specified time intervals (entered in `Delta Time`).
                *   `Periodic`: Reports generated at specified time intervals (entered in `Delta Time`).
            *   **Recommended Settings:** `Print` and `Periodic` are commonly used.

*   **5.3 Running Dynamic Simulation**
    *   **Starting Dynamic Simulation:** Click the `Transient` button on the Simulation Toolbar or menu, using the steady-state results as the initial state.
    *   **Process:** A dialog box shows the start time, current time, and end time of the simulation. The simulation ends when the current time equals the end time.
    *   **Restarting Dynamic Simulation:** Use the `Transient Restart` button if using the results of the previous dynamic simulation as the initial state.
    *   **Multiple Case Tool:** For running multiple simulations simultaneously without manual intervention, use the `Tools > Multiple Case Tool`. This allows selecting multiple model files and specifying calculation types (Steady-State, Dynamic, or Steady-State + Dynamic).

*   **Hands-on Exercise 3: Lab3**
    *   **Objective:** Build a model and create a dynamic script to analyze a scenario.
    *   **Model Setup:**
        *   **Supply:** Pres Max 58 barg, Temp 60 Deg C, Mode (Init) Max Pressure.
        *   **Delivery (Node0016):** Flow Max 56 kM3/h, Pres Min 25 barg, Mode (Init) Max Flow.
        *   **Block Valve (Blkv0001):** % open 0 percent, CV 2000, Size 0.37 m.
        *   **Pipes:** Len 360 km, Dia 0.37 m, HTC 1 W/m2.K, Amb Temp 5 Deg C, GasEq Colebrook, Rough 30 micron.
    *   **Dynamic Script Creation:**
        *   **Device Type:** `Block Valve`
        *   **Device Name:** `Blkv0001`
        *   **Device Setpoint:** `% open`
        *   **Initial Value:** 100
        *   **Time 1:** Setpoint to 0 at time 1.
        *   **Time 2:** Setpoint to 0 at time 48.
    *   **Script Interpretation:** "This script means closing the block valve in the first hour, and studying the pipeline's state over 48 hours."
    *   **Simulation Tasks:**
        1.  In the trend dialog for the pipeline, select upstream/downstream pressure, upstream/downstream flow, and gas inventory as trend report content.
        2.  Set dynamic report frequency to hourly and trend report frequency to 0.1 hourly.
        3.  Run the dynamic simulation.
        4.  View the dynamic simulation report and trend report.

---

### **Module 6: Interactive Dynamic Simulation (Chapter 6)**

This module covers dynamic simulations where the user can intervene, control the simulation speed, and observe intermediate results.

*   **6.1 Starting Interactive Dynamic Simulation**
    *   **Initiation:** Click the `Interactive Transient` button on the Simulation Toolbar or menu.
    *   **Prerequisites:** If no steady-state simulation has been performed, the software will first run one to establish the initial state.
    *   **Interface:** The Interactive Simulation command toolbar becomes available.
    *   **Preparation:** Before starting calculations, it's advisable to zoom into relevant data blocks or create charts (e.g., pressure drop, temperature drop, flow rate curves) for observation during the simulation.

*   **6.2 Controlling Simulation Speed and Data Refresh Time**
    *   **Access:** Click the `Interactive System Data` button on the Interactive Simulation command toolbar.
    *   **Dialog Options:**
        *   **Time Multiplier:** Controls simulation speed. Entering `1` makes the simulation speed match the real-time dynamic changes. Larger numbers increase calculation speed. `9999` provides the fastest possible calculation.
        *   **Minimum Timestep:** Sets the minimum time step for calculations.
        *   **Maximum Timestep:** Sets the maximum time step for calculations.
        *   **Data Updates:** Options to update data based on `Iteration(s)` or `Wall Clock` time.

*   **6.3 Selecting Initial State**
    *   **Default Initial State:** The steady-state calculation result is used as the initial state.
    *   **Changing Initial State:**
        *   `Load Saved Data`: Load previously saved states.
        *   `Load Final State`: Load the results from the last dynamic simulation.
        *   `Load Initial State`: Reverts to using the steady-state simulation results as the initial state.

*   **6.4 Interactive Commands**
    *   **Starting Simulation:** Click `Start Simulation` or step/multi-step buttons on the Interactive Simulation command toolbar.
    *   **Observation:** During calculation, data blocks and predefined curves (pressure, temperature, flow) change over time.
    *   **Uncontrolled Simulation:** If no stop command is issued, the simulation continues. If the time exceeds the script's duration, setpoints will remain constant, and the simulation will continue.
    *   **Pausing Simulation:** Click the `Pause Simulation` button on the Interactive Simulation command toolbar to temporarily halt the calculation.
    *   **Modifying Setpoints:**
        *   Right-click a device, select `ramp a setpoint`.
        *   In the `Ramp a setpoint` dialog, select the device type, name, and setpoint.
        *   Enter the new `Value` and `Rate` (if applicable). Click `OK`.
    *   **Saving and Exiting:**
        *   `Write Snapshot to Report`: Saves the current state to the dynamic simulation report.
        *   `Save Current State`: Saves the current state for use as an initial state in future simulations.
        *   `Ramp a Setpoint`: Allows changing a component's setpoint.
        *   `Lock`: Locks a component's setpoint, preventing changes to its constraint conditions. `Unlock` removes the lock.
        *   `Stop`: Stops the simulation but does not exit the interactive mode.
        *   `Stop, Save State, and Exit`: Saves the dynamic simulation and trend reports, then exits the interactive simulation.
        *   `Abort`: Exits the interactive simulation without saving results.

*   **Hands-on Exercise 4: Lab4**
    *   **Based on:** Model `examp3`, saved as `Lab4`.
    *   **Steps:**
        1.  Select `Pipe0001`, hold `Shift`, then select `Pipe0010`.
        2.  Display the PQ (Pressure-Flow) curve.
        3.  Run interactive dynamic simulation.
        4.  Stop the dynamic simulation.
        5.  Right-click in the chart area to modify the left and right Y-axis properties (Axis Title, Labels, Scaling, Upper/Lower Values).

---

### **Module 7: Case Studies and Advanced Topics (Chapter 7)**

This module applies the learned concepts to practical scenarios, demonstrating how TGNET/Pipeline Studio can be used to analyze various pipeline operations and challenges.

*   **7.1 Case Study Review:**
    *   **1. Gas Storage Capacity Case Study**
        *   **Objective:** Analyze the impact of adding parallel pipes on storage capacity and how their location affects it. Study how the change in stored gas volume in parallel pipes improves pipeline supply capacity.
        *   **Model:** `LOOPANDINVENTORY`.
        *   **Tasks:**
            *   Perform steady-state calculations with different flow maximums for DE0001.
            *   Add parallel pipes (P10001, P10002, P10003) and analyze changes in maximum flow, pressure control time, and gas inventory.
            *   Analyze the impact of pipe diameter and length on storage capacity.
    *   **2. Peak Shaving Analysis Case Study**
        *   **Objective:** Analyze peak shaving operations in a hypothetical city gas network.
        *   **Model:** `Peakshaving`.
        *   **Tasks:**
            *   Analyze the impact of pipe diameter and supply constraints on peak shaving.
            *   Investigate how different pipe sizes affect the ability to meet peak demand.
            *   Examine the role of supply flexibility and pipeline storage.
    *   **3. Supply Interruption, Duration, and Restoration Case Study**
        *   **Objective:** Analyze the impact of a gas supply plant outage on the network, including pressure drops, restoration times, and the effect of temporary user shutdowns to aid recovery.
        *   **Model:** `Gpplost`.
        *   **Tasks:**
            *   Simulate a supply interruption and observe pressure alarms.
            *   Analyze the time required for system recovery after supply is restored.
            *   Investigate the effect of temporarily shutting down users to manage gas inventory and speed up recovery.
    *   **4. Compressor Shutdown and Consequences Case Study**
        *   **Objective:** Study the short-term and long-term effects of a compressor station shutdown on pipeline pressure and flow.
        *   **Model:** `Linewithcomp`.
        *   **Tasks:**
            *   Simulate the shutdown of a compressor station (e.g., GC0001-3) and observe pressure and flow changes upstream and downstream.
            *   Analyze the impact of compressor bypass operation.
            *   Examine the long-term effects of a compressor shutdown on other stations in the network.
    *   **5. Compressor Restart Timing and System Recovery Case Study**
        *   **Objective:** Determine the earliest and latest times for compressor restart after a shutdown to maintain user pressure requirements and analyze system recovery.
        *   **Model:** Variations of `Linewithcomp`.
        *   **Tasks:**
            *   Simulate compressor restarts at different times and observe their impact on user pressures and system recovery.
            *   Analyze the role of upstream compressor stations and supply capacity in system recovery.
    *   **6. Leak Analysis Case Study**
        *   **Objective:** Analyze the impact of a pipeline leak on pressure, flow, and gas inventory.
        *   **Model:** A network with a defined leak point.
        *   **Tasks:**
            *   Simulate a leak occurring at a specific time and location.
            *   Analyze the leak flow rate, peak flow, and cumulative flow.
            *   Observe changes in gas inventory and pressure/flow at the source and user points.
            *   Simulate shutting off valves around the leak and the supply to analyze containment.
    *   **7. Gas Storage, Peak Shaving, and Pressure Regulation Temperature Change Case Study**
        *   **Objective:** Study temperature variations in a gas pipeline system involving storage, peak shaving, and pressure regulation.
        *   **Model:** `Temp` model.
        *   **Tasks:**
            *   Analyze temperature changes at a pressure regulating station (Station1) under different upstream pressure and flow conditions.
            *   Examine the relationship between upstream pressure, flow rate, and temperature.
            *   Observe the impact of gas expansion (throttling effect) on temperature.

*   **Troubleshooting and Best Practices**
    *   **Error Checking**
        *   **Input Errors:** Unconnected subnets, MODE settings inconsistent with constraints, missing data for MODE constraints.
        *   **KW File Errors:** "Error: Keyword Processor was not successful." View the Keyword Processor Report for details.
        *   **Simulation Calculation Errors:** Steady-state calculation failure due to unreasonable setpoints (e.g., high flow, low starting pressure), unreasonable network parameters (e.g., small pipe diameter), or inconsistent/conflicting constraints leading to oscillations.
    *   **Constraint Logic**
        *   Use constraints judiciously to avoid excessive switching and potential unsolvable scenarios.
        *   For initial calculations, use minimal constraints. Add more constraints gradually as the model stabilizes.
        *   For dynamic simulations, use constraints that are realistic for the actual operation.
    *   **General Advice:** "Be careful when selecting simulation parameters."

*   **Q&A and Wrap-up**
    *   Open forum for participants to ask questions about any aspect of the software or simulation process.
    *   Review of key concepts covered during the 3-day training.
    *   Guidance on further learning and resources.

---
