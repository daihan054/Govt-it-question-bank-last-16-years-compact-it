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

10. **BREB power transmission interrupt related.** *[BREB Assistant General Manager (IT) 2021 compact it 935 (ET: N/A)]*

11. **EEE related 3 math question.** *[BREB Assistant General Manager (IT) 2021 compact it 935 (ET: N/A)]*

12. **নিচের সার্কিটের মোট রেজিস্ট্যান্স বের করে, I_3 এর কারেন্ট বের কর।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

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

2. **RLC সার্কিট কী? বৈদ্যুতিক সার্কিটে ট্রানজিস্টরের ভূমিকা কী?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 809-810 (ET: IBA)]*

## Operational Amplifiers (Op-Amp) (2)

1. **Assuming Ideal Op Amps, Find The Voltage Gain V_o/V_i of the following circuit.** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*

2. **একটি Operational Amplifier এর প্রধান বৈশিষ্ট কী কী? AC Power কিভাবে DC পাওয়ারে রূপান্তরিত হয়?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 809 (ET: IBA)]*

## Sensor Circuits & Automated Control Systems (2)

1. **Design and implement an automated street light control system. The system should ensure that the street lights remain off during the presence of sunlight and automatically turn on in the absence of sunlight (i.e., during nighttime or low ambient light conditions).** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*

2. **Which signal a sensor could to send the signal to microcontroller if the sensor finds any gas leakage point?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 861 (ET: N/A)]*

## Circuit Theorems (Thevenin, Norton, Superposition) (2)

1. **Find current across 2 \Omega resistor using Thevenin Theorem:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 417 (ET: BUET)]*

2. **Find the Value of I_{ab} using Norton's Theorem.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*

## Electrical Machines (Motors & Alternators) (1)

1. **A 3phase 12 pole alternator running at 500 rpm supplying power to an 8 pole induction motor. If ship is 3% what is the full load speed of the motor?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1054 (ET: BUET)]*
