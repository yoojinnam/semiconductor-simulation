# Semiconductor Device Physics - Conceptual Notes

Personal notes written alongside the simulation project to document understanding of the underlying physics.

---

## 1. What is a PN Junction?

Putting two pieces of silicon (N-type and P-type) together. The space where these two silicons meet is called the junction. When the charge build up from the electrons moving from N to P-type silicons creates a strong enough electric field, the equilibrium is reached and the electrons no longer cross (the electric field pointing N→P stops further electron crossing because electrons are negatively charged and the field pushes them back toward the N side). This creates the depletion region which is emptied of all free carriers (result of the electric field pushing electrons to N side and holes to P side). 

### Understanding the Movement of Electrons
The electrons that travel from N to P move by “filling holes” what this means is that the electrons move “seats” to fill the hole and the next electron fills the hole created by the first one’s movement. This chain of movement is what happens as recombination happens at the junction. Consequently, the electrons and holes move in opposite directions. Electrons flow N→P through the junction. Holes flow P→N. Both contribute to current flowing the same direction. Even though electrons move N→P, conventional current flows P→N inside the device, and P → external circuit → N in the full circuit loop


---

## 2. Why Silicon?
It is not the best conductor or insulator–it is a SEMICONDUCTOR → we can control it.

Pros:
Abundant
Forms a perfect natural oxide (SiO2) that is a nearly perfect electrical insulator
Its oxide (SiO2) is stable and compatible w fabrication (survive high temp and mechanically strong)
Useful bandgap (1.1eV) – Small enough that moderate voltage/heat can activate carriers; Large enough that it doesn't conduct randomly at room temperature; Right in the sweet spot for logic devices operating at normal voltages.
Can be grown as near-perfect crystals (less defects and high purity)
Decades of using silicon (have knowledge in using silicon for the process)

Cons:
Other materials like GaAs is faster (higher frequency/speed)
Other materials like SiC handles extreme conditions better (high power/high temperature)
Other materials like GaN emit light. Silicon is terrible at emitting light. 

### Doping Silicon
Silicon is a poor conductor on its own so we must dope it to use it as a core component of the PN junction and control its electrical properties

You add impurities (dope or perform doping) on pieces of silicon to make:
N-type- add atoms (ie. P) to bring extra electrons (negative charge carriers)
P-type- add atoms (ie. B) that create holes (absence of electrons) (positive charge carriers–due to the movement of electrons)

---

## 3. Doping and Depletion Region

### How does doping vary and matter?
Light doping → wide depletion → ions spread thin → weak stopping field per unit length → easier to overcome with forward bias → turns on at lower voltage → larger I_s
Heavy doping → narrow depletion → ions packed dense → intense stopping field → harder to overcome → turns on at higher voltage → smaller I_s

Standard amounts of doping (how many dopant atoms per cubic centimeter of silicon)
10^14 atoms/cm^3 (light)
10^17 atoms/cm^3 (moderate)
10^20 atoms/cm^3 (heavy)

### Why is the width of depletiondifferent? 
The depletion region must grow wide enough to collect sufficient charge to build a stopping electric field. In lightly doped material each slice contains few ions so the region must reach further. In heavily doped material each slice is ion-rich so the stopping field is reached quickly in a narrow zone. (scale = 1/√N) N = doping concentration.

When doping amount varies in each of the silicon pieces (P and N), an asymmetrical depletion region is created where the lightly doped has a wide and the heavily doped as a narrow depletion region. (This is because the total charge on each side must balance — Na × Wp = Nd × Wn — so the side with fewer ions per cm³ must extend further to contribute an equal amount of charge; Nd = donor concentration on the N side (Phosphorus atoms/cm³)
Na = acceptor concentration on the P side (Boron atoms/cm³)). This is a technique used to control where the depletion region sits and its width. 

### The Shockley Equation
I = I_s × (e^(V/V_T) - 1)
I_s = reverse saturation current (leakage current)
V_T = thermal voltage ≈ 0.026V at room temperature
V — Voltage (volts) = the electric potential difference applied across the PN junction
I — Current (amperes) = the amount of charge flowing through the junction per second as a result of that voltage.
e = Euler's number (~2.718) — the natural exponential, reflects how current grows exponentially with voltage 

I_s is directly determined by doping concentration — Na and Nd appear in the denominator of the full I_s equation, so higher doping → smaller I_s.

### Applying voltage to a PN junction
No voltage: the PN junction stays at the equilibrium that is reached and has a net current of 0. (does have two currents–drift current (driven by the electric field) and diffusion current (driven by concentration difference)–going opposite ways at the junction–still current movement).

Forward bias (positive voltage applied on the P-type): applying an electric potential difference that reduces the electric field created at the junction (reduces the built-in electric field enough that electrons can cross the junction freely once the applied voltage exceeds ~0.6V for silicon) and thus allows for the crossing of electrons from the field. 

Reverse bias (negative voltage applied on the P-type): applying an electric potential difference that increases that electric field created at the junction and thus reduces the current to approach 0 (cannot exactly approach 0–because of a tiny leakage current denoted by I_s which exists because of thermal energy that can kick some carriers across at any temperature above absolute zero)

Heavy reverse: too much reverse bias applied such that a breakdown happens. 1) Zener breakdown: happens at the Zener voltage; the electric field becomes so strong that the electrons are ripped out of the silicon, allowing the current to flow in reverse. 2) Avalanche breakdown : carriers accelerate in the strong field created that they knock other electrons loose in a cascade manner.

Simple diagram/explanation:
No voltage:        [N side] [depletion region] [P side]    net current = 0
Forward bias:      [N]    [smaller depletion]    [P]        current flows →
Reverse bias:      [N] [much wider depletion]  [P]          ~0 current
Heavy reverse:     [N] [breakdown!]             [P]          current flows ←

---

## 4. MOSFET

### Why MOSFET?
It is more complex and useful than a PN junction because it can control the amount of current flow rather than an on and off switch like a PN junction (forward/reverse bias). 
→ This is possible because MOSFET has a knob. This knob connects the P and N (through an electric field it creates). You can control the amount of current flow by changing the amount of voltage you apply to the knob. 

This makes amplifiers, logic gates, and much computing possible. 

### What is a MOSFET?
Metal
- Gate (layer above SiO2 that controls current flow w electric field) was made of metal. Now it is made of polysilicon instead.
Oxide
- The SiO2 layer between gate and silicon. Silicon’s natural oxide
Semiconductor
- The silicon body underneath everything.
Field Effect
- Because the gate controls current through the electric field
Transistor
- Its a transistor–a device that can amplify or switch electrical signals

Physical diagram:
            Gate (G)
                   │
    ──────┴──────
            │   SiO₂   │      ← thin insulating oxide layer
    ──────────────
[N+ Source] [P-body] [N+ Drain]
      S                   D

Three terminals → Gate (G), Drain (D), Source (S)
- G: The control terminal. Where you apply voltage to change the current flow.
- D: where the current flows out.
- S: where the current flows in.
S → D is possible due to the electrical field created by G and its consequent channel that acts as a bridge.

When no gate voltage is applied, the transistor only consists of N+ Source, P-body, N+ Drain so that there are two back-to-back PN junctions and hence no current can flow through them in either directions. (transistor is OFF).

### How does the transistor turn ON?
You do inversion. You invert the surface of the P-type silicon to N-type behaviorally with the help of an electric field. 

When you apply a positive voltage to the Gate, an electric field is created. This electric field penetrates through the SiO2 when applied strong enough (does not produce current here because SiO2 is an insulator). When this electric field reaches the P-type silicon, it repels the holes and attracts the electrons. When there is enough attraction and repulsion, a channel of electrons are formed at the surface of the P-type silicon through which the current can flow from source to drain (S → D). 

Threshold Voltage (V_th): the minimum gate voltage required to form the channel. (for a typical NMOS transistor, V_th ~= 0.7V).
- Controlled by doping concentration of P-type (more doping → high V_th; because more holes have to repelled and more electrons attracted), oxide thickness (thicker → higher V_th; thicker oxide weakens the field reaching the silicon), and gate material (which affects the electric potential at the gate)

V_GS < V_th: → not enough field → no inversion layer → no channel → transistor completely off → zero current \
V_GS > V_th: → sufficient field → inversion layer forms → channel exists → current can flow 

### Two Operating Regions
-depends on how much voltage exists between the drain and source (V_DS)

Linear Region (triode region): 
When V_DS is small the channel is uniform from source to drain and behaves like a simple resistor (or like a closed switch (minimal resistance and passes current)). The higher the V_DS, the current flow increases almost linearly (not exactly linear because the channel becomes slightly thinner in the drain).
Equation: I_D = μCox(W/L) × [(V_GS - V_th) × V_DS - V_DS²/2] 

Saturation Region:
Pinch-off happens when the channel collapses in the Drain end. It occurs when V_DS = V_GS - V_th (when V_DS = the overdrive voltage). No matter the increase in voltage, the channels shape and capacity is fixed by V_GS (to the max). Thus, increasing the V_DS does not change the current flow beyond what the channel can carry. Rather it only extends the small depleted zone near the Drain. 
Equation: I_D = ½ × μCox(W/L) × (V_GS - V_th)² 

### The parameters and their fabrication origins
μ (mobility) — how easily electrons slide through the channel. Set by crystal quality and any strain engineering in the silicon. Better crystal = fewer defects = higher μ = more current.
Cox (oxide capacitance) — how strongly the gate field reaches through the oxide. Set by oxide thickness during thermal oxidation. Thinner oxide = higher Cox = stronger gate control.
W/L (width to length ratio) — geometry of the channel set by lithography. Wider channel carries more current. Shorter channel switches faster. Making L smaller is what every process node advancement is about — 7nm, 5nm, 3nm refers to this dimension.
V_th — set by body doping and oxide thickness as described above.

### Connection to Fabrication
When Intel or TSMC announces a new process node they are fundamentally making L smaller — shrinking the channel length. This means 
1. Faster switching (electrons cross the channel quicker and channel can form quicker(turn ON quicker)) → this makes it so that we can minimize the power waste in the partially-on state
2. Lower power (less voltage needed to switch because the distance of channel is shorter less voltage is needed to create it) 
3. More transistor per chip (if reduce L, the chip can put more transistors in the area).


---

## 5. Simulation Results and Interpretation

### PN Junction I-V Curve
![PN Junction](figures/iv_curve.png)
- Flat near-zero current across negative voltages (reverse bias blocking current)
- No significant current from 0-0.5V (below forward bias threshold)
- Sharp exponential rise after ~0.6V
- Direct visual output of the Shockley equation

### Doping Variation 
![Doping Variation](figures/doping_variation.png)
- Light doping (large I_s) turns on earliest due to a weaker built-in field/ easier to overcome with forward bias
- Heavy doping (small I_s) turns on latest due to a stronger built-in field/ high voltage needed to overcome
- Directly models electrical consequence of doping variation in semiconductor fabrication

### MOSFET Curves
![MOSFET](figures/mosfet_curves.png)
- Each curve rising steeply in an almost linear fashion (linear region)
- Each curve leveling off/flattening after a certain voltage (saturation region)
- The higher the V_GS, it flattens at a higher current→ higher V_GS, higher electric field, wider channel, more current flow possible (overdrive voltage is higher)