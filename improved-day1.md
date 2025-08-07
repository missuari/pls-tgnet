

## Day 1: Fundamentals of Gas Pipeline Simulation & Software Introduction

**Objective:** To introduce the basic principles of gas pipeline flow, the software's capabilities, and the initial steps for setting up a simulation project.

**Starting Exercise:** 
> 📖 **Case Study 1 (pages 1-10)** - Hands-on introduction to creating a simple A-B pipeline configuration that reinforces the theoretical concepts covered below.

---

### **Module 1: Introduction to Gas Pipeline Flow (Chapter 1)**

This module lays the groundwork by explaining the fundamental physics and mathematical models governing gas flow in pipelines, as well as the software's core calculation methods.

#### **1.1 Hydrology Basics**

**Fundamental Equations of Gas Pipeline Flow:**

The behavior of gas flow in pipelines is governed by six fundamental equations that form a closed system:

1. **Continuity Equation:**
   $$A \frac{\partial \rho}{\partial t} + \frac{\partial}{\partial x} (\rho w A) = 0$$

2. **Momentum Equation:**
   $$\frac{\partial (\rho w)}{\partial t} + \frac{\partial p}{\partial x} + \frac{\partial (\rho w^2)}{\partial x} = -g \rho \frac{ds}{dx} - \frac{\lambda}{d} \frac{w^2}{2} \rho$$

3. **Energy Equation:**
   $$-\frac{\partial Q}{\partial x} (\rho w A) = \frac{\partial}{\partial t} \left[ (\rho A) \left( u + \frac{w^2}{2} + gs \right) \right] + \frac{\partial}{\partial x} \left[ (\rho w A) \left( h + \frac{w^2}{2} + gs \right) \right]$$

4. **Equation of State:**
   $$\rho = \rho(p, T)$$

5. **Internal Energy Equation:**
   $$u = u(p, T)$$

6. **Enthalpy Equation:**
   $$h = h(p, T)$$

**Symbol Definitions:**
- $p$: Absolute pressure of the gas
- $T$: Absolute temperature of the gas, K
- $\rho$: Gas density
- $w$: Gas velocity
- $A$: Pipeline cross-sectional area
- $u$: Specific internal energy of the gas
- $h$: Specific enthalpy of the gas
- $x$: Distance from the start of the pipeline segment
- $\tau$: Time describing the flow process
- $s$: Elevation at each cross-section of the pipeline segment
- $g$: Acceleration due to gravity
- $\lambda$: Hydraulic friction factor for the pipeline segment
- $Q$: Heat transfer flow rate from the gas in the pipeline to the surroundings

#### **1.2 Basic Flow Formulas for Gas Pipelines**

**General Flow Equation:**
$$Q = 77.54 \left( \frac{T_b}{P_b} \right) \left( \frac{P_1^2 - P_2^2}{G T_f L Z f} \right)^{0.5} D^{2.5}$$

Where:
- $Q$: Gas flow rate, ft³/day (SCFD)
- $f$: Friction factor, dimensionless
- $P_b$: Base pressure, psia
- $T_b$: Base temperature, °R (460 + °F)
- $P_1$: Upstream pressure, psia
- $P_2$: Downstream pressure, psia
- $G$: Gas gravity (air = 1.00)
- $T_f$: Average gas flowing temperature, °R
- $L$: Pipe segment length, miles
- $Z$: Gas compressibility factor
- $D$: Pipe inside diameter, inches

#### **1.3 Flow Regime Classification and Reynolds Number**

**Reynolds Number (USCS units):**
$$Re = \frac{u D \rho}{\mu}$$

**Flow Regime Classification:**
- **Laminar Flow:** $Re \leq 2000$
- **Transition Flow:** $2000 < Re \leq 4000$
- **Turbulent Flow:** $Re > 4000$

**Practical Applications:**
- Hot oil pipelines: $Re \approx 10^4$ (turbulent hydraulically smooth zone)
- Gas pipelines: $Re \approx 10^5$ to $10^7$ (rough or transition turbulent zones)
- City distribution pipelines: Typically in hydraulically smooth zone

> 📖 **Hands-on Practice:** Complete PDF Module Tuning, Case Study 1C (pages 18-23) to understand how Reynolds number affects flow calculations in different regimes.

#### **1.4 TGNET's Steady-State Flow Formula**

**TGNET Steady-State Flow Formula:**
$$Q_b = 38.774 \left( \frac{T_b}{P_b} \right) \left[\frac{(P_1^2 - P_2^2 - 0.0375 G (h_2 - h_1))\frac{P_{avg}^2}{z_{avg} T_{avg}}}{G L T_{avg} z_{avg} f}\right]^{1/2} D^{2.5}$$

This formula accounts for:
- Elevation changes $(h_2 - h_1)$
- Average conditions along the pipeline
- Gas compressibility effects

#### **1.5 Friction Factor Formulas**

##### **Colebrook White Formula (Recommended for General Use)**

> 📖 **Essential Exercise:** Complete PDF Module Tuning, Case Study 1B (pages 13-17) to learn pipeline tuning using Colebrook formula.

$$\frac{1}{\sqrt{f}} = -2 \log \left( \frac{e}{3.7 D} + \frac{2.51}{Re \sqrt{f}} \right)$$

For laminar flow ($Re < 2000$): $f = \frac{64}{Re}$

**Advantages:** 
- Suitable for all flow conditions
- Good accuracy across wide flow range
- Considers both smooth and rough pipe conditions

##### **Weymouth Formula**

$$\frac{1}{\sqrt{f}} = 11.19 D^{0.167} E$$

**Applications:**
- Suitable for NPS36 pipes and fully turbulent flow
- Early formula (1912) for small diameter, low flow systems
- Efficiency factor $E$ typical values: 0.9-0.96

##### **Panhandle A Formula**

$$Q_b = 435.87 \left( \frac{T_b}{P_b} \right)^{1.0788} \left[ \frac{P_1^2 - P_2^2 - 0.0375 G (h_2 - h_1))\frac{P_{avg}^2}{z_{avg} T_{avg}}}{G^{0.8539} L T_{avg} z_{avg}} \right]^{0.5394} D^{2.6182}$$

**Best for:** 6-24 inch pipes, Re = 5×10⁶ to 14×10⁶

##### **Panhandle B Formula**

$$Q_b = 737 \left( \frac{T_b}{P_b} \right)^{1.020} \left[ \frac{P_1^2 - P_2^2 - 0.0375 G (h_2 - h_1))\frac{P_{avg}^2}{z_{avg} T_{avg}}}{G^{0.861} L T_{avg} z_{avg}} \right]^{0.516} D^{2.530}$$

**Best for:** Long-distance pipelines > 24 inches

> 📖 **Comparison Exercise:** Complete PDF Module Tuning, Case Study 1C (pages 20-22) to compare the impact of different friction formulas on flow calculations.

#### **1.6 Gas State Equations**

| Equation | Complexity | Speed | Best Application |
|----------|------------|-------|------------------|
| **SAREM** | Simple | Fastest | Dry gas, unknown composition |
| **Peng-Robinson** | Moderate | Medium | Known composition, wide range |
| **BWRS** | Complex | Slowest | Wet gas, non-hydrocarbons, phase transitions |

**Selection Guidelines:**
- Use SAREM when gas composition is unknown
- Use Peng-Robinson or BWRS when composition is known
- Use BWRS for high C2+ content or many non-hydrocarbons

> 📖 **Practice:** See PDF Module Tuning, Case Study 1C (pages 20-22) for EOS comparison effects on flow.

#### **1.7 Temperature Calculations**

**Overall Heat Transfer Coefficient:**
$$\frac{1}{U} = \frac{R_i}{R_o} \times \left[ \frac{1}{k_{env}} + R_o \times \ln \left( \frac{R_o}{R_i} \right) \frac{1}{k_{steel}} \right]$$

**Temperature Tracking Options:**
1. **Basic:** Uses overall heat transfer coefficient
2. **Detailed:** Layer-by-layer wall calculations
3. **Wall Temperature:** Most accurate but computationally intensive

> 📖 **Advanced Topic:** Complete PDF Module Thermal Effects (pages 1-20) for comprehensive thermal modeling including:
> - Joule-Thomson effects
> - Wall layer calculations
> - Burial depth considerations
> - Inner/outer wall correlations

---

### **Module 2: TGNET/Pipeline Studio Software Overview (Chapter 2)**

#### **2.1 Software Features and Purpose**

**Key Capabilities:**
- Steady-state and dynamic simulation
- Graphical network modeling
- Temperature and quality tracking
- Batch and interactive operation modes
- Comprehensive equipment simulation

**Primary Applications:**
- Pipeline capacity analysis
- Operational optimization
- Upset condition analysis
- Design validation
- Real-time simulation support

#### **2.2 User Interface Components**

**Essential Toolbars:**

1. **Drawing Toolbar** - Network construction
   - Pipes, compressors, valves, regulators
   - Sources and deliveries
   - Measurement points

2. **Simulation Toolbar** - Analysis functions
   - Network validation
   - Steady-state simulation
   - Dynamic simulation
   - Interactive simulation

3. **Chart Toolbar** - Results visualization
   - Pressure profiles
   - Flow profiles
   - Temperature profiles
   - Combined P-Q curves

4. **Table Toolbar** - Data management
   - Input tables
   - Output tables
   - Batch editing capabilities

> 📖 **Getting Started:** After familiarizing with the interface, complete PDF Module Tuning, Case Study 1 (pages 1-10) for your first model.

---

### **Module 3: Preparing for Simulation - Initial Setup (Chapter 3)**

#### **3.1 Creating Network Models**

**Four Methods:**
1. **New Model** - Start from scratch
2. **Open Existing** - Modify previous work
3. **Save As** - Derive from existing
4. **Template** - Use pre-configured base

**Best Practice Workflow:**
1. Create network sketch
2. Apply consistent naming convention
3. Build incrementally, test frequently
4. Validate before simulation

#### **3.2 Setting Units and Options**

**Critical Settings:**
- **Units:** Select appropriate system (SI, USCS, Custom)
- **Standard Conditions:** Verify temperature and pressure basis
- **Tracking Options:**
  - Quality tracking for gas mixing
  - Temperature tracking for thermal effects
  - Wall temperature for detailed heat transfer

#### **3.3 Simulation Options Configuration**

**General Tab:**
- Simulation title
- Standard conditions (verify local standards)
- Enable tracking options as needed

**Fluid Tab:**
- Select equation of state
- Configure PVT options
- Set viscosity calculation method

> 📖 **Configuration Exercise:** Use settings from PDF Module Tuning, Case Study 1A (pages 11-12) to configure temperature tracking properly.

---

### **Module 4: Day 1 Laboratory Exercises**

#### **Lab 1.1: Simple Model Creation**
> 📖 **Complete:** PDF Module Tuning, Case Study 1 (pages 1-10)
- Build A-B pipeline configuration
- Use default values
- Run steady-state simulation
- Analyze results

#### **Lab 1.2: Temperature Effects**
> 📖 **Complete:** PDF Module Tuning, Case Study 1A (pages 11-12)
- Enable temperature tracking
- Compare isothermal vs. non-isothermal
- Observe temperature profiles

#### **Lab 1.3: Parameter Sensitivity**
> 📖 **Complete:** PDF Module Tuning, Case Study 1C (pages 18-23)
- Test sensitivity to diameter, roughness, length
- Compare friction formulas
- Compare equations of state

---

### **Day 1 Checklist**

✅ Understand fundamental flow equations  
✅ Know flow regime classifications  
✅ Can select appropriate friction formula  
✅ Can choose suitable equation of state  
✅ Familiar with software interface  
✅ Created and ran first model  
✅ Understand temperature tracking basics  

---
