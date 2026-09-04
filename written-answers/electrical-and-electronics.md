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

2. **How many terminals does a BJT have?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

3. **In an NPN transistor, the current flows from _____** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

4. **Which BJT configuration gives maximum voltage gain?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

5. **Collector current (Ic) is related to base current (Ib) by _____** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

6. **N-Channel MOS operating in the linear region. Calculate the current passing through the channel of the transistor. Given: \mu_n C_{ox} (W/L) = 1.3\text{ mA/V}^2, V_{GS} = 2.5\text{ V}, V_t = 0.95\text{ V}. Assume reasonable values for missing parameters if necessary.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

7. **Describe cut off, saturation and active region of operation of a transistor with diagram. Explain the working principal of ab n-channel JFET with various values of V_{GS} and V_{DS}.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 445 (ET: BIBM)]*

8. **(a) Draw and explain the operation of NMOS transistor.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*

9. **ইমিটার কারেন্টের মান 1 Amp, কালেক্টর কারেন্ট 0.95 A হলে বেইস (Base) কারেন্টের মান কত? একটি চিত্র দেওয়া ছিল!!** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

## Semiconductor Devices & Diodes (4)

1. Explain the working principle of a PN junction diode. Draw its symbol and describe the difference between forward bias and reverse bias. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

2. **Determine the current passing through a 10\text{ k}\Omega resistor. Assume a forward voltage drop of 0.75\text{ V} across the diode.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

3. **What is Diode and Inductor?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

4. **How does LED differ from Laser Diod? What are the function of Diode?** *[BTRC Assistant Director (Technical) 2021 compact it 808 (ET: IBA)]*

## Digital-to-Analog & Analog-to-Digital Converters (DAC/ADC) (4)

1. **You are required to convert a 12-bit digital number to an analogue voltage over the voltage range of 0 to 3.3V with a Digital-to-Analogue Converter (DAC). What is the resolution of the analogue output?** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 419 (ET: BIBM)]*

2. **An 8 bit (Analog to Digital Converter) = 2.56v. Let the minimum analog voltage = 0v. Calculate binary data output if analog input=1.7** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)]*

3. **Draw an ADC converter circuit which convert an analog signal to digital signal.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*

4. **(ক) A/D Converter দ্বারা কিভাবে একটি Analog signal Digital signal এ রূপান্তরিত করা হয়। ডায়াগ্রাম সহ লিখুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 776 (ET: N/A)]*

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
