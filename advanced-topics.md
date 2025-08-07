## Advanced Topics, System Integration & Optimization

**Objective:** To master advanced simulation techniques, system optimization, and real-world applications using comprehensive case studies.

**Morning Session:** Advanced equipment modeling and optimization  
**Afternoon Session:** Integrated case studies and best practices

---

### **Module 1: Advanced Compressor Modeling**

> 📖 **Complete Module:** PDF Module Compressors (pages 1-26) for comprehensive compressor analysis

#### **1.1 Centrifugal Compressor Deep Dive**

**Performance Map Development:**

**Head-Flow Relationship:**
$$H = a_0 + a_1Q + a_2Q^2 + a_3Q^3$$

Where coefficients vary with speed:
$$a_i(N) = b_{i0} + b_{i1}N + b_{i2}N^2$$

**Efficiency Modeling:**
$$\eta = \eta_{peak} \times f\left(\frac{Q}{Q_{BEP}}\right) \times g\left(\frac{N}{N_{design}}\right)$$

**Surge Line Definition:**
$$Q_{surge} = k_1 \times N + k_2$$

**Stonewall Line:**
$$Q_{stonewall} = k_3 \times N^{0.5}$$

**Power Calculation:**
$$P = \frac{Q \times H \times \rho}{\eta_{ad} \times \eta_{mech}} \times \frac{1}{33000}$$

#### **1.2 Driver Integration**

**Power Derating with Conditions:**
$$P_{available} = P_{rated} \times f_{altitude} \times f_{temperature} \times f_{fuel}$$

**Temperature Derating:**
$$f_{temperature} = 1 - k_T(T_{ambient} - T_{rated})$$

Where $k_T$ ≈ 0.004-0.006 per °F

**Fuel Consumption:**
$$Q_{fuel} = \frac{P_{shaft}}{HV_{fuel} \times \eta_{thermal}}$$

**Typical Thermal Efficiencies:**
- Gas turbine: 28-35%
- Reciprocating engine: 35-42%
- Electric motor: 92-96%

#### **1.3 Station Configuration**

**Series Configuration:**
$$PR_{total} = PR_1 \times PR_2 \times ... \times PR_n$$

**Parallel Configuration:**
$$Q_{total} = Q_1 + Q_2 + ... + Q_n$$

**Load Sharing Strategy:**
- Equal percentage loading
- Equal incremental cost
- Maximum efficiency point

> 📖 **Exercise:** PDF Module Compressors, Case Study 1C (pages 20-26) - Configure multi-unit station

---

### **Module 2: Advanced Thermal Analysis**

> 📖 **Complete Module:** PDF Module Thermal Effects (pages 1-20)

#### **2.1 Detailed Wall Temperature Tracking**

**Multi-Layer Heat Transfer:**
$$\frac{1}{U} = \sum_{i=1}^{n} \frac{\Delta x_i}{k_i} + \frac{1}{h_{inner}} + \frac{1}{h_{outer}}$$

**Layer Configuration Example:**

| Layer | Material | Thickness (in) | k (BTU/hr·ft·°F) | Purpose |
|-------|----------|---------------|------------------|---------|
| 1 | FBE Coating | 0.024 | 0.23 | Corrosion protection |
| 2 | Steel | 0.500 | 30.0 | Structural |
| 3 | Insulation | 2.000 | 0.087 | Thermal protection |
| 4 | Jacket | 0.125 | 0.10 | Weather protection |

**Burial Effects:**

**Shallow Burial (depth < 2D):**
$$h_{soil} = \frac{2k_{soil}}{\pi D} \ln\left(\frac{4h}{D} + \sqrt{\left(\frac{4h}{D}\right)^2 - 1}\right)$$

**Deep Burial (depth > 2D):**
$$h_{soil} = \frac{2k_{soil}}{\pi D} \ln\left(\frac{4h}{D}\right)$$

#### **2.2 Joule-Thomson Applications**

**Temperature Drop Across Regulators:**
$$\Delta T_{JT} = \int_{P_1}^{P_2} \mu_{JT} dP$$

**For ideal gas approximation:**
$$\mu_{JT} = \frac{T}{C_p} \left(\frac{\partial Z}{\partial T}\right)_P$$

**Hydrate Prevention:**
$$T_{outlet} > T_{hydrate} + \text{Safety Margin}$$

**Heating Requirements:**
$$Q_{heater} = \dot{m} C_p (T_{required} - T_{predicted})$$

> 📖 **Practice:** PDF Module Thermal Effects, Case Study 1B (pages 18-20) - Wall layer optimization

---

### **Module 3: Network Optimization Strategies**

#### **3.1 Capacity Optimization**

**Objective Function:**
$$\max(Q_{total}) = \sum_{i} Q_{delivery,i}$$

**Subject to Constraints:**
- $P_{min,i} \leq P_i \leq P_{max,i}$ (Pressure limits)
- $v_i \leq v_{max}$ (Velocity limits)
- $\sum Q_{in} = \sum Q_{out}$ (Mass balance)
- Equipment operating envelopes

**Optimization Methods:**
1. **Linear Programming** - For linearized problems
2. **Gradient Search** - For smooth nonlinear problems
3. **Genetic Algorithms** - For discrete variables
4. **Simulation-Based** - Trial and error with guidance

#### **3.2 Energy Optimization**

**Minimize Compression Power:**
$$\min \sum_{j} P_{comp,j}$$

**Strategies:**
1. **Load Balancing** - Distribute compression efficiently
2. **Pressure Profile** - Optimize intermediate pressures
3. **Cooling** - Reduce compression work
4. **Operational Scheduling** - Time-of-use considerations

**Economic Optimization:**
$$\min(\text{OPEX}) = \text{Fuel Cost} + \text{Maintenance} + \text{Losses}$$

#### **3.3 Reliability Analysis**

**System Availability:**
$$A_{system} = \prod_{i} A_i^{critical} \times \left(1 - \prod_{j}(1 - A_j^{parallel})\right)$$

**N-1 Contingency Analysis:**
- Test system with each component failed
- Verify minimum requirements met
- Document mitigation strategies

> 📖 **Case Study:** PDF Module Capacity, Case Study 1C (pages 16-19) - Multi-delivery optimization

---

### **Module 4: Quality Tracking and Blending**

> 📖 **Complete Module:** PDF Module Quality Tracking (pages 1-12)

#### **4.1 Advanced Mixing Calculations**

**Component Tracking:**
$$C_{i,out} = \frac{\sum_j Q_j C_{i,j}}{\sum_j Q_j}$$

**Property Calculations:**

**Heating Value (Volume Basis):**
$$HV_{mix} = \sum_i y_i \times HV_i$$

**Density:**
$$\rho_{mix} = \sum_i y_i \times \rho_i$$

**Wobbe Index:**
$$WI = \frac{HV}{\sqrt{SG}}$$

#### **4.2 Contamination Management**

**H₂S Tracking Example:**

**Maximum Allowable:**
- Pipeline: 4 ppm (health)
- Power plants: 1% (equipment)
- Residential: 0.25 grain/100 scf

**Dilution Requirements:**
$$Q_{clean} = Q_{contaminated} \times \left(\frac{C_{current} - C_{target}}{C_{target} - C_{clean}}\right)$$

**Displacement Time:**
$$t_{displacement} = \frac{V_{pipeline}}{Q} \times \left(1 + \frac{1}{Pe}\right)$$

Where Peclet number $Pe = \frac{vL}{D_{eff}}$

> 📖 **Exercise:** PDF Module Quality Tracking, Case Study 1A (pages 6-12) - H₂S emergency response

---

### **Module 5: Emergency Response Procedures**

#### **5.1 Pipeline Rupture Response**

> 📖 **Reference:** PDF Module Leak (pages 1-3) and Module Blowdown (pages 1-14)

**Immediate Actions Timeline:**

| Time | Action | Expected Result |
|------|--------|----------------|
| 0-5 min | Detect anomaly | Pressure/flow deviation |
| 5-10 min | Confirm rupture | Multiple indicators |
| 10-15 min | Isolate section | Close block valves |
| 15-30 min | Depressurize | Reduce hazard |
| 30-60 min | Assess impact | Determine affected area |

**Leak Rate Estimation:**
$$Q_{leak} = 38.85 \times d^2 \times P \times \sqrt{\frac{1}{SG \times T}}$$ 
(For sonic flow, d in inches, P in psia, Q in MMSCFD)

#### **5.2 Overpressure Protection**

> 📖 **Complete:** PDF Module Relief Valve (pages 1-8)

**Relief System Design:**

**Primary Relief:**
- Set at 95-100% MAOP
- Size for maximum upset case
- Minimum 2% accumulation

**Secondary Protection:**
- Set at 105% MAOP
- Full capacity at 110% MAOP
- Prevent equipment damage

**Relief Capacity Required:**
$$Q_{relief} = Q_{max\_supply} - Q_{min\_demand} + Q_{thermal\_expansion}$$

#### **5.3 System Recovery**

**Blowdown Procedures:**
$$t_{blowdown} = \frac{2V}{Q_{vent}} \times \frac{P_i - P_f}{P_i + P_f}$$

**Purge Requirements:**
- Volume = 1.5-3.0 × line volume
- Maintain 50+ psig during purge
- Monitor O₂ < 2% before gas introduction

**Repressurization Rate:**
$$\frac{dP}{dt}_{max} = \min\left(100 \text{ psi/hr}, \frac{0.1 \times \text{MAOP}}{\text{hr}}\right)$$

> 📖 **Exercise:** PDF Module Blowdown, Case Study 1B (pages 11-14) - Startup procedures

---

### **Module 6: Advanced Equipment Applications**

> 📖 **Reference:** PDF Module Equipment (pages 1-10)

#### **6.1 Complex Regulator Stations**

**Monitor/Working Configuration:**
```
     ┌─── Monitor (Set 5% below) ───┐
─────┤                               ├─────
     └─── Working (Normal set) ─────┘
```

**Capacity Calculation:**
$$Q = 520 \times C_v \times P_1 \times \sqrt{\frac{1 - (P_2/P_1)^2}{SG \times T}}$$

**Noise Prediction:**
$$SPL = 10 \log\left(\frac{P_1 - P_2}{P_1}\right) + 20 \log(Q) + K$$

#### **6.2 Resistance Elements**

**Modeling Unknown Equipment:**
$$\Delta P = K \times Q^n$$

Where:
- n = 2 for turbulent flow
- n = 1 for laminar flow
- K determined from test data

**Applications:**
- Filters: $K = f(fouling)$
- Meters: $K = f(type, size)$
- Fittings: $K = f(geometry)$

#### **6.3 Advanced Control Logic**

**Cascade Control Example:**
1. Pressure controller sets flow target
2. Flow controller adjusts valve
3. Feedback loop maintains stability

**Split-Range Control:**
- 0-50% signal: Valve A opens
- 50-100% signal: Valve B opens
- Provides extended rangeability

---

### **Module 7: Integrated Case Study**

#### **7.1 Scenario: City Gate Station Upgrade**

**Current System:**
- Supply: 1000 psig transmission line
- Demand: 250 MMSCFD average, 400 MMSCFD peak
- Delivery: 125 psig distribution

**Challenges:**
1. Peak shaving requirements
2. Hourly demand variations
3. Temperature constraints
4. Future growth (20% over 5 years)

**Analysis Steps:**

1. **Steady-State Baseline**
   - Model existing configuration
   - Verify current capacity
   - Identify bottlenecks

2. **Transient Analysis**
   - Model daily demand pattern
   - Determine line pack utilization
   - Calculate survival time

3. **Thermal Considerations**
   - Joule-Thomson cooling
   - Heating requirements
   - Hydrate prevention

4. **Quality Tracking**
   - Multiple supply sources
   - Heating value variations
   - Odorization requirements

5. **Emergency Planning**
   - Relief sizing
   - Isolation strategy
   - Recovery procedures

**Solution Development:**
- Parallel regulator trains
- Inlet heating system
- Line pack optimization
- SCADA integration

> 📖 **Complete Exercise:** Combine techniques from all PDF modules

---

### **Module 8: Best Practices and Troubleshooting**

#### **8.1 Model Development Best Practices**

**Progressive Complexity:**
1. Start simple, add complexity incrementally
2. Validate at each step
3. Document assumptions
4. Version control

**Validation Hierarchy:**
1. Component level (individual equipment)
2. Section level (station or segment)
3. System level (entire network)
4. Scenario level (operations)

#### **8.2 Common Issues and Solutions**

| Problem | Likely Cause | Solution |
|---------|--------------|----------|
| Non-convergence | Over-constrained | Remove redundant constraints |
| Oscillations | Time step too large | Reduce time step |
| Unrealistic temperatures | Missing thermal data | Verify heat transfer inputs |
| Wrong gas properties | Incorrect EOS | Check composition/equation |
| Excessive runtime | Too many knots | Increase knot spacing |

#### **8.3 Results Validation**

**Sanity Checks:**
- Mass balance error < 0.1%
- Energy balance reasonable
- Velocities < erosional limit
- Temperatures above hydrate
- Pressures within equipment limits

**Calibration Process:**
1. Collect field data
2. Adjust model parameters
3. Validate predictions
4. Document changes
5. Periodic recalibration

---


