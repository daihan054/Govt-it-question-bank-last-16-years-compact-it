<!-- TOC START -->
**Table of Contents** — 9 subtopics · 39 questions

- [Electrical Circuits & Protection Devices (13)](#electrical-circuits--protection-devices-13)
  - [Circuit Analysis & Theorems (R, I, Norton calculations) (4)](#circuit-analysis--theorems-r-i-norton-calculations-4)
  - [Protection Devices (Fuse, MCB, Relay, Breaker) (2)](#protection-devices-fuse-mcb-relay-breaker-2)
  - [AC-DC Conversion & Transformers (3)](#ac-dc-conversion--transformers-3)
  - [Power Systems & Frequency (3)](#power-systems--frequency-3)
  - [Component Comparison (Battery vs Capacitor) (1)](#component-comparison-battery-vs-capacitor-1)
- [Transistors (BJT & FET) (9)](#transistors-bjt--fet-9)
- [Semiconductor Devices & Diodes (4)](#semiconductor-devices--diodes-4)
- [Digital-to-Analog & Analog-to-Digital Converters (DAC/ADC) (4)](#digital-to-analog--analog-to-digital-converters-dacadc-4)
- [AC Circuits & Power Analysis (2)](#ac-circuits--power-analysis-2)
- [Operational Amplifiers (Op-Amp) (2)](#operational-amplifiers-op-amp-2)
- [Sensor Circuits & Automated Control Systems (2)](#sensor-circuits--automated-control-systems-2)
- [Circuit Theorems (Thevenin, Norton, Superposition) (2)](#circuit-theorems-thevenin-norton-superposition-2)
- [Electrical Machines (Motors & Alternators) (1)](#electrical-machines-motors--alternators-1)

<!-- TOC END -->

---

## Electrical Circuits & Protection Devices (13)

### Circuit Analysis & Theorems (R, I, Norton calculations) (4)

1. **Find the Norton equivalent circuit for a DC power supply that has a 30 V terminal voltage when delivering 400mA and a 28V terminal voltage. When delivering 600mA.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1436 (ET: BUET)]*

Answer: A real DC supply behaves as an ideal source with an internal resistance. Its terminal voltage falls as the load current rises.
   ```
      V(terminal) = V(Thevenin) - I . R(internal)
   ```

   Step 1 — write one equation for each measurement
   ```
      30 = Vth - (0.400)(Rth)          ... (1)   400 mA = 0.4 A
      28 = Vth - (0.600)(Rth)          ... (2)   600 mA = 0.6 A
   ```

   Step 2 — subtract (2) from (1)
   ```
      30 - 28 = [ Vth - 0.4 Rth ] - [ Vth - 0.6 Rth ]
           2  = 0.2 Rth

      Rth = 2 / 0.2 = 10 ohms
   ```

   Step 3 — find Vth from equation (1)
   ```
      30 = Vth - (0.4)(10)
      30 = Vth - 4
      Vth = 34 V
   ```

   Step 4 — convert the Thevenin equivalent into a Norton equivalent
   ```
      R(Norton) = R(Thevenin) = 10 ohms

      I(Norton) = Vth / Rth = 34 / 10 = 3.4 A
   ```
   - `IN` is the current that flows when the terminals are short-circuited, and `RN` is the same resistance seen looking back into the source.

   Norton equivalent circuit
   ```
           +---------------------+------o  A
           |                     |
         (   )                  ###
         ( ^ ) IN = 3.4 A       ### RN = 10 ohms
         (   )  (current source)###
           |                     |
           +---------------------+------o  B
   ```

   Verification against both given readings
   ```
      At I(load) = 0.4 A :
         current through RN = 3.4 - 0.4 = 3.0 A
         V = 3.0 x 10 = 30 V           matches the first reading

      At I(load) = 0.6 A :
         current through RN = 3.4 - 0.6 = 2.8 A
         V = 2.8 x 10 = 28 V           matches the second reading
   ```

   Thevenin equivalent, for comparison
   ```
           Rth = 10 ohms
      +---/\/\/\---+------o A
      |            |
     (+) 34 V      |
      |            |
      +------------+------o B
   ```

   Answer
   ```
      Norton current    IN = 3.4 A
      Norton resistance RN = 10 ohms
   ```

   - The relationship to remember: `Vth = IN x RN`, and the two equivalents can always be converted into each other by that one equation. Here 34 = 3.4 x 10, which confirms the working.

2. **Find R and I from a circuit.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*

Answer: The question is `incomplete` — the circuit diagram is not present. The method for finding an unknown resistance and current, with a worked example, is given below.
   ```
      OHM'S LAW  V = IR                KCL: sum I(in) = sum I(out)          KVL: sum V round a loop = 0
      SERIES   : R(eq) = R1+R2+...     same current, voltage divides
      PARALLEL : 1/R(eq) = 1/R1+1/R2+...  same voltage, current divides ; two resistors: R1R2/(R1+R2)
   ```

   Worked example
   ```
           +----[ R1 = 4 ohm ]----+----[ R = ? ]----+
           |                      |                 |
         (+) 24 V              [ R2 = 12 ohm ]      |
           |                      |                 |
           +----------------------+-----------------+

      Given : total current I = 3 A.   Find : R, and the current through each branch.
   ```
   Step 1 — total resistance
   ```
      R(total) = V / I = 24 / 3 = 8 ohms
   ```
   Step 2 — R2 in parallel with R, that combination in series with R1
   ```
      8 = 4 + (12 R)/(12 + R)
      4(12 + R) = 12R
      48 + 4R = 12R  ->  48 = 8R  ->  R = 6 ohms
   ```
   Step 3 — branch currents
   ```
      Parallel section = (12 x 6)/(12 + 6) = 4 ohms ; V = 3 x 4 = 12 V
      I(R2) = 12/12 = 1 A ,  I(R) = 12/6 = 2 A
      Check (KCL) : 1 + 2 = 3 A       correct
   ```
   Step 4 — verify with KVL
   ```
      24 - (3 x 4) - 12 = 0     correct
   ```
   - General procedure: label nodes, reduce series/parallel groups, apply KCL/KVL, solve, then verify. For a harder network use the voltage/current divider, mesh, node, Thevenin, Norton or superposition methods.

3. **Find the Value of I.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*

Answer: The question is `incomplete` — the circuit diagram is not present. The methods for finding an unknown current are given below with one worked example.

   Method 1 — Ohm's law (single branch)
   ```
      I = V/R          e.g. 12 V across 4 ohm :  I = 12/4 = 3 A
   ```

   Method 2 — series/parallel reduction
   ```
           +---[ 4 ohm ]---+---[ 6 ohm ]---+
           |               |               |
         (+) 24 V      [ 12 ohm ]          |
           |               |               |
           +---------------+---------------+

      Parallel part : (12 x 6)/(12 + 6) = 4 ohms
      Total         : 4 + 4 = 8 ohms
      Total current : I = 24/8 = 3 A

      V across parallel section = 3 x 4 = 12 V
      I(12 ohm) = 12/12 = 1 A ,  I(6 ohm) = 12/6 = 2 A
      Check (KCL) : 1 + 2 = 3 A       correct
   ```

   Method 3 — current divider rule (two resistors in parallel)
   ```
      I(R1) = I x R2/(R1+R2)      I(R2) = I x R1/(R1+R2)

      I = 3 A into 12||6 :  I(12) = 3x6/18 = 1 A ,  I(6) = 3x12/18 = 2 A   (same as above)
   ```

   Method 4 — Kirchhoff's laws, for a network that will not reduce
   - Apply `KCL` (sum of currents into a node = sum out) at every node and `KVL` (sum of voltages round a closed loop = 0) round every independent loop, then solve the simultaneous equations for the unknown currents.

   Method 5 — mesh/nodal analysis, for a larger network
   - Mesh: assign a circulating current to each mesh and write KVL for each. Nodal: write KCL at every node in terms of node voltages. Nodal is usually faster when there are more loops than nodes.

   Method 6 — Thevenin, when only one branch current is wanted
   ```
      Remove the branch -> find Vth (open-circuit voltage) and Rth (sources zeroed)
      -> reconnect :   I = Vth / (Rth + R(branch))
   ```
   - Fastest route when the network is large but only one current matters.

   - Always finish by verifying: KCL at every node, KVL round every loop, and power delivered = power dissipated.

4. **নিচের সার্কিটের মোট রেজিস্ট্যান্স বের করে, I_3 এর কারেন্ট বের কর।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) The question is `incomplete` — the circuit diagram is not present. The method for finding the total resistance and a branch current is set out below with a worked example.
    ```
       SERIES   : R(eq) = R1+R2+...            same current through each
       PARALLEL : 1/R(eq) = 1/R1+1/R2+...      same voltage across each ; two resistors: R1R2/(R1+R2)
       I(total) = V / R(total)
       Current divider : I(R1) = I x R2/(R1+R2)
    ```

    Worked example
    ```
                     I1        R1 = 6 ohm
            +--------/\/\/\-----------+
            |                         |
            |        I2   R2 = 12 ohm |
          (+) 24 V --/\/\/\-----------+
            |                         |
            |        I3   R3 = 4 ohm  |
            +--------/\/\/\-----------+
            |                         |
            +-------------------------+

       Three resistors in PARALLEL across a 24 V source.
       Find the total resistance and I3.
    ```
    Total resistance
    ```
       1/R(total) = 1/6 + 1/12 + 1/4
                 = 2/12 + 1/12 + 3/12
                 = 6/12
       R(total)  = 12/6 = 2 ohms
    ```
    Total current
    ```
       I(total) = V/R(total) = 24/2 = 12 A
    ```
    The branch currents
    ```
       In a PARALLEL circuit every branch has the FULL 24 V across it, so
       each branch current is found directly :

            I1 = 24/6  = 4 A
            I2 = 24/12 = 2 A
            I3 = 24/4  = 6 A

       Check (KCL) : 4 + 2 + 6 = 12 A = I(total)      correct
    ```
    Answer
    ```
       Total resistance R(total) = 2 ohms
       Current I3                = 6 A
    ```
    Power check
    ```
       Delivered   : P = V I = 24 x 12 = 288 W
       Dissipated  : 4^2 x 6 + 2^2 x 12 + 6^2 x 4
                   = 96 + 48 + 144 = 288 W           correct
    ```

    - General procedure for any such network: redraw and mark every node, reduce the innermost series and parallel groups first working outward to a single resistance, find the total current from Ohm's law, then expand back outward using the voltage divider for series sections and the current divider for parallel ones — and verify with KCL, KVL and the power balance.

### Protection Devices (Fuse, MCB, Relay, Breaker) (2)

1. **Differentiate between a Fuse and a Miniature Circuit Breaker (MCB). Which one is more suitable for modern office electrical installations and why?** *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

Answer: Both protect a circuit from `overcurrent`, but differ in how they act and whether they survive the event.

   - `Fuse` — a thin wire/strip that `melts` on overcurrent, breaking the circuit. A `one-time` device that must be replaced after it blows. Very fast on a large short-circuit current, cheap, no moving parts, but gives no indication of which circuit failed.
   - `MCB` — an electromechanical switch that `trips` and is `reset` by hand. Has two sensing elements: thermal (bimetallic strip — sustained overload, with a delay) and magnetic (solenoid — short circuit, almost instant). The tripped handle shows which circuit faulted and the breaker also serves as an isolating switch.

   | Point | Fuse | MCB |
   |---|---|---|
   | Operation | Wire melts | Mechanical contacts trip open |
   | Reusable | No — replace after every fault | Yes — reset the handle |
   | Reset time | Minutes; a spare must be at hand | Seconds |
   | Fault indication | Poor; must be inspected | Clear — the handle drops |
   | Sensing | One characteristic only | Separate thermal and magnetic |
   | Acts as a switch | No | Yes, doubles as an isolator |
   | Cost | Low initial, recurring replacement | Higher initial, one-time |
   | Life | Single use | Thousands of operations |

   Which suits a modern office — the `MCB`
   - Resets in seconds, so work is not held up waiting for a spare fuse, and its rating cannot be tampered with by fitting a thicker wire.
   - The tripped handle gives instant fault diagnosis and also isolates the circuit safely for maintenance.
   - A type-C MCB tolerates the `inrush current` of computers/UPS at switch-on without nuisance tripping, and pairs with an RCCB/RCD for earth-leakage protection — the standard modern arrangement.
   - Fuses (especially HRC types) remain the better choice in main incomers and high-fault-level industrial supplies, where their faster short-circuit clearing outperforms an MCB.

2. **Write down the function of Relay, Fuse and Circuit Breaker.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

Answer: All three are protection or control devices, but each does a different job.

   `Relay` — an electrically operated switch: a small coil current creates a magnetic field that closes (or opens) a separate set of contacts, switching a much larger current elsewhere.
   ```
           control side              switched side
      +-------------------+      +------------------+
      |   coil  (low      |      |   contacts       |
      |   current, 5-12 V)|~~~~~>|  (high current,  |
      |                   |mag   |   220 V, motor)  |
      +-------------------+      +------------------+
   ```
   - Functions: isolation (5 V logic safely switches a 220 V load), amplification, remote control, protection (senses a fault and commands a breaker to trip), and logic (one input switches several contacts). It does `not` break the fault current itself — it detects and signals.

   `Fuse` — a thin wire/strip that `melts` on overcurrent, permanently breaking the circuit.
   - Functions: overcurrent protection, saves the wiring/appliance from burning, and prevents fire from an overheated cable. A `one-time` device that must be replaced; cheapest, and in HRC form the fastest against a large short-circuit current.

   `Circuit breaker` — an automatic switch that `trips` on a fault and is `reset` by hand, combining thermal (bimetallic strip — delayed overload trip) and magnetic (solenoid — instant short-circuit trip) sensing.
   - Functions: overcurrent/short-circuit protection like a fuse, but reusable (reset, not replaced), also serves as a manual isolator, and its tripped handle indicates the faulted circuit.

   | Point | Relay | Fuse | Circuit breaker |
   |---|---|---|---|
   | Main job | Switch/sense, then command | Break circuit on overcurrent | Break circuit on overcurrent |
   | Operation | Electromagnetic coil | Melting element | Thermal + magnetic trip |
   | Reusable | Yes | No | Yes, reset by hand |
   | Breaks fault current | No (signals only) | Yes | Yes |
   | Acts as a switch | Yes | No | Yes |
   | Cost | Low-moderate | Very low | Higher |

   - In practice: a `protective relay` detects the fault, a `circuit breaker` interrupts it, and a `fuse` gives simple backup protection on smaller branches.

### AC-DC Conversion & Transformers (3)

1. **Which Transformer is used in computer?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*

Answer: A computer's power supply uses a `step-down transformer`.

   - The mains supply in Bangladesh is `220 V AC, 50 Hz`, but the internal circuits need low DC voltages:
   ```
      +12 V   : drives, fans, motors
      +5  V   : USB, older logic, drive electronics
      +3.3 V  : motherboard logic, RAM
   ```
   - A step-down transformer reduces 220 V to a low AC voltage, which a rectifier, filter and regulator then convert to steady DC.
   ```
      Ns < Np    ->    Vs < Vp        step-down

      Vs / Vp = Ns / Np
   ```

   Type used in a modern PC — a high-frequency ferrite-core transformer
   - A modern PC uses an `SMPS` (Switched Mode Power Supply), not a plain 50 Hz iron-core transformer.
   - In an SMPS the mains is rectified first, then chopped at `20 kHz to 100 kHz` and fed to a small ferrite-core step-down transformer.
   ```
      Mains 220 V AC --> rectifier --> high-frequency switch (20-100 kHz)
           --> small ferrite step-down transformer --> rectifier --> filter
           --> regulated +12 V, +5 V, +3.3 V DC
   ```
   - Why the high frequency helps: the size of a transformer core is set by the frequency. At 50 Hz the core must be large and heavy; at 100 kHz the same power passes through a core the size of a thumb. This is why a 500 W PC supply weighs about a kilogram instead of ten.

   Other advantages of the SMPS transformer
   - Efficiency of 80-90 per cent, against about 50-60 per cent for a linear supply, so far less heat.
   - Light and compact, which is essential in a laptop adapter.
   - The transformer also provides `galvanic isolation` between the mains and the low-voltage side, which is a safety requirement.

   - Short exam answer: `a step-down transformer` — specifically a `high-frequency ferrite-core step-down transformer` inside the SMPS.

2. **What is the name of AC current to DC current?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*

Answer: The process of converting AC to DC is called `rectification`, and the circuit that does it is a `rectifier`.

   ```
      AC input  ---->  [ RECTIFIER ]  ---->  pulsating DC
   ```

   Types of rectifier
   ```
   Half-wave rectifier   : 1 diode  , uses only one half of each AC cycle
   Full-wave centre-tap  : 2 diodes , uses both halves, needs a tapped transformer
   Full-wave bridge      : 4 diodes , uses both halves, no centre tap needed
   ```
   - The `bridge rectifier` is the one used in almost every practical supply.

   Complete DC power supply
   ```
      AC 220 V --> Transformer --> Rectifier --> Filter --> Regulator --> DC out
                   (step down)     (AC to DC)   (smooth)   (steady)
   ```
   - `Rectifier` converts AC to pulsating DC.
   - `Filter` (a capacitor) smooths the pulses into a nearly steady voltage.
   - `Regulator` (7805, 7812, or an IC) holds the output fixed despite changes in load and mains voltage.

   Waveforms
   ```
      AC input        /‾\    /‾\        sine wave, both polarities
                 ----/   \--/   \----
                      \_/    \_/

      Half-wave       /‾\    /‾\        only the positive halves
                 ----/   \______/   \--

      Full-wave       /‾\/‾\/‾\/‾\      both halves made positive
                 ----/  \/  \/  \/  \--

      After filter    ‾‾‾\_/‾‾‾\_/‾‾    almost flat, with a small ripple
   ```

   The opposite device
   ```
      AC -> DC  :  RECTIFIER   (this question)
      DC -> AC  :  INVERTER
      DC -> DC  :  CHOPPER / DC-DC converter
      AC -> AC  :  TRANSFORMER (voltage change) or CYCLOCONVERTER (frequency change)
   ```

   - Short answer: the conversion is called `rectification` and the device is a `rectifier`. Everyday examples are the mobile phone charger, the laptop adapter and the SMPS inside a computer, all of which contain a bridge rectifier.

3. **How to AC converted into DC?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*

Answer: AC is converted to DC by `rectification`. A complete supply has four stages.
   ```
      AC 220 V --> Transformer --> Rectifier --> Filter --> Regulator --> steady DC
                   (step down)    (AC to DC)   (smooth)   (hold fixed)
   ```

   `Transformer` — steps the 220 V mains down to a low AC voltage (say 12 V) and gives `galvanic isolation` for safety (Vs/Vp = Ns/Np).

   `Rectifier` — diodes conduct in one direction only, turning AC into pulsating DC. A half-wave rectifier (1 diode) uses only the positive half of each cycle; the practical choice is the `full-wave bridge rectifier` (4 diodes), which uses both halves and needs no centre tap:
   ```
                 D1        D2
           +----|>|---+---|<|----+
           |          |          |
      AC ~ |          +---- + ---|--- output
           |          |          |
           +----|<|---+---|>|----+
                 D3        D4            output frequency = 100 Hz
   ```

   `Filter` — a large electrolytic capacitor charges at each peak and discharges slowly between peaks, smoothing the pulses.
   ```
      Before filter    /‾\/‾\/‾\/‾\        pulsating
      After filter     ‾‾‾\_/‾‾‾\_/‾‾      nearly flat, small ripple

      Ripple factor = V(rms ripple) / V(dc)   :  half-wave 1.21 , full-wave 0.48
   ```
   - A bigger capacitor, or an LC/pi filter, gives less ripple.

   `Regulator` — holds the output constant despite load or mains changes: a `zener diode` for small loads, or an IC such as `7805` (+5 V) / `7812` (+12 V).

   Modern method — SMPS
   ```
      Mains --> rectify --> chop at 20-100 kHz --> small ferrite transformer
            --> rectify --> filter --> feedback-regulated DC output
   ```
   - Used in every computer power supply, mobile charger and laptop adapter; the high-frequency transformer is tiny, and efficiency reaches 80-90% versus 50-60% for a linear supply.

   - Summary: `rectifier` makes the current one-directional, `filter` smooths it, `regulator` keeps it steady — all three are needed.

### Power Systems & Frequency (3)

1. **Audio Frequency ও Radio Frequency এর মধ্যেকার পার্থক্য লিখুন। ১০ ওহমের ১০টি ট্রানজিস্টর কোন সিরিজে সংযুক্ত হলে তাতে রেজিস্ট্যান্স কত হবে?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 810 (ET: IBA)]*

Answer: (Answered in English, as required for IT topics.) Part 1 — Audio frequency versus Radio frequency

   `Audio frequency (AF)` — the band the human ear hears: `20 Hz to 20 kHz`. A `mechanical` (pressure) wave in air; too low to radiate as a radio wave (a 1 kHz antenna would need to be tens of km long).

   `Radio frequency (RF)` — used for wireless transmission: about `3 kHz to 300 GHz`. An `electromagnetic` wave, travelling through air, vacuum and space at the speed of light. Sub-bands: LF, MF (AM radio), HF (short wave), VHF (FM/TV), UHF (mobile, Wi-Fi), SHF (satellite, radar).

   | Point | Audio frequency | Radio frequency |
   |---|---|---|
   | Range | 20 Hz - 20 kHz | ~3 kHz - 300 GHz |
   | Nature of wave | Mechanical (sound) | Electromagnetic |
   | Medium needed | Air or another material | Travels in vacuum too |
   | Antenna | Not usable | Practical (short wavelength) |
   | Range of travel | A few metres | Km to interplanetary |
   | Devices | Microphone, speaker, amplifier | Antenna, transmitter, receiver |
   | Uses | Music, speech, telephony | Broadcasting, mobile, Wi-Fi, radar |

   - They work together: an audio signal is `modulated` onto a radio carrier (AM/FM) for transmission and `demodulated` back to audio at the receiver.

   Part 2 — Ten 10-ohm resistors in series
   ```
      R(total) = R1 + R2 + ... + R10 = 10 x 10 ohm = 100 ohms

      For comparison, in parallel : 1/R = 10 x (1/10) = 1   ->   R = 1 ohm
   ```
   - General rule for `n` equal resistors: series gives `nR`, parallel gives `R/n`.

2. **BREB power transmission interrupt related.** *[BREB Assistant General Manager (IT) 2021 compact it 935 (ET: N/A)]*

Answer: The question is `incomplete` — only the topic "BREB power transmission interrupt related" was recorded, not the question itself. `BREB` is the Bangladesh Rural Electrification Board, so the subject is `interruptions in power transmission and distribution`, which is covered below.

    ```
       Types   : MOMENTARY (<5 min, cleared by a RECLOSER) , SUSTAINED (>5 min, needs a crew) ,
                 PLANNED (announced) , UNPLANNED (fault/storm/failure) ,
                 LOAD SHEDDING (deliberate, generation less than demand)

       Causes  : NATURAL (storm, lightning, flood, fallen tree, pollution) ,
                 EQUIPMENT (transformer/insulator/conductor/breaker failure, ageing) ,
                 ELECTRICAL (short circuit, overload, over/under-voltage) ,
                 OPERATIONAL (switching error, maintenance) ,
                 EXTERNAL (vehicle hit, cable damage, theft) ,
                 SYSTEM (generation shortfall, cascading trip / grid collapse)

       Faults  : SYMMETRICAL (3-phase, ~5%, most severe but simplest) ;
                 UNSYMMETRICAL (~95%) - L-G commonest (~70%), L-L (~15%), L-L-G (~10%)
    ```

    Protection that clears a fault
    ```
       RELAY (over-current, differential, distance, earth-fault) detects the fault and commands the breaker
       CIRCUIT BREAKER (oil, air-blast, SF6, vacuum) interrupts the fault current
       RECLOSER re-closes automatically after a transient fault (tries about 3 times)
       ISOLATOR gives visible off-load disconnection ; LIGHTNING ARRESTER diverts surges ; EARTH WIRE shields phase conductors
    ```

    Reliability indices
    ```
       SAIFI = interruptions / customers served      -> how OFTEN supply is lost
       SAIDI = customer-minutes lost / customers     -> how LONG it is lost
       CAIDI = SAIDI / SAIFI                          -> average length of one interruption
       ASAI  = available hours / demanded hours x 100 %
    ```

    - Reducing interruptions: `prevention` (tree trimming, insulator cleaning, replacing ageing conductor), `design` (ring-main/mesh instead of radial feeders, underground cable in storm-prone areas), `protection` (graded relay settings, auto-reclosers), `automation` (SCADA, smart meters), and `management` (outage management system, stocked spares, trained crews).

    - For BREB specifically, the network is `largely rural and radial`, with long 11 kV/33 kV feeders, so one fault far from the substation can black out a wide area — which is why rural electrification concentrates on `auto-reclosers, feeder sectionalising and right-of-way clearance` rather than costly undergrounding.

3. **EEE related 3 math question.** *[BREB Assistant General Manager (IT) 2021 compact it 935 (ET: N/A)]*

Answer: The question is `incomplete` — only "EEE related 3 math question" was recorded, not the three problems. The three topics such a paper usually draws from are worked below.

    Problem 1 — DC network: find the total resistance and branch currents
    ```
            +---[ 4 ohm ]---+---[ 6 ohm ]---+
            |               |               |
          (+) 24 V      [ 12 ohm ]          |
            |               |               |
            +---------------+---------------+

       R(p) = (12 x 6)/(12 + 6) = 4 ohms          R(total) = 4 + 4 = 8 ohms
       I = V/R = 24/8 = 3 A                       V(p) = 3 x 4 = 12 V
       I(12) = 12/12 = 1 A ,  I(6) = 12/6 = 2 A   Check (KCL) : 1 + 2 = 3 A
       P = V I = 24 x 3 = 72 W                    Check : 3^2x4 + 1^2x12 + 2^2x6 = 72 W
    ```

    Problem 2 — AC series RLC: R = 30 ohm, L = 0.1 H, C = 100 uF, V = 230 V at 50 Hz. Find Z, I, pf.
    ```
       X(L) = 2 pi f L = 31.42 ohms            X(C) = 1/(2 pi f C) = 31.83 ohms
       X = X(L) - X(C) = -0.41 ohms (slightly capacitive)
       Z = sqrt(R^2 + X^2) = 30.003 ohms       I = V/Z = 230/30.003 = 7.666 A
       pf = R/Z = 0.9999 leading ,  theta = arctan(X/R) = -0.78 deg
       P = VI cos(theta) = 1763 W ,  S = VI = 1763 VA ,  Q = VI sin(theta) = -24 VAR
       f(r) = 1/(2 pi sqrt(LC)) = 50.33 Hz  -> supply is almost at resonance, hence pf near 1
    ```

    Problem 3 — transformer: 2200/220 V, 50 Hz, 10 kVA. Find turns ratio and rated currents.
    ```
       a = V1/V2 = 2200/220 = 10 : 1
       I1 = S/V1 = 10000/2200 = 4.545 A       I2 = S/V2 = 10000/220 = 45.45 A
       Check : I1/I2 = 1/10 = 1/a       correct
    ```

    Formulas these rest on
    ```
       DC       : V=IR , P=VI=I^2R=V^2/R , series R=R1+R2 , parallel 1/R=1/R1+1/R2 , KCL/KVL
       AC       : X(L)=2 pi f L , X(C)=1/(2 pi f C) , Z=sqrt(R^2+X^2) , pf=R/Z , P=VIcos(theta) , f(r)=1/(2 pi sqrt(LC))
       Machines : f=PN/120 , Ns=120f/P , s=(Ns-N)/Ns , a=V1/V2=N1/N2=I2/I1
    ```
    - The habit that earns marks: write the formula, substitute with units, compute, then verify — KCL/power balance for DC, P=I^2R for AC, ratio check for machines.

### Component Comparison (Battery vs Capacitor) (1)

1. **What is the difference between battery and capacitor?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1226 (ET: N/A)]*

**Which types of transformer is used in computer?** *[BRiCM Assistant Maintenance Engineer; Date: 24 Feburary, 2025 Exam Taker: BRiCM; Exam Type: Written [bitbox it book 41]]*

**What is the name of components which convert AC current to DC current?** *[BRiCM Assistant Maintenance Engineer; Date: 24 Feburary, 2025 Exam Taker: BRiCM; Exam Type: Written [bitbox it book 41]]*

Answer: Both store electrical energy, but in different ways — a `battery` stores it chemically, a `capacitor` stores it in an electric field.

    `Battery` — two electrodes and an electrolyte; energy is stored as `chemical` energy, released by a reaction that drives electrons round the circuit. Supplies a nearly `steady voltage` for a long time; charges and discharges slowly; the chemistry wears out after a few hundred to a few thousand cycles.
    ```
       Energy stored = capacity (Ah) x voltage (V)
    ```

    `Capacitor` — two conducting plates separated by a dielectric; energy is stored `physically` as separated charge in an electric field, with no chemical reaction. Charges/discharges in `microseconds`, so it can deliver very high power briefly; voltage falls exponentially as it discharges; survives millions of cycles.
    ```
       Q = C . V              Energy = (1/2) C V^2
    ```

    | Point | Battery | Capacitor |
    |---|---|---|
    | Form of storage | Chemical energy | Electric field (separated charge) |
    | Energy density | High | Very low |
    | Power density | Low — releases slowly | Very high — releases instantly |
    | Charge / discharge time | Minutes to hours | Microseconds to seconds |
    | Output voltage | Nearly constant until exhausted | Falls exponentially at once |
    | Cycle life | Hundreds to a few thousand | Millions; essentially unlimited |
    | Self-discharge | Slow, weeks or months | Fast, minutes to hours |
    | Used in | Powering a device for hours | Smoothing, filtering, timing, coupling, camera flash |

    - `Battery` powers phones, laptops, UPS and vehicle starting; `capacitor` smooths ripple, couples/decouples amplifier stages, times a 555 circuit, tunes a radio and fires a camera flash.
    - A `supercapacitor` sits between the two: energy density well above an ordinary capacitor but still below a battery, with the capacitor's fast charging and near-unlimited cycle life — used for regenerative braking and short-term backup, where a battery would wear out too quickly.

## Transistors (BJT & FET) (9)

1. **What does BJT stand for?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

Answer: `BJT` stands for `Bipolar Junction Transistor`.

   - "Bipolar" because `both` types of charge carrier take part in conduction — electrons and holes. A FET, by contrast, is unipolar and uses only one type.
   - "Junction" because it is built from two `PN junctions` placed back to back.
   - It has three terminals: `Emitter (E)`, `Base (B)` and `Collector (C)`.
   ```
      NPN                         PNP
           C                           C
           |                           |
      B ---|<                     B ---|>
           |                           |
           E   (arrow out on E)        E   (arrow in on E)
   ```
   - Two types: `NPN` (a thin P base between two N regions) and `PNP` (a thin N base between two P regions).
   - It is a `current-controlled` device: a small base current controls a much larger collector current.
   ```
      IC = beta . IB           beta is typically 50 to 300
      IE = IB + IC
   ```
   - Uses: amplification, switching, oscillators, and as the basis of the TTL logic family.

2. **How many terminals does a BJT have?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

Answer: A BJT has `three` terminals.
   ```
      Emitter   (E)  : heavily doped, emits the charge carriers
      Base      (B)  : very thin and lightly doped, controls the flow
      Collector (C)  : moderately doped and physically largest, collects the carriers
   ```
   ```
      NPN                         PNP
           C                           C
           |                           |
      B ---|<                     B ---|>
           |                           |
           E                           E
      arrow points OUT of E       arrow points IN to E
   ```
   - The `arrow is always on the emitter` and shows the direction of conventional current; that is how NPN and PNP are told apart on a diagram.
   - The three terminals give three possible amplifier configurations:
   ```
      Common Emitter  (CE)  : the most used; high voltage and current gain
      Common Base     (CB)  : high voltage gain, current gain slightly under 1
      Common Collector (CC) : emitter follower; used as a buffer, gain about 1
   ```
   - Current relationship:
   ```
      IE = IB + IC            Kirchhoff's current law at the transistor
   ```

3. **In an NPN transistor, the current flows from _____** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

Answer: In an `NPN` transistor, conventional current flows `from the collector to the emitter` inside the device, and the base current also flows `from the base to the emitter`.

   - The emitter is the terminal through which all the current leaves, which is why the arrow on the NPN symbol points `out` of the emitter.
   ```
           C   (collector)
           |
           |   IC flows IN at the collector
      B ---|<  IB flows IN at the base
           |
           |   IE flows OUT at the emitter
           E   (emitter)

      IE = IB + IC
   ```
   - Electron flow is the opposite: electrons move from the `emitter to the collector`. That is where the name comes from — the emitter emits electrons and the collector collects them.

   Biasing for normal (active) operation
   ```
      Emitter-Base junction   : FORWARD biased   (base positive with respect to emitter)
      Collector-Base junction : REVERSE biased   (collector positive with respect to base)

      For silicon : V(BE) is about 0.7 V when conducting
   ```

   Comparison with PNP
   ```
      NPN : current flows collector -> emitter ; the emitter is grounded
      PNP : current flows emitter -> collector ; the emitter goes to the positive rail
   ```
   - Short answer: `from collector to emitter` (conventional current), and `from base to emitter` for the control current.

4. **Which BJT configuration gives maximum voltage gain?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

Answer: The `common-emitter (CE)` configuration gives the maximum voltage gain — and it is the only configuration that gives high voltage gain `and` high current gain together, so it is also the highest power gain.

   Comparison of the three configurations

   | Point | Common Base (CB) | Common Emitter (CE) | Common Collector (CC) |
   |---|---|---|---|
   | Voltage gain | High | `High` (highest overall) | Less than 1 (about 0.99) |
   | Current gain | Less than 1 (alpha) | High (beta) | High (1 + beta) |
   | Power gain | Moderate | `Highest` | Moderate |
   | Input resistance | Very low (~50 ohm) | Medium (~1 k) | Very high (~500 k) |
   | Output resistance | Very high (~1 M) | High (~50 k) | Very low (~50 ohm) |
   | Phase shift | 0 degrees | `180 degrees` | 0 degrees |
   | Typical use | High-frequency, RF stages | General amplification, switching | Impedance buffer, emitter follower |

   Why CE gives the largest voltage gain
   ```
      Av = -beta . (Rc / r_in)

      beta is 50 to 300 , so a small base signal produces a large collector current
      change, which develops a large voltage across the collector resistor Rc.
   ```
   - The minus sign is the `180 degree phase inversion`, a signature of the CE stage.

   Common-emitter circuit
   ```
                 +Vcc
                   |
                  ###  Rc
                   |
                   +-------- Vout
                   |
      Vin ---||----|<
             C1    |
                   |
                  GND  (emitter common to input and output)
   ```

   - Points worth noting: `CB` also gives a high voltage gain, but its current gain is below 1, so its power gain is much lower. `CC` (emitter follower) has essentially no voltage gain; it is used as a buffer, to match a high-impedance source to a low-impedance load.

5. **Collector current (Ic) is related to base current (Ib) by _____** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

Answer: The collector current is related to the base current by the `current gain beta`.
   ```
      IC = beta . IB
   ```
   - `beta` (also written h_FE) is the common-emitter DC current gain. Typical silicon transistors have beta between `50 and 300`.
   - The relationship means a BJT is a `current-controlled` device: a small base current controls a much larger collector current, which is what makes amplification possible.

   The full set of relationships
   ```
      IE = IB + IC                        Kirchhoff's current law

      IC = beta . IB                      common-emitter current gain
      IC = alpha . IE                     common-base current gain

      alpha = IC / IE       (0.95 to 0.995, always just under 1)
      beta  = IC / IB       (50 to 300)

      beta  = alpha / (1 - alpha)
      alpha = beta / (1 + beta)
   ```

   Worked example
   ```
      IB = 20 uA , beta = 100

      IC = beta . IB = 100 x 20 uA = 2 mA
      IE = IB + IC  = 0.02 + 2 = 2.02 mA
      alpha = IC / IE = 2 / 2.02 = 0.990
   ```

   Circuit view
   ```
                   +Vcc
                     |
                    ### Rc      IC (large)
                     |
                     +------- Vout
           IB        |
      -----/\/\/\----|<
           Rb        |
                     |  IE = IB + IC
                    GND
   ```

   - Points to note: `beta varies` widely between individual transistors of the same type, and it also changes with temperature and with the collector current. Practical amplifier circuits therefore use `emitter degeneration` and a stable bias network so the operating point does not depend on beta.

6. **N-Channel MOS operating in the linear region. Calculate the current passing through the channel of the transistor. Given: \mu_n C_{ox} (W/L) = 1.3\text{ mA/V}^2, V_{GS} = 2.5\text{ V}, V_t = 0.95\text{ V}. Assume reasonable values for missing parameters if necessary.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

Answer: An NMOS transistor in the `linear` (triode) region behaves like a voltage-controlled resistor. The drain current is
   ```
      ID = mu_n Cox (W/L) [ (VGS - Vt) VDS - VDS^2 / 2 ]      valid while VDS < VGS - Vt (triode condition)
   ```

   Given: mu_n Cox (W/L) = 1.3 mA/V^2, VGS = 2.5 V, Vt = 0.95 V. VDS is not given, so assume a small value typical of deep triode: VDS = 0.1 V.

   Step 1 — overdrive voltage
   ```
      V(ov) = VGS - Vt = 2.5 - 0.95 = 1.55 V
   ```

   Step 2 — check the region
   ```
      VDS = 0.1 V  <  V(ov) = 1.55 V        linear region confirmed
   ```

   Step 3 — substitute into the formula
   ```
      ID = 1.3 mA/V^2 x [ (1.55)(0.1) - (0.1)^2 / 2 ]
         = 1.3 x [ 0.155 - 0.005 ] = 1.3 x 0.150 = 0.195 mA
   ```

   Check (deep-triode approximation, VDS^2/2 negligible)
   ```
      ID ~= mu_n Cox (W/L) (VGS - Vt) VDS = 1.3 x 1.55 x 0.1 = 0.2015 mA
      close to the exact 0.195 mA, so the working is consistent
   ```
   - Equivalent channel resistance: r(DS) = VDS/ID = 0.1/0.195 mA = 513 ohms — the MOSFET behaves as a VGS-controlled resistor, the basis of the CMOS transmission gate.

   Output characteristic
   ```
      ID
       |          saturation region (ID nearly constant)
       |        ___________________
       |      /
       |    /   linear (triode) region
       |  /
       |/________________________________ VDS
       0        V(ov) = 1.55 V
   ```
   - Since VDS was not stated in the question, the assumed value must be written down explicitly, as done above; the method and the formula are what carry the marks. <!-- verify -->

7. **Describe cut off, saturation and active region of operation of a transistor with diagram. Explain the working principal of ab n-channel JFET with various values of V_{GS} and V_{DS}.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 445 (ET: BIBM)]*

Answer: Part 1 — the three regions of BJT operation

   The region depends on how the `two junctions` are biased.
   ```
   Region      | Emitter-Base | Collector-Base | Behaviour
   ------------+--------------+----------------+---------------------------
   Cut-off     | Reverse      | Reverse        | OFF, acts as an open switch
   Active      | Forward      | Reverse        | Amplifier, IC = beta . IB
   Saturation  | Forward      | Forward        | ON, acts as a closed switch
   ```
   - `Cut-off`: both junctions reverse biased, IB = IC = 0 (only leakage), V(CE) = Vcc — an open switch, logic 1.
   - `Active`: emitter-base forward, collector-base reverse; IC = beta.IB, independent of V(CE); used for `amplification`; 0.2 V < V(CE) < Vcc.
   - `Saturation`: both junctions forward biased; base current is so large the collector cannot take more, so IC < beta.IB; V(CE,sat) ~ 0.2 V — a closed switch, logic 0.

   Output characteristics
   ```
      IC
       |                                       IB4
       |    saturation |  active region        ______
       |  <----------->|<--------------------  IB3
       |               |  ____________________
       |    /|         |  ____________________ IB2
       |   / |         |  ____________________ IB1
       |  /  |         |
       | /   |         |______________________ IB = 0  (cut-off)
       |/____|_________________________________ VCE
       0    0.2 V                      Vcc
   ```
   - Switching circuits work at the two ends — cut-off and saturation; an amplifier is biased in the middle of the active region.

   Part 2 — n-channel JFET operation
   ```
         Drain (D)
           |
      +----+----+
      |    N    |          Gate (G) is a P region on each side
    G-|=========|-G        of the N channel
      |    N    |
      +----+----+
           |
         Source (S)
   ```
   - The gate-source junction is always reverse biased, so gate current is essentially zero — giving a very high input impedance, unlike a BJT. It is `voltage-controlled`: V(GS) widens or narrows the depletion region, changing the channel width. For an n-channel JFET, V(GS) stays `zero or negative`.
   ```
      VGS = 0     : depletion thin, channel widest, ID maximum = I(DSS)
      VGS = -1,-2 V : channel narrows, ID falls
      VGS = V(P)  : depletion regions meet, channel PINCHED OFF, ID = 0  (VP negative for n-channel)
   ```
   - With V(GS) fixed at 0, as V(DS) rises: `ohmic region` (0 to |VP|, channel acts as a resistor, ID rises ~linearly) -> `pinch-off` at VDS = |VP| -> `saturation` (VDS > |VP|, ID nearly constant at I(DSS)) -> `breakdown` at very high VDS (junction fails, ID rises sharply, device damaged).

   Drain characteristics
   ```
      ID
       |  ohmic |         saturation           | breakdown
       | region |                              |
       |   /|   |____________________  VGS = 0 |  /
       |  / |   |____________________  VGS=-1V | /
       | /  |   |____________________  VGS=-2V |/
       |/___|________________________  VGS=VP _|______ VDS
       0   |VP|
   ```

   Governing equation in saturation
   ```
      ID = I(DSS) [ 1 - (VGS / VP) ]^2           Shockley's equation
   ```

   | Point | BJT | JFET |
   |---|---|---|
   | Controlled by | Base current | Gate voltage |
   | Input impedance | Low (~1 k) | Very high (~10^8 ohm) |
   | Carriers | Both electrons and holes | One type only (unipolar) |
   | Noise | Higher | Lower |
   | Gain | Higher | Lower |

8. **(a) Draw and explain the operation of NMOS transistor.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*

Answer: An `NMOS` transistor is a MOSFET whose channel carries `electrons`. It has four terminals — Gate, Source, Drain and Body (substrate) — and the body is normally tied to the source.

   Structure
   ```
               Gate (G)
                  |
           +--------------+
           |   metal      |
           |==============|  <- thin SiO2 insulating layer
      +----+--------------+----+
      |    |              |    |
      | N+ |   P-substrate| N+ |
      +----+--------------+----+
        |                   |
      Source (S)          Drain (D)
                        Body (B) -> tied to source
   ```
   - Two heavily doped `N+` regions (source, drain) sit in a lightly doped `P` substrate. The gate is insulated from the substrate by a thin SiO2 layer, so it draws `no DC current` — input impedance ~10^12 ohms. It is `enhancement-type`: with no gate voltage there is no channel, so the device is off.

   Operation
   - `VGS = 0` or `0 < VGS < Vt` : no channel exists yet (source/drain are back-to-back PN junctions, one always reverse biased) or not enough electrons have been attracted — `cut-off`, ID ~ 0.
   - `VGS > Vt` : the gate attracts electrons from the substrate, forming a thin N-type `inversion layer/channel` joining source to drain. Vt (threshold, typically 0.4-1 V) is the channel-forming voltage; V(ov) = VGS - Vt sets its thickness.
   - `VDS < VGS - Vt` — `linear (triode)` region: ID = mu_n Cox (W/L) [(VGS-Vt)VDS - VDS^2/2]; the channel is a VGS-set resistor, so ID rises almost linearly with VDS. Used by the CMOS transmission gate.
   - `VDS >= VGS - Vt` — `saturation` region: the channel pinches off at the drain end; ID = (1/2) mu_n Cox (W/L) (VGS-Vt)^2, almost independent of VDS — this is the region used for amplification.

   Output characteristics
   ```
      ID
       |  linear |        saturation
       | region  |
       |    /|   |_____________________  VGS = 3.0 V
       |   / |   |_____________________  VGS = 2.5 V
       |  /  |   |_____________________  VGS = 2.0 V
       | /   |   |
       |/____|___|_____________________  VGS < Vt  (cut-off)
       0   V(ov)                          VDS
   ```

   Key points
   - `Voltage controlled` — the gate current is zero, unlike a BJT where base current does the controlling.
   - `Enhancement mode` — the channel has to be created; the device is normally off. A depletion-mode NMOS has a channel built in and is normally on.
   - In `digital logic`, only cut-off and deep linear are used: VGS = 0 is an open switch, VGS = Vdd is a closed switch of a few hundred ohms.
   - Pairing an NMOS with a `PMOS` gives `CMOS`, in which one of the two is always off, so no static current flows. This is why CMOS consumes almost no power when idle.

9. **ইমিটার কারেন্টের মান 1 Amp, কালেক্টর কারেন্ট 0.95 A হলে বেইস (Base) কারেন্টের মান কত? একটি চিত্র দেওয়া ছিল!!** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) For a transistor, Kirchhoff's current law gives
   ```
      IE = IB + IC
   ```
   - The emitter current is the sum of the base current and the collector current, because all the current entering at the base and the collector leaves through the emitter.

   Given
   ```
      IE = 1 A          (emitter current)
      IC = 0.95 A       (collector current)
      IB = ?            (base current)
   ```

   Calculation
   ```
      IE = IB + IC

      IB = IE - IC
         = 1 - 0.95
         = 0.05 A
   ```
   ```
      IB = 0.05 A = 50 mA
   ```

   Current gains, from the same figures
   ```
      alpha = IC / IE = 0.95 / 1    = 0.95

      beta  = IC / IB = 0.95 / 0.05 = 19

      check : beta = alpha / (1 - alpha) = 0.95 / 0.05 = 19        consistent
   ```

   Circuit
   ```
                 IC = 0.95 A
                     |
                     C
                     |
      IB = 0.05 A ---|<
                     |
                     E
                     |
                 IE = 1 A
   ```

   - Points worth noting: the base current is always the `smallest` of the three, typically 1 to 5 per cent of the emitter current, because the base is very thin and lightly doped so most carriers pass straight through to the collector.
   - `alpha` is always just under 1 (0.95 to 0.995), while `beta` is large (here 19, and 50 to 300 in a modern transistor). A low beta of 19 means this device is a power transistor rather than a small-signal one.

## Semiconductor Devices & Diodes (4)

1. **Explain the working principle of a PN junction diode. Draw its symbol and describe the difference between forward bias and reverse bias.** *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

Answer: A `PN junction diode` is formed by joining a `P-type` semiconductor (rich in holes) to an `N-type` semiconductor (rich in free electrons) on the same crystal. It conducts current in `one direction only`.

   Formation of the depletion region — electrons from the N side diffuse across and fill holes on the P side, leaving fixed positive ions on the N side and fixed negative ions on the P side: a `depletion region` empty of free carriers. The exposed ions set up an internal `barrier potential` (Silicon 0.7 V, Germanium 0.3 V) that stops further diffusion.
   ```
           P side                 N side
      +  +  +  +  |- - + +|  -  -  -  -
      holes       | depletion |   free electrons
                  |  region   |
                  <---------->
                 barrier potential
   ```

   Symbol
   ```
           anode          cathode
         P ----|>|---- N

      Current flows in the direction the triangle points, from anode to cathode.
   ```

   `Forward bias` — P side to `+`, N side to `-`. The applied voltage `opposes` the barrier potential, narrowing the depletion region; past about `0.7 V` (silicon) the barrier collapses and a large current flows. The diode behaves like a `closed switch`, resistance very low.

   `Reverse bias` — P side to `-`, N side to `+`. The applied voltage `adds` to the barrier potential, widening the depletion region; almost no current flows, only a tiny nanoampere `reverse saturation current`. The diode behaves like an `open switch`, resistance very high. Too high a reverse voltage causes `breakdown` (avalanche or Zener), usually destroying an ordinary diode.

   V-I characteristic
   ```
           I (mA)
             |               forward
             |                 /
             |                /
             |               /
      -------+--------------+--------- V
         breakdown      0.7 V (knee)
             |
      -------|  reverse, only microamperes
             |
             | (uA)
   ```

   | Point | Forward bias | Reverse bias |
   |---|---|---|
   | Connection | P to +, N to - | P to -, N to + |
   | Depletion region | Narrows | Widens |
   | Current | Large, in mA | Negligible, in uA or nA |
   | Resistance | Very low | Very high |
   | Behaves as | Closed switch | Open switch |
   | Carriers involved | Majority carriers | Minority carriers only |

   - Uses: rectification (AC to DC), clipping/clamping, reverse-polarity protection, and special forms — the `Zener` diode (voltage regulation) and the `LED` (light emission).

2. **Determine the current passing through a 10\text{ k}\Omega resistor. Assume a forward voltage drop of 0.75\text{ V} across the diode.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

Answer: A diode in series with a resistor forms a simple series circuit. The diode drops a fixed forward voltage, and the rest of the supply appears across the resistor.

   Circuit
   ```
           Vs
           (+)
            |
           ---
           |>|   diode , forward drop VD = 0.75 V
           ---
            |
           ###
           ### R = 10 k ohm
           ###
            |
           GND
   ```

   The supply voltage is not stated in the question, so the usual laboratory value `Vs = 5 V` is assumed. The method is the same for any supply.

   Step 1 — apply Kirchhoff's voltage law round the loop
   ```
      Vs = VD + VR

      VR = Vs - VD
         = 5 - 0.75
         = 4.25 V
   ```

   Step 2 — apply Ohm's law to the resistor
   ```
      I = VR / R
        = 4.25 / 10,000
        = 0.000425 A
   ```
   ```
      I = 0.425 mA = 425 microamperes
   ```

   Step 3 — check
   ```
      Voltage across R : I x R = 0.000425 x 10,000 = 4.25 V
      Voltage across D :                             0.75 V
      Total            :                             5.00 V = Vs      correct
   ```

   The general formula
   ```
      I = (Vs - VD) / R
   ```

   Result for other common supply voltages
   ```
      Vs = 5 V   ->  I = (5 - 0.75) / 10k   = 0.425 mA
      Vs = 9 V   ->  I = (9 - 0.75) / 10k   = 0.825 mA
      Vs = 12 V  ->  I = (12 - 0.75) / 10k  = 1.125 mA
   ```

   Points to note
   - The diode is modelled as a `constant 0.75 V drop` once it conducts. This is the standard "practical diode" model used in exams; the ideal model takes VD = 0, and the full model adds a small bulk resistance.
   - If the diode were `reverse biased`, it would block, and the current would be only the reverse leakage — a few nanoamperes, effectively zero.
   - The supply must exceed the forward drop for any current to flow at all. With `Vs = 0.5 V` the diode never turns on and `I = 0`. <!-- verify -->

3. **What is Diode and Inductor?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

Answer: `Diode` — a two-terminal semiconductor device that lets current flow in `one direction only`, formed by joining a P-type and an N-type semiconductor (a `PN junction`).
   ```
           anode          cathode
         P ----|>|---- N
   ```
   - Forward biased (P to +, N to -): past about `0.7 V` (silicon) it conducts, acting as a closed switch. Reverse biased (P to -, N to +): it blocks, acting as an open switch (only nanoamperes leak).
   - Types: rectifier (AC to DC), Zener (voltage regulation via reverse breakdown), LED (emits light), photodiode (light to current), Schottky (fast, low drop), varactor (voltage-controlled capacitor). Also used for clipping, clamping and reverse-polarity/free-wheeling protection.

   `Inductor` — a passive coil (often on a magnetic core) that stores energy in a `magnetic field` when current flows through it.
   ```
      ---(((((---     symbol
      V = L (dI/dt)          Energy = (1/2) L I^2          Unit : henry (H)
   ```
   - Opposes any change in current: resists a rising current with a back EMF, and generates a voltage spike when the current is cut off.
   ```
      DC (steady) : acts as a plain wire, impedance = 0
      AC          : impedance XL = 2 pi f L, rises with frequency
      High freq   : acts as an open circuit -> blocks AC, passes DC
   ```
   - Uses: filters/chokes, tuned circuits (with a capacitor), transformers, relays, motors, and energy storage in switching converters.

   | Point | Diode | Inductor |
   |---|---|---|
   | Type | Active semiconductor | Passive component |
   | Polarity | Polarised — direction matters | Not polarised |
   | Stores | Nothing | Energy in a magnetic field |
   | Main property | Conducts one way only | Opposes a change in current |
   | Behaviour with AC | Rectifies | Impedance rises with frequency |
   | Main use | Rectification, protection | Filtering, tuning, energy storage |

   - Used together in a switching power supply: the inductor stores energy while the switch is on, and the diode gives it a path to the load when the switch turns off.

4. **How does LED differ from Laser Diod? What are the function of Diode?** *[BTRC Assistant Director (Technical) 2021 compact it 808 (ET: IBA)]*

Answer: Both an `LED` and a `laser diode` are forward-biased PN junctions that emit light when electrons and holes recombine, but they differ in `how` the light is produced.

   `LED` — light by `spontaneous emission`: each electron falls across the band gap at a random moment and direction, giving `incoherent` light over a wide spectrum (~30-50 nm), spread in all directions. No optical cavity or threshold current — it glows as soon as it conducts.

   `Laser diode` — light by `stimulated emission`: one photon triggers an identical one (same direction and phase), amplified by a `resonant cavity` (two mirrored facets). Needs a minimum `threshold current` — below it, poor LED-like output; above it, laser action. Result: `coherent`, `monochromatic` (~1-2 nm), a narrow directional beam.

   | Point | LED | Laser diode |
   |---|---|---|
   | Emission | Spontaneous | Stimulated |
   | Light | Incoherent | Coherent |
   | Spectral width | Wide, 30-50 nm | Very narrow, 1-2 nm |
   | Beam | Spreads in all directions | Narrow, directional |
   | Threshold current | None | Yes — lases only above it |
   | Optical cavity | None | Two mirrored facets |
   | Modulation speed | Up to ~200 Mbps | Several Gbps |
   | Fibre used with | Multimode, short distance | Single-mode, long distance |
   | Safety | Safe to look at | Can damage the eye |
   | Uses | Indicators, displays, lighting, short-haul fibre | Long-haul fibre, CD/DVD, barcode readers, surgery |

   Functions of a diode: `rectification` (AC to DC — the main use), `voltage regulation` (Zener, held in reverse breakdown), `clipping`/`clamping` (shaping a waveform), `protection` (blocks a reversed supply; a free-wheeling diode absorbs an inductive spike), `switching` (fast on/off element), `light emission/detection` (LED, laser diode, photodiode, solar cell), `tuning` (varactor as a voltage-controlled capacitor), and `demodulation` (recovering audio from an AM carrier).

## Digital-to-Analog & Analog-to-Digital Converters (DAC/ADC) (4)

1. **You are required to convert a 12-bit digital number to an analogue voltage over the voltage range of 0 to 3.3V with a Digital-to-Analogue Converter (DAC). What is the resolution of the analogue output?** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 419 (ET: BIBM)]*

Answer: The `resolution` of a DAC is the smallest change in output voltage produced by a change of `1` in the digital input — the size of one step.
   ```
      Resolution = Full-scale voltage range / (2^n - 1)
   ```
   - `2^n` is the number of distinct codes, so there are `2^n - 1` steps between the lowest and the highest output.

   Given
   ```
      n = 12 bits
      Output range = 0 V to 3.3 V , so V(FS) = 3.3 V
   ```

   Step 1 — number of codes and steps
   ```
      Number of codes = 2^12 = 4096        (0000 0000 0000 to 1111 1111 1111)
      Number of steps = 4096 - 1 = 4095
   ```

   Step 2 — resolution
   ```
      Resolution = 3.3 / 4095
                 = 0.0008059 V
   ```
   ```
      Resolution = 0.806 mV = 806 microvolts per bit
   ```

   Step 3 — check the end points
   ```
      Code 0000 0000 0000 (0)     ->  0 x 0.806 mV      = 0 V
      Code 1111 1111 1111 (4095)  ->  4095 x 0.806 mV   = 3.3 V      correct
   ```

   The alternative convention
   ```
      Some texts divide by 2^n instead of 2^n - 1 :

      3.3 / 4096 = 0.0008057 V = 0.806 mV

      The two answers agree to three decimal places, so either is accepted.
      Dividing by 2^n - 1 makes the highest code equal exactly full scale;
      dividing by 2^n makes the step size an exact binary fraction.
   ```

   Resolution as a percentage
   ```
      (1 / 4095) x 100 = 0.0244 %
   ```

   How resolution changes with the number of bits, over the same 0-3.3 V range
   ```
       8 bit :  3.3 / 255   = 12.94 mV
      10 bit :  3.3 / 1023  =  3.23 mV
      12 bit :  3.3 / 4095  =  0.806 mV
      16 bit :  3.3 / 65535 =  0.050 mV
   ```
   - Each extra bit `halves` the step size, so resolution improves exponentially with bit count.

   - Point worth noting: resolution is not the same as `accuracy`. Resolution is the smallest step the converter can produce; accuracy is how close the real output is to the ideal value, and it is limited by offset error, gain error, and differential and integral non-linearity.

2. **An 8 bit (Analog to Digital Converter) = 2.56v. Let the minimum analog voltage = 0v. Calculate binary data output if analog input=1.7** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)]*

Answer: An ADC divides its full-scale input range into `2^n` equal steps and outputs the code corresponding to the input level.
   ```
      Step size (resolution) = (V(max) - V(min)) / 2^n

      Digital output = (V(in) - V(min)) / step size
   ```

   Given
   ```
      n        = 8 bits
      V(max)   = 2.56 V        (full-scale reference)
      V(min)   = 0 V
      V(in)    = 1.7 V
   ```

   Step 1 — number of levels
   ```
      2^8 = 256 levels , codes 0 to 255
   ```

   Step 2 — step size
   ```
      Step = (2.56 - 0) / 256
           = 0.01 V
           = 10 mV per bit
   ```
   - This is a convenient reference voltage, chosen exactly so that one bit equals 10 mV.

   Step 3 — digital output in decimal
   ```
      D = (V(in) - V(min)) / step
        = (1.7 - 0) / 0.01
        = 170
   ```

   Step 4 — convert 170 to 8-bit binary
   ```
      170 / 2 = 85  r 0     (LSB)
       85 / 2 = 42  r 1
       42 / 2 = 21  r 0
       21 / 2 = 10  r 1
       10 / 2 =  5  r 0
        5 / 2 =  2  r 1
        2 / 2 =  1  r 0
        1 / 2 =  0  r 1     (MSB)

      Reading upward : 1010 1010
   ```
   ```
      Binary output = 1010 1010  =  (AA)16  =  170 decimal
   ```

   Verification
   ```
      1010 1010 = 128 + 32 + 8 + 2 = 170
      170 x 0.01 V = 1.70 V        matches the analogue input exactly
   ```

   Quantisation check
   ```
      1.7 V falls exactly on a step boundary, so there is no quantisation error here.

      In general the maximum quantisation error is +/- half a step
          = +/- 5 mV for this converter.
   ```

   Some other input values, for practice
   ```
      V(in) = 0.00 V  ->  code   0 = 0000 0000
      V(in) = 1.28 V  ->  code 128 = 1000 0000
      V(in) = 2.55 V  ->  code 255 = 1111 1111
      V(in) = 2.56 V  ->  saturates at 255; the top code represents 2.55 V
   ```
   - Point worth noting: the highest code represents `V(max) - one step`, not V(max) itself. Any input above 2.55 V is clipped to 1111 1111.

3. **Draw an ADC converter circuit which convert an analog signal to digital signal.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*

Answer: An `ADC` converts a continuously varying analogue voltage into a binary number. The most common exam circuit is the `successive approximation` type, which is what almost every microcontroller uses.

   Complete signal chain
   ```mermaid
   flowchart LR
       A[Analog input] --> B[Anti-aliasing<br/>low-pass filter]
       B --> C[Sample and Hold]
       C --> D[Comparator]
       D --> E[SAR logic]
       E --> F[Internal DAC]
       F --> D
       E --> G[Digital output]
   ```

   Successive Approximation Register (SAR) ADC
   ```
                           +-------------+
      Vin ---> S/H ------->|             |
                           | Comparator  |----+
                 +-------->|             |    |
                 |         +-------------+    |
                 |                            v
                 |                    +---------------+
                 |                    |  SAR control  |----> digital output
                 |                    |    logic      |      (n bits)
                 |                    +-------+-------+
                 |                            |
                 |         +----------------+ |
                 +---------|  internal DAC  |<+
                           +----------------+
                                   ^
                                V(ref)
   ```
   - Sample-and-hold freezes Vin; the SAR sets each bit from MSB to LSB, the DAC converts the trial code to a voltage, and the comparator keeps the bit as 1 if Vin exceeds it, else clears it to 0. It performs a `binary search`, so an n-bit conversion takes exactly n clock cycles.

   Worked example — 8-bit ADC, Vref = 2.56 V, Vin = 1.7 V (step = 2.56/256 = 10 mV)
   ```
      bit7 1000 0000=1.28V keep    bit6 1100 0000=1.92V clear   bit5 1010 0000=1.60V keep
      bit4 1011 0000=1.76V clear   bit3 1010 1000=1.68V keep    bit2 1010 1100=1.72V clear
      bit1 1010 1010=1.70V keep (equal)   bit0 1010 1011=1.71V clear

      Result = 1010 1010 = 170  ->  170 x 10 mV = 1.70 V     correct
   ```

   Simplest circuit — the flash (parallel) ADC
   ```
      V(ref)
        |
       ###
        +---------|\
       ###        | > comparator 3 ---+
        +---------|/                  |
       ###                            |    +---------+
        +---------|\                  +--->|         |
       ###        | > comparator 2 ------->| Priority|--- D1
        +---------|/                  +--->| encoder |--- D0
       ###                            |    +---------+
        +---------|\                  |
       ###        | > comparator 1 ---+
        +---------|/
       ###
        |         ^
       GND        |
                 Vin
   ```
   - A resistor ladder creates `2^n - 1` reference levels, one comparator per level, and a priority encoder turns the comparator outputs into a binary code. It converts in a `single clock cycle` — the fastest type — but needs 255 comparators for 8 bits, so it is used only for very high speed video and radar work.

   | Type | Speed | Resolution | Cost | Used in |
   |---|---|---|---|---|
   | Flash | Fastest | Low (up to 8 bit) | Very high | Video, radar |
   | SAR | Medium | 8 to 18 bit | Low | Microcontrollers, data acquisition |
   | Dual slope | Slow | Very high | Low | Digital multimeters |
   | Sigma-delta | Slow | Highest (24 bit) | Medium | Audio, precision measurement |

4. **(ক) A/D Converter দ্বারা কিভাবে একটি Analog signal Digital signal এ রূপান্তরিত করা হয়। ডায়াগ্রাম সহ লিখুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 776 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) An `A/D converter` turns a continuously varying analogue voltage into a binary number a computer can process. The conversion has four stages.

   ```mermaid
   flowchart LR
       A[Analog signal] --> B[Sampling]
       B --> C[Quantization]
       C --> D[Encoding]
       D --> E[Digital output]
   ```

   `Sampling` — the signal is measured at regular intervals, `f(s)` times per second, and a sample-and-hold circuit freezes each value while it is converted. `Nyquist theorem`: f(s) >= 2.f(max) (e.g. speech to 4 kHz sampled at 8 kHz; CD audio to 20 kHz at 44.1 kHz). Breaking this rule makes high frequencies fold back as false low ones — `aliasing` — so an anti-aliasing low-pass filter precedes the sampler.

   `Quantization` — each sample is rounded to the nearest of `2^n` levels, step size = (Vmax - Vmin)/2^n. This introduces `quantization error` (at most half a step); more bits reduce it: SNR(dB) = 6.02n + 1.76.

   `Encoding` — each level is written as an `n-bit binary number`, then delivered (`output`) in parallel or serially to the processor.

   Circuit — successive approximation ADC
   ```
                           +-------------+
      Vin ---> S/H ------->|             |
                           | Comparator  |----+
                 +-------->|             |    |
                 |         +-------------+    |
                 |                            v
                 |                    +---------------+
                 |                    |  SAR control  |---> digital output
                 |                    |    logic      |
                 |                    +-------+-------+
                 |         +----------------+ |
                 +---------|  internal DAC  |<+
                           +----------------+
                                   ^
                                V(ref)
   ```
   - The SAR sets the most significant bit, the DAC converts the trial code back to a voltage, and the comparator decides whether to keep or clear that bit. Repeating this for every bit is a `binary search`, so an n-bit conversion takes exactly n clock cycles.

   Worked example — 8-bit ADC, V(ref) = 2.56 V, V(in) = 1.7 V
   ```
      Step = 2.56 / 256 = 10 mV
      Code = 1.7 / 0.01 = 170 = 1010 1010

      Check : 170 x 10 mV = 1.70 V        correct
   ```

   Waveforms
   ```
      Analog       /‾‾\      /‾‾\
              ----/    \____/    \----

      Sampled      | | | | | | | | |      values taken at intervals of 1/fs

      Quantized    _|‾|_|‾‾|_|‾|__        each held at the nearest level

      Encoded      101 110 100 011 ...    the binary output
   ```

   - Points worth noting: `sampling rate` decides which frequencies survive, and `number of bits` decides how accurately each sample is represented. The reverse device is the `DAC`, which reconstructs the analogue waveform, and the two together form the basis of every digital audio, video and instrumentation system.

## AC Circuits & Power Analysis (2)

1. **A two-element series circuit has an average power of 940\text{W} and a power factor of 0.707 (leading). Determine the circuit elements if the applied voltage is V = 99\cos(600t + 30^\circ)\text{V}.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

Answer: A `leading` power factor means the current leads the voltage, so the circuit is `resistive-capacitive` — a resistor in series with a capacitor.

   Given
   ```
      P = 940 W ,  pf = 0.707 leading -> theta = -45 degrees ,  v(t) = 99 cos(600t + 30) V
      Vm = 99 V ,  omega = 600 rad/s
   ```

   Step 1 — RMS voltage
   ```
      V(rms) = Vm / sqrt(2) = 99 / 1.4142 = 70.00 V
   ```

   Step 2 — magnitude of the impedance
   ```
      |Z| = V(rms)^2 . cos(theta) / P = (70.00)^2 x 0.707 / 940 = 3464.3 / 940 = 3.686 ohms
   ```

   Step 3 — RMS current, as a check
   ```
      I(rms) = V(rms) / |Z| = 70.00 / 3.686 = 18.99 A
      check : P = V I cos(theta) = 70.00 x 18.99 x 0.707 = 940 W      correct
   ```

   Step 4 — resistance
   ```
      R = |Z| . cos(theta) = 3.686 x 0.707 = 2.606 ohms
   ```

   Step 5 — capacitive reactance (at 45 degrees, X = R)
   ```
      Xc = |Z| . sin(theta) = 3.686 x 0.707 = 2.606 ohms
   ```

   Step 6 — the capacitance
   ```
      C = 1 / (omega . Xc) = 1 / (600 x 2.606) = 0.0006395 F = 639.5 microfarads
   ```

   Answer
   ```
      R = 2.61 ohms (resistor) ,  C = 639.5 uF (capacitor) , connected in series.

      Check : Z = R - j Xc = 2.606 - j 2.606 = 3.686 angle -45 degrees ; pf = cos(-45) = 0.707 leading ;
              P = I(rms)^2 . R = (18.99)^2 x 2.606 = 940 W        all correct
   ```

   - A `leading` power factor always means a capacitive circuit; a `lagging` one would mean an inductor, with step 6 using `L = XL / omega` instead. At exactly 0.707 the phase angle is 45 degrees, so `R and X are equal` — a useful shortcut worth spotting immediately.

2. **RLC সার্কিট কী? বৈদ্যুতিক সার্কিটে ট্রানজিস্টরের ভূমিকা কী?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 809-810 (ET: IBA)]*

Answer: (Answered in English, as required for IT topics.) RLC circuit
   - An `RLC circuit` contains a `resistor (R)`, `inductor (L)` and `capacitor (C)` together — the basic circuit for tuning, filtering and oscillation.
   ```
      Series RLC
      ---/\/\/\---(((((---||---
           R         L      C
   ```
   - Each element's opposition varies with frequency: R is constant; X(L) = 2 pi f L rises with frequency; X(C) = 1/(2 pi f C) falls with frequency. Total impedance Z = sqrt(R^2 + (XL-XC)^2), phase theta = arctan((XL-XC)/R).

   Resonance — at `f(r) = 1/(2 pi sqrt(LC))` the two reactances cancel (XL = XC). In a `series` RLC at resonance, Z = R (minimum), current is maximum, pf = 1; in a `parallel` RLC the opposite holds (Z maximum, current minimum).
   ```
      Q = (1/R) sqrt(L/C)          Bandwidth = f(r) / Q
   ```
   - Uses: tuning a radio/TV to a station, band-pass/band-stop filters, oscillators, impedance matching.

   Role of a transistor in an electrical circuit
   - A `transistor` is a three-terminal semiconductor device that uses a small input signal to control a much larger current. Its two fundamental roles are `switching` (cut-off = OFF/open switch, saturation = ON/closed switch — the basis of every logic gate) and `amplification` (biased in the active region, `IC = beta.IB` makes the collector current a magnified copy of the base current, beta ~50-300 — used in audio amplifiers, radio receivers, instrumentation).
   - Other roles: `oscillator` (with an RLC or crystal feedback network), `voltage regulator` (series-pass transistor), `current source`, `buffer` (emitter follower), and modulation/demodulation in communication circuits.
   - The two meet in a `tuned amplifier`: an RLC circuit selects one frequency and the transistor amplifies it — the basis of a radio receiver.

## Operational Amplifiers (Op-Amp) (2)

1. **Assuming Ideal Op Amps, Find The Voltage Gain V_o/V_i of the following circuit.** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*

Answer: The question is `incomplete` — the op-amp circuit diagram is not present. The gain of every standard ideal op-amp configuration is derived below, so the right formula can be applied to whichever circuit was printed.

   Two golden rules for an ideal op-amp: (1) no current flows into either input (infinite input impedance); (2) with negative feedback, the two inputs sit at the same voltage (a `virtual short`). Every gain formula below follows from these two rules alone.

   Inverting amplifier
   ```
           Rf
      +---/\/\/\---+
      |            |
      |   Rin      |
      Vi--/\/\/\---+---|-\
                       |  \
                       |   >--- Vo
                       |  /
                GND ---|+/
   ```
   ```
      The '-' input is a virtual earth, so it sits at 0 V.
      Current through Rin = Vi/Rin , and it must all flow through Rf.

           Vi/Rin = -Vo/Rf

      Av = Vo/Vi = -Rf / Rin
   ```
   - The minus sign is a `180 degree phase inversion`.

   Non-inverting amplifier
   ```
      Vi ---|+\
            |  \
            |   >--- Vo
            |  /
         +--|-/
         |      Rf
         +----/\/\/\---+--- Vo
         |             |
        Rin            |
         |             |
        GND ----------+
   ```
   ```
      The '-' input equals Vi (virtual short), and it is the tap of a
      divider from Vo :

           Vi = Vo x Rin/(Rin + Rf)

      Av = Vo/Vi = 1 + Rf / Rin
   ```
   - Always `positive` and always `at least 1`.

   Other standard configurations, from the same two rules
   ```
      Voltage follower (buffer)   : Rf=0, Rin=inf  ->  Av = 1                (impedance conversion only)
      Summing amplifier           : Vo = -Rf (V1/R1 + V2/R2 + V3/R3)
      Difference amplifier        : Vo = (Rf/R1)(V2 - V1)   when R1=R3, R2=Rf
      Integrator (C in feedback)  : Vo = -(1/(Rin C)) integral of Vi dt
      Differentiator (C at input) : Vo = -(Rf C) dVi/dt
      Cascaded stages             : Av(total) = Av1 x Av2 x Av3 ...   (product of individual gains)
   ```

   How to identify which formula applies
   ```
      Input fed to the '-' terminal only     -> INVERTING , -Rf/Rin
      Input fed to the '+' terminal only     -> NON-INVERTING , 1+Rf/Rin
      Output tied straight back to '-'       -> FOLLOWER , gain 1
      Several inputs joined at '-'           -> SUMMING
      Inputs at BOTH terminals               -> DIFFERENTIAL
      Capacitor in the feedback path         -> INTEGRATOR
      Capacitor at the input                 -> DIFFERENTIATOR
      Several op-amps in a chain             -> MULTIPLY the gains
   ```

   - Ideal characteristics to state alongside the answer: infinite open-loop gain, infinite input impedance, zero output impedance, infinite bandwidth and infinite CMRR — real devices approach this closely enough that these formulas stay accurate to a fraction of a per cent.

2. **একটি Operational Amplifier এর প্রধান বৈশিষ্ট কী কী? AC Power কিভাবে DC পাওয়ারে রূপান্তরিত হয়?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 809 (ET: IBA)]*

Answer: (Answered in English, as required for IT topics.) Main characteristics of an operational amplifier
   - An `op-amp` is a high-gain DC-coupled differential amplifier with two inputs — inverting (-) and non-inverting (+) — and one output.
   ```
      V1 ---|-\
            |  \
            |   >--- Vo = A (V2 - V1)
            |  /
      V2 ---|+/
   ```

   Ideal characteristics (real-world value in brackets)
   ```
      Open-loop gain A : infinite (10^5-10^6)       Input impedance Zin : infinite (1M-10^12 ohm)
      Output impedance Zo : zero (20-100 ohm)       Bandwidth : infinite (limited by GBW)
      CMRR : infinite (90-120 dB)                   Offset voltage/current, drift : zero
   ```
   - Two golden rules used in every analysis: (1) no current flows into either input; (2) with negative feedback, the two inputs sit at the same voltage (`virtual short`).
   - Practical points: the gain is so high the op-amp is almost never used open loop — negative feedback sets a stable, predictable gain instead; `differential input` rejects any signal common to both inputs (kills common noise); wide supply range (+/-5 to +/-18 V, or single-supply); `slew rate` limits how fast the output can change; `gain-bandwidth product` is constant, so more closed-loop gain means less usable bandwidth.
   - Common configurations: inverting (Av = -Rf/Rin), non-inverting (Av = 1+Rf/Rin), follower (Av = 1), plus summing, difference, integrator, differentiator, comparator, active filter and oscillator.

   How AC power is converted to DC power
   - `Rectification`, in four stages: `transformer` (steps 220 V down, isolates from mains) -> `rectifier` -> `filter` -> `regulator`. A `bridge rectifier` of four diodes uses both halves of each cycle:
   ```
                 D1        D2
           +----|>|---+---|<|----+
           |          |          |
      AC ~ |          +--- + ----|--- output
           |          |          |
           +----|<|---+---|>|----+
                 D3        D4
   ```
   - The `filter` (a large electrolytic capacitor) charges at each peak and discharges slowly between peaks:
   ```
      Before filter   /‾\/‾\/‾\      pulsating
      After filter    ‾‾‾\_/‾‾‾      nearly flat, with a small ripple
   ```
   - The `regulator` (a zener diode or an IC such as 7805/7812) then holds the output fixed. Modern equipment uses an `SMPS` instead: rectify, chop at 20-100 kHz, pass through a small ferrite transformer, rectify again — tiny and 80-90% efficient versus 50-60% for a linear supply.

## Sensor Circuits & Automated Control Systems (2)

1. **Design and implement an automated street light control system. The system should ensure that the street lights remain off during the presence of sunlight and automatically turn on in the absence of sunlight (i.e., during nighttime or low ambient light conditions).** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*

Answer: The system must turn the street light `off in daylight` and `on in darkness`, automatically. The sensing element is an `LDR` (Light Dependent Resistor), whose resistance falls when light falls on it.
   ```
      Bright light  ->  LDR resistance LOW   (about 1 k ohm)
      Darkness      ->  LDR resistance HIGH  (about 1 M ohm)
   ```

   Block diagram
   ```mermaid
   flowchart LR
       A[LDR sensor] --> B[Voltage divider]
       B --> C[Comparator / Schmitt trigger]
       C --> D[Transistor driver]
       D --> E[Relay]
       E --> F[Street lamp 220V]
   ```

   Circuit
   ```
           +5V
            |
           ###  LDR
           ###
            |
            +-------------------|+\
            |                   |  \  LM393
           ###  R1 = 10k        |   >------+
           ### (fixed)      +---|- /       |
            |               |   |  /       |
           GND              |   +-/        |
                           ###              |
                preset  ###  RV (threshold) |
                           ###              |
                           GND              |
                                            v
                                       +---/\/\/\--- base
                                       |    1k        |
                                       |             |<  Q1 (BC547)
                                       |              |
                                     (from            |
                                  comparator)        +--- relay coil ---+5V (12V)
                                                      |     with a flyback
                                                     GND    diode across it

      Relay contacts (NO) switch the 220 V mains to the street lamp.
   ```

   How it works: LDR and R1 form a divider whose junction voltage is HIGH in daylight (LDR resistance low) and LOW at night (LDR resistance high). The comparator compares this to a threshold set by preset RV — output LOW (Q1 off) in daylight, output HIGH (Q1 on) at night. Q1 energises the relay, closing its normally-open contacts to feed the lamp; at sunrise the process reverses and the lamp turns off.

   Microcontroller version (Arduino)
   ```c
   const int LDR = A0;        // LDR divider output
   const int RELAY = 8;       // relay drive pin
   const int THRESHOLD = 400; // set by measurement at dusk

   void setup() {
       pinMode(RELAY, OUTPUT);
   }

   void loop() {
       int light = analogRead(LDR);      // 0 = dark, 1023 = bright

       if (light < THRESHOLD)
           digitalWrite(RELAY, HIGH);    // dark  -> lamp ON
       else
           digitalWrite(RELAY, LOW);     // light -> lamp OFF

       delay(1000);                      // check once per second
   }
   ```

   Design points that earn marks
   - `Hysteresis` (via a Schmitt trigger) prevents flicker at dusk as the light hovers near the threshold — e.g. turn on below 380, turn off above 420.
   - A `flyback diode` across the relay coil protects the transistor from the inductive spike at switch-off.
   - A short `delay` before acting avoids false triggers from a passing headlight or lightning.
   - A `PIR motion sensor` can dim the lamp all night and brighten it only when someone approaches — the standard energy-saving design; an `SSR`/triac can replace the mechanical relay for silent, longer-life operation; and the mains side must stay `isolated` from the low-voltage side (which the relay/opto-triac provides).

2. **Which signal a sensor could to send the signal to microcontroller if the sensor finds any gas leakage point?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 861 (ET: N/A)]*

Answer: A gas sensor sends the microcontroller either an `analogue voltage` or a `digital HIGH/LOW`, depending on which output pin is used. Almost every gas sensor module — the `MQ` series is the standard — provides `both`.

   The two output signals
   ```
      AO (analogue) : voltage that RISES with gas concentration, 0-5 V, read by the ADC — gives the actual level.
      DO (digital)  : a single bit from an on-board LM393 comparator vs a preset threshold — usually ACTIVE LOW (LOW when gas is detected).
   ```

   How it works: the MQ-series sensor uses a heated `tin dioxide (SnO2)` element whose resistance is high in clean air and `falls` when a combustible gas (LPG, methane, CO) adsorbs on it; a load resistor converts that change to a voltage — no gas: high resistance, low AO, DO=HIGH; gas leak: low resistance, high AO, DO=LOW.

   Connection
   ```
           MQ-6 / MQ-2 module            Microcontroller
         +---------------+
         | VCC           |----------------- 5 V
         | GND           |----------------- GND
         | AO  (analog)  |----------------- A0   (ADC input)
         | DO  (digital) |----------------- D2   (interrupt-capable pin)
         +---------------+
   ```

   Code
   ```c
   const int AO = A0, DO = 2, BUZZER = 8, VALVE = 9;
   const int THRESHOLD = 300;         // set by calibration

   void setup() {
       pinMode(DO, INPUT);
       pinMode(BUZZER, OUTPUT);
       pinMode(VALVE, OUTPUT);
       Serial.begin(9600);
   }

   void loop() {
       int level = analogRead(AO);            // 0 to 1023, gas concentration
       int alarm = digitalRead(DO);           // LOW when gas is detected

       if (level > THRESHOLD || alarm == LOW) {
           digitalWrite(BUZZER, HIGH);        // sound the alarm
           digitalWrite(VALVE, HIGH);         // close the solenoid valve
       } else {
           digitalWrite(BUZZER, LOW);
       }
       delay(500);
   }
   ```

   | Point | Analogue (AO) | Digital (DO) |
   |---|---|---|
   | Signal | Continuous voltage | Single bit, HIGH or LOW |
   | Information | Actual concentration | Only "gas present / absent" |
   | Threshold set by | Software, changeable | Hardware preset on the module |
   | Can trigger an interrupt | No | Yes |
   | Best for | Monitoring, graded alarms | Simple alarm, waking the MCU from sleep |

   - Best practice: use `both` — wire `DO` to an interrupt so the microcontroller reacts instantly, and read `AO` to log concentration and distinguish a small leak from a dangerous one. MQ sensors need a `warm-up` (20 s to a few minutes), are `not gas-selective`, and drift with temperature/humidity — a real installation calibrates them or uses an industrial `4-20 mA` transmitter instead of a hobby module.

## Circuit Theorems (Thevenin, Norton, Superposition) (2)

1. **Find current across 2 \Omega resistor using Thevenin Theorem:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 417 (ET: BUET)]*

Answer: The question is `incomplete` — the circuit diagram is not present. Thevenin's theorem and the full procedure are set out below with a worked example, so it can be applied to whichever circuit was printed.

   Thevenin's theorem
   ```
      Any linear two-terminal network of sources and resistances can be
      replaced, as seen from those two terminals, by a SINGLE voltage
      source V(th) in SERIES with a SINGLE resistance R(th).

           R(th)
      +---/\/\/\---+------o A
      |            |
     (+) V(th)   [ R(L) ]      the load reconnected here
      |            |
      +------------+------o B
   ```
   ```
      Then the load current is simply

           I(L) = V(th) / (R(th) + R(L))
   ```

   The five-step procedure
   ```
      1. REMOVE the load resistor (here the 2 ohm) from the circuit.

      2. Find V(th) = the OPEN-CIRCUIT voltage across the two terminals
         where the load was. Use KVL, nodal analysis or a voltage divider.

      3. Find R(th) = the resistance looking back into those terminals
         with EVERY INDEPENDENT SOURCE SET TO ZERO :
              a voltage source becomes a SHORT circuit
              a current source becomes an OPEN circuit
         Then reduce the remaining resistors by series and parallel rules.

      4. Draw the Thevenin equivalent : V(th) in series with R(th).

      5. RECONNECT the load and compute
              I(L) = V(th)/(R(th) + R(L))
   ```

   Worked example
   ```
           R1 = 4 ohm        R3 = 1 ohm
      +---/\/\/\-----+------/\/\/\----+---o A
      |              |                |
     (+) 12 V    [ R2 = 6 ohm ]    [ R(L) = 2 ohm ]
      |              |                |
      +--------------+----------------+---o B

      Find the current through the 2 ohm resistor.
   ```
   Step 1 — remove the 2 ohm load
   ```
           4 ohm             1 ohm
      +---/\/\/\-----+------/\/\/\----o A
      |              |
     (+) 12 V    [ 6 ohm ]
      |              |
      +--------------+----------------o B
   ```
   Step 2 — find V(th), the open-circuit voltage
   ```
      With the load removed, NO current flows through R3, so there is no
      drop across it. V(th) is therefore the voltage across R2, given by
      the voltage divider :

      V(th) = 12 x R2/(R1 + R2) = 12 x 6/(4 + 6) = 12 x 0.6 = 7.2 V
   ```
   Step 3 — find R(th)
   ```
      SHORT the 12 V source and look back in from A-B :

      R1 (4) is now in PARALLEL with R2 (6) :
           (4 x 6)/(4 + 6) = 24/10 = 2.4 ohms

      R3 (1) is in SERIES with that :
           R(th) = 2.4 + 1 = 3.4 ohms
   ```
   Step 4 — the Thevenin equivalent
   ```
           R(th) = 3.4 ohm
      +---/\/\/\---+------o A
      |            |
     (+) 7.2 V   [ 2 ohm ]
      |            |
      +------------+------o B
   ```
   Step 5 — the load current
   ```
      I(L) = V(th) / (R(th) + R(L))
           = 7.2 / (3.4 + 2)
           = 7.2 / 5.4
      I(L) = 1.333 A

      Voltage across the 2 ohm = 1.333 x 2 = 2.67 V
   ```

   Why the theorem is worth using
   ```
      If only ONE branch current is wanted, Thevenin avoids solving the
      whole network. It is especially valuable when the LOAD is going to
      be CHANGED several times - V(th) and R(th) are found once, and each
      new load needs only one division.
   ```

   Related results
   ```
      NORTON  : the dual - a current source I(N) in PARALLEL with R(N)
                I(N) = V(th)/R(th)  ,  R(N) = R(th)

      MAXIMUM POWER TRANSFER : the load receives maximum power when
                R(L) = R(th) , and that power is V(th)^2/(4 R(th))

      SUPERPOSITION : with several sources, find the response to each one
                separately (the others set to zero) and add the results.
   ```

2. **Find the Value of I_{ab} using Norton's Theorem.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*

Answer: The question is `incomplete` — the circuit diagram is not present. Norton's theorem and the complete procedure are set out below with a worked example.

   Norton's theorem
   ```
      Any linear two-terminal network of sources and resistances can be
      replaced, as seen from those terminals, by a SINGLE current source
      I(N) in PARALLEL with a SINGLE resistance R(N).

           +---------------+--------+------o a
           |               |        |
         (   )            ###      ###
         ( ^ ) I(N)       ### R(N) ### R(L)
         (   )            ###      ###
           |               |        |
           +---------------+--------+------o b
   ```
   ```
      Then the load current follows from the current divider :

           I(ab) = I(N) x R(N)/(R(N) + R(L))
   ```

   The five-step procedure
   ```
      1. REMOVE the load resistor from between a and b.

      2. Find I(N) = the SHORT-CIRCUIT current. Place a short across a-b
         and compute the current through that short.

      3. Find R(N) = the resistance looking back into a-b with EVERY
         INDEPENDENT SOURCE SET TO ZERO :
              a voltage source becomes a SHORT
              a current source becomes an OPEN
         R(N) is identical to R(th).

      4. Draw the Norton equivalent : I(N) in parallel with R(N).

      5. RECONNECT the load and apply the current divider.
   ```

   Worked example
   ```
           R1 = 4 ohm         R3 = 1 ohm
      +---/\/\/\-----+-------/\/\/\----+---o a
      |              |                 |
     (+) 12 V    [ R2 = 6 ohm ]     [ R(L) = 2 ohm ]
      |              |                 |
      +--------------+-----------------+---o b

      Find I(ab), the current through the 2 ohm resistor.
   ```
   Step 1 and 2 — find I(N), the short-circuit current
   ```
      Remove the 2 ohm and SHORT a to b. R3 (1 ohm) is now in parallel
      with R2 (6 ohm) :

           R2 parallel R3 = (6 x 1)/(6 + 1) = 6/7 = 0.857 ohms

      Total resistance seen by the source = 4 + 0.857 = 4.857 ohms
      Source current = 12/4.857 = 2.471 A

      That current divides between R2 and R3. The short-circuit current
      is the part flowing through R3 :

           I(N) = 2.471 x R2/(R2 + R3) = 2.471 x 6/7 = 2.118 A
   ```
   Step 3 — find R(N)
   ```
      SHORT the 12 V source and look back from a-b :

           R1 (4) parallel R2 (6) = 24/10 = 2.4 ohms
           R3 (1) in SERIES with that

           R(N) = 2.4 + 1 = 3.4 ohms
   ```
   Step 4 — the Norton equivalent
   ```
           +--------+--------+------o a
           |        |        |
         (   )     ###      ###
         ( ^ )     ### 3.4  ### 2 ohm
         (   )2.118A###      ###
           |        |        |
           +--------+--------+------o b
   ```
   Step 5 — the load current, by the current divider
   ```
      I(ab) = I(N) x R(N)/(R(N) + R(L))
            = 2.118 x 3.4/(3.4 + 2)
            = 2.118 x 3.4/5.4
            = 2.118 x 0.6296
      I(ab) = 1.333 A
   ```

   Cross-check with Thevenin
   ```
      V(th) = I(N) x R(N) = 2.118 x 3.4 = 7.2 V
      R(th) = R(N) = 3.4 ohms

      I(ab) = V(th)/(R(th) + R(L)) = 7.2/5.4 = 1.333 A     same answer
   ```
   - The two theorems are `duals`, and this identity is the standard way to verify either result.

   Norton versus Thevenin

   | Point | Thevenin | Norton |
   |---|---|---|
   | Equivalent | Voltage source in `series` with R | Current source in `parallel` with R |
   | Source found from | The `open-circuit` voltage | The `short-circuit` current |
   | Resistance | R(th) | R(N) = R(th) — identical |
   | Conversion | V(th) = I(N) x R(N) | I(N) = V(th) / R(th) |
   | Load current | V(th)/(R(th) + R(L)) | I(N) x R(N)/(R(N) + R(L)) |
   | Easier when | The load is in series | The load is in parallel |

   - Both theorems apply only to `linear` networks, and both replace the network only `as seen from the two chosen terminals` — the internal currents and voltages of the original circuit are not reproduced by the equivalent.

## Electrical Machines (Motors & Alternators) (1)

1. **A 3phase 12 pole alternator running at 500 rpm supplying power to an 8 pole induction motor. If ship is 3% what is the full load speed of the motor?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1054 (ET: BUET)]*

Answer: The alternator sets the supply frequency; that frequency then sets the induction motor's synchronous speed, and the slip reduces it to the actual running speed.

   Given
   ```
      Alternator : 3-phase , P1 = 12 poles , N1 = 500 rpm
      Motor      : P2 = 8 poles , slip s = 3 % = 0.03
      Find       : full-load speed of the motor
   ```

   Step 1 — supply frequency generated by the alternator
   ```
      f = (P1 x N1) / 120

        = (12 x 500) / 120
        = 6000 / 120
      f = 50 Hz
   ```

   Step 2 — synchronous speed of the induction motor
   ```
      Ns = (120 x f) / P2

         = (120 x 50) / 8
         = 6000 / 8
      Ns = 750 rpm
   ```

   Step 3 — full-load speed from the slip
   ```
      slip  s = (Ns - N) / Ns

      so    N = Ns (1 - s)

        N = 750 (1 - 0.03)
          = 750 x 0.97
      N = 727.5 rpm
   ```

   Answer
   ```
      Supply frequency          f  = 50 Hz
      Synchronous speed         Ns = 750 rpm
      Full-load speed of motor  N  = 727.5 rpm
   ```

   Verification
   ```
      Slip speed  = Ns - N = 750 - 727.5 = 22.5 rpm
      Slip        = 22.5 / 750 = 0.03 = 3 %        correct

      Rotor frequency f(r) = s . f = 0.03 x 50 = 1.5 Hz
   ```

   Formulas used
   ```
      Alternator :  f  = P N / 120        (N in rpm, P = number of poles)
      Motor      :  Ns = 120 f / P
      Slip       :  s  = (Ns - N) / Ns    ->  N = Ns (1 - s)
   ```

   - Points to note: an induction motor `can never run at synchronous speed`. If the rotor reached Ns there would be no relative motion, so no EMF would be induced in the rotor and no torque would be produced. Some slip is therefore essential, typically 2 to 5 per cent at full load and nearly zero at no load.
