<!-- TOC START -->
**Table of Contents** — 9 subtopics · 39 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Electrical Circuits & Protection Devices](#electrical-circuits--protection-devices-13) | 13 |
| 2 | [Transistors (BJT & FET)](#transistors-bjt--fet-9) | 9 |
| 3 | [Semiconductor Devices & Diodes](#semiconductor-devices--diodes-4) | 4 |
| 4 | [Digital-to-Analog & Analog-to-Digital Converters (DAC/ADC)](#digital-to-analog--analog-to-digital-converters-dacadc-4) | 4 |
| 5 | [AC Circuits & Power Analysis](#ac-circuits--power-analysis-2) | 2 |
| 6 | [Operational Amplifiers (Op-Amp)](#operational-amplifiers-op-amp-2) | 2 |
| 7 | [Sensor Circuits & Automated Control Systems](#sensor-circuits--automated-control-systems-2) | 2 |
| 8 | [Circuit Theorems (Thevenin, Norton, Superposition)](#circuit-theorems-thevenin-norton-superposition-2) | 2 |
| 9 | [Electrical Machines (Motors & Alternators)](#electrical-machines-motors--alternators-1) | 1 |

<!-- TOC END -->

---

## Electrical Circuits & Protection Devices (13)

1. Differentiate between a Fuse and a Miniature Circuit Breaker (MCB). Which one is more suitable for modern office electrical installations and why? *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

   Answer: Both protect a circuit from `overcurrent`. The difference is how they do it and whether they survive the event.

   Fuse
   - A thin metal wire or strip that `melts` when the current exceeds its rating, breaking the circuit.
   - It is a `one-time` device: once blown it must be replaced.
   - Very fast on a large short-circuit current, and very cheap.
   - No moving parts, so nothing to wear out — but also no indication of which circuit failed beyond the blown element.

   MCB (Miniature Circuit Breaker)
   - An electromechanical switch that `trips` and opens the circuit, then is `reset` by hand.
   - It has `two` sensing elements:
   ```
   Thermal (bimetallic strip) : responds to a sustained OVERLOAD, with a delay
   Magnetic (solenoid)        : responds to a SHORT CIRCUIT, almost instantly
   ```
   - The handle shows clearly which circuit tripped, and the same breaker also works as an isolating switch.

   Difference

   | Point | Fuse | MCB |
   |---|---|---|
   | Operation | Wire melts | Mechanical contacts trip open |
   | Reusable | No — replace after every fault | Yes — just reset the handle |
   | Reset time | Minutes; a spare must be at hand | Seconds |
   | Fault indication | Poor; must be inspected | Clear — the handle drops |
   | Sensing | One characteristic only | Separate thermal and magnetic |
   | Accuracy | Rating drifts with age and heat | Stable, calibrated trip curve |
   | Acts as a switch | No | Yes, doubles as an isolator |
   | Initial cost | Low | Higher |
   | Long-run cost | Replacement fuses, downtime | One-time |
   | Safety | Risk of a wrong-rated wire being fitted | Rating is fixed and cannot be tampered with |
   | Speed on short circuit | Very fast (HRC fuses fastest) | Fast, though slightly slower than an HRC fuse |
   | Life | Single use | Thousands of operations |

   Which suits a modern office — the `MCB`
   - `Fast recovery.` An office cannot wait while someone finds a spare fuse of the right rating; the MCB is reset in seconds and work continues.
   - `No tampering.` The classic and dangerous habit of replacing a blown fuse with a thicker wire or a nail is impossible with an MCB, because its rating is built in.
   - `Clear diagnosis.` The tripped handle identifies the faulty circuit at a glance, which matters in a distribution board serving many rooms.
   - `Doubles as an isolator`, so a circuit can be switched off safely for maintenance without extra hardware.
   - `Correct protection for electronic loads.` Computers and UPS systems draw a large `inrush current` at switch-on. A type-C MCB tolerates that inrush but still trips on a real fault, whereas a fuse sized to survive the inrush is too slow for genuine overloads.
   - `Combines with an RCCB/RCD` in the same board to give earth-leakage protection for personnel — the standard modern arrangement.

   - Fuses are still used where they are best: as HRC fuses in main incomers and in high-fault-level industrial supplies, where their extremely fast short-circuit clearing outperforms an MCB.

2. **Find the Norton equivalent circuit for a DC power supply that has a 30 V terminal voltage when delivering 400mA and a 28V terminal voltage. When delivering 600mA.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1436 (ET: BUET)]*

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

3. **Which Transformer is used in computer?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*

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

4. **What is the name of AC current to DC current?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*

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

5. **How to AC converted into DC?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*

   Answer: AC is converted to DC by `rectification`. A complete supply has four stages.
   ```
      AC 220 V --> Transformer --> Rectifier --> Filter --> Regulator --> steady DC
                   (step down)    (AC to DC)   (smooth)   (hold fixed)
   ```

   Stage 1 — Transformer
   - Steps the 220 V mains down to a low AC voltage, say 12 V, and gives `galvanic isolation` from the mains for safety.
   ```
      Vs / Vp = Ns / Np
   ```

   Stage 2 — Rectifier
   - Diodes conduct in one direction only, so they turn the alternating waveform into a one-directional (pulsating) DC.

   `Half-wave rectifier` — 1 diode
   ```
      AC ---|>|---+------ output
                 ###
                 ### R(load)
      AC --------+------
   ```
   - Passes only the positive half of each cycle. Output frequency = 50 Hz, and half the input is wasted.

   `Full-wave bridge rectifier` — 4 diodes, the practical choice
   ```
                 D1        D2
           +----|>|---+---|<|----+
           |          |          |
      AC ~ |          +---- + ---|--- output
           |          |          |
           +----|<|---+---|>|----+
                 D3        D4            output frequency = 100 Hz
   ```
   - Both halves of the input are used, so the output is smoother and the transformer is used more efficiently. No centre tap is needed.

   Stage 3 — Filter
   - A large electrolytic capacitor across the output charges at each peak and discharges slowly between peaks, filling in the gaps.
   ```
      Before filter    /‾\/‾\/‾\/‾\        pulsating
      After filter     ‾‾‾\_/‾‾‾\_/‾‾      nearly flat, small ripple
   ```
   ```
      Ripple factor = V(rms ripple) / V(dc)

      Half-wave  : 1.21          Full-wave : 0.48      (before filtering)
   ```
   - A bigger capacitor gives less ripple. An LC or pi filter reduces it further.

   Stage 4 — Regulator
   - Holds the output constant when the load or the mains voltage changes. A `zener diode` for small loads, or a three-terminal IC such as `7805` (+5 V) and `7812` (+12 V).

   Modern method — SMPS
   ```
      Mains --> rectify --> chop at 20-100 kHz --> small ferrite transformer
            --> rectify --> filter --> feedback-regulated DC output
   ```
   - Used in every computer power supply, mobile charger and laptop adapter. Because the transformer runs at high frequency it is tiny, and efficiency reaches 80-90 per cent instead of the 50-60 per cent of a linear supply.

   - Summary: `rectifier` makes the current one-directional, `filter` smooths it, and `regulator` keeps it steady. All three are needed — a rectifier alone gives pulsating DC, not usable DC.

6. **Find R and I from a circuit.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*

   Answer: The question is `incomplete` — the circuit diagram is not present. The complete method for finding an unknown resistance and current is given below with a worked example.

   The three laws every such problem uses
   ```
      OHM'S LAW        V = I R          ,  I = V/R  ,  R = V/I

      KIRCHHOFF'S CURRENT LAW (KCL)
           The sum of currents ENTERING a node equals the sum LEAVING it.
           sum I(in) = sum I(out)

      KIRCHHOFF'S VOLTAGE LAW (KVL)
           Round any closed loop, the sum of all voltages is zero.
           sum V = 0
   ```

   Series and parallel combination
   ```
      SERIES   :  R(eq) = R1 + R2 + R3 + ...
                  the SAME current flows through each
                  the voltage DIVIDES

      PARALLEL :  1/R(eq) = 1/R1 + 1/R2 + 1/R3 + ...
                  two resistors :  R(eq) = R1 R2 / (R1 + R2)
                  the SAME voltage across each
                  the current DIVIDES
   ```

   Worked example
   ```
           +----[ R1 = 4 ohm ]----+----[ R = ? ]----+
           |                      |                 |
         (+) 24 V              [ R2 = 12 ohm ]      |
           |                      |                 |
           +----------------------+-----------------+

      Given : the total current drawn from the source is I = 3 A
      Find  : R , and the current through each branch
   ```
   Step 1 — total resistance from Ohm's law
   ```
      R(total) = V / I = 24 / 3 = 8 ohms
   ```
   Step 2 — express R(total) in terms of the unknown
   ```
      R2 is in parallel with R , and that combination is in series with R1 :

      R(total) = R1 + (R2 R)/(R2 + R)

           8 = 4 + (12 R)/(12 + R)
           4 = 12R / (12 + R)
           4(12 + R) = 12R
           48 + 4R = 12R
           48 = 8R
           R = 6 ohms
   ```
   Step 3 — the branch currents
   ```
      Parallel combination = (12 x 6)/(12 + 6) = 72/18 = 4 ohms
      Voltage across the parallel section = I x 4 = 3 x 4 = 12 V

      I through R2 = 12 / 12 = 1 A
      I through R  = 12 / 6  = 2 A
      Check : 1 + 2 = 3 A = total current       correct  (KCL)
   ```
   Step 4 — verify with KVL
   ```
      Round the loop :  24 - (3 x 4) - 12 = 24 - 12 - 12 = 0     correct
   ```

   The general procedure
   ```
      1. Label every node and assume a direction for every current.
      2. Reduce any obvious series and parallel groups first.
      3. Apply KCL at each node and KVL round each independent loop.
      4. Solve the simultaneous equations for the unknowns.
      5. VERIFY : substitute the answers back and confirm that KCL holds
         at every node and KVL round every loop, and that the power
         delivered equals the power dissipated.
   ```

   Other techniques for a harder network
   ```
      Voltage divider :  V(R2) = V x R2/(R1 + R2)
      Current divider :  I(R1) = I x R2/(R1 + R2)
      Mesh analysis   :  KVL round each mesh, solve for the mesh currents
      Node analysis   :  KCL at each node, solve for the node voltages
      Thevenin        :  replace the network by V(th) in series with R(th)
      Norton          :  replace it by I(N) in parallel with R(N)
      Superposition   :  one source at a time, then add the results
   ```

7. **Audio Frequency ও Radio Frequency এর মধ্যেকার পার্থক্য লিখুন। ১০ ওহমের ১০টি ট্রানজিস্টর কোন সিরিজে সংযুক্ত হলে তাতে রেজিস্ট্যান্স কত হবে?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 810 (ET: IBA)]*

   Answer: (Answered in English, as required for IT topics.) Part 1 — Audio frequency versus Radio frequency

   `Audio frequency (AF)`
   - The band of frequencies the human ear can hear: `20 Hz to 20 kHz`.
   - It is a `mechanical` (pressure) wave in air, but the electrical signal that represents it is also called an audio-frequency signal.
   - It cannot travel far as a radio wave, because an antenna for 1 kHz would have to be tens of kilometres long.

   `Radio frequency (RF)`
   - The band used for wireless transmission: about `3 kHz to 300 GHz`, with the practical broadcast range starting near 30 kHz.
   - It is an `electromagnetic` wave and travels through air, vacuum and space at the speed of light.
   - Sub-bands: LF, MF (AM radio), HF (short wave), VHF (FM radio, TV), UHF (mobile, Wi-Fi), SHF (satellite, radar).

   | Point | Audio frequency | Radio frequency |
   |---|---|---|
   | Range | 20 Hz - 20 kHz | ~3 kHz - 300 GHz |
   | Nature of wave | Mechanical (sound) or its electrical form | Electromagnetic |
   | Medium needed | Air or another material | Travels in vacuum too |
   | Speed | 343 m/s in air | 3 x 10^8 m/s |
   | Wavelength | 17 m to 17 mm (in air) | 100 km down to 1 mm |
   | Antenna | Not usable | Practical, since wavelength is short |
   | Range of travel | A few metres | Kilometres to interplanetary |
   | Devices | Microphone, speaker, amplifier | Antenna, transmitter, receiver |
   | Uses | Music, speech, telephony | Broadcasting, mobile, Wi-Fi, radar |

   - How they work together: an audio signal is too low in frequency to radiate, so it is `modulated` onto a radio carrier (AM, FM) for transmission and `demodulated` back to audio at the receiver.

   Part 2 — Ten 10-ohm resistors in series

   - In a `series` connection the same current flows through every element and the resistances simply add.
   ```
      R(total) = R1 + R2 + ... + Rn
   ```
   ```
      R(total) = 10 + 10 + 10 + 10 + 10 + 10 + 10 + 10 + 10 + 10
               = 10 x 10
      R(total) = 100 ohms
   ```
   ```
      ---/\/\---/\/\---/\/\--- ... ---/\/\---
        10      10      10             10
                (ten resistors in series)
   ```

   For comparison, the same ten in parallel
   ```
      1/R = 1/10 + 1/10 + ... (ten times) = 10/10 = 1
      R(parallel) = 10 / 10 = 1 ohm
   ```
   - General rule for `n equal resistors`: series gives `nR`, parallel gives `R/n`. Here 10 x 10 = 100 ohms and 10 / 10 = 1 ohm.

8. **Write down the function of Relay, Fuse and Circuit Breaker.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

   Answer: All three are protection or control devices in a circuit, but each does a different job.

   Relay
   - A `relay` is an electrically operated switch. A small current through its coil creates a magnetic field that pulls an armature and closes (or opens) a separate set of contacts, switching a much larger current in another circuit.
   ```
           control side              switched side
      +-------------------+      +------------------+
      |   coil  (low      |      |   contacts       |
      |   current, 5-12 V)|~~~~~>|  (high current,  |
      |                   |mag   |   220 V, motor)  |
      +-------------------+      +------------------+
   ```
   - Functions:
   ```
   Isolation      : a 5 V microcontroller safely switches a 220 V load
   Amplification  : a small signal controls a large power circuit
   Remote control : the control circuit can be far from the load
   Protection     : a protective relay senses over-current, earth fault or
                    over-voltage and commands a circuit breaker to trip
   Logic          : one input can switch several contacts at once
   ```
   - It does `not` break the fault current itself in power systems; it detects the fault and tells the breaker to open.

   Fuse
   - A `fuse` is a thin metal wire or strip that `melts` when the current exceeds its rating, permanently breaking the circuit.
   - Functions:
   ```
   Overcurrent protection : opens the circuit on overload or short circuit
   Equipment protection   : saves the wiring and the appliance from burning
   Fire prevention        : stops an overheated cable before it ignites
   ```
   - It is a `one-time` device — after it blows, it must be replaced. It is the cheapest and, in the HRC form, the fastest protection against a large short-circuit current.

   Circuit breaker
   - A `circuit breaker` is an automatic switch that `trips open` on a fault and can then be `reset` by hand. It combines two sensing elements:
   ```
   Thermal (bimetallic strip) : sustained OVERLOAD, with an inverse time delay
   Magnetic (solenoid)        : SHORT CIRCUIT, almost instantaneous
   ```
   - Functions:
   ```
   Overcurrent and short-circuit protection, like a fuse
   Reusable  : reset instead of replace
   Isolation : also serves as a manual on/off switch for maintenance
   Indication: the tripped handle shows which circuit faulted
   ```

   Comparison

   | Point | Relay | Fuse | Circuit breaker |
   |---|---|---|---|
   | Main job | Switch or sense, then command | Break the circuit on overcurrent | Break the circuit on overcurrent |
   | Operation | Electromagnetic coil | Melting element | Thermal + magnetic trip |
   | Reusable | Yes | No | Yes, reset by hand |
   | Breaks fault current | No (protective relay signals only) | Yes | Yes |
   | Acts as a switch | Yes | No | Yes |
   | Cost | Low to moderate | Very low | Higher |

   - How they work together in a real installation: a `protective relay` detects the abnormal condition, a `circuit breaker` does the actual interruption, and a `fuse` gives simple backup protection on smaller branches.

9. **Find the Value of I.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*

   Answer: The question is `incomplete` — the circuit diagram is not present. The methods for finding an unknown current are given below with worked examples.

   Method 1 — Ohm's law, for a single branch
   ```
      I = V / R
   ```
   ```
      A 12 V source across a 4 ohm resistor :   I = 12/4 = 3 A
   ```

   Method 2 — series and parallel reduction
   ```
      SERIES   : R(eq) = R1 + R2 + ...        same current through each
      PARALLEL : 1/R(eq) = 1/R1 + 1/R2 + ...  same voltage across each
                 two resistors : R(eq) = R1 R2/(R1 + R2)
   ```
   Worked example
   ```
           +---[ 4 ohm ]---+---[ 6 ohm ]---+
           |               |               |
         (+) 24 V      [ 12 ohm ]          |
           |               |               |
           +---------------+---------------+

      Parallel part : (12 x 6)/(12 + 6) = 4 ohms
      Total         : 4 + 4 = 8 ohms
      Total current : I = 24/8 = 3 A

      Voltage across the parallel section = 3 x 4 = 12 V
      I through 12 ohm = 12/12 = 1 A
      I through 6  ohm = 12/6  = 2 A
      Check (KCL) : 1 + 2 = 3 A       correct
   ```

   Method 3 — the current divider rule
   ```
      For two resistors in parallel carrying a total current I :

           I(R1) = I x  R2/(R1 + R2)
           I(R2) = I x  R1/(R1 + R2)

      Note the CROSS multiplication - the current prefers the SMALLER
      resistance, so R1's share is proportional to R2.
   ```
   ```
      I = 3 A into 12 ohm parallel 6 ohm :
           I(12) = 3 x 6/18 = 1 A
           I(6)  = 3 x 12/18 = 2 A       same as above
   ```

   Method 4 — Kirchhoff's laws, for a network that will not reduce
   ```
      KCL : sum of currents into a node = sum out
      KVL : sum of voltages round any closed loop = 0
   ```
   Worked example — two loops
   ```
          I1 ->  [ 2 ohm ]        I2 ->  [ 3 ohm ]
        +-------/\/\/\------+-------/\/\/\-------+
        |                   |                    |
      (+) 10 V          [ 5 ohm ]              (+) 5 V
        |                 I3 |                    |
        +-------------------+--------------------+

      KCL at the middle node :   I1 = I2 + I3
      KVL loop 1 :  10 - 2 I1 - 5 I3 = 0
      KVL loop 2 :   5 - 3 I2 - 5 I3 = 0        (traversed appropriately)

      Substituting I1 = I2 + I3 and solving the two equations gives the
      three currents. Always finish by checking KCL at the node and KVL
      round both loops.
   ```

   Method 5 — mesh or nodal analysis, for anything larger
   ```
      MESH  : assign a circulating current to each mesh, write KVL for
              each, and solve the simultaneous equations.
      NODAL : choose a reference node, write KCL at every other node in
              terms of the node voltages, and solve.

      Nodal is usually easier when there are more loops than nodes.
   ```

   Method 6 — Thevenin, when only one branch current is wanted
   ```
      1. REMOVE the branch whose current is wanted.
      2. Find V(th) - the open-circuit voltage across those terminals.
      3. Find R(th) - the resistance looking back in, with all
         independent sources set to zero (voltage sources shorted,
         current sources opened).
      4. Reconnect the branch :

           I = V(th) / (R(th) + R(branch))
   ```
   - This is the fastest route when the network is large but only one current matters.

   The verification that should always be done
   ```
      KCL holds at every node
      KVL holds round every loop
      Power delivered by the sources = power dissipated in the resistors
           sum (V x I) sources = sum (I^2 R) resistors
   ```

10. **BREB power transmission interrupt related.** *[BREB Assistant General Manager (IT) 2021 compact it 935 (ET: N/A)]*

    Answer: The question is `incomplete` — only the topic "BREB power transmission interrupt related" was recorded, not the question itself. `BREB` is the Bangladesh Rural Electrification Board, so the subject is `interruptions in power transmission and distribution`, which is covered below.

    Types of interruption
    ```
       MOMENTARY   : less than 5 minutes. Usually cleared automatically by
                     a RECLOSER after a transient fault such as a branch
                     touching a line.
       SUSTAINED   : longer than 5 minutes. Needs a crew to attend.
       PLANNED     : announced in advance, for maintenance or new connections.
       UNPLANNED   : a fault, a storm, or equipment failure.
       LOAD SHEDDING : a deliberate interruption because generation is less
                     than demand - a managed rotation of outages.
    ```

    Causes of transmission and distribution interruption
    ```
       NATURAL      : storm, lightning strike, flood, fallen tree,
                      salt or dust pollution on insulators, birds and animals
       EQUIPMENT    : transformer failure, insulator flashover, conductor
                      snapping, breaker or CT/PT failure, cable fault,
                      ageing infrastructure
       ELECTRICAL   : short circuit (line-to-line, line-to-ground), overload,
                      over-voltage, under-frequency
       OPERATIONAL  : switching error, wrong protection setting, maintenance
       EXTERNAL     : vehicle hitting a pole, construction damage to an
                      underground cable, theft of conductor, vandalism
       SYSTEM       : generation shortfall, a cascading trip, a grid
                      collapse such as the national blackout of 1 November 2014
    ```

    Types of electrical fault
    ```
       SYMMETRICAL (rare, about 5 %)
            Three-phase (L-L-L) , three-phase-to-ground (L-L-L-G)
            The most severe, but balanced and simplest to analyse.

       UNSYMMETRICAL (about 95 %)
            Single line-to-ground (L-G)   - the COMMONEST, about 70 %
            Line-to-line (L-L)            - about 15 %
            Double line-to-ground (L-L-G) - about 10 %
    ```

    The protection scheme that clears a fault
    ```
       RELAY detects the abnormal condition and commands the breaker
            Over-current relay     : too much current
            Differential relay     : current in does not equal current out -
                                     used for transformers and generators
            Distance relay         : impedance indicates how far the fault is -
                                     used for transmission lines
            Earth-fault relay      : unbalanced current to ground

       CIRCUIT BREAKER interrupts the fault current
            Oil , air-blast , SF6 , vacuum

       RECLOSER automatically re-closes after a delay, in case the fault
            was transient. Typically tries three times before locking out.

       ISOLATOR provides a visible off-load disconnection for safe working

       LIGHTNING ARRESTER diverts a surge to earth
       EARTH WIRE on top of the tower shields the phase conductors
    ```

    The reliability indices BREB and every utility is measured by
    ```
       SAIFI = System Average Interruption FREQUENCY Index
             = total customer interruptions / total customers served
               -> how OFTEN the average customer loses supply

       SAIDI = System Average Interruption DURATION Index
             = sum of customer-minutes lost / total customers
               -> how LONG the average customer is without supply

       CAIDI = SAIDI / SAIFI
               -> the average length of ONE interruption

       ASAI  = Average Service Availability Index
             = (available hours / demanded hours) x 100 %
    ```

    How interruptions are reduced
    ```
       PREVENTION   : tree trimming along the right of way, insulator
                      cleaning, thermographic inspection, transformer oil
                      testing, replacing ageing conductor
       DESIGN       : ring-main and mesh networks instead of radial feeders,
                      so an alternative path exists ; underground cable in
                      storm-prone areas ; higher insulation levels
       PROTECTION   : properly graded relay settings, so only the nearest
                      breaker trips ; auto-reclosers on rural feeders
       AUTOMATION   : SCADA for remote monitoring and switching ;
                      a distribution management system ; smart meters that
                      report an outage without a customer call
       MANAGEMENT   : an outage management system, stocked spares, trained
                      crews and a published restoration target
    ```

    - For BREB specifically, the network is `largely rural and radial`, with long 11 kV and 33 kV feeders, so a single fault far from the substation can black out a wide area. That is why rural electrification programmes concentrate on `auto-reclosers, feeder sectionalising and right-of-way clearance` rather than on undergrounding, which is far too costly per kilometre for a rural line.

11. **EEE related 3 math question.** *[BREB Assistant General Manager (IT) 2021 compact it 935 (ET: N/A)]*

    Answer: The question is `incomplete` — only "EEE related 3 math question" was recorded, not the three problems. The three topics that such a paper almost always draws them from are worked below, so the methods are available.

    Problem type 1 — DC network analysis
    ```
       Find the total resistance and the branch currents.

            +---[ 4 ohm ]---+---[ 6 ohm ]---+
            |               |               |
          (+) 24 V      [ 12 ohm ]          |
            |               |               |
            +---------------+---------------+
    ```
    ```
       Step 1 : the parallel pair
            R(p) = (12 x 6)/(12 + 6) = 72/18 = 4 ohms

       Step 2 : total resistance
            R(total) = 4 + 4 = 8 ohms

       Step 3 : total current
            I = V/R = 24/8 = 3 A

       Step 4 : voltage across the parallel section
            V(p) = 3 x 4 = 12 V

       Step 5 : branch currents
            I(12) = 12/12 = 1 A
            I(6)  = 12/6  = 2 A
            Check : 1 + 2 = 3 A   (KCL)      correct

       Step 6 : power
            P = V I = 24 x 3 = 72 W
            Check : 3^2 x 4 + 1^2 x 12 + 2^2 x 6 = 36 + 12 + 24 = 72 W
    ```

    Problem type 2 — AC series RLC circuit
    ```
       R = 30 ohm , L = 0.1 H , C = 100 uF , V = 230 V at 50 Hz.
       Find the impedance, the current and the power factor.
    ```
    ```
       X(L) = 2 pi f L = 2 x 3.1416 x 50 x 0.1 = 31.42 ohms
       X(C) = 1/(2 pi f C) = 1/(2 x 3.1416 x 50 x 100e-6) = 31.83 ohms

       Net reactance X = X(L) - X(C) = 31.42 - 31.83 = -0.41 ohms
            (negative, so the circuit is slightly CAPACITIVE)

       Z = sqrt(R^2 + X^2) = sqrt(900 + 0.168) = 30.003 ohms

       I = V/Z = 230/30.003 = 7.666 A

       pf = cos(theta) = R/Z = 30/30.003 = 0.9999 leading
            theta = arctan(X/R) = arctan(-0.41/30) = -0.78 degrees

       Real power     P = V I cos(theta) = 230 x 7.666 x 0.9999 = 1763 W
       Apparent power S = V I = 230 x 7.666 = 1763 VA
       Reactive power Q = V I sin(theta) = -24 VAR

       Resonant frequency f(r) = 1/(2 pi sqrt(LC))
                               = 1/(2 x 3.1416 x sqrt(0.1 x 100e-6))
                               = 50.33 Hz
       The supply is almost at resonance, which is why the pf is nearly 1.
    ```

    Problem type 3 — transformer or motor calculation
    ```
       A single-phase transformer : 2200/220 V , 50 Hz , 10 kVA.
       Find the turns ratio and the rated currents.
    ```
    ```
       Turns ratio  a = V1/V2 = 2200/220 = 10 : 1

       Primary current   I1 = S/V1 = 10,000/2200 = 4.545 A
       Secondary current I2 = S/V2 = 10,000/220  = 45.45 A
       Check : I1/I2 = 4.545/45.45 = 1/10 = 1/a      correct
    ```
    ```
       Three-phase induction motor : 12-pole alternator at 500 rpm feeding
       an 8-pole motor, slip 3 %.

       Supply frequency  f  = P N /120 = 12 x 500/120 = 50 Hz
       Synchronous speed Ns = 120 f/P  = 120 x 50/8  = 750 rpm
       Full-load speed   N  = Ns(1 - s) = 750 x 0.97 = 727.5 rpm
    ```

    The formulas these three problems rest on
    ```
       DC        : V = IR , P = VI = I^2 R = V^2/R
                   Series R = R1+R2 ; Parallel 1/R = 1/R1+1/R2
                   KCL : sum I(in) = sum I(out)
                   KVL : sum V round a loop = 0

       AC        : X(L) = 2 pi f L , X(C) = 1/(2 pi f C)
                   Z = sqrt(R^2 + (XL - XC)^2)
                   pf = cos(theta) = R/Z
                   P = VI cos(theta) , S = VI , Q = VI sin(theta)
                   Resonance : f(r) = 1/(2 pi sqrt(LC))

       Machines  : f = PN/120 , Ns = 120f/P , s = (Ns - N)/Ns
                   a = V1/V2 = N1/N2 = I2/I1
                   Efficiency = output/input x 100
    ```
    - The habit that earns marks in all three: `write the formula, substitute the numbers with their units, compute, and then verify` — for DC by checking KCL and the power balance, for AC by checking that P = I^2 R, and for machines by checking the turns or speed ratio.

12. **নিচের সার্কিটের মোট রেজিস্ট্যান্স বের করে, I_3 এর কারেন্ট বের কর।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The question is `incomplete` — the circuit diagram is not present. The method for finding the total resistance and then a particular branch current is set out below with a worked example.

    Step 1 — reduce the network to find the total resistance
    ```
       SERIES   : R(eq) = R1 + R2 + R3 + ...
                  the same current flows through each

       PARALLEL : 1/R(eq) = 1/R1 + 1/R2 + ...
                  two resistors : R(eq) = R1 R2/(R1 + R2)
                  the same voltage across each
    ```

    Step 2 — find the total current from Ohm's law
    ```
       I(total) = V / R(total)
    ```

    Step 3 — work back through the network to the branch wanted, using the current divider rule
    ```
       For two resistors in parallel carrying a total current I :

            I(R1) = I x R2/(R1 + R2)
            I(R2) = I x R1/(R1 + R2)

       The CROSS multiplication is the point : current prefers the smaller
       resistance, so R1's share is proportional to R2.
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

    A mixed series-parallel example, which is the harder case
    ```
            +---[ R1 = 2 ]---+---[ R2 = 6 ]---+
            |                |                |
          (+) 24 V       [ R3 = 3 ]           |
            |                |                |
            +----------------+----------------+

       R2 in parallel with R3 : (6 x 3)/(6 + 3) = 2 ohms
       R(total) = R1 + 2 = 4 ohms
       I(total) = 24/4 = 6 A

       Voltage across the parallel section = 6 x 2 = 12 V
       I(R2) = 12/6 = 2 A
       I(R3) = 12/3 = 4 A
       Check : 2 + 4 = 6 A                            correct
    ```

    The general procedure to state
    ```
       1. Redraw the circuit, marking every node.
       2. Reduce the innermost series and parallel groups first, working
          outward until a single resistance remains.
       3. Find the total current with Ohm's law.
       4. Expand back outward, using the voltage divider for series
          sections and the current divider for parallel ones.
       5. VERIFY : KCL at every node, KVL round every loop, and the power
          delivered equal to the power dissipated.
    ```

13. **What is the difference between battery and capacitor?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1226 (ET: N/A)]*

    Answer: Both store electrical energy, but in completely different ways — a `battery` stores it chemically, a `capacitor` stores it in an electric field.

    Battery
    - Two electrodes and an electrolyte. Energy is stored as `chemical` energy and released by a chemical reaction that drives electrons through the external circuit.
    - It supplies a `steady voltage` for a long time, and the voltage stays nearly constant until the cell is almost exhausted.
    - Charging and discharging are slow, because a chemical reaction has to take place.
    - The chemistry wears out, so a rechargeable battery lasts only a few hundred to a few thousand cycles.
    ```
       Energy stored = capacity (Ah) x voltage (V)
    ```

    Capacitor
    - Two conducting plates separated by a dielectric. Energy is stored `physically`, as charge separated across an electric field. No chemical reaction takes place.
    - It charges and discharges in `microseconds`, so it can deliver very high power for a very short time.
    - Its voltage `falls continuously` as it discharges, following an exponential curve.
    - Because nothing is consumed, it survives millions of cycles.
    ```
       Q = C . V              Energy = (1/2) C V^2
    ```

    Difference

    | Point | Battery | Capacitor |
    |---|---|---|
    | Form of storage | Chemical energy | Electric field (separated charge) |
    | Energy density | High — stores far more per unit volume | Very low |
    | Power density | Low — releases energy slowly | Very high — releases it instantly |
    | Charge / discharge time | Minutes to hours | Microseconds to seconds |
    | Output voltage | Nearly constant until exhausted | Falls exponentially at once |
    | Internal resistance | Higher | Very low |
    | Cycle life | Hundreds to a few thousand | Millions; essentially unlimited |
    | Self-discharge | Slow, weeks or months | Fast, minutes to hours |
    | Effect of temperature | Strong | Small |
    | Used in | Powering a device for hours | Smoothing, filtering, timing, coupling, camera flash |
    | Symbol | `--\|\|---` (long and short plates) | `--\|\|---` (two equal plates) |

    Where each is used
    - `Battery` — phone, laptop, UPS, vehicle starting, backup power. Anything that must run for hours.
    - `Capacitor` — smoothing the ripple in a power supply, coupling and decoupling in amplifiers, timing in a 555 circuit, tuning a radio, the flash in a camera, and motor starting.

    - A `supercapacitor` sits between the two: energy density far above an ordinary capacitor but still below a battery, with the capacitor's fast charging and near-unlimited cycle life. It is used for regenerative braking and short-term backup, where a battery would wear out too quickly.

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
      ID = mu_n Cox (W/L) [ (VGS - Vt) VDS - VDS^2 / 2 ]

   valid while  VDS < VGS - Vt   (the linear / triode condition)
   ```

   Given
   ```
      mu_n Cox (W/L) = 1.3 mA/V^2
      VGS            = 2.5 V
      Vt             = 0.95 V
      VDS            = not given -> assume 0.1 V, a small value typical of the
                       deep linear region
   ```

   Step 1 — find the overdrive voltage
   ```
      V(ov) = VGS - Vt = 2.5 - 0.95 = 1.55 V
   ```

   Step 2 — check that the device really is in the linear region
   ```
      VDS = 0.1 V  <  V(ov) = 1.55 V        yes, linear region confirmed
   ```

   Step 3 — substitute into the formula
   ```
      ID = 1.3 mA/V^2 x [ (1.55)(0.1) - (0.1)^2 / 2 ]
         = 1.3 x [ 0.155 - 0.005 ]
         = 1.3 x 0.150
         = 0.195 mA
   ```
   ```
      ID = 0.195 mA = 195 microamperes
   ```

   Check with the small-signal (deep triode) approximation
   ```
      When VDS is very small, the VDS^2/2 term is negligible :

      ID ~= mu_n Cox (W/L) (VGS - Vt) VDS
          = 1.3 x 1.55 x 0.1
          = 0.2015 mA

      Close to the exact 0.195 mA, so the working is consistent.
   ```

   Equivalent channel resistance
   ```
      r(DS) = VDS / ID = 0.1 / 0.195 mA = 513 ohms
   ```
   - This is the useful property of the linear region: the MOSFET acts as a resistor whose value is set by VGS. It is the basis of the CMOS transmission gate and the analogue switch.

   For comparison — the same device at the edge of saturation
   ```
      If VDS >= V(ov) = 1.55 V the device saturates :

      ID = (1/2) mu_n Cox (W/L) (VGS - Vt)^2
         = 0.5 x 1.3 x (1.55)^2
         = 0.5 x 1.3 x 2.4025
         = 1.562 mA
   ```

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

   The region is decided by how the `two junctions` are biased.
   ```
   Region      | Emitter-Base | Collector-Base | Behaviour
   ------------+--------------+----------------+---------------------------
   Cut-off     | Reverse      | Reverse        | OFF, acts as an open switch
   Active      | Forward      | Reverse        | Amplifier, IC = beta . IB
   Saturation  | Forward      | Forward        | ON, acts as a closed switch
   ```

   `Cut-off region`
   - Both junctions reverse biased, `V(BE) < 0.7 V`, so `IB = 0` and `IC = 0` (only a tiny leakage).
   - `V(CE) = Vcc`, the full supply appears across the transistor.
   - The transistor is an `open switch` — logic 1 at the collector.

   `Active region`
   - Emitter-base forward, collector-base reverse. `IC = beta . IB`, independent of V(CE).
   - Used for `amplification`, because the output faithfully follows the input.
   - `0.2 V < V(CE) < Vcc`.

   `Saturation region`
   - Both junctions forward biased. The base current is so large that the collector cannot take any more current, so `IC < beta . IB`.
   - `V(CE,sat) is about 0.2 V`, essentially zero.
   - The transistor is a `closed switch` — logic 0 at the collector.

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
   - A switching circuit works only at the two ends — cut-off and saturation. An amplifier is biased in the middle of the active region.

   Part 2 — n-channel JFET operation

   Structure
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
   - The `gate-source junction is always reverse biased`, so gate current is essentially zero. This is why a JFET has a very high input impedance, unlike a BJT.
   - It is a `voltage-controlled` device: V(GS) widens or narrows the depletion region, which changes the width of the channel.

   Effect of V(GS) with V(DS) fixed and small
   ```
      VGS = 0        : depletion region thin, channel widest, ID maximum = I(DSS)
      VGS = -1 V     : depletion region grows, channel narrows, ID falls
      VGS = -2 V     : channel narrower still, ID smaller
      VGS = V(P)     : the two depletion regions meet, channel PINCHED OFF,
                       ID = 0.  V(P) is the pinch-off (cut-off) voltage,
                       negative for an n-channel JFET
   ```
   - For an n-channel JFET, V(GS) is always `zero or negative`. Making it positive would forward-bias the gate junction and destroy the high input impedance.

   Effect of V(DS) with V(GS) fixed at 0
   ```
      Small VDS (0 to VP)   : OHMIC region. The channel behaves as a resistor,
                              ID rises almost linearly with VDS.

      VDS = |VP|            : PINCH-OFF point. The depletion region touches near
                              the drain end.

      VDS > |VP|            : SATURATION (constant-current) region. ID stays
                              almost constant at I(DSS) even as VDS rises.

      VDS very large        : BREAKDOWN. The junction breaks down and ID rises
                              sharply; the device is damaged.
   ```

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
   - Two heavily doped `N+` regions (source and drain) sit in a lightly doped `P` substrate.
   - The gate is a metal or polysilicon plate `insulated` from the substrate by a very thin silicon-dioxide layer, so the gate draws `no DC current` at all. That is why a MOSFET's input impedance is enormous — about 10^12 ohms.
   - It is an `enhancement-type` device: with no gate voltage there is no channel and the transistor is off.

   Operation

   Case 1 — V(GS) = 0 : cut-off
   ```
      No channel exists. The source and drain are two back-to-back PN junctions,
      one of which is always reverse biased.

      ID = 0   ->  the transistor is OFF (an open switch)
   ```

   Case 2 — 0 < V(GS) < Vt : still off
   ```
      The positive gate voltage pushes holes away from the surface, leaving a
      depletion region, but not enough electrons have been attracted yet.

      ID is still essentially 0
   ```

   Case 3 — V(GS) > Vt : the channel forms
   ```
      The positive gate attracts minority electrons from the P substrate to the
      surface. They form a thin layer of N-type material joining source to drain
      -- the INVERSION LAYER or CHANNEL.

      Vt = threshold voltage, typically 0.4 to 1 V.
      V(ov) = VGS - Vt is the overdrive voltage; it sets how thick the channel is.
   ```

   Case 4 — apply V(DS), small : linear (triode) region
   ```
      Condition : VDS < VGS - Vt

      ID = mu_n Cox (W/L) [ (VGS - Vt) VDS - VDS^2 / 2 ]

      The channel is a uniform resistor whose value is set by VGS,
      so ID rises almost linearly with VDS. This is the region used by the
      CMOS transmission gate and the analogue switch.
   ```

   Case 5 — V(DS) >= V(GS) - Vt : saturation region
   ```
      The voltage across the oxide at the drain end falls to Vt, so the channel
      PINCHES OFF near the drain. Raising VDS further does not widen the channel;
      it only extends the pinch-off point.

      ID = (1/2) mu_n Cox (W/L) (VGS - Vt)^2

      ID is now almost independent of VDS -- a constant-current source.
      This is the region used for amplification.
   ```

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

1. Explain the working principle of a PN junction diode. Draw its symbol and describe the difference between forward bias and reverse bias. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

   Answer: A `PN junction diode` is formed by joining a `P-type` semiconductor (rich in holes) to an `N-type` semiconductor (rich in free electrons) on the same crystal. It conducts current in `one direction only`.

   Formation of the depletion region
   - At the moment of joining, electrons from the N side diffuse across and fill holes on the P side.
   - This leaves fixed positive ions on the N side and fixed negative ions on the P side, forming a `depletion region` empty of free carriers.
   - The exposed ions set up an internal `barrier potential` that stops further diffusion.
   ```
      Barrier potential :  Silicon 0.7 V ,  Germanium 0.3 V
   ```
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
      The bar marks the cathode; on a real diode it is the painted ring.
   ```

   Forward bias
   - The `positive` terminal of the supply is connected to the `P` side and the negative to the N side.
   ```
      +  ---| P | N |--- -
   ```
   - The applied voltage `opposes` the barrier potential, so the depletion region narrows.
   - Once the supply exceeds about `0.7 V` (silicon), the barrier collapses and a large current flows.
   - The diode acts almost like a `closed switch` with a small fixed drop of 0.7 V.
   - Resistance is very low, a few ohms.

   Reverse bias
   - The `positive` terminal is connected to the `N` side and the negative to the P side.
   ```
      -  ---| P | N |--- +
   ```
   - The applied voltage `adds` to the barrier potential, so the depletion region widens.
   - Almost no current flows — only a tiny `reverse saturation current` of nanoamperes, caused by minority carriers.
   - The diode acts like an `open switch`. Resistance is very high, megohms.
   - If the reverse voltage is raised too far, the junction `breaks down` (avalanche or Zener breakdown) and a large current flows, usually destroying an ordinary diode.

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

   Difference

   | Point | Forward bias | Reverse bias |
   |---|---|---|
   | Connection | P to +, N to - | P to -, N to + |
   | Depletion region | Narrows | Widens |
   | Barrier potential | Reduced | Increased |
   | Current | Large, in mA | Negligible, in uA or nA |
   | Resistance | Very low | Very high |
   | Behaves as | Closed switch | Open switch |
   | Voltage drop | About 0.7 V (Si) | Nearly the whole supply |
   | Carriers involved | Majority carriers | Minority carriers only |

   - Uses: rectification (AC to DC), clipping and clamping, protection against reverse polarity, and — in special forms — the `Zener` diode for voltage regulation and the `LED` for light emission.

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

   Answer: Diode
   - A `diode` is a two-terminal semiconductor device that lets current flow in `one direction only`. It is made by joining a P-type and an N-type semiconductor to form a `PN junction`.
   ```
           anode          cathode
         P ----|>|---- N
   ```
   - `Forward bias` (P to +, N to -): once the supply exceeds about `0.7 V` for silicon, the depletion region collapses and a large current flows. The diode acts as a closed switch.
   - `Reverse bias` (P to -, N to +): the depletion region widens and only a few nanoamperes of leakage flow. The diode acts as an open switch.
   - Types and uses:
   ```
   Rectifier diode : converts AC to DC in every power supply
   Zener diode     : deliberately operated in reverse breakdown, for voltage regulation
   LED             : emits light when forward biased
   Photodiode      : converts light into current
   Schottky diode  : very fast switching, low forward drop (0.3 V)
   Varactor diode  : acts as a voltage-controlled capacitor, used for tuning
   ```
   - Other uses: clipping, clamping, protection against reverse polarity, and free-wheeling across a relay coil.

   Inductor
   - An `inductor` is a passive two-terminal component — usually a coil of wire, often on a magnetic core — that stores energy in a `magnetic field` when current flows through it.
   ```
      ---(((((---            symbol : a coil, sometimes with core lines
   ```
   ```
      V = L . (dI / dt)              Faraday's law of induction
      Energy stored = (1/2) L I^2
      Unit : henry (H)
   ```
   - Its defining behaviour: an inductor `opposes any change in current`. When the current tries to rise, the inductor generates a back EMF that resists it; when the current is cut off, it generates a large voltage spike trying to keep it flowing.
   ```
      DC (steady)    : acts as a plain wire, impedance = 0
      AC             : impedance XL = 2 pi f L , rises with frequency
      High frequency : acts as an open circuit -> it blocks AC, passes DC
   ```
   - Uses: filters and chokes in power supplies, tuned circuits in radios (with a capacitor), transformers, relays, motors, and energy storage in switching converters.

   Difference

   | Point | Diode | Inductor |
   |---|---|---|
   | Type | Active semiconductor | Passive component |
   | Terminals | 2 (anode, cathode) | 2 |
   | Polarity | Polarised — direction matters | Not polarised |
   | Stores | Nothing | Energy in a magnetic field |
   | Main property | Conducts one way only | Opposes a change in current |
   | Behaviour with DC | Conducts or blocks by polarity | Acts as a wire |
   | Behaviour with AC | Rectifies | Impedance rises with frequency |
   | Unit | Volt drop (0.7 V) | Henry (H) |
   | Main use | Rectification, protection | Filtering, tuning, energy storage |

   - The two are often used together: in a switching power supply the inductor stores energy while the switch is on, and the diode gives that energy a path to the load when the switch turns off.

4. **How does LED differ from Laser Diod? What are the function of Diode?** *[BTRC Assistant Director (Technical) 2021 compact it 808 (ET: IBA)]*

   Answer: Both an `LED` and a `laser diode` are forward-biased PN junctions that emit light when electrons and holes recombine. The difference is `how` the light is produced.

   LED (Light Emitting Diode)
   - Light is produced by `spontaneous emission`: each electron falls across the band gap at a random moment and in a random direction.
   - The result is `incoherent`, spread over a `wide spectrum` (about 30-50 nm) and emitted in all directions.
   - It has no optical cavity and no threshold current — it starts glowing as soon as it conducts, and brightness rises smoothly with current.

   Laser diode
   - Light is produced by `stimulated emission`: one photon triggers the release of an identical photon, in the same direction and phase.
   - The chip has a `resonant cavity` formed by two mirrored end facets, which reflects photons back and forth so the effect multiplies.
   - It needs a minimum `threshold current`; below it the device behaves like a poor LED, above it the output rises steeply and becomes laser light.
   - The result is `coherent`, `monochromatic` (about 1-2 nm wide) and a narrow directional beam.

   | Point | LED | Laser diode |
   |---|---|---|
   | Emission | Spontaneous | Stimulated |
   | Light | Incoherent | Coherent |
   | Spectral width | Wide, 30-50 nm | Very narrow, 1-2 nm |
   | Beam | Spreads in all directions | Narrow, highly directional |
   | Threshold current | None | Yes — lases only above it |
   | Optical cavity | None | Two mirrored facets |
   | Output power | Low, a few mW | High, tens of mW to watts |
   | Modulation speed | Up to ~200 Mbps | Several Gbps |
   | Fibre used with | Multimode, short distance | Single-mode, long distance |
   | Cost | Very low | High |
   | Temperature sensitivity | Low | High, needs a controlled circuit |
   | Safety | Safe to look at | Can damage the eye |
   | Uses | Indicators, displays, lighting, remote controls, short-haul fibre | Long-haul fibre, CD/DVD, barcode readers, printers, surgery |

   Functions of a diode
   - `Rectification` — converting AC to DC. This is the main use, in half-wave, full-wave and bridge rectifiers.
   - `Voltage regulation` — a Zener diode held in reverse breakdown keeps a fixed voltage.
   - `Clipping` — cutting off part of a waveform above or below a set level, used to protect inputs.
   - `Clamping` — shifting a waveform up or down to a chosen DC level.
   - `Protection` — a diode in series blocks a reversed supply; a `free-wheeling` diode across a relay or motor coil absorbs the inductive spike when the current is switched off.
   - `Switching` — a fast diode acts as an electronic on/off element in logic and converter circuits.
   - `Light emission and detection` — LED and laser diode emit; photodiode and solar cell absorb.
   - `Tuning` — a varactor diode acts as a voltage-controlled capacitor in radio tuners and PLLs.
   - `Demodulation` — recovering the audio signal from an AM radio carrier.

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

   How it works
   ```
      1. The sample-and-hold freezes the input voltage so it cannot change
         while the conversion runs.
      2. The SAR sets the MSB to 1 and clears the rest    ->  1000 0000
      3. The DAC turns that code into a voltage, and the comparator asks
         "is Vin greater than the DAC output?"
            YES -> keep the bit as 1
            NO  -> clear it back to 0
      4. Move to the next bit and repeat.
      5. After n comparisons, the register holds the answer.
   ```
   - It performs a `binary search`, so an 8-bit conversion needs exactly 8 clock cycles, and a 12-bit one exactly 12.

   Worked example — 8-bit ADC, Vref = 2.56 V, Vin = 1.7 V
   ```
      Step = 2.56 / 256 = 10 mV

      bit 7 : try 1000 0000 = 1.28 V   -> 1.7 > 1.28  keep 1
      bit 6 : try 1100 0000 = 1.92 V   -> 1.7 < 1.92  clear to 0
      bit 5 : try 1010 0000 = 1.60 V   -> 1.7 > 1.60  keep 1
      bit 4 : try 1011 0000 = 1.76 V   -> 1.7 < 1.76  clear to 0
      bit 3 : try 1010 1000 = 1.68 V   -> 1.7 > 1.68  keep 1
      bit 2 : try 1010 1100 = 1.72 V   -> 1.7 < 1.72  clear to 0
      bit 1 : try 1010 1010 = 1.70 V   -> equal        keep 1
      bit 0 : try 1010 1011 = 1.71 V   -> 1.7 < 1.71  clear to 0

      Result = 1010 1010 = 170       and 170 x 10 mV = 1.70 V     correct
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
   - A resistor ladder creates `2^n - 1` reference levels, one comparator per level, and a priority encoder turns the comparator outputs into a binary code.
   - It converts in a `single clock cycle` — the fastest type — but needs 255 comparators for 8 bits, so it is used only for very high speed video and radar work.

   Comparison of ADC types

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

   Stage 1 — Sampling
   - The continuous signal is measured at regular intervals, `f(s)` times per second, and a sample-and-hold circuit freezes each value while it is converted.
   - `Nyquist theorem`: the sampling rate must be at least twice the highest frequency present.
   ```
      f(s) >= 2 . f(max)
   ```
   - Example: speech up to 4 kHz is sampled at 8 kHz; CD audio up to 20 kHz is sampled at 44.1 kHz.
   - If this rule is broken, high frequencies fold back and appear as false low frequencies — `aliasing` — so an anti-aliasing low-pass filter is placed before the sampler.

   Stage 2 — Quantization
   - Each sample is rounded to the nearest of `2^n` fixed levels.
   ```
      Step size = (V(max) - V(min)) / 2^n
   ```
   - The rounding introduces `quantization error`, at most half a step. More bits give smaller steps and less error:
   ```
      SNR(dB) = 6.02 n + 1.76
   ```

   Stage 3 — Encoding
   - Each level is written as an `n-bit binary number`.

   Stage 4 — Output
   - The bits are delivered in parallel or serially to the processor.

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
      P    = 940 W
      pf   = 0.707 leading   ->  theta = -45 degrees  (current leads)
      v(t) = 99 cos(600t + 30) V

      Vm = 99 V ,  omega = 600 rad/s
   ```

   Step 1 — RMS voltage and frequency
   ```
      V(rms) = Vm / sqrt(2) = 99 / 1.4142 = 70.00 V

      omega = 600 rad/s
      f = omega / (2 pi) = 600 / 6.2832 = 95.49 Hz
   ```

   Step 2 — magnitude of the impedance
   ```
      P = V(rms)^2 . cos(theta) / |Z|

      |Z| = V(rms)^2 . cos(theta) / P
          = (70.00)^2 x 0.707 / 940
          = 4900 x 0.707 / 940
          = 3464.3 / 940
      |Z| = 3.686 ohms
   ```

   Step 3 — RMS current, as a check
   ```
      I(rms) = V(rms) / |Z| = 70.00 / 3.686 = 18.99 A

      check : P = V I cos(theta) = 70.00 x 18.99 x 0.707 = 940 W      correct
   ```

   Step 4 — resistance
   ```
      R = |Z| . cos(theta)
        = 3.686 x 0.707
      R = 2.606 ohms
   ```

   Step 5 — capacitive reactance
   ```
      sin(45) = 0.707 , so for a 45 degree angle  X = R

      Xc = |Z| . sin(theta)
         = 3.686 x 0.707
      Xc = 2.606 ohms
   ```

   Step 6 — the capacitance
   ```
      Xc = 1 / (omega C)

      C = 1 / (omega . Xc)
        = 1 / (600 x 2.606)
        = 1 / 1563.6
      C = 0.0006395 F
   ```
   ```
      C = 639.5 microfarads
   ```

   Answer
   ```
      The two elements are

         R = 2.61 ohms          (resistor)
         C = 639.5 uF           (capacitor)

      connected in series.
   ```

   Verification
   ```
      Z = R - j Xc = 2.606 - j 2.606 = 3.686 angle -45 degrees      correct
      pf = cos(-45) = 0.707 leading                                 correct
      P  = I(rms)^2 . R = (18.99)^2 x 2.606 = 940 W                 correct
   ```

   - Points to note: a `leading` power factor always means a capacitive circuit; a `lagging` one would mean an inductor, and step 6 would then use `L = XL / omega`. At exactly 0.707 the phase angle is 45 degrees, so `R and X are equal` — a useful shortcut worth spotting immediately.

2. **RLC সার্কিট কী? বৈদ্যুতিক সার্কিটে ট্রানজিস্টরের ভূমিকা কী?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 809-810 (ET: IBA)]*

   Answer: (Answered in English, as required for IT topics.) RLC circuit
   - An `RLC circuit` contains a `resistor (R)`, an `inductor (L)` and a `capacitor (C)` connected together. It is the basic circuit for tuning, filtering and oscillation.
   ```
      Series RLC
      ---/\/\/\---(((((---||---
           R         L      C
   ```
   - Each element behaves differently with frequency:
   ```
      R  : opposition = R              , independent of frequency
      L  : reactance  X(L) = 2 pi f L  , rises with frequency
      C  : reactance  X(C) = 1/(2 pi f C) , falls with frequency
   ```
   - Total opposition is the `impedance`:
   ```
      Z = sqrt( R^2 + (XL - XC)^2 )

      phase angle  theta = arctan( (XL - XC) / R )
   ```

   Resonance
   - At one particular frequency the two reactances cancel exactly.
   ```
      XL = XC   ->   2 pi f L = 1 / (2 pi f C)

      f(r) = 1 / (2 pi sqrt(LC))
   ```
   - At resonance in a `series` RLC circuit: `Z = R` (minimum), current is `maximum`, and the power factor is 1. In a `parallel` RLC circuit the opposite happens — impedance is maximum and current minimum.
   - `Quality factor` measures how sharp the resonance is:
   ```
      Q = (1/R) sqrt(L/C)          Bandwidth = f(r) / Q
   ```

   Uses
   - Tuning a radio or television to one station, band-pass and band-stop filters, oscillators, and impedance matching.

   Role of a transistor in an electrical circuit
   - A `transistor` is a three-terminal semiconductor device that uses a small input signal to control a much larger current. Its two fundamental roles are `switching` and `amplification`.

   `Switching`
   ```
      Cut-off region    : the transistor is OFF -> an open switch  -> logic 1 at output
      Saturation region : the transistor is ON  -> a closed switch -> logic 0 at output
   ```
   - A 5 V microcontroller pin can therefore control a relay, a motor or a lamp. This on/off behaviour is the basis of every logic gate, and hence of every processor and memory chip.

   `Amplification`
   - Biased in the `active region`, the transistor makes the collector current a faithful, magnified copy of the base current.
   ```
      IC = beta . IB           beta is 50 to 300
   ```
   - Used in audio amplifiers, radio receivers, sensor signal conditioning and instrumentation.

   Other roles
   ```
   Oscillator      : with an RLC or crystal feedback network, it generates a waveform
   Voltage regulator : a series-pass transistor holds the output steady
   Current source  : supplies a fixed current regardless of load
   Buffer          : an emitter follower matches a high-impedance source
                     to a low-impedance load
   Modulation and demodulation in communication circuits
   ```

   - The two meet in a `tuned amplifier`: an RLC circuit selects one frequency, and the transistor amplifies it. That combination is what makes a radio receiver work.

## Operational Amplifiers (Op-Amp) (2)

1. **Assuming Ideal Op Amps, Find The Voltage Gain V_o/V_i of the following circuit.** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*

   Answer: The question is `incomplete` — the op-amp circuit diagram is not present. The gain of every standard ideal op-amp configuration is derived below, so the right formula can be applied to whichever circuit was printed.

   The two golden rules for an ideal op-amp
   ```
      1. NO CURRENT flows into either input     (input impedance is infinite)
      2. The two inputs are at the SAME voltage (a VIRTUAL SHORT), whenever
         negative feedback is present
   ```
   - Every gain formula below follows from these two rules alone.

   1. Inverting amplifier
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

   2. Non-inverting amplifier
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

   3. Voltage follower (buffer)
   ```
      Vi ---|+\
            |  \
            |   >---+--- Vo
            |  /    |
         +--|-/     |
         |          |
         +----------+
   ```
   ```
      Rf = 0 and Rin = infinity , so

      Av = 1 + 0/inf = 1        Vo = Vi
   ```
   - Gain of 1, but it converts a high-impedance source into a low-impedance output — the whole point of it.

   4. Summing amplifier
   ```
      V1 --/\/\/\--+
           R1      |         Rf
      V2 --/\/\/\--+---+---/\/\/\---+
           R2      |   |            |
      V3 --/\/\/\--+---+---|-\      |
           R3              |  \     |
                           |   >----+--- Vo
                    GND ---|+/
   ```
   ```
      Vo = -Rf ( V1/R1 + V2/R2 + V3/R3 )

      If R1 = R2 = R3 = R :   Vo = -(Rf/R)(V1 + V2 + V3)
      If also Rf = R      :   Vo = -(V1 + V2 + V3)
   ```

   5. Difference (differential) amplifier
   ```
      Vo = (Rf/R1)(V2 - V1)        when R1 = R3 and R2 = Rf
   ```

   6. Integrator and differentiator
   ```
      INTEGRATOR   : Rin in , C in the feedback path
           Vo = -(1/(Rin C)) integral of Vi dt

      DIFFERENTIATOR : C in , Rf in the feedback path
           Vo = -(Rf C) dVi/dt
   ```

   7. Cascaded stages
   ```
      Overall gain = the PRODUCT of the individual gains

      Av(total) = Av1 x Av2 x Av3 ...
   ```
   ```
      Example : an inverting stage of -10 followed by a non-inverting
      stage of +5 gives  -10 x 5 = -50
   ```

   How to identify which formula applies
   ```
      Is the input fed to the '-' terminal ?      -> INVERTING , -Rf/Rin
      Is the input fed to the '+' terminal ?      -> NON-INVERTING , 1+Rf/Rin
      Is the output tied straight back to '-' ?   -> FOLLOWER , gain 1
      Are several inputs joined at '-' ?          -> SUMMING
      Are inputs at BOTH terminals ?              -> DIFFERENTIAL
      Is there a capacitor in the feedback path ? -> INTEGRATOR
      Is there a capacitor at the input ?         -> DIFFERENTIATOR
      Are there several op-amps in a chain ?      -> MULTIPLY the gains
   ```

   - Ideal characteristics to state alongside the answer: infinite open-loop gain, infinite input impedance, zero output impedance, infinite bandwidth and infinite CMRR. Real devices have gain around 10^5, input impedance in megohms and a finite gain-bandwidth product, but the ideal assumptions give answers accurate to a fraction of a per cent in any ordinary feedback circuit.

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

   Ideal characteristics
   ```
      Open-loop voltage gain  A   : infinite            (real: 10^5 to 10^6)
      Input impedance         Zin : infinite            (real: 1 M to 10^12 ohm)
      Output impedance        Zo  : zero                (real: 20 to 100 ohm)
      Bandwidth                   : infinite            (real: limited by GBW)
      Common-mode rejection ratio : infinite            (real: 90 to 120 dB)
      Slew rate                   : infinite            (real: 0.5 to 20 V/us)
      Offset voltage and current  : zero                (real: small but non-zero)
      Drift with temperature      : zero
   ```

   The two golden rules used in every analysis
   ```
      1. No current flows into either input      (input impedance is infinite)
      2. The two inputs are at the same voltage  (virtual short, when negative
                                                  feedback is present)
   ```

   Practical characteristics that matter
   - `Very high gain` — so high that the op-amp is almost never used open loop. Negative feedback sets the gain instead, which makes it stable and predictable.
   - `Differential input` — it amplifies the difference between the inputs and rejects any signal common to both, which is what kills noise picked up on both wires.
   - `Wide supply range`, typically +/-5 V to +/-18 V, or single supply in modern parts.
   - `Slew rate` limits how fast the output can change; exceeding it distorts a fast signal.
   - `Gain-bandwidth product` is constant, so raising the closed-loop gain reduces the usable bandwidth.

   Common configurations
   ```
      Inverting amplifier      : Av = -Rf / Rin
      Non-inverting amplifier  : Av = 1 + Rf / Rin
      Voltage follower         : Av = 1        (buffer)
      Summing amplifier, difference amplifier, integrator, differentiator,
      comparator, active filter, oscillator
   ```

   How AC power is converted to DC power
   - The process is `rectification`, and a complete supply has four stages.
   ```
      AC 220 V --> Transformer --> Rectifier --> Filter --> Regulator --> DC out
                   (step down)    (AC to DC)   (smooth)   (hold steady)
   ```
   - `Transformer` steps 220 V down to a low AC voltage and isolates the load from the mains.
   - `Rectifier` — diodes conduct one way only, so the alternating waveform becomes one-directional (pulsating DC). A `bridge rectifier` of four diodes uses both halves of each cycle.
   ```
                 D1        D2
           +----|>|---+---|<|----+
           |          |          |
      AC ~ |          +--- + ----|--- output
           |          |          |
           +----|<|---+---|>|----+
                 D3        D4
   ```
   - `Filter` — a large electrolytic capacitor charges at each peak and discharges slowly between peaks, filling in the gaps.
   ```
      Before filter   /‾\/‾\/‾\      pulsating
      After filter    ‾‾‾\_/‾‾‾      nearly flat, with a small ripple
   ```
   - `Regulator` — a zener diode or an IC such as `7805` or `7812` holds the output fixed despite changes in load current and mains voltage.

   - Modern equipment uses an `SMPS` instead: the mains is rectified, chopped at 20-100 kHz, passed through a small ferrite transformer and rectified again. Because the transformer runs at high frequency it is tiny, and efficiency reaches 80-90 per cent against 50-60 per cent for the linear supply above.

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

   How it works
   ```
      1. LDR and R1 form a voltage divider. The voltage at their junction
         depends on how much light falls on the LDR.

            Daylight  : LDR resistance low  -> junction voltage HIGH
            Night     : LDR resistance high -> junction voltage LOW

      2. The comparator compares that voltage with a threshold set by the preset RV.

            Junction voltage > threshold (day)   -> output LOW  -> Q1 off
            Junction voltage < threshold (night) -> output HIGH -> Q1 on

      3. Q1 energises the relay coil, whose normally-open contacts close and
         connect the 220 V mains to the lamp.

      4. At sunrise the LDR resistance falls again, the comparator flips back,
         Q1 turns off and the lamp goes out.
   ```

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
   - `Hysteresis` is essential. Without it the lamp flickers on and off at dusk as the light hovers around the threshold. A Schmitt trigger, or positive feedback around the comparator, gives two separate switching levels — turn on below 380, turn off above 420.
   - A `flyback diode` must be fitted across the relay coil, otherwise the inductive spike destroys the transistor when the coil is switched off.
   - Add a `delay of a few seconds` before acting, so a passing headlight or a lightning flash does not switch the lamp.
   - A `PIR motion sensor` can be added so the lamp runs at low brightness all night and goes to full brightness only when someone approaches — the standard energy-saving design.
   - An `SSR` (solid-state relay) or a triac can replace the mechanical relay for silent operation and a much longer life.
   - The mains side must be `isolated` from the low-voltage side, which the relay or an opto-triac provides.

2. **Which signal a sensor could to send the signal to microcontroller if the sensor finds any gas leakage point?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 861 (ET: N/A)]*

   Answer: A gas sensor sends the microcontroller either an `analogue voltage` or a `digital HIGH/LOW`, depending on which output pin is used. Almost every gas sensor module — the `MQ` series is the standard — provides `both`.

   The two output signals
   ```
      AO  (analogue out) : a voltage that RISES as the gas concentration rises
                           Typically 0 to 5 V, read by the microcontroller's ADC.
                           Gives the actual concentration, not just present/absent.

      DO  (digital out)  : a single bit, produced by an on-board LM393 comparator
                           that compares AO with a threshold set by a preset.
                           Usually ACTIVE LOW - it goes LOW when gas is detected.
   ```

   How the sensor works
   - The MQ-series sensor uses a heated `tin dioxide (SnO2)` element. In clean air its resistance is high; when a combustible gas such as LPG, methane or CO adsorbs on the surface, its `resistance falls`. A load resistor turns that change into a voltage.
   ```
      No gas     ->  high sensor resistance ->  low  AO voltage , DO = HIGH
      Gas leak   ->  low  sensor resistance ->  high AO voltage , DO = LOW
   ```

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

       Serial.println(level);

       if (level > THRESHOLD || alarm == LOW) {
           digitalWrite(BUZZER, HIGH);        // sound the alarm
           digitalWrite(VALVE, HIGH);         // close the solenoid valve
           // send an SMS or MQTT message here
       } else {
           digitalWrite(BUZZER, LOW);
       }
       delay(500);
   }
   ```

   Which output to use

   | Point | Analogue (AO) | Digital (DO) |
   |---|---|---|
   | Signal | Continuous voltage | Single bit, HIGH or LOW |
   | Read by | ADC pin | Any digital pin |
   | Information | The actual concentration | Only "gas present / absent" |
   | Threshold set by | Software, changeable | Hardware preset on the module |
   | Can trigger an interrupt | No | Yes |
   | Best for | Monitoring, logging, graded alarms | A simple alarm, waking the MCU from sleep |

   - Best practice for a gas-leak system: use `both`. Wire `DO` to an interrupt pin so the microcontroller wakes and reacts instantly, and read `AO` to log the concentration and distinguish a small leak from a dangerous one.
   - Practical points: MQ sensors need a `warm-up` of 20 seconds to a few minutes before their reading is valid, they are `not gas-selective`, and they drift with temperature and humidity — so a proper installation calibrates them and, in a real gas plant, uses an industrial `4-20 mA` transmitter instead of a hobby module.

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
