

---

## Day 2: Steady-State Simulation and Model Building

**Objective:** To master the process of building a detailed network model, inputting various parameters, and performing steady-state simulations.

---

### **Module 3: Preparing for Simulation (Continued)**

This module builds upon Day 1 by delving into the selection of critical simulation parameters and the detailed setup required before running a steady-state analysis.

*   **3.4 Selecting Friction Formulas and Knot Space**
    *   **Friction Formulas:**
        *   **Colebrook White:** Described as "a very good friction formula, suitable for various flow conditions."
        *   **Weymouth:** Stated as "only suitable for low-pressure systems."
        *   **Panhandle A & B:** Mentioned as "only reasonably accurate within a small range of flow conditions."
    *   **Knot Space:**
        *   **Impact on Simulation:** "For smaller models or higher accuracy requirements, a smaller Knot space can be used. For very large models, a larger Knot space is needed. A smaller Knot space requires longer calculation time, and using too small a Knot space in a large model can lead to simulation failure."

*   **3.5 Selecting Gas State Equations**
    *   **Guidance on Selection:**
        *   "When the gas composition is known, use Peng-Robinson or BWRS state equations. Otherwise, use the SAREM equation."
        *   "If the gas contains many non-hydrocarbon components or a high C2+ content, the BWRS state equation should be used."
        *   **Calculation Speed:** "SAREM equation provides the fastest calculation, while BWRS is the slowest."
    *   **Simulation Options - Fluid Tab**
        *   **Equation of State:** A dropdown list allows selection of Sarem, BWRS, or Peng.
        *   **Sarem Description:** "Suitable for calculating the compressibility factor when gas composition is unknown. It is an empirical formula for typical gas pipelines and is not suitable for very low pressures or gases with high non-hydrocarbon content."
        *   **BWRS and Peng Description:** "Used when gas composition is known and have a wide range of applicability."
        *   **PVT Options:**
            *   **System-wide temperature:** Example values like "Peng-78" are shown.
            *   **Computations:** Settings for Pressure tolerance, Heat capacity tolerance, and Z-factor tolerance are available.
            *   **Heating value:** Options to select `low` or `high` heating values.
            *   **Calculation Method:** Options include `Mole Average` or `ISO6976`.
            *   **Viscosity:** Can be set to `Constant` (with a default or user-entered value) or `Calculate` (where the software computes the viscosity).
        *   **Heating Value Selection:** Users choose between `low` or `high` heating values.
        *   **Viscosity Selection:** Users can select `Constant` viscosity (providing a value) or opt for the software to `Calculate` it.

---

### **Module 4: Steady-State Simulation Steps (Chapter 4)**

This module covers the process of building a detailed network model, inputting various parameters, and performing steady-state simulations.

*   **4.1 Inputting Gas Parameters**
    *   **Two Input Methods:**
        *   **Simplified Fluid:** Accessed via `Insert > Simplified fluid`. This method requires inputting the main gas properties: relative density, heating value, and CO₂ content. It's described as a simplified gas model that must be used with the Sarem state equation (as mentioned in Section 2.3) and is suitable for typical gas pipelines.
        *   **Compositional Fluid:** Accessed via `Insert > Compositional Fluid`. This method involves inputting the mole percentage of each gas component. A check is provided to ensure the sum of mole percentages equals 100%. This component-based gas model requires the use of BWRS or Peng state equations (Section 2.3). The software automatically calculates the gas's physical properties, offering a broader range of applicability.
    *   **Handling Multiple Gas Streams:** The software permits the input of multiple gas streams. Each stream is automatically named, allowing for later reference when specifying different gas sources.

*   **4.2 Building the Network Model**
    *   **4.2.1 Drawing the Network Model Structure**
        *   **Using Drawing Tools:** Users select buttons from the Drawing Toolbar to place pipeline components such as pipes, nodes, and equipment.
        *   **Placement Process:** Clicking a button places a component. Clicking the same button again will draw another identical component. Clicking the button or the arrow button again exits the drawing mode and returns to the selection tool.
        *   **Component Movement:** Selected components can be moved individually or as a group.
        *   **Connectivity Rules:** Pipes can be connected in parallel, but pipes cannot be connected in parallel with other component types like valves.
        *   **Replication Strategy:** For sections of the network that are similar, it's efficient to build one and then use the copy function (holding `Ctrl` and `Shift` while dragging) to replicate it.
    *   **4.2.2 Inputting Network Component Parameters**
        *   **Four Methods for Inputting Parameters:**
            1.  **Component Dialog Box:** Double-clicking any network component opens a dialog box for parameter input.
                *   **Advantages:** Intuitive and less prone to errors.
                *   **Disadvantages:** Can be tedious for complex networks or when entering the same data repeatedly, potentially leading to errors or omissions.
            2.  **Table View:** Select the "Input Table" option from the Table Toolbar or Menu corresponding to the component type. This opens a table containing all components of that type.
                *   **Advantages:** Significantly reduces the chance of missing parameters due to the comprehensive tabular format.
                *   **Batch Input:** Parameters for multiple components can be selected, and then the `Set To` option (accessed by right-clicking) can be used for efficient input of the same data across several components.
                *   **Disadvantages:** The table can obscure the network view, potentially leading to errors like misassigning data. Careful drawing and sequential naming of components (e.g., left-to-right, top-to-bottom, clockwise) can help maintain order and reduce errors.
            3.  **Property View:** Click the `Property view` button on the Standard Toolbar or select it from the `View` menu. This opens a window that displays all properties of the selected component.
                *   **Advantages:** Allows simultaneous viewing of the network diagram and component properties, making it ideal for checking input data and calculation results.
                *   **Tabs:** Three tabs display all data, output data (calculation results), or input data, facilitating efficient review and input.
            4.  **Format Painter** Located next to the "Push Pin" button on the Standard Toolbar, this tool allows copying data from a source component to target components of the same type. It's particularly useful for components with identical parameters. Note that some data, such as pipe length, cannot be transferred using the Format Painter. The "Push Pin" feature enables repeated use of the Format Painter without re-selecting it.

*   **4.3 Network Model Validation**
    *   **Purpose:** To ensure the integrity of the network model, especially after initial creation or significant modifications.
    *   **Process:** Click the `Validate Network` button on the Simulation Toolbar or select it from the `Simulation` menu.
    *   **Checks Performed:** The validation process checks for:
        *   Connectivity of network components.
        *   Completeness of required input data.
        *   Validity of the entered input data.
    *   **Error Reporting:** Errors are categorized as "Warnings" (non-critical, should be corrected) and "Errors" (critical, must be corrected before simulation). Some errors have a "Fix" button to directly access the relevant input dialog.

*   **4.4 Running Steady-State Simulation and Viewing Results**
    *   **Initiating Simulation:** Click the `Steady-State` button on the Simulation Toolbar or menu. The software first checks if validation has been performed. If validation passed, it proceeds directly to calculation. If not, it performs validation first.
    *   **Convergence:** During calculation, a convergence curve is displayed. If all curves (e.g., iteration error) fall within the convergence tolerance, the results are considered reliable.
    *   **Troubleshooting Convergence Issues:** Common causes for non-convergence include: low starting pressure, high flow rates, or undersized pipes.
    *   **Viewing Results:**
        *   **Data Blocks:** Key results can be displayed directly on the network diagram if data blocks were inserted.
        *   **Output Tables:** Detailed results for each component can be viewed in the `Output Tables` window (accessed via `View > Output > Output Tables`).
        *   **Property View:** Individual component results can be viewed by selecting the component and checking its properties.
        *   **Steady-State Report:** A comprehensive report containing all calculation results, network statistics, iteration records, and mass balance errors is available via `View > Output > Steady-State Report`.
        *   **Chart View:** Pressure, flow, temperature, and elevation profiles along the pipeline can be generated using the Chart Toolbar or `Chart` menu. For example, selecting pipeline segments and clicking `Pressure Profile` displays a pressure drop curve with a corresponding data table showing mileage points and pressures.

*   **Hands-on Exercise 2: Lab2**
    *   **Objective:** To build a model based on the provided diagram and perform simulations to analyze the impact of various parameters.
    *   **Model Setup:**
        *   **Node N00001:** Temp 50 Deg C, Mode (Init) Max Pressure, Pres Max 4 MPAG.
        *   **Node N0002:** Len 20 km, Dia 0.3048 m, WT 12.7 mm, GasEq Colebrook, Rough 25.4 micron, HTC 1.13517 W/m2.K, Amb Temp 10 Deg C.
        *   **Supply (SU0001):** Flow 12 10km3/h, Mode (Init) Max Flow.
        *   **Delivery (DE0001):** Flow 12 10km3/h, Mode (Init) Max Flow.
    *   **Simulation Tasks:**
        1.  **Calculate end pressure** for pipe wall roughness values of 10, 25.4, and 45 Micron. View KW file and steady-state report to observe pressure drop and flow velocity curves.
        2.  **Change friction formula** to Weymouth, PAN(A), and PAN(B) and calculate end pressure (MPaG). Note the effect of pipe wall roughness.
        3.  **Set end pressure to 1 MPaG**, remove flow setting, remove upstream pressure setting, and set upstream flow to 12 10km3/h. Calculate with Weymouth, PAN(A), and PAN(B) friction formulas.
        4.  **Set pipe wall roughness to 30 Micron**, use Colebrook friction formula, remove upstream and downstream flow settings, set upstream pressure to 4.0 MPaG, and downstream pressure to 1.0 MPaG. Calculate flow with pipe diameters of 0.25m, 0.3m, and 0.35m, enabling and disabling temperature tracking.

---
