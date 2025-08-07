## Day 3: Dynamic Simulation, Case Studies & Advanced Analysis

**Objective:** To master dynamic (transient) simulations, understand time-dependent behavior, and apply advanced analysis techniques to real-world scenarios.

**Morning Session:** Batch and interactive dynamic simulation  
**Afternoon Session:** Case studies and troubleshooting

---

### **Module 1: Introduction to Dynamic Simulation**

#### **1.1 Steady-State vs. Transient Analysis**

**Key Differences:**

| Aspect | Steady-State | Transient |
|--------|--------------|-----------|
| Time dependency | None | Time-varying |
| Line pack | Constant | Variable |
| Flow balance | In = Out | In ≠ Out (instantaneous) |
| Computation | Fast, single solution | Slow, time-stepping |
| Application | Design, capacity | Operations, upset conditions |

**When to Use Transient Analysis:**
- Supply/demand variations > 10%
- Compressor startup/shutdown
- Valve operations
- Leak detection
- Survival time analysis
- Peak shaving operations

> 📖 **Comparison Exercise:** PDF Module Capacity, Case Study 2 (pages 20-24) demonstrates steady-state vs. transient capacity differences.

#### **1.2 Line Pack and Storage**

**Line Pack Calculation:**
$$V_{pack} = \frac{\pi D^2 L P_{avg}}{4 \times z_{avg} R T_{avg}}$$

**Usable Line Pack:**
$$V_{usable} = V_{pack}(P_{max}) - V_{pack}(P_{min})$$

**Storage Time Available:**
$$t_{storage} = \frac{V_{usable}}{Q_{deficit}}$$

Where $Q_{deficit}$ = Demand - Supply

---

### **Module 2: Batch Dynamic Simulation**

#### **2.1 Creating Dynamic Scenarios**

> 📖 **Step-by-Step Guide:** PDF Module Capacity, Case Study 2 (pages 20-22) shows transient scenario creation.

**Scenario Building Process:**

1. **Define Initial State**
   - Usually steady-state results
   - Can use previous transient results
   - Must be balanced and converged

2. **Create Event Timeline**
   - Component selection (Device Type, Name, Setpoint)
   - Time-based changes (ramps or steps)
   - Multiple simultaneous events allowed

3. **Set Simulation Parameters**
   - End time
   - Report frequency
   - Trend selection
   - Time step control

**Example Transient Scenario Table:**

| Time (hr) | Component | Parameter | Value | Action |
|-----------|-----------|-----------|-------|--------|
| 0 | System | Initial | SS Result | Start |
| 1 | Delivery-1 | Flow | 150% nominal | Increase demand |
| 5 | Compressor-1 | Status | OFF | Shutdown |
| 6 | Valve-1 | % Open | 0 | Close |
| 10 | Compressor-1 | Status | ON | Restart |

#### **2.2 Trend and Report Configuration**

**Essential Trends to Monitor:**
- Pressure (all critical points)
- Flow (boundaries and key locations)
- Line pack (for storage analysis)
- Compressor power/speed
- Temperature (if tracked)
- Accumulated volumes (for leak/relief)

**Report Frequency Guidelines:**
- Fast transients (< 1 hr): Every 1-5 minutes
- Normal operations (1-24 hr): Every 10-30 minutes
- Long-term (> 24 hr): Every 1-2 hours
- Critical events: Maximum frequency

> 📖 **Trending Practice:** PDF Module Survival Time, Case Study 1 (pages 3-7) demonstrates effective trend usage.

---

### **Module 3: Interactive Dynamic Simulation**

#### **3.1 Interactive Controls**

**Real-Time Intervention Capabilities:**
- Start/stop/pause simulation
- Modify setpoints during run
- Lock/unlock components
- Save snapshots
- Change time multiplier

**Time Multiplier Settings:**
- 1x = Real-time simulation
- 10x = 1 hour simulated in 6 minutes
- 100x = 1 hour simulated in 36 seconds
- 9999x = Maximum speed

#### **3.2 Interactive Analysis Techniques**

**Visualization During Simulation:**
1. **Live Data Blocks** - Values update in real-time
2. **Dynamic Profiles** - Pressure/flow curves animate
3. **Color Coding** - Visual status indicators
4. **Alarm Monitoring** - Real-time violation alerts

> 📖 **Interactive Exercise:** PDF Module Quality Tracking, Case Study 1A (pages 6-12) shows interactive simulation for quality tracking.

---

### **Module 4: Survival Time Analysis**

> 📖 **Core Exercise:** Complete PDF Module Survival Time, Case Study 1 (pages 3-7)

#### **4.1 Survival Time Concepts**

**Definition:** Duration system can maintain minimum requirements after supply loss

**Calculation Method:**
$$t_{survival} = \frac{V_{pack} - V_{min}}{Q_{demand}}$$

**Factors Affecting Survival Time:**
- Initial line pack
- Demand rate
- Minimum pressure constraints
- Pipeline volume
- Temperature effects

#### **4.2 Survival Strategies**

**Extending Survival Time:**
1. **Load Shedding** - Reduce non-critical demands
2. **Pressure Reduction** - Lower delivery pressures
3. **Storage Utilization** - Use parallel pipes/loops
4. **Selective Isolation** - Protect critical users

**Example Survival Scenario:**

| Strategy | Survival Time | Impact |
|----------|---------------|---------|
| No action | 2.3 hours | System fails |
| Shed 30% load | 3.5 hours | Some users affected |
| Reduce pressure | 4.1 hours | All users at minimum |
| Combined | 5.8 hours | Optimized response |

---

### **Module 5: Advanced Case Studies**

#### **5.1 Compressor Station Analysis**

> 📖 **Complete Study:** PDF Module Compressors (pages 1-26)

**Generic Compressor Setup:**
- Efficiency: 75-85% typical
- Pressure ratio: 1.2-1.5 per stage
- Power limitation considerations

**Centrifugal Compressor Modeling:**
- Head curves (6+ points, 2+ speeds)
- Efficiency curves
- Surge/stonewall limits
- Speed range (min/max RPM)

**Driver Considerations:**
- Power derating with temperature
- Fuel gas consumption
- Efficiency factors

#### **5.2 Leak Detection and Analysis**

> 📖 **Complete Exercise:** PDF Module Leak (pages 1-3)

**Leak Modeling Parameters:**
- Hole diameter or area
- Discharge coefficient (0.6-1.0)
- Ambient pressure
- Opening time/profile

**Leak Flow Calculation:**
$$Q_{leak} = C_d A \sqrt{\frac{2 \gamma}{\gamma-1} \frac{P_1}{\rho_1} \left[\left(\frac{P_2}{P_1}\right)^{2/\gamma} - \left(\frac{P_2}{P_1}\right)^{(\gamma+1)/\gamma}\right]}$$

For critical flow $(P_2/P_1 < 0.54)$:
$$Q_{leak} = C_d A P_1 \sqrt{\frac{\gamma}{RT_1} \left(\frac{2}{\gamma+1}\right)^{(\gamma+1)/(\gamma-1)}}$$

#### **5.3 Blowdown and Startup Procedures**

> 📖 **Complete Exercise:** PDF Module Blowdown (pages 1-14)

**Blowdown Time Estimation:**
$$t_{blowdown} = \frac{V_{pipe}}{Q_{vent}} \times \ln\left(\frac{P_{initial}}{P_{final}}\right)$$

**Startup/Purge Requirements:**
- Purge volume = 1.5 × pipe volume (typical)
- Maintain minimum purge pressure
- Monitor gas quality
- Track displacement front

**Example Procedure Timeline:**

| Phase | Duration | Key Parameters |
|-------|----------|----------------|
| Isolation | 10 min | Close valves |
| Blowdown | 4.7 hr | 8" vent, 765→50 psig |
| Purge | 1.7 hr | 1.5× volume |
| Pressurization | 40 min | 50→765 psig |
| Stabilization | 20 min | Flow introduction |

#### **5.4 Relief Valve Sizing**

> 📖 **Complete Exercise:** PDF Module Relief Valve (pages 1-8)

**Relief Requirements:**
- Set pressure: 95-98% MAOP typical
- Full flow at 110% set pressure
- Prevent chatter (hysteresis)

**Relief Flow Sizing:**
$$Q_{relief} = Q_{max\_upset} - Q_{min\_outlet}$$

**MAOP Protection Strategy:**
1. Monitor pressure trends
2. Implement staged relief
3. Document relief events
4. Size for worst-case scenario

---

### **Module 6: Equipment and Network Elements**

> 📖 **Reference:** PDF Module Equipment (pages 1-10)

#### **6.1 Regulators**

**Types and Applications:**
- Pressure reduction (most common)
- Back-pressure (upstream control)
- Flow control
- Monitor regulators (backup)

**Regulator Sizing:**
$$C_v = Q \sqrt{\frac{SG \times T}{P_1 - P_2}}$$

#### **6.2 Valves**

**Block Valve Modeling:**
- CV and size specification
- % open control
- Pressure drop calculation

**Check Valve Behavior:**
- Prevents reverse flow
- Opens at ΔP > 0
- No control required

#### **6.3 Temperature Control Equipment**

> 📖 **Thermal Control:** PDF Module Thermal Effects (pages 12-20)

**Heaters:**
- Fixed outlet temperature
- Temperature rise (ΔT)
- Power requirements

**Coolers:**
- After-compression cooling
- Hydrate prevention
- Process requirements

**Joule-Thomson Effects:**
$$\Delta T = \mu_{JT} \times \Delta P$$

Where $\mu_{JT}$ ≈ 3-7°F/100 psi for natural gas

---

### **Module 7: Quality Tracking Applications**

> 📖 **Complete Exercise:** PDF Module Quality Tracking (pages 1-12)

#### **7.1 Gas Mixing Scenarios**

**Mixing Calculations:**
$$C_{mix} = \frac{\sum Q_i C_i}{\sum Q_i}$$

Where:
- $C_{mix}$ = Mixed concentration
- $Q_i$ = Flow from source i
- $C_i$ = Concentration from source i

**Applications:**
- H₂S monitoring
- Heating value control
- CO₂ limits
- Nitrogen tracking

#### **7.2 Displacement Tracking**

**Front Velocity:**
$$v_{front} = \frac{Q}{A} = \frac{4Q}{\pi D^2}$$

**Arrival Time:**
$$t_{arrival} = \frac{L}{v_{front}} = \frac{\pi D^2 L}{4Q}$$

---

### **Module 8: Laboratory Exercises - Day 3**

#### **Lab 3.1: Dynamic Capacity Analysis**
> 📖 **Complete:** PDF Module Capacity, Case Study 2 (pages 20-28)
- Model daily demand variations
- Compare with steady-state capacity
- Identify drafting periods
- Optimize loop placement for transients

#### **Lab 3.2: Survival Time Study**
> 📖 **Complete:** PDF Module Survival Time, Case Study 1 (pages 3-7)
- Simulate supply interruption
- Determine survival duration
- Test mitigation strategies
- Document pressure decay

#### **Lab 3.3: Compressor Operations**
> 📖 **Complete:** PDF Module Compressors, Case Study 1A (pages 7-13)
- Model compressor shutdown
- Analyze system response
- Determine restart timing
- Calculate fuel consumption

#### **Lab 3.4: Emergency Response**
> 📖 **Complete:** PDF Module Relief Valve, Case Study 1A (pages 6-8)
- Simulate upset condition
- Verify relief valve operation
- Track vented volumes
- Ensure MAOP protection

---

### **Day 3 Checklist**

#### **Competency Checklist:**
✅ Can create and run transient scenarios  
✅ Understand line pack utilization  
✅ Can perform survival time analysis  
✅ Can model equipment operations  
✅ Understand leak behavior  
✅ Can track gas quality  
✅ Can protect against overpressure  
✅ Can optimize transient response  

#### **Practical Skills Test:**
Create a transient scenario that includes:
1. Compressor trip at t=2 hr
2. Demand increase at t=4 hr
3. Valve closure at t=6 hr
4. System recovery by t=24 hr

**Success Criteria:**
- No MAOP violations
- All minimum pressures maintained
- Proper trend configuration
- Complete documentation

---
