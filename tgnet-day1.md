Here is the detailed content for Day 1 of the training plan, presented in Markdown format, covering the exact information from the document references.


---

## Day 1: Fundamentals of Gas Pipeline Simulation & Software Introduction

**Objective:** To introduce the basic principles of gas pipeline flow, the software's capabilities, and the initial steps for setting up a simulation project.

---

### **Module 1: Introduction to Gas Pipeline Flow (Chapter 1)**

This module lays the groundwork by explaining the fundamental physics and mathematical models governing gas flow in pipelines, as well as the software's core calculation methods.

*   **1.1 Hydrology Basics (Page 4)**
    *   **Fundamental Equations of Gas Pipeline Flow:**
        *   **Continuity Equation:**
            $$A \frac{\partial \rho}{\partial t} + \frac{\partial}{\partial x} (\rho w A) = 0$$
        *   **Momentum Equation:**
            $$\frac{\partial (\rho w)}{\partial t} + \frac{\partial p}{\partial x} + \frac{\partial (\rho w^2)}{\partial x} = -g \rho \frac{ds}{dx} - \frac{\lambda}{d} \frac{w^2}{2} \rho$$
        *   **Energy Equation:**
            $$- \frac{\partial Q}{\partial x} (\rho w A) = \frac{\partial}{\partial t} \left[ (\rho A) \left( u + \frac{w^2}{2} + gs \right) \right] + \frac{\partial}{\partial x} \left[ (\rho w A) \left( h + \frac{w^2}{2} + gs \right) \right]$$
        *   **Equation of State:**
            $$\rho = \rho(p, T)$$
        *   **Internal Energy Equation:**
            $$u = u(p, T)$$
        *   **Enthalpy Equation:**
            $$h = h(p, T)$$
        *   **Symbol Definitions:**
            *   `p`: Absolute pressure of the gas.
            *   `T`: Absolute temperature of the gas, K.
            *   `ρ`: Gas density.
            *   `w`: Gas velocity.
            *   `A`: Pipeline cross-sectional area.
            *   `u`: Specific internal energy of the gas.
            *   `h`: Specific enthalpy of the gas.
            *   `x`: Distance from the start of the pipeline segment.
            *   `τ`: Time describing the flow process.
            *   `s`: Elevation at each cross-section of the pipeline segment.
            *   `g`: Acceleration due to gravity.
            *   `λ`: Hydraulic friction factor for the pipeline segment.
            *   `Q`: Heat transfer flow rate from the gas in the pipeline to the surroundings in the segment [0, x].
        *   The text states that these 6 equations, including the definitions of `p`, `T`, `ρ`, `w`, `u`, and `h`, form a closed system from the perspective of solving differential equations, and this system is commonly referred to as the basic differential equation system for gas flow.

*   **1.2 Basic Flow Formulas for Gas Pipelines (Page 5)**
    *   **Steady-State Flow Formula:** "This is a formula for calculating flow rate based on the pressure at both ends of the pipeline segment, applicable only to steady-state conditions."
    *   **Horizontal Pipeline Basic Flow Formula:**
        $$Q = 0.03848 \left[ \frac{(p_Q^2 - p_Z^2)d^5}{\lambda Z \Delta_\ast T L} \right]^{0.5}$$
        *   **Symbol Definitions:**
            *   `Q`: Standard volumetric flow rate, Nm³/s (oil industry term).
            *   `p₀`: Upstream pressure at the start of the pipeline segment, Pa.
            *   `pz`: Downstream pressure at the end of the pipeline segment, Pa.
            *   `d`: Internal diameter of the pipeline segment, m.
            *   `L`: Length of the pipeline segment, m.
            *   `T`: Average temperature of the gas in the pipeline segment, K.
            *   `Z`: Average compressibility factor of the gas in the pipeline segment, dimensionless.
            *   `Δ*`: Relative density of the gas in the pipeline segment under standard conditions, dimensionless.
            *   `λ`: Hydraulic friction factor for the pipeline segment, dimensionless, related to Reynolds number and pipe wall roughness (see next chapter).

*   **1.3 Flow Regime Classification and Reynolds Number (Page 5)**
    *   **Reynolds Number:**
        $$\text{Re} = 1.536 ^\frac{Q \Delta_\ast}{d \mu}$$
        *   `μ`: Dynamic viscosity of the gas. For natural gas, it can be taken as approximately 10⁻⁵ Pa·s.
    *   **Flow Regime Classification:** For gas flow, it can generally be divided into laminar, turbulent, and transition flow.
        *   **Laminar Flow:** `Re ≤ 2000`
        *   **Transition Flow:** `2000 ≤ Re ≤ 4000`
        *   **Turbulent Flow:** `Re ≥ 4000`
    *   **Turbulent Flow Zones:**
        *   **Hydraulically Smooth Zone:** `Re < Re₁`
        *   **Transition Zone:** `Re₁ ≤ Re < Re₂`
        *   **Rough Zone:** `Re ≥ Re₂`
        *   Formulas for `Re₁` and `Re₂`:
            $$Re_1 = 59.7 / (d^{0.167})$$
            $$Re_2 = 11 / (d^{1.5})$$
            *(Note: The provided text has a typo in the formula for Re1, showing `d` in the denominator, but the context suggests it should be related to roughness or diameter. The formula for Re2 also seems incomplete or specific to a context not fully provided here. However, the general concept of zones is explained.)*
    *   **Application:**
        *   Hot oil pipelines: `Re` is on the order of 10⁴, mostly in the turbulent hydraulically smooth zone.
        *   Gas pipelines: `Re` is on the order of 10⁵ to 10⁷. Generally, trunk gas pipelines are in the rough or transition turbulent zones, while city distribution pipelines are typically in the hydraulically smooth zone.

*   **1.4 TGNET's Steady-State Flow Formula (Page 6)**
    *   **TGNET Steady-State Flow Formula:**
        $$Q_b = 38.774 \left( \frac{T_b}{P_b} \right) \left[\frac{\left( P_1^2 - P_2^2 - 0.0375 G (h_2 - h_1) \right)\dfrac{P_{\text{avg}}^2}{z_{\text{avg}} T_{\text{avg}}}}{G L T_{\text{avg}} z_{\text{avg}} f}\right]^{1/2}D^{2.5}$$

        *   **Symbol Definitions:**
            *   `Qb`: Standard volumetric flow rate in mmscfd (million standard cubic feet per day).
            *   `Tb`: Standard temperature (K).
            *   `Pb`: Standard pressure (psia).
            *   `P₁`: Upstream pressure (psia).
            *   `P₂`: Downstream pressure (psia).
            *   `h₁`: Upstream elevation (feet).
            *   `h₂`: Downstream elevation (feet).
            *   `f`: Moody friction factor (a function of relative roughness `e` and flow rate `Q`, dimensionless).
            *   `Zavg`: Average compressibility factor of the gas (dimensionless).
            *   `Tavg`: Average temperature of the gas (K).
            *   `D`: Internal diameter (inches).
            *   `L`: Length of the pipeline segment (miles).
            *   `G`: Gas specific gravity (relative to air, where air = 1.0, dimensionless).
    *   **Hydraulic Friction Factor for Gas Pipelines:**
        *   **Friction Factor Correlations:**
            *   In the rough zone (Fully Turbulent), it depends only on pipe wall roughness.
            *   In the hydraulically smooth zone (Smooth Flow), it depends only on the Reynolds number.
            *   In the transition zone (Partially Turbulent), it depends on both pipe wall roughness and Reynolds number.
    *   **Friction Factor for Smooth Zone:**
        $$f = \frac{0.1844}{Re^{0.2}}$$

*   **Mixed Friction Zone (Page 7)**
    *   **Friction Factor Formula:**
        $$f = 0.067 \left[ \frac{158}{Re} + \left( \frac{2e}{D} \right)^{0.2} \right]$$
        *   `e`: Absolute pipe wall roughness (e.g., 0.02 mm for US, 0.03 mm for former Soviet Union, 0.03 mm for Chinese design).

*   **Other Resistance Coefficient Formulas (Including Rough Zone) (Page 7)**
    *   **1) Weymouth Formula:**
        $$\sqrt{\frac{1}{f}} = 11.19 D^{0.167} E$$
        *   `E`: Efficiency factor. "The gas pipeline efficiency factor represents the reduction in pipeline flow rate due to factors such as internal corrosion, condensate, and local accumulation of water."
        *   **Efficiency Factor Calculation:**
            $$E = \frac{Q_{actual}}{Q_{design}}$$
            where `Q_{actual}` is the actual flow rate and `Q_{design}` is the design flow rate.
        *   **Relationship with Friction Factor:**
            $$E = \sqrt{\frac{f_L}{f_s}}$$
            where `f_L` is the design friction factor and `f_s` is the measured friction factor.
        *   **Setting `E` in TGNET:** The software allows setting `E` for all formulas. In pipeline design, `E` is used to maintain the original design capacity over time. Typical values: 0.9-0.96 in the US, 1 for new uncoated pipes in the former Soviet Union, and 0.95 in China.
        *   **Modified Flow Formula with Weymouth:**
            $$Q_b = 433.49 \left( \frac{T_b}{P_b} \right) \left[ \frac{ \left( P_1^2 - P_2^2 - 0.0375 G (h_2 - h_1) \right) \frac{P_{\text{avg}}^2}{z_{\text{avg}} T_{\text{avg}}} }{G L T_{\text{avg}} z_{\text{avg}}} \right]^{0.5} D^{8/3}$$
        *   **Applicability of Weymouth Formula:**
            *   ESI's technical manual suggests it's suitable for pipe diameters around 900 mm (NPS36) and fully turbulent flow.
            *   For diameters less than 700 mm (NPS30), it tends to overestimate friction, leading to lower calculated throughputs (E > 100%).
            *   Many textbooks suggest it was developed early (1912) with a large absolute roughness (0.0508 mm), making it suitable for small diameter, low flow rate, and less purified mine gas gathering networks.

*   **2) Colebrook White Formula (Page 8)**
    *   **Colebrook White Formula:**
        $$\sqrt{\frac{1}{f}} = -2 \log \left( \frac{e}{3.7 D} + \frac{2.51}{R_e \sqrt{f}} \right)$$
        *   `e`: Equivalent pipe wall roughness.
        *   For `Re < 2000`, `f = 64/Re`.
        *   The Colebrook White formula is recommended for general use, considering various pipe wall conditions (smooth or rough) and providing good accuracy across a wide flow range, including all three turbulent zones. Other formulas may require specific conditions for similar accuracy.
        *   **Simplified Iterative Formula:**
            $$\frac{1}{\sqrt{f}} = 1.14 - 2 \log \left( \frac{K_e}{d} + \frac{21.25}{R_e^{0.9}} \right)$$
            *(This simplified version has about 2% error compared to the original.)*
        *   **Modified Flow Formula with Colebrook White:**
           $$Q_b = 38.77 \left( \frac{T_b}{P_b} \right) \left[ \frac{\left( P_1^2 - P_2^2 - 0.375 G (h_2 - h_1) \right) \frac{P_{\text{avg}}^2}{z_{\text{avg}} T_{\text{avg}}}}{G L T_{\text{avg}} z_{\text{avg}}} \right]^{0.5} \cdot 4 \log \left[ \frac{k}{3.7 D} + \frac{1.4 \sqrt{1/f}}{N_{\text{Re}}} \right] \cdot D^{2.5}$$
*   **3) AGA Formula (Page 8)**
    *   AGA (American Gas Association) research in 1965 indicated that measured friction factors were greater than those calculated using "hydraulically smooth" or "mixed friction" laws. AGA suggests this proves that in turbulent flow at lower velocities (partially turbulent), friction factor depends only on Reynolds number, while at higher turbulent velocities (fully turbulent), it depends on pipe wall roughness.
    *   **AGA Formula for Partially Turbulent Flow:**
        $$\frac{1}{\sqrt{f}} = 2.0 \log \left( \frac{R}{3.7D} \right) - 0.60$$
        *(Note: The formula in the text appears to be for a different parameter or has a typo. The standard AGA formula for friction factor is typically related to Reynolds number and roughness.)*
    *   **Modified Flow Formula with AGA:**
        $$Q_b = 38.77 \left( \frac{T_b}{P_b} \right)^{0.5} \left[ \frac{P_1^2 - P_2^2 - 0.375 G (h_2 - h_1)}{G L T_{avg} Z_{avg} f} \right]^{0.5} D^{2.5}$$

*   **4) Panhandle A Formula (Page 9)**
    *   Developed by Panhandle & Eastern Gas Co. It assumes pipe wall roughness is small and constant, with friction factor depending only on Reynolds number.
    *   **Accuracy:** High precision for pipe diameters from 150 mm (NPS6) to 600 mm (NPS24) and Reynolds numbers from 5,000,000 to 14,000,000. For Reynolds numbers above 300,000 (partially turbulent), predictions may be optimistic.
    *   **Panhandle A Friction Factor Formula:**
        $$ \frac{1}{\sqrt{\lambda}} = 3.436 * Re^{0.0730} E $$
        *   `E`: Efficiency factor, dependent on pipe diameter (table provided).
    *   **Modified Flow Formula with Panhandle A:**
        $$ Q_b = 435.87 \left( \frac{T_b}{P_b} \right)^{1.0788} \left[ \frac{P_1^2 - P_2^2 - 0.0375 G (h_2 - h_1)}{G^{0.8539} L T_{avg} Z_{avg}} \right]^{0.5394} D^{2.6182} $$

*   **5) Panhandle B Formula (Page 10)**
    *   Similar to Panhandle A, but with less dependence on Reynolds number.
    *   **Panhandle B Friction Factor Formula:**
        $$ \frac{1}{\sqrt{\lambda}} = 8.245 * Re^{0.01961} E $$
        *   `E`: Recommended value of 0.90 for Panhandle B. Suitable for long-distance natural gas pipelines with diameters greater than 600 mm (NPS24).
    *   **Modified Flow Formula with Panhandle B:**
        $$ Q_b = 737 \left( \frac{T_b}{P_b} \right)^{1.020} \left[ \frac{P_1^2 - P_2^2 - 0.0375 G (h_2 - h_1)}{G^{0.961} L T_{avg} Z_{avg}} \right]^{0.516} D^{2.530} $$

*   **Gas State Equations (Page 10-11)**
    *   **1. Ideal Gas State Equation:** `P = ρRT`
    *   **2. General Gas State Equation:** `P = ZρRT`
    *   **3. Van der Waals State Equation:** `P = RT/(V-b) - a/V²`
        *   `b`: Correction for molecular volume.
        *   `a`: Correction for intermolecular forces.
    *   **Z-factor Calculation:** A summation formula is presented for calculating `Z`.
    *   **1. Sarem (Page 11):** An empirical equation that addresses compressibility factor calculation for typical gas pipelines. It uses reduced pressure and temperature concepts and Legendre polynomials.
        *   **Advantages:** High accuracy within normal operating ranges for most natural gas systems, requires fewer gas parameters (relative density, heating value, CO₂ content), allows user-defined properties, assumes ideal gas for specific heat.
        *   **Disadvantages:** Inaccurate at low pressures and near phase transitions.
    *   **2. Peng-Robinson (Page 12):** An extension of the Van der Waals equation, considering temperature and acentric factors.
        *   **Advantages:** More accurate for a wider range of conditions.
        *   **Disadvantages:** Requires gas composition data, based on an extended Van der Waals equation, proportional to Z³.
    *   **3. BWRS Equation (Page 12):** Addresses limitations of previous equations by considering more factors, leading to more parameters and wider applicability.
        *   **Advantages:** Accurate over a wide range of pressures and temperatures, good for phase transition regions, allows gas composition tracking, handles gases with many non-hydrocarbon components.
        *   **Disadvantages:** Requires all gas components, computationally intensive.
    *   **Summary of Gas State Equations (Page 13):**
        *   Ideal gas equations are insufficient.
        *   Empirical formulas (SAREM, NX-19, AGA-8) are most accurate within their specified ranges. AGA-8 is often legally mandated.
        *   SRK, Peng, and BWRS have wider applicability, including liquid hydrocarbon and phase equilibrium calculations.
        *   **Comparison Table:**
            | Feature        | BWRS                                  | Sarem                               | Peng-Robinson |
            | :------------- | :------------------------------------ | :---------------------------------- | :------------ |
            | Complexity     | Complex, slowest computation          | Simplest, fastest computation       | Moderate      |
            | Applicability  | Wet gas, wide range                   | Dry gas, specific conditions        | All gases     |

*   **Temperature Calculation (Page 13-14)**
    *   **Temperature Calculation Selection (Page 13):**
        *   Two options in PLS:
            *   If only temperature tracking is enabled (not wall temperature), PLS uses the user-specified overall heat transfer coefficient.
            *   If both temperature and wall temperature tracking are enabled, PLS performs detailed heat transfer calculations (gas to wall, wall to ambient, and through wall layers).
    *   **Overall Heat Transfer Coefficient (Page 14):**
        *   Can be looked up in a manual or calculated using formulas for bare pipes.
        *   Formula for `U`:
            $$ \frac{1}{U} = \frac{1}{R_{env}} + R_{k_{env}} \ln \left( \frac{R_o}{R_i} \right) + \frac{1}{R_{k_{steel}}} $$
        *   **Symbol Definitions:** `U` (overall heat transfer coefficient, BTU/hr·ft²·°F), `R₀` (outer pipe radius, feet), `Rᵢ` (inner pipe radius, feet), `k_steel` (thermal conductivity of steel, BTU/hr·ft²·°F), `k_env` (environmental heat transfer coefficient, BTU/hr·ft²·°F).
    *   **Detailed Heat Transfer Calculation (Page 14):**
        *   When both temperature and wall temperature tracking are enabled, PLS requires input for heat transfer data, not just the overall coefficient.
        *   **Input Options:**
            *   User inputs a constant film heat transfer coefficient for the inner wall.
            *   PLS uses standard correlations to calculate the inner wall heat transfer coefficient.
            *   User defines custom correlations for the inner wall heat transfer coefficient.
        *   **Heat Transfer to Ambient:** Three options for calculating heat transfer from the outer pipe wall to the environment:
            *   User inputs a constant film heat transfer coefficient for the outer wall.
            *   PLS uses shallow burial correlations (depth < 2 * diameter) based on soil thermal conductivity and burial depth.
            *   PLS uses deep burial correlations (depth > 2 * diameter) based on soil thermal conductivity and burial depth.
    *   **Temperature Calculation Comparison (Page 15):**
        *   Detailed layer-by-layer heat transfer calculations are more accurate than using a single overall heat transfer coefficient, but they require more input data and computational effort.
        *   When detailed calculations are not performed, the pipe's heat capacity is not considered.
        *   PLS does not account for thermal expansion/contraction of the pipe.

---

### **Module 2: TGNET/Pipeline Studio Software Overview (Chapter 2)**

This module introduces the software, its capabilities, and how to navigate its interface.

*   **2.1 Software Features and Purpose (Page 15)**
    *   **TGNET for Gas / Pipeline Studio:** Described as a proven, long-standing offline simulation software for gas pipelines, capable of steady-state and dynamic simulation of single-phase flow. It has been widely applied globally.
    *   **Key Features:**
        *   Full-featured graphical interface.
        *   Stable numerical solver.
        *   Comprehensive equipment simulation.
        *   Flexible and practical control methods.
        *   Support for multiple constraints.
        *   Temperature and gas property tracking.
        *   Extensive default value library.
        *   Batch and interactive operation modes.
        *   Flexible input/output methods.
        *   Easy to learn and use.
    *   **Applications:** Analyzing normal and upset operating conditions, testing design or operational parameter settings, optimizing system performance, and providing modeling data for real-time simulation software configuration.

*   **2.2 User Interface (Page 15-18)**
    *   **2.2.1 Main Window (Page 15)**
        *   **Operation:** TGNET runs in a window environment. Upon startup, it displays the main window.
        *   **Standard Window Controls:** Contains standard window control buttons (maximize, minimize, close).
        *   **Layout:** From top to bottom, it includes the title bar, menu bar, toolbars, workspace, and status bar.
    *   **2.2.2 Menu Bar (Page 16)**
        *   **Content:** The workspace and toolbars are described as being detailed later. The menu bar's functions are largely covered by the toolbars. Key information is highlighted from the title bar and status bar.
        *   **Title Bar:** Displays the software name ("Pipeline Studio") and the current network model name (e.g., "gas" or "liq"). An asterisk (*) appears if the model has been modified and not saved. It also shows the simulation time (00:00:00 for steady-state, or the current time during interactive dynamic simulation) and any alarms (e.g., "Alarm x").
        *   **Status Bar:** Located below the workspace, it provides concise help information when hovering over menu items or toolbar buttons. It displays component names or cursor position when hovering over the network view. It also shows messages about the success or completion of operations.
        *   **Menu Items and Functions:**
            *   **File:** Open, Close, Save files.
            *   **Edit:** Copy, Cut, Paste, Edit objects.
            *   **View:** Pan, Zoom, Grid control.
            *   **Insert:** Add gas parameters, property curves, objects.
            *   **Simulation:** Set units, simulation options, run simulations.
            *   **Chart:** Create trend plots and profile plots.
            *   **Tools:** Multi-case tools, options.
            *   **Table:** Open tables for input and output data.
            *   **Windows:** Arrange and control windows.
            *   **Help:** Access help and technical support.
    *   **2.2.3 Toolbars (Page 17-18)**
        *   **General:** Toolbars are located below the menu bar and group commonly used functions to enhance usability.
        *   **Standard Toolbar:** Functions include: New file, Open file, Save file, Send Email, Print, Print Preview, Cut, Copy, Paste, Format Painter, Find, Open Property Window, Open Alarm Window, Unit dialog, Layout window.
        *   **Chart Toolbar:** Available after calculation when one or more pipeline segments are selected. Functions include: Pressure profile along the line, Flow profile along the line, Pressure and Flow profile, Temperature profile, Longitudinal profile, Head and longitudinal profile.
        *   **Table Toolbar:** Displays input and output tables for various components: Pipe input data, external regulator input, compressor input, pump input; Pipe calculation results, external regulator output, compressor output, pump output.
        *   **Zoom Toolbar:** Controls zooming, panning, and full-screen display of the network view.
        *   **Drawing Toolbar (gas):** Used for drawing the network structure. Allows continuous drawing of a selected component type by clicking the button again or clicking the arrow button to cancel and revert to the selection tool. Functions include: Select, Delete, Add Text, Add Table, Draw Pipe, Draw Generic Compressor, Draw Centrifugal Compressor, Draw Reciprocating Compressor, Draw Compressor Station, Draw Block Valve, Draw Check Valve, Draw Stop Valve, Draw Relief Valve, Draw Meter. It also includes drawing for regulators, sources (inlet points), delivery points, fuel valves, flow measurement points, leak points, and instruments.
        *   **Graphic Editing Toolbar:** For controlling the network view grid, rotating, flipping, and breaking pipeline components. Can also be used to insert data blocks and modify their format. Functions include: Rotate Right, Rotate Left, Flip Horizontal, Flip Vertical, Open, Break Left, Break Right, Zoom Component, Toggle Grid, Toggle Grid Snap, Orthogonal Drawing, Insert Data Block, Add Data Item, Lock Graphic, Draw Flow Direction.
        *   **Simulation Toolbar:** Includes functions for: Network validity check, View KW file, View steady-state report, View dynamic report, Steady-state simulation, Dynamic simulation, Restart dynamic simulation, Interactive steady-state simulation, Interactive dynamic simulation, Edit dynamic script, View trend plot, Profile plot.
        *   **Interactive Simulation Toolbar:** Specific commands for interactive dynamic simulation, which become available only after starting an interactive dynamic simulation. Commands include: Use steady-state as initial state, Use final state as initial state, Start simulation, Stop simulation, Pause simulation, Single step simulation, Step simulation by specified number, Save and exit, Discard, Lock device, Unlock device, Write current state to report file, Change setpoint, Load state file, Save state file, Use current value for steady-state simulation, Use final setpoint for steady-state simulation, Set system parameters.
        *   **Text Viewer Toolbar:** Used for viewing large output files, allowing search, bookmarking, and navigation between bookmarks.

---

### **Module 3: Preparing for Simulation - Initial Setup (Chapter 3)**

This module guides users through the essential steps of setting up a new simulation project.

*   **3.1 Creating a Network Model File (Page 19-20)**
    *   **3.1.1 Creating a New Network Model File (Page 20)**
        *   **Purpose:** To input the structure and data of the pipeline to be simulated.
        *   **Method:** Create a model file (.tgw file).
        *   **Four Methods for Creating a Model File:** Each with its own characteristics and applications.
        *   **Drawing the Network Model:**
            *   Click `File > New` or the `New` button on the Standard Toolbar. A blank network window will appear in the TGNET main window.
            *   **Steps for Drawing the Network Model:**
                1.  Draw a network sketch.
                2.  Name network components according to specific naming rules.
                3.  Develop a step-by-step plan for complex networks.
            *   **Key Considerations:** Ensure correct connectivity between network components and unique naming for each component when drawing the network model.
    *   **3.1.2 Inputting Pipeline Physical Parameters (Page 20)**
        *   **Process:** After drawing the network model, double-click each component icon to input constraint conditions and basic parameters sequentially.
        *   **Example:** For a pipeline, input parameters such as internal diameter, length, wall thickness, roughness, gas equation, friction factor, efficiency, and knot spacing.
        *   **Dialog Example:** "Details for Pipe P10001-T" showing input fields for General, Connections, Wall layers, Heat Transfer Data, Velocity Alarm Limits, and Trends.

*   **3.1.3 Opening Existing Model Files (Page 24)**
    *   **Process:** Click the `File` menu or the `Open` button on the Standard Toolbar to open the file dialog. Select an existing model file, and its diagram will appear in the network window.
    *   **Model Modification:** If the settings in the existing model file meet requirements, they can be directly modified or refined.
    *   **Automatic Reload:** TGNET can be configured to automatically open the most recently used model file at startup by selecting "Reload last document at start up" in the `Tools > Option > General` dialog.

*   **3.1.4 Deriving New Model Files from Existing Ones (Page 24)**
    *   **Method:** Open a model file with satisfactory settings, then use `Save As` to create a new model file with modifications. Alternatively, create several blank basic model files with pre-set configurations. To create a new model, open a suitable basic model file and save it under a new name.

*   **3.2 Setting Units and Simulation Options (Page 24-26)**
    *   **3.2 Setting Units (Page 24)**
        *   **Access:** Click the `Simulation` menu or the `Units` button on the Standard Toolbar to open the `Unit` dialog.
        *   **Convenient Approach for China:** Click the `Load` button in the `Unit` dialog to directly load and use metric units. Most metric units are compatible with Chinese conventions and can be used directly.
        *   **Customization:** If specific units are needed (e.g., pressure in MPa, flow rate in thousand cubic meters per day), click `Manager > Add` in the `Unit` dialog. Enter the unit string and conversion factor in the subsequent dialog.
        *   **Units Dialog Example:** Shows categories like Density, Diameter, Elevation, Energy Flow, Flow Rate (Actual vol, mass, standard vol), Head, Heat Capacity, Heat Transfer Coeff., Heating Value, Line Pack, Percent, Power. It also allows setting pressure units (Absolute, Gauge) and suffixes.
    *   **3.3 Setting Simulation Options (Page 25-26)**
        *   **Access:** Click the `Simulation` menu and then the `Option` button. This opens a dialog box with 11 tabs.
        *   **Key Tabs:** For general use, focus on the `General` and `Fluid` tabs. For dynamic simulation, `Report` and `Control` tabs are important. Other tabs can generally be left at their default settings.
        *   **General Tab (Page 26):**
            *   **Title for simulation:** Enter a text title in the right-hand text box. An alarm will appear if no title is entered, but it won't affect normal operation. The title will appear in generated reports.
            *   **Reference for Standard Conditions:** Enter standard pressure and temperature values. Note that the default standard temperature (20°C) may differ from Chinese standards, requiring adjustment. The default standard pressure is usually consistent with Chinese standards but will change based on the selected gauge or absolute pressure unit.
            *   **Tracking Options:**
                *   `Quality`: If selected, the software automatically calculates mixed gas properties and tracks component changes along the pipeline. If not selected, only the first gas component's properties are used.
                *   `Temperature`: If selected, the software performs a heat balance calculation using user-specified overall heat transfer coefficients and gas temperatures, determining the temperature at each calculation point. If not selected, default system temperatures are used without heat balance calculation.
                *   `Wall Temperature`: If selected, the software performs detailed heat transfer calculations through pipe wall layers, considering user-defined properties (density, thickness, thermal conductivity, specific heat). If not selected, heat transfer is calculated using the overall heat transfer coefficient.

---
