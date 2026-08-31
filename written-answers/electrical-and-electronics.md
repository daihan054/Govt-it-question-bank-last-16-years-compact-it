<!-- TOC START -->
**Table of Contents** — 8 subtopics · 37 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Electrical Circuits & Protection Devices](#electrical-circuits--protection-devices-12) | 12 |
| 2 | [Transistors (BJT & FET)](#transistors-bjt--fet-9) | 9 |
| 3 | [Semiconductor Devices & Diodes](#semiconductor-devices--diodes-4) | 4 |
| 4 | [Digital-to-Analog & Analog-to-Digital Converters (DAC/ADC)](#digital-to-analog--analog-to-digital-converters-dacadc-4) | 4 |
| 5 | [AC Circuits & Power Analysis](#ac-circuits--power-analysis-2) | 2 |
| 6 | [Operational Amplifiers (Op-Amp)](#operational-amplifiers-op-amp-2) | 2 |
| 7 | [Sensor Circuits & Automated Control Systems](#sensor-circuits--automated-control-systems-2) | 2 |
| 8 | [Circuit Theorems (Thevenin, Norton, Superposition)](#circuit-theorems-thevenin-norton-superposition-2) | 2 |

<!-- TOC END -->

---

## Electrical Circuits & Protection Devices (12)

1. Differentiate between a Fuse and a Miniature Circuit Breaker (MCB). Which one is more suitable for modern office electrical installations and why? *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer: Both a fuse and an MCB protect a circuit from overcurrent, but they work on different principles.

   | Point | Fuse | Miniature Circuit Breaker (MCB) |
   |---|---|---|
   | Working principle | A thin metal wire melts when the current exceeds its rating (thermal only) | Bimetallic strip for overload plus an electromagnetic solenoid for short circuit |
   | After a fault | Destroyed, must be replaced | Simply reset by flipping the lever |
   | Operating speed | Slow for overload, fast for short circuit | Very fast for short circuit (about 2.5 ms), time-delayed for overload |
   | Accuracy of tripping | Loose, depends on ambient temperature and wire ageing | Precise, follows a defined B, C or D tripping curve |
   | Fault indication | No indication, must be tested to find the blown one | The tripped lever shows exactly which circuit failed |
   | Manual switching | Cannot be used as a switch | Can be used as an ON/OFF isolating switch |
   | Sensitivity to people | Does not detect earth leakage | Can be combined with an RCCB/RCBO for earth leakage protection |
   | Initial cost | Low | Higher (about 3 to 5 times) |
   | Running cost | Recurring cost of replacement fuse wire and downtime | Almost zero, reusable |
   | Safety during replacement | Person must open the holder and handle live parts | No handling needed, just reset |

   More suitable for a modern office: the MCB.

   Reasons:
   - Offices run many computers, servers, UPS units and air conditioners. A nuisance trip in one branch must be cleared in seconds, not after finding a spare fuse wire.
   - The MCB is reset instantly by a non-technical person, so downtime is minutes instead of hours.
   - Its tripping curve is accurate and repeatable, so a sensitive load such as a server power supply is protected consistently; a fuse rating drifts as the element ages.
   - The tripped switch identifies the faulty circuit immediately, which speeds up maintenance in a distribution board with many branch circuits.
   - It acts as an isolating switch, so a circuit can be shut down safely for maintenance without touching live parts.
   - It can be combined with an RCBO to give both overcurrent and earth leakage protection in one unit, which matters where people touch metal-bodied equipment all day.
   - The higher purchase cost is recovered quickly through zero replacement cost and reduced downtime.

   Fuses remain useful only where cost is critical or where extremely fast short-circuit clearing is needed, such as inside an electronic power supply.
2. **Find the Norton equivalent circuit for a DC power supply that has a 30 V terminal voltage when delivering 400mA and a 28V terminal voltage. When delivering 600mA.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1436 (ET: BUET)]*


   Answer: A real DC supply behaves as an ideal source with an internal resistance in series, so the terminal voltage falls as the load current rises. Two measurement points are enough to find both the internal resistance and the open-circuit voltage.

   Given:
   - V1 = 30 V at I1 = 400 mA = 0.4 A
   - V2 = 28 V at I2 = 600 mA = 0.6 A

   Step 1 - find the internal (Thevenin/Norton) resistance from the slope of the V-I line:
   - R = (V1 - V2) / (I2 - I1)
   - R = (30 - 28) / (0.6 - 0.4) = 2 / 0.2 = 10 ohm

   Step 2 - find the open-circuit (Thevenin) voltage using V = Voc - I.R:
   - Voc = V1 + I1.R = 30 + (0.4 x 10) = 30 + 4 = 34 V
   - Check with the second point: Voc = 28 + (0.6 x 10) = 28 + 6 = 34 V. Both agree.

   Step 3 - find the Norton current, which is the short-circuit current:
   - IN = Voc / RN = 34 / 10 = 3.4 A

   Step 4 - Norton resistance equals Thevenin resistance:
   - RN = 10 ohm

   Norton equivalent circuit:

   ```
        +----------------+-------o a
        |                |
      ( ^ ) IN = 3.4 A   [ ] RN = 10 ohm
        |                |
        +----------------+-------o b
   ```

   Final answer: a 3.4 A ideal current source in parallel with a 10 ohm resistance.

   Verification at 400 mA: the resistor carries 3.4 - 0.4 = 3.0 A, so the terminal voltage is 3.0 x 10 = 30 V. Correct.
3. **Which Transformer is used in computer?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*


   Answer: A step-down transformer is used in a computer.

   Explanation:
   - The SMPS (Switched Mode Power Supply) inside a computer takes 220 V AC from the mains and must produce the low DC rails the machine needs: +12 V, +5 V, +3.3 V and their negative counterparts.
   - So the transformer must reduce the voltage, which means the secondary has fewer turns than the primary: Ns is less than Np, and Vs/Vp = Ns/Np.
   - Specifically it is a high-frequency ferrite-core step-down transformer. The SMPS first rectifies the mains to about 310 V DC, chops it at 50 to 100 kHz, and then steps it down. Working at a high frequency lets the core be small and light, which is why a computer power supply is far smaller than an old iron-core linear supply of the same rating.
   - An isolation function comes with it: the transformer separates the mains side from the low-voltage side, so the user never touches a circuit connected directly to the mains.

   Final answer: a step-down (high-frequency ferrite-core) transformer inside the SMPS.
4. **What is the name of AC current to DC current?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*


   Answer: The process of converting AC current into DC current is called rectification, and the circuit that performs it is called a rectifier.

   - The device most commonly used is the semiconductor diode, which conducts in only one direction.
   - Types: half-wave rectifier (one diode, uses one half cycle), full-wave centre-tapped rectifier (two diodes), and full-wave bridge rectifier (four diodes, the type used in almost all equipment).
   - The rectifier output is pulsating DC, so a filter capacitor and usually a voltage regulator follow it to give smooth constant DC.
   - The reverse process, DC to AC, is called inversion and the circuit is called an inverter.

   Final answer: rectification (carried out by a rectifier).
5. **How to AC converted into DC?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*


   Answer: AC is converted into DC by rectification followed by filtering and regulation. A complete DC power supply has four stages.

   ```mermaid
   flowchart LR
     AC[220 V AC Mains] --> T[Step-down Transformer]
     T --> R[Rectifier - Bridge of 4 Diodes]
     R --> F[Filter - Capacitor]
     F --> RG[Regulator - IC 7805 or Zener]
     RG --> DC[Steady DC Output]
   ```

   Stage 1 - Transformer:
   - Steps the 220 V AC mains down to a low AC voltage, for example 12 V AC, and isolates the load from the mains.

   Stage 2 - Rectifier:
   - Diodes conduct in one direction only, so they let current pass in one direction and block the reverse direction.
   - Half-wave rectifier: one diode, output present in only one half cycle, poor efficiency (40.6 percent), ripple frequency = 50 Hz.
   - Full-wave bridge rectifier: four diodes in a bridge. In each half cycle two diodes conduct, so both halves of the input appear at the output with the same polarity. Efficiency 81.2 percent, ripple frequency = 100 Hz. This is the type normally used.
   - The output at this point is pulsating DC, that is unidirectional but not constant.

   Stage 3 - Filter:
   - A large electrolytic capacitor in parallel with the load charges at the peak and discharges slowly between peaks, filling the gaps and smoothing the waveform.
   - Ripple factor of a bridge rectifier without a filter is 0.48; with a capacitor filter it drops to a few percent.
   - Ripple voltage is approximately Vr = I / (f x C), so a larger capacitor gives smaller ripple.

   Stage 4 - Regulator:
   - A Zener diode or a three-terminal regulator IC (7805, 7812, LM317) holds the output constant even when the mains voltage or the load current changes.

   Final answer: AC is converted to DC by a rectifier (usually a full-wave bridge), and the pulsating DC is then smoothed by a capacitor filter and held constant by a voltage regulator.
6. **Find R and I from a circuit.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*

7. **Audio Frequency ও Radio Frequency এর মধ্যেকার পার্থক্য লিখুন। ১০ ওহমের ১০টি ট্রানজিস্টর কোন সিরিজে সংযুক্ত হলে তাতে রেজিস্ট্যান্স কত হবে?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 810 (ET: IBA)]*


   Answer:

   Difference between audio frequency and radio frequency:

   | Point | Audio Frequency (AF) | Radio Frequency (RF) |
   |---|---|---|
   | Range | 20 Hz to 20 kHz | About 3 kHz to 300 GHz |
   | Perception | Audible to the human ear | Not audible |
   | Radiation | Does not radiate usefully; the antenna needed would be kilometres long | Radiates efficiently through space with a practical antenna |
   | Antenna length | Impractical (an antenna is about one quarter of a wavelength; at 1 kHz that is 75 km) | Practical (at 100 MHz a quarter wave is only 0.75 m) |
   | Transmission medium | Wire, or air as a sound wave over a short distance | Free space as an electromagnetic wave |
   | Role in communication | It is the baseband or message signal | It is the carrier signal |
   | Typical circuit | Audio amplifier, loudspeaker, microphone | Oscillator, mixer, modulator, antenna |
   | Example | Speech at 300 to 3400 Hz, music | FM radio at 88 to 108 MHz, Wi-Fi at 2.4 GHz |

   The reason a carrier is needed: the audio signal is modulated onto the RF carrier so that it can be radiated from a small antenna and so that many stations can share the same space on different carrier frequencies.

   Numerical part - ten 10 ohm elements connected in series:

   In a series connection the total resistance is the simple sum of the individual resistances:
   - Rtotal = R1 + R2 + ... + R10
   - Rtotal = 10 x 10 ohm
   - Rtotal = 100 ohm

   Final answer: 100 ohm.

   For comparison, the same ten elements in parallel would give 1/Rtotal = 10/10, so Rtotal = 1 ohm.
8. **Write down the function of Relay, Fuse and Circuit Breaker.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*


   Answer:

   Relay:
   - An electrically operated switch. A small current through a coil creates a magnetic field that pulls an armature and moves one or more contacts.
   - Function: to let a low-power circuit (a microcontroller output of 5 V, 20 mA) switch a high-power circuit (230 V, 10 A motor or lamp).
   - It also gives electrical isolation between the control side and the load side, so a fault on the load side cannot damage the controller.
   - Contact types: NO (normally open), NC (normally closed) and changeover.
   - Protective relays additionally sense overcurrent, undervoltage or earth fault and command a circuit breaker to trip.

   Fuse:
   - A short piece of thin metal wire with a low melting point, connected in series with the load.
   - Function: to protect the circuit and the wiring from overcurrent. When the current exceeds the rated value, the heat I^2.R.t melts the wire and breaks the circuit.
   - It is a sacrificial device: it destroys itself to save the equipment and must be replaced after operating.
   - It is fast against a short circuit but cannot be reset, and it does not protect a person against electric shock.

   Circuit breaker:
   - An automatic, resettable protective switch, for example an MCB or MCCB.
   - Function: to break the circuit automatically on overload or short circuit, and also to serve as a manual isolating switch.
   - It has two mechanisms: a bimetallic strip that bends slowly on a sustained overload (thermal), and an electromagnetic coil that trips instantly on a heavy short circuit (magnetic).
   - After the fault is cleared it is simply reset by hand, so there is no consumable part.

   Summary of the difference in role:
   - The relay is a control device that switches a circuit on command.
   - The fuse and the circuit breaker are protection devices that open the circuit on fault; the fuse is one-time, the circuit breaker is reusable.
9. **Find the Value of I.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*

10. **BREB power transmission interrupt related.** *[BREB Assistant General Manager (IT) 2021 compact it 935 (ET: N/A)]*

11. **EEE related 3 math question.** *[BREB Assistant General Manager (IT) 2021 compact it 935 (ET: N/A)]*

12. **নিচের সার্কিটের মোট রেজিস্ট্যান্স বের করে, I_3 এর কারেন্ট বের কর।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

## Transistors (BJT & FET) (9)

1. **What does BJT stand for?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: BJT stands for Bipolar Junction Transistor.

   It is a three terminal semiconductor device made of two p-n junctions. We use it mainly for amplifying a signal and for switching. It is called bipolar because both electrons and holes carry the current inside it.

2. **How many terminals does a BJT have?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: A BJT has three terminals.

   - Emitter (E): the outermost layer, heavily doped. It supplies the charge carriers into the base.
   - Base (B): the middle layer, lightly doped and very thin. It sits between the emitter and the collector.
   - Collector (C): the other outer layer, moderately doped. It collects the charge carriers coming through the base.

   The doping is deliberately unequal. The emitter is heavily doped so it can inject plenty of carriers. The base is thin and lightly doped so that most of those carriers pass straight through instead of recombining. The collector is the largest, because it has to dissipate the heat.

3. **In an NPN transistor, the current flows from _____** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: In an NPN transistor the conventional current flows from the collector to the emitter.

   Explanation:
   - An NPN transistor has a P-type base sandwiched between two N-type layers, which are the emitter and the collector.
   - The actual charge carriers are electrons. They move from the emitter into the base and on to the collector.
   - Conventional current is defined opposite to electron flow. So the conventional current enters at the collector and at the base, and leaves at the emitter.
   - The relation is IE = IC + IB, so the emitter current is the largest of the three.
   - In a PNP transistor everything is reversed: holes carry the current, and the conventional current flows from the emitter to the collector.

4. **Which BJT configuration gives maximum voltage gain?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: The Common Base (CB) configuration gives the maximum voltage gain.

   | Configuration | Current gain | Voltage gain | Main use |
   |---|---|---|---|
   | Common Base | Low, α = IC/IE, always less than 1 | High | Impedance matching, RF amplifiers |
   | Common Emitter | Medium, β = IC/IB | Medium | General purpose amplification |
   | Common Collector | High, γ = IE/IB | Low, less than 1 | Current buffering, impedance transformation |

   - Common Base gives the highest voltage gain, because its input resistance is very low and its output resistance is very high. But its current gain is below 1, so it cannot amplify current at all.
   - Note the distinction the examiner is testing: Common Emitter gives the highest power gain, because it amplifies both voltage and current. Common Base gives the highest voltage gain alone. Common Collector, also called the emitter follower, gives the highest current gain.

5. **Collector current (Ic) is related to base current (Ib) by _____** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: The collector current is related to the base current by the current gain β, that is beta.

   IC = β × IB

   Key points:
   - β is the current gain of the common emitter configuration. It is also written as hFE.
   - β = IC / IB. A typical value is between 20 and 200, so a very small base current controls a much larger collector current. That is what makes the transistor an amplifier.
   - The related constant α is the common base current gain: α = IC / IE, and it is always slightly less than 1.
   - The three currents are linked by IE = IC + IB.
   - Relation between the two gains: β = α / (1 − α), and α = β / (1 + β).

6. **N-Channel MOS operating in the linear region. Calculate the current passing through the channel of the transistor. Given: \mu_n C_{ox} (W/L) = 1.3\text{ mA/V}^2, V_{GS} = 2.5\text{ V}, V_t = 0.95\text{ V}. Assume reasonable values for missing parameters if necessary.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*


   Answer:

   Given: μₙCₒₓ(W/L) = 1.3 mA/V², V_GS = 2.5 V, V_t = 0.95 V. The transistor is stated to be in the linear, that is triode, region.

   Step 1: find the overdrive voltage

   V_ov = V_GS − V_t
   = 2.5 − 0.95
   = 1.55 V

   Step 2: check the condition for the linear region

   An NMOS is in the linear region when V_DS < V_GS − V_t, that is V_DS < 1.55 V.
   The value of V_DS is not given in the question, so we assume a reasonable value inside that range. Take V_DS = 0.5 V.

   Step 3: apply the linear region current equation

   I_D = μₙCₒₓ(W/L) × [ (V_GS − V_t)·V_DS − ½·V_DS² ]

   Step 4: substitute the numbers

   I_D = 1.3 × [ (1.55)(0.5) − 0.5 × (0.5)² ]
   = 1.3 × [ 0.775 − 0.125 ]
   = 1.3 × 0.65

   Final answer: I_D = 0.845 mA

   Note on the assumption: V_DS was missing from the question, so it had to be assumed. Any value below 1.55 V keeps the device in the linear region. For example, with V_DS = 0.2 V the current would be 1.3 × [(1.55)(0.2) − 0.5(0.04)] = 1.3 × 0.29 = 0.377 mA. The method is the same; only the assumed V_DS changes the number. <!-- verify -->

7. **Describe cut off, saturation and active region of operation of a transistor with diagram. Explain the working principal of ab n-channel JFET with various values of V_{GS} and V_{DS}.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 445 (ET: BIBM)]*


   Answer:

   Part 1: the three regions of operation of a BJT

   | Region | Emitter-Base junction | Collector-Base junction | Behaviour |
   |---|---|---|---|
   | Cut off | Reverse biased | Reverse biased | The transistor is fully OFF. IB = 0, so IC = 0. It acts like an open switch |
   | Active | Forward biased | Reverse biased | The transistor amplifies. IC = β·IB. A small base current controls a large collector current |
   | Saturation | Forward biased | Forward biased | The transistor is fully ON. V_CE is very small, about 0.2 V. It acts like a closed switch |

   Output characteristic diagram, IC against V_CE:

   ```
   IC ^
      |            Active region
      |   ,-------------------------------  IB = 60 µA
      |  /
      | /  ,--------------------------------  IB = 40 µA
      |/  /
      |  /  ,-------------------------------  IB = 20 µA
      | /  /
      |/  /
      +--+--------------------------------->  V_CE
      |<>| Saturation region
      +--------------------------------------  IB = 0  (Cut off region)
   ```

   - In the saturation region, at the far left, IC rises very steeply with V_CE.
   - In the active region the curves are almost flat, so IC depends on IB and hardly on V_CE. This is where amplification happens.
   - Along the bottom axis, with IB = 0, is the cut off region.
   - For switching we use only cut off and saturation. For amplifying we use only the active region.

   Part 2: working of an n-channel JFET

   Construction: a bar of n-type silicon forms the channel. Two heavily doped p-type regions on its sides form the gate. The two ends of the bar are the drain and the source. In normal operation the gate-channel junction is always reverse biased, which is why the gate draws almost no current.

   Effect of V_GS, with V_DS held small:
   - V_GS = 0: the channel is at its widest. The current I_D is maximum, and we call it I_DSS, the drain to source saturation current.
   - V_GS made negative: the reverse bias widens the depletion regions on both sides. They squeeze into the channel and make it narrower, so I_D falls.
   - V_GS more negative still: at one particular value the two depletion regions meet in the middle and close the channel completely. I_D becomes zero. That voltage is called the pinch-off voltage V_P, or the gate-source cutoff voltage.
   - So the gate voltage controls the drain current by changing the width of the channel. This is why a JFET is called a voltage controlled device, unlike a BJT, which is current controlled.

   Effect of V_DS, with V_GS held at 0:
   - Ohmic region, small V_DS: the channel behaves like a simple resistor, and I_D rises almost in a straight line with V_DS.
   - As V_DS grows: the drain end of the channel becomes more reverse biased than the source end, so the depletion region is wider at the drain end and the channel becomes wedge shaped. The rise of I_D starts to bend over.
   - Pinch-off point, V_DS = V_P: the channel just closes at the drain end.
   - Saturation region, V_DS > V_P: I_D stays almost constant even though V_DS keeps rising. This flat region is where the JFET is used as an amplifier.
   - Breakdown region, V_DS very high: the junction breaks down and I_D shoots up. The device must not be operated here.

   The drain current in the saturation region follows Shockley's equation:

   I_D = I_DSS (1 − V_GS/V_P)²

8. **(a) Draw and explain the operation of NMOS transistor.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*


   Answer: NMOS stands for n-channel Metal Oxide Semiconductor Field Effect Transistor.

   Construction:

   ```
            Gate
             |
      +------+------+
      |   metal     |         <- gate terminal
      +-------------+
      |  oxide SiO2 |         <- thin insulating layer
   +--+-------------+--+
   |  n+         n+    |      <- source and drain, heavily doped n-type
   |  |  channel  |    |
   |  +-----------+    |
   |     p-substrate   |      <- body, p-type
   +-------------------+
      |               |
    Source          Drain
   ```

   - Two heavily doped n-type regions sit in a p-type substrate. These are the source and the drain.
   - The gate is a metal or polysilicon plate, separated from the substrate by a very thin layer of silicon dioxide. This oxide is an insulator, so no current ever flows into the gate. That is why the input resistance is enormous.
   - The region between source and drain, under the gate, is where the channel will form.

   Operation:
   - V_GS = 0: there is no channel. The source and drain are two back to back p-n junctions, so no current can flow between them. The device is OFF.
   - V_GS positive but below V_t: the positive gate pushes the holes of the p-substrate away, leaving a depletion region under the gate. There is still no channel, so still no current.
   - V_GS reaches the threshold voltage V_t: the gate now pulls enough free electrons to the surface to form a thin n-type layer joining the source to the drain. This layer is the channel, and it is called an inversion layer, because the p-type surface has been inverted into n-type. The device is ON.
   - Raising V_GS further makes the channel thicker, so more current flows. This is how the gate voltage controls the drain current, without ever drawing gate current.

   Two regions of operation once the channel exists:
   - Linear or triode region, when V_DS < V_GS − V_t. The channel is continuous from source to drain and behaves like a controlled resistor.

     I_D = μₙCₒₓ(W/L) × [ (V_GS − V_t)V_DS − ½V_DS² ]

   - Saturation region, when V_DS ≥ V_GS − V_t. The channel pinches off at the drain end, and I_D becomes almost independent of V_DS.

     I_D = ½ μₙCₒₓ(W/L) × (V_GS − V_t)²

   Why NMOS is important: it is the building block of all digital logic. In a CMOS inverter an NMOS and a PMOS are used together, so that current flows only while the output is switching. That is why CMOS uses so little power, and it is why almost every chip today is CMOS.

9. **ইমিটার কারেন্টের মান 1 Amp, কালেক্টর কারেন্ট 0.95 A হলে বেইস (Base) কারেন্টের মান কত? একটি চিত্র দেওয়া ছিল!!** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*


   Answer:

   Given: emitter current I_E = 1 A, collector current I_C = 0.95 A. Find the base current I_B.

   Formula: the three transistor currents are related by

   I_E = I_C + I_B

   Rearranging for the base current:

   I_B = I_E − I_C

   Substituting:

   I_B = 1 − 0.95
   = 0.05 A

   Final answer: I_B = 0.05 A, that is 50 mA.

   Two related quantities that follow from the same figures:
   - Common base current gain: α = I_C / I_E = 0.95 / 1 = 0.95
   - Common emitter current gain: β = I_C / I_B = 0.95 / 0.05 = 19
   - Check with the standard relation: β = α/(1 − α) = 0.95/0.05 = 19. It matches.

   Note that the base current is always the smallest of the three, because the base is thin and lightly doped, so only a small fraction of the carriers recombine there. That is exactly what makes the transistor useful as an amplifier.

## Semiconductor Devices & Diodes (4)

1. Explain the working principle of a PN junction diode. Draw its symbol and describe the difference between forward bias and reverse bias. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer: A PN junction diode is formed when a p-type semiconductor (rich in holes) is joined to an n-type semiconductor (rich in electrons) in a single crystal. It conducts current in one direction only.

   Formation of the junction:
   - At the moment of joining, electrons from the n-side diffuse into the p-side and holes from the p-side diffuse into the n-side, and they recombine near the junction.
   - This leaves behind fixed positive ions on the n-side and fixed negative ions on the p-side, forming a region with no free carriers called the depletion region.
   - The fixed charges set up an internal electric field, and the potential across it is called the barrier potential: about 0.7 V for silicon and 0.3 V for germanium. This field stops further diffusion, so the junction reaches equilibrium.

   Symbol:

   ```
        Anode (P)          Cathode (N)
           ----|>|----
              A     K
   ```

   The triangle points in the direction of conventional current flow, and the bar is the cathode (marked with a band on the body of the component).

   | Point | Forward bias | Reverse bias |
   |---|---|---|
   | Connection | P side to positive terminal, N side to negative terminal | P side to negative terminal, N side to positive terminal |
   | Effect on depletion region | Narrows | Widens |
   | Effect on barrier potential | Reduced | Increased |
   | Junction resistance | Very low, a few ohm | Very high, in mega ohm |
   | Current | Large, due to majority carriers; typically mA to A | Very small reverse saturation current, in nA (Si) or microampere (Ge), due to minority carriers |
   | Voltage across the diode | Almost constant at 0.7 V (Si) once conducting | Equal to the applied reverse voltage |
   | State | ON, acts as a closed switch | OFF, acts as an open switch |
   | Effect of temperature | Barrier voltage falls about 2 mV per degree C | Reverse current roughly doubles every 10 degree C |

   Forward bias in detail: once the applied voltage exceeds the barrier potential (the knee or cut-in voltage), the external field overcomes the internal field, majority carriers cross the junction and a large current flows. Beyond the knee the current rises almost exponentially, following the diode equation I = Is.(e^(V/nVT) - 1), so a series resistor must limit it.

   Reverse bias in detail: the applied field adds to the internal field, so the depletion region widens and only the tiny minority-carrier current flows. If the reverse voltage is raised beyond the breakdown voltage, avalanche or Zener breakdown occurs and the current rises sharply. An ordinary diode is destroyed by this, but a Zener diode is designed to operate there and is used as a voltage regulator.

   Main applications: rectification, clipping and clamping, freewheeling protection across a relay coil, and demodulation.
2. **Determine the current passing through a 10\text{ k}\Omega resistor. Assume a forward voltage drop of 0.75\text{ V} across the diode.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*


   Answer: In a simple series circuit of a source, a diode and a resistor, the diode drops a fixed forward voltage and the rest of the source voltage appears across the resistor.

   Given:
   - R = 10 k ohm = 10,000 ohm
   - Forward voltage drop of the diode, VD = 0.75 V
   - The source voltage is not stated, so a standard laboratory supply is assumed: VS = 5 V

   Step 1 - apply Kirchhoff's voltage law around the loop:
   VS = VD + VR

   Step 2 - find the voltage across the resistor:
   - VR = VS - VD
   - VR = 5 - 0.75 = 4.25 V

   Step 3 - apply Ohm's law:
   - I = VR / R
   - I = 4.25 / 10,000
   - I = 0.425 x 10^-3 A

   Final answer: I = 0.425 mA (with the assumed 5 V supply).

   General formula for any supply voltage:
   I = (VS - 0.75) / 10 k ohm

   For example, with VS = 12 V the current would be (12 - 0.75)/10,000 = 1.125 mA.

   Note: if the diode were reverse biased, it would block and the current would be only the reverse saturation current, which is a few nanoamperes and is treated as zero.
3. **What is Diode and Inductor?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*


   Answer:

   Diode:
   - A two-terminal semiconductor device formed by a PN junction, having an anode (P side) and a cathode (N side).
   - It conducts current in one direction only: it conducts when forward biased (anode positive, drop about 0.7 V for silicon) and blocks when reverse biased.
   - It is a non-linear and unidirectional device, so it acts as an electronic one-way valve or switch.
   - Uses: rectification (AC to DC), clipping and clamping of waveforms, freewheeling protection across inductive loads, voltage regulation (Zener diode), light emission (LED), and light detection (photodiode).

   Inductor:
   - A passive two-terminal component made of a coil of wire, often wound on an iron or ferrite core.
   - It stores energy in a magnetic field when current flows through it. Its property is called inductance L, measured in henry (H).
   - Its defining relation is v = L.(di/dt), so it opposes any change of current through it. By Lenz's law it induces a back EMF that resists the change.
   - Energy stored: W = (1/2).L.I^2
   - Its reactance rises with frequency: XL = 2.pi.f.L. So it passes DC easily and blocks high frequency, which makes it act as a low-pass element.
   - The current through an inductor cannot change instantly, which is why a spark appears when an inductive circuit is broken.
   - Uses: filters and chokes in power supplies, tuned LC circuits in radios, transformers, relay and motor coils, and energy storage in switching regulators.

   Key contrast: a diode is an active, non-linear semiconductor device that controls the direction of current, while an inductor is a passive, linear component that stores magnetic energy and opposes change of current.
4. **How does LED differ from Laser Diod? What are the function of Diode?** *[BTRC Assistant Director (Technical) 2021 compact it 808 (ET: IBA)]*


   Answer:

   Difference between an LED and a Laser diode:

   | Point | LED (Light Emitting Diode) | Laser Diode |
   |---|---|---|
   | Emission process | Spontaneous emission | Stimulated emission inside an optical cavity |
   | Light coherence | Incoherent, random phase | Coherent, all photons in phase |
   | Spectral width | Wide, about 30 to 50 nm | Narrow, about 1 to 3 nm |
   | Beam divergence | Wide, about 60 degree, spreads quickly | Very narrow, about 5 to 10 degree |
   | Threshold current | None, emits light from a very low current | Emits laser light only above a threshold current |
   | Output power | Low, microwatt to a few mW | High, mW to watt |
   | Modulation speed | Slower, up to about 200 Mbps | Fast, several Gbps and above |
   | Coupling into fibre | Poor, suits multimode fibre only | Efficient, suits single-mode fibre |
   | Transmission distance | Short, up to about 2 km | Long, tens to hundreds of km |
   | Temperature sensitivity | Low | High, needs a cooler and a monitor photodiode |
   | Cost and lifetime | Cheap, long life | Expensive, shorter life |
   | Typical use | Indicators, displays, short-haul fibre links, remote controls | Long-haul fibre optic communication, optical drives, barcode scanners, surgery, printing |

   Functions of a diode:
   - Rectification: converts AC into DC in half-wave, full-wave and bridge rectifiers.
   - Switching: turns a circuit path on or off, used in logic circuits and in switching power supplies.
   - Clipping: limits a waveform to a fixed level, used to protect an input from overvoltage.
   - Clamping: shifts the DC level of a waveform without changing its shape.
   - Freewheeling (flyback) protection: placed across a relay or motor coil to absorb the back EMF when the coil is switched off.
   - Voltage regulation: a Zener diode operated in reverse breakdown holds a constant output voltage.
   - Reverse polarity protection: blocks current if the supply is connected the wrong way round.
   - Demodulation: recovers the audio signal from an AM radio carrier.
   - Light emission and detection: LED, laser diode, photodiode and solar cell.
   - Voltage multiplication: diode and capacitor ladders produce a high DC voltage from a low AC voltage.
   - Variable capacitance: a varactor diode is used to tune an oscillator.

## Digital-to-Analog & Analog-to-Digital Converters (DAC/ADC) (4)

1. **You are required to convert a 12-bit digital number to an analogue voltage over the voltage range of 0 to 3.3V with a Digital-to-Analogue Converter (DAC). What is the resolution of the analogue output?** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 419 (ET: BIBM)]*


   Answer: The resolution of a DAC is the smallest change in the analogue output produced by a change of one LSB in the digital input.

   Given:
   - Number of bits, n = 12
   - Output voltage range (full-scale range, FSR) = 0 to 3.3 V, so FSR = 3.3 V

   Step 1 - find the number of discrete output steps:
   - Number of codes = 2^n = 2^12 = 4096
   - Number of steps between the lowest and the highest code = 2^n - 1 = 4095

   Step 2 - apply the resolution formula:
   - Resolution = FSR / (2^n - 1)
   - Resolution = 3.3 / 4095

   Step 3 - compute:
   - Resolution = 0.00080586 V
   - Resolution = 0.806 mV = 806 microvolt (approximately)

   Final answer: the resolution is about 0.806 mV per LSB (roughly 0.8 mV).

   Notes:
   - Expressed as a percentage, resolution = 1/4095 x 100 = 0.0244 percent of full scale.
   - Some texts use FSR / 2^n = 3.3 / 4096 = 0.8057 mV. The difference is negligible; the 2^n - 1 form is used when the maximum code must give exactly 3.3 V.
   - The maximum output voltage is therefore 4095 x 0.806 mV = 3.3 V and the minimum is 0 V.
2. **An 8 bit (Analog to Digital Converter) = 2.56v. Let the minimum analog voltage = 0v. Calculate binary data output if analog input=1.7** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)]*


   Answer: An ADC divides its reference (full-scale) voltage into 2^n equal steps and outputs the code that corresponds to the input.

   Given:
   - Number of bits, n = 8
   - Full-scale (reference) voltage, Vref = 2.56 V
   - Minimum analogue voltage = 0 V
   - Analogue input, Vin = 1.7 V

   Step 1 - find the number of steps:
   - 2^n = 2^8 = 256

   Step 2 - find the step size (resolution):
   - Step size = Vref / 2^n
   - Step size = 2.56 / 256 = 0.01 V = 10 mV per LSB

   Step 3 - find the digital output code:
   - Code = Vin / step size
   - Code = 1.7 / 0.01 = 170 (decimal)

   Step 4 - convert 170 to 8-bit binary by repeated division by 2:
   - 170 / 2 = 85, remainder 0
   - 85 / 2 = 42, remainder 1
   - 42 / 2 = 21, remainder 0
   - 21 / 2 = 10, remainder 1
   - 10 / 2 = 5, remainder 0
   - 5 / 2 = 2, remainder 1
   - 2 / 2 = 1, remainder 0
   - 1 / 2 = 0, remainder 1
   - Reading the remainders from bottom to top: 1010 1010

   Final answer: the binary output is 1010 1010 (170 in decimal, AA in hexadecimal).

   Verification: 170 x 0.01 V = 1.70 V, which matches the input exactly, so there is no quantisation error for this particular input.
3. **Draw an ADC converter circuit which convert an analog signal to digital signal.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*


   Answer: The most commonly drawn ADC is the successive approximation register (SAR) type, because it gives a good balance of speed, accuracy and cost and is the type built into almost every microcontroller.

   Block diagram of a SAR ADC:

   ```mermaid
   flowchart LR
     AIN[Analog Input Vin] --> SH[Sample and Hold]
     SH --> CMP[Comparator]
     DAC[Internal DAC] --> CMP
     CMP --> SAR[Successive Approximation Register]
     SAR --> DAC
     SAR --> OUT[n-bit Digital Output]
     CLK[Clock] --> SAR
     VREF[Reference Voltage] --> DAC
   ```

   Working:
   1. The sample-and-hold circuit takes a sample of the input and holds it steady while the conversion runs, so the value cannot drift during comparison.
   2. The SAR sets the MSB of its register to 1 and clears the rest, so the internal DAC outputs Vref/2.
   3. The comparator compares Vin with the DAC output. If Vin is greater, the bit is kept as 1; otherwise it is reset to 0.
   4. The next lower bit is tried in the same way, and so on down to the LSB.
   5. After n clock cycles the register holds the digital equivalent of the input, and the end-of-conversion signal goes high.

   An n-bit SAR ADC therefore needs exactly n clock cycles per conversion, no matter what the input is.

   Alternative simpler circuit - the flash (parallel comparator) ADC, which is easier to draw for a 3-bit example:

   ```
     Vref
      |
     [R]---+---> comparator 7 --+
      |    |                    |
     [R]---+---> comparator 6 --+
      |    |                    |
     [R]---+---> comparator 5 --+   Priority
      |    |                    +-> Encoder --> 3-bit
     [R]---+---> comparator 4 --+   (8 to 3)      output
      |    |                    |
     [R]---+---> comparator 3 --+
      |    |                    |
     [R]---+---> comparator 2 --+
      |    |                    |
     [R]---+---> comparator 1 --+
      |
     GND        (Vin is fed to the other input of every comparator)
   ```

   Working of the flash ADC: a resistor ladder divides Vref into equally spaced reference levels. Vin is compared with every level at the same time by 2^n - 1 comparators. All comparators below the input level output 1, forming a thermometer code, and a priority encoder converts that into an n-bit binary number.

   Comparison:

   | Type | Speed | Components | Use |
   |---|---|---|---|
   | Flash | Fastest, one clock cycle | 2^n - 1 comparators, very costly for large n | Video, radar, high-speed sampling |
   | SAR | Medium, n clock cycles | One comparator and one DAC | General purpose, microcontrollers |
   | Dual slope | Slowest | One integrator and one counter | Digital multimeters, high noise rejection |
4. **(ক) A/D Converter দ্বারা কিভাবে একটি Analog signal Digital signal এ রূপান্তরিত করা হয়। ডায়াগ্রাম সহ লিখুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 776 (ET: N/A)]*


   Answer: An A/D converter changes a continuous analogue signal into a stream of binary numbers, so that a computer or microcontroller can process it. The conversion is done in four steps.

   ```mermaid
   flowchart LR
     A[Analog Signal from Sensor] --> F[Anti-aliasing Low Pass Filter]
     F --> S[Sampling]
     S --> H[Hold Circuit]
     H --> Q[Quantization]
     Q --> E[Encoding]
     E --> D[Digital Output - Binary Code]
   ```

   Step 1 - Filtering:
   - A low-pass anti-aliasing filter removes any frequency component above half the sampling rate, because such components would fold back and appear as false low frequencies in the output.

   Step 2 - Sampling:
   - The value of the analogue signal is measured at regular intervals Ts, so a continuous-time signal becomes a discrete-time signal.
   - Sampling rate fs = 1/Ts.
   - Nyquist criterion: fs must be at least 2 x fmax, where fmax is the highest frequency in the signal. Speech limited to 4 kHz is therefore sampled at 8 kHz in a telephone system.
   - If fs is less than 2.fmax, aliasing occurs and the original signal cannot be recovered.

   Step 3 - Holding:
   - A sample-and-hold circuit (a capacitor plus a switch and buffer) keeps each sample constant while the conversion takes place, so the value does not change during the comparison.

   Step 4 - Quantization:
   - The full-scale range is divided into 2^n equal levels, where n is the number of bits, and each held sample is rounded to the nearest level.
   - Step size (resolution) = Vref / 2^n.
   - The rounding introduces an unavoidable error called quantization error, whose maximum value is half a step. Increasing n reduces this error.
   - Signal-to-quantization-noise ratio is approximately SQNR = 6.02n + 1.76 dB, so each extra bit adds about 6 dB.

   Step 5 - Encoding:
   - Each quantized level is given a unique n-bit binary code, and the codes are sent out either in parallel or serially.

   Worked example:
   - An 8-bit ADC with Vref = 5 V has a step size of 5/256 = 19.53 mV.
   - An input of 2.5 V gives a code of 2.5/0.01953 = 128, that is 1000 0000.

   Common ADC types: flash (fastest), successive approximation (general purpose), sigma-delta (highest resolution, used in audio) and dual slope (most noise immune, used in multimeters).

## AC Circuits & Power Analysis (2)

1. **A two-element series circuit has an average power of 940\text{W} and a power factor of 0.707 (leading). Determine the circuit elements if the applied voltage is V = 99\cos(600t + 30^\circ)\text{V}.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*


   Answer: A leading power factor means the current leads the voltage, so the reactive element is a capacitor. The two elements in series are therefore a resistor R and a capacitor C.

   Given:
   - Average (real) power, P = 940 W
   - Power factor, cos(theta) = 0.707 leading, so theta = -45 degree
   - Applied voltage, v = 99.cos(600t + 30 degree) V, so Vm = 99 V and omega = 600 rad/s

   Step 1 - find the rms voltage:
   - Vrms = Vm / sqrt(2) = 99 / 1.4142 = 70.00 V

   Step 2 - find the apparent power:
   - S = P / cos(theta) = 940 / 0.707 = 1329.56 VA

   Step 3 - find the rms current:
   - Irms = S / Vrms = 1329.56 / 70.00 = 18.99 A

   Step 4 - find the magnitude of the impedance:
   - |Z| = Vrms / Irms = 70.00 / 18.99 = 3.686 ohm

   Step 5 - resolve the impedance into its two components. With theta = -45 degree:
   - R = |Z|.cos(theta) = 3.686 x 0.707 = 2.606 ohm
   - Xc = |Z|.sin(theta) = 3.686 x 0.707 = 2.606 ohm (capacitive)
   - So Z = 2.606 - j2.606 ohm

   Step 6 - find the capacitance from Xc = 1 / (omega.C):
   - C = 1 / (omega x Xc)
   - C = 1 / (600 x 2.606)
   - C = 1 / 1563.6
   - C = 6.395 x 10^-4 F

   Final answer:
   - R = 2.61 ohm
   - C = 639.4 microfarad (about 640 microfarad)

   Verification: P = Irms^2 x R = (18.99)^2 x 2.606 = 360.6 x 2.606 = 940 W. This matches the given power, so the answer is correct.

   Note: R can also be found directly from P = Irms^2.R once Irms is known, which avoids Step 4.
2. **RLC সার্কিট কী? বৈদ্যুতিক সার্কিটে ট্রানজিস্টরের ভূমিকা কী?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 809-810 (ET: IBA)]*


   Answer:

   RLC circuit:
   - A circuit containing a resistor (R), an inductor (L) and a capacitor (C), connected either in series or in parallel and driven by an AC source.
   - Impedance of the series form: Z = R + j(XL - Xc), where XL = 2.pi.f.L and Xc = 1/(2.pi.f.C).
   - Magnitude: |Z| = sqrt(R^2 + (XL - Xc)^2), and phase angle theta = arctan((XL - Xc)/R).
   - Behaviour with frequency:
     - When XL is greater than Xc the circuit is inductive and the current lags the voltage.
     - When Xc is greater than XL the circuit is capacitive and the current leads the voltage.
     - When XL = Xc the circuit is at resonance.
   - Resonance: XL = Xc gives the resonant frequency
     fr = 1 / (2.pi.sqrt(L.C))
     At resonance the series RLC circuit has minimum impedance Z = R, so the current is maximum and the power factor is unity. The parallel RLC circuit behaves the opposite way: maximum impedance and minimum current, which is why it is called a rejector or tank circuit.
   - Quality factor Q = (1/R).sqrt(L/C), and bandwidth BW = fr / Q. A high Q gives a sharp, selective response.
   - Uses: tuning a radio or television receiver to one station, band-pass and band-stop filters, oscillator tank circuits, and power factor correction.

   Role of a transistor in an electrical circuit:
   - Amplification: a small signal current or voltage at the input controls a much larger current at the output, so weak signals from a microphone, sensor or antenna can be raised to a usable level. In the common-emitter configuration IC = beta.IB.
   - Switching: driven between cut-off (fully OFF, acts as an open switch) and saturation (fully ON, acts as a closed switch), a transistor replaces a mechanical relay and switches millions of times per second with no moving parts. This is the basis of every digital circuit.
   - Oscillation: with positive feedback around an amplifier stage, a transistor generates a continuous waveform without any input, which produces clock signals and carrier frequencies.
   - Voltage regulation: it acts as the series pass element in a regulated power supply, adjusting its resistance to hold the output constant.
   - Impedance matching: in the emitter follower (common collector) configuration it converts a high source impedance to a low output impedance, so a weak source can drive a heavy load.
   - Modulation and demodulation in communication circuits.
   - As the building block of ICs: the logic gates, memory cells and microprocessors of a computer are all made of millions to billions of transistors.

   In short, the transistor is the active device that gives a circuit gain and control, while R, L and C are passive elements that only shape and store the signal.

## Operational Amplifiers (Op-Amp) (2)

1. **Assuming Ideal Op Amps, Find The Voltage Gain V_o/V_i of the following circuit.** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*


   Answer: An ideal op-amp is analysed using two rules, and the gain follows directly from them.

   Ideal op-amp assumptions:
   - Infinite open-loop gain, so with negative feedback the two input terminals are at the same voltage. This is the virtual short rule: V+ = V-.
   - Infinite input impedance, so no current enters either input terminal. This is the virtual open rule: I+ = I- = 0.
   - Zero output impedance, infinite bandwidth and infinite CMRR.

   The exact circuit is not reproduced here, so the gain is derived for the two standard connections that the question refers to.

   Inverting amplifier (input applied through R1 to the minus terminal, feedback resistor Rf, plus terminal grounded):
   - Since V+ = 0 (grounded), the virtual short gives V- = 0, which is called a virtual ground.
   - Current through the input resistor: I1 = (Vi - 0)/R1 = Vi/R1
   - No current enters the op-amp input, so the same current flows through Rf: I1 = (0 - Vo)/Rf
   - Equating: Vi/R1 = -Vo/Rf

   Voltage gain: Vo/Vi = -Rf/R1

   The minus sign means the output is 180 degree out of phase with the input.

   Non-inverting amplifier (input applied to the plus terminal, Rf from output to the minus terminal, R1 from the minus terminal to ground):
   - Virtual short gives V- = V+ = Vi
   - The output divides across Rf and R1, so V- = Vo.R1/(R1 + Rf)
   - Equating: Vi = Vo.R1/(R1 + Rf)

   Voltage gain: Vo/Vi = 1 + Rf/R1

   The gain is positive, so the output is in phase with the input, and it can never be less than 1.

   Special cases used as building blocks:
   - Voltage follower (buffer): Rf = 0 and R1 = infinity, so Vo/Vi = 1. Used for impedance matching.
   - Summing amplifier: several inputs through R1, R2, R3 into the virtual ground give Vo = -Rf(V1/R1 + V2/R2 + V3/R3).
   - Difference amplifier with all four resistors equal: Vo = V2 - V1.

   Method to apply to any given circuit:
   1. Mark the two input terminals and set V+ = V- (virtual short).
   2. Write a node equation at the inverting terminal, remembering that no current enters the op-amp.
   3. Solve for Vo in terms of Vi and take the ratio Vo/Vi.
2. **একটি Operational Amplifier এর প্রধান বৈশিষ্ট কী কী? AC Power কিভাবে DC পাওয়ারে রূপান্তরিত হয়?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 809 (ET: IBA)]*


   Answer:

   Main characteristics of an operational amplifier:

   - Very high open-loop voltage gain: typically 10^5 to 10^6 (100 to 120 dB). Ideally infinite. This is what makes accurate negative-feedback design possible, because the closed-loop gain then depends only on the external resistors.
   - Very high input impedance: about 2 M ohm for a 741 and 10^12 ohm for a FET-input type. Ideally infinite, so the op-amp draws almost no current from the source and does not load it.
   - Very low output impedance: about 75 ohm, ideally zero, so the output voltage does not fall when a load is connected.
   - Differential input: it amplifies only the difference between the two inputs, Vo = A(V+ - V-).
   - High common mode rejection ratio (CMRR): about 90 dB. Noise picked up equally by both input wires is rejected, which is essential for instrumentation and long sensor cables.
   - Wide bandwidth and a fixed gain-bandwidth product: for a 741 it is about 1 MHz, so gain x bandwidth is constant. A gain of 100 leaves only 10 kHz of bandwidth.
   - Slew rate: the maximum rate of change of the output, about 0.5 V per microsecond for a 741. It limits the largest undistorted output at high frequency.
   - Low input offset voltage and low input bias current, ideally zero, so the output is zero when both inputs are equal.
   - High power supply rejection ratio, so ripple on the supply does not appear at the output.
   - Two operating rules used in analysis, valid whenever negative feedback is present: the two inputs are at the same voltage (virtual short), and no current flows into either input (virtual open).
   - Applications: inverting and non-inverting amplifier, summing amplifier, difference amplifier, integrator, differentiator, comparator, active filter, and instrumentation amplifier.

   How AC power is converted into DC power:

   The conversion is called rectification and a complete DC power supply has four stages.

   ```mermaid
   flowchart LR
     AC[220 V AC Mains] --> T[Step-down Transformer]
     T --> R[Bridge Rectifier - 4 Diodes]
     R --> F[Capacitor Filter]
     F --> RG[Voltage Regulator]
     RG --> DC[Constant DC Output]
   ```

   - Transformer: steps the 220 V mains down to a low AC voltage such as 12 V and isolates the load from the mains.
   - Rectifier: diodes conduct in one direction only. In a full-wave bridge, two of the four diodes conduct in each half cycle, so both halves of the input appear at the output with the same polarity. The output is pulsating DC. Efficiency is 81.2 percent and the ripple frequency is 100 Hz for a 50 Hz supply.
   - Filter: a large electrolytic capacitor across the load charges at each peak and discharges slowly in between, filling the valleys and smoothing the waveform. Ripple voltage is approximately Vr = I/(f.C), so a larger capacitor gives less ripple.
   - Regulator: a Zener diode or a regulator IC such as 7805 or LM317 holds the output constant against changes in mains voltage and load current.

   In a modern SMPS the order is different and more efficient: the mains is rectified first, then chopped at 50 to 100 kHz, stepped down by a small ferrite transformer, rectified again and filtered. This gives 85 to 95 percent efficiency and a much smaller and lighter unit.

## Sensor Circuits & Automated Control Systems (2)

1. **Design and implement an automated street light control system. The system should ensure that the street lights remain off during the presence of sunlight and automatically turn on in the absence of sunlight (i.e., during nighttime or low ambient light conditions).** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*


   Answer: An automatic street light control system turns the lamp ON when the ambient light falls below a set level and OFF when daylight returns. The light sensor is an LDR (Light Dependent Resistor), whose resistance falls in bright light and rises in darkness.

   Block diagram:

   ```mermaid
   flowchart LR
     LDR[LDR Light Sensor] --> DIV[Voltage Divider]
     DIV --> CMP[Comparator LM393 with Preset Threshold]
     POT[Preset Potentiometer - Sensitivity] --> CMP
     CMP --> DRV[Transistor Driver Stage]
     DRV --> RLY[Relay 5V]
     RLY --> LAMP[Street Light 220 V AC]
     PS[Regulated 5V DC Supply] --> CMP
     PS --> DRV
   ```

   Circuit description:
   - The LDR is connected in series with a fixed resistor R across the 5 V supply, forming a voltage divider. The junction voltage is the sensor output.
     - In daylight the LDR resistance is low (about 1 k ohm), so the junction voltage is low.
     - At night the LDR resistance is high (about 1 M ohm), so the junction voltage is high.
   - This junction feeds the non-inverting input of an LM393 comparator. A potentiometer sets the reference voltage on the inverting input, which fixes the darkness level at which the lamp should switch on.
   - When the sensor voltage rises above the reference, the comparator output goes HIGH.
   - The comparator output drives an NPN transistor (BC547) through a base resistor. The transistor energises a 5 V relay coil, and the relay contact switches the 220 V lamp circuit.
   - A freewheeling diode (1N4007) is placed across the relay coil to absorb the back EMF when the coil is de-energised, protecting the transistor.
   - An optocoupler or the relay itself provides isolation between the low-voltage control side and the 220 V mains side.

   Truth table of the control logic:

   | Condition | LDR resistance | Sensor voltage | Comparator output | Relay | Lamp |
   |---|---|---|---|---|---|
   | Daylight | Low | Below reference | LOW | OFF | OFF |
   | Night / low light | High | Above reference | HIGH | ON | ON |

   Microcontroller version (more flexible):
   - The LDR divider output goes to an analogue input of an Arduino or a similar microcontroller, and the relay is driven from a digital output pin.

   ```c
   const int LDR_PIN   = A0;
   const int RELAY_PIN = 7;
   const int THRESHOLD = 400;   // set during commissioning
   const int HYSTERESIS = 40;   // prevents flicker at dusk

   void setup() {
       pinMode(RELAY_PIN, OUTPUT);
       digitalWrite(RELAY_PIN, LOW);
   }

   void loop() {
       int light = analogRead(LDR_PIN);      // 0 = dark, 1023 = bright
       if (light < THRESHOLD - HYSTERESIS) {
           digitalWrite(RELAY_PIN, HIGH);    // dark -> lamp ON
       } else if (light > THRESHOLD + HYSTERESIS) {
           digitalWrite(RELAY_PIN, LOW);     // bright -> lamp OFF
       }
       delay(1000);                          // sample once per second
   }
   ```

   Design points to mention:
   - Hysteresis is essential. Without it, the lamp flickers on and off at dusk and dawn when the light level hovers around the threshold. In the analogue version hysteresis is added with a feedback resistor from the comparator output back to its non-inverting input, making it a Schmitt trigger.
   - A time delay of a few seconds prevents false switching when a vehicle headlight or a passing cloud changes the light level briefly.
   - The LDR must be shielded from the lamp it controls, otherwise the lamp lights the sensor, the sensor switches the lamp off, and the circuit oscillates.
   - Enhancement: add a PIR motion sensor so the lamp runs at 30 percent brightness when the road is empty and full brightness when a person or vehicle passes, which saves a large amount of energy.
   - Enhancement: an RTC or a GPS time source can act as a backup, so the lamp still follows sunset and sunrise times if the LDR fails.

   Advantages: no manual switching, no wasted energy in daylight, longer lamp life, and consistent operation across the whole city.
2. **Which signal a sensor could to send the signal to microcontroller if the sensor finds any gas leakage point?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 861 (ET: N/A)]*


   Answer: A gas leakage sensor such as the MQ-2, MQ-5 or MQ-6 produces an analogue voltage that rises with the gas concentration, and most modules also provide a digital threshold output. Both can be sent to a microcontroller.

   Analogue signal (AOUT pin):
   - The sensing element is a tin dioxide (SnO2) film whose resistance falls as the concentration of combustible gas rises.
   - The module converts that resistance into a voltage of 0 to 5 V through a load resistor, and this voltage is proportional to the gas concentration in ppm.
   - The microcontroller reads it on an ADC input pin.
   - This is the preferred signal, because it tells the controller how much gas is present, not merely whether gas is present. That allows two levels of response: a warning at a low concentration and a shutdown at a high one.

   Digital signal (DOUT pin):
   - An on-board LM393 comparator compares the sensor voltage with a level set by a preset potentiometer.
   - It outputs logic LOW (0 V) in clean air and logic HIGH (5 V) when the gas crosses the set level, or the opposite depending on the module.
   - The microcontroller reads it on an ordinary digital input, or better on an external interrupt pin so that a leak is detected immediately without polling.

   Recommended answer: an analogue voltage signal on the ADC input, with the digital comparator output connected to an interrupt pin as a fast backup.

   Reading and response in a microcontroller:

   ```c
   const int GAS_AOUT = A0;
   const int BUZZER   = 8;
   const int VALVE    = 9;      // solenoid shut-off valve
   const int WARN_LEVEL  = 300;
   const int ALARM_LEVEL = 600;

   void loop() {
       int gas = analogRead(GAS_AOUT);
       if (gas > ALARM_LEVEL) {
           digitalWrite(BUZZER, HIGH);
           digitalWrite(VALVE, HIGH);     // close the gas line
           sendSMSAlert();
       } else if (gas > WARN_LEVEL) {
           digitalWrite(BUZZER, HIGH);    // warning only
       } else {
           digitalWrite(BUZZER, LOW);
       }
       delay(500);
   }
   ```

   Other signal types used by industrial gas detectors:
   - 4 to 20 mA current loop: the standard for long cable runs in a plant, because current does not drop over distance and a reading of 0 mA immediately indicates a broken wire.
   - Digital serial output over UART, I2C or Modbus RS-485 for calibrated smart sensors.
   - Contact closure to a SCADA input for a simple trip signal.

   Practical points:
   - MQ-series sensors need a warm-up (preheat) time of 20 seconds to a few minutes before the reading is valid, and 24 to 48 hours of burn-in for a new sensor.
   - The output drifts with temperature and humidity, so periodic calibration in clean air is required.
   - The sensor must be mounted according to the gas: LPG is heavier than air, so the detector goes near the floor; methane or natural gas is lighter, so the detector goes near the ceiling.
   - The alarm circuit must be intrinsically safe, because a spark from a relay in a gas-filled room is itself an ignition source.

## Circuit Theorems (Thevenin, Norton, Superposition) (2)

1. **Find current across 2 \Omega resistor using Thevenin Theorem:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 417 (ET: BUET)]*


   Answer: Thevenin's theorem states that any two terminal linear network or circuit can be replaced by an equivalent circuit made of one voltage source in series with one resistor.

   The equivalent circuit has two parts:
   - Thevenin voltage, Vth: the voltage source in the equivalent circuit.
   - Thevenin resistance, Rth: the series resistor.

   The specific circuit is not reproduced here, so the complete standard procedure is given and then applied to a worked example.

   Procedure:

   Step 1 - Remove the load resistor (the 2 ohm resistor) from the circuit and leave its two terminals open, marked A and B.

   Step 2 - Find Vth, the open-circuit voltage across A and B. Use any method: series-parallel reduction, voltage divider, mesh analysis or nodal analysis. No current flows through a branch that ends at an open terminal, so any resistor in that branch has no voltage drop across it.

   Step 3 - Find Rth, the resistance looking back into the network from A and B with all independent sources deactivated:
   - Replace every independent voltage source by a short circuit.
   - Replace every independent current source by an open circuit.
   - Dependent sources are kept. When a circuit has both dependent and independent sources, we cannot just deactivate them. Instead we short the open terminals, find the short circuit current Isc, and then use Rth = Vth / Isc. Another way is to apply a 1 V test source at A-B and compute Rth = Vtest / Itest.
   - Then reduce the remaining resistor network by series and parallel combination.

   Step 4 - Draw the Thevenin equivalent: Vth in series with Rth, and reconnect the 2 ohm load.

   Step 5 - Compute the load current:
   IL = Vth / (Rth + RL) = Vth / (Rth + 2)

   Worked example with typical values:
   - Suppose a 12 V source is in series with 4 ohm, that node feeds a 6 ohm resistor to ground, and the 2 ohm load is taken from that node.
   - Step 2: with the 2 ohm removed, the open-circuit voltage is the divider output
     Vth = 12 x 6 / (4 + 6) = 12 x 0.6 = 7.2 V
   - Step 3: short the 12 V source. Looking back from A-B, the 4 ohm and 6 ohm are in parallel
     Rth = (4 x 6) / (4 + 6) = 24 / 10 = 2.4 ohm
   - Step 5: reconnect the 2 ohm load
     IL = 7.2 / (2.4 + 2) = 7.2 / 4.4 = 1.636 A
   - Voltage across the 2 ohm resistor = 1.636 x 2 = 3.27 V

   Equivalent circuit:

   ```
       Rth = 2.4 ohm
    +---/\/\/\---+------o A
    |              |
   (Vth = 7.2 V)  [ 2 ohm load ]
    |              |
    +--------------+------o B
   ```

   Why the theorem is useful: once Vth and Rth are known, the load can be changed to any value and the current is found from one division, without solving the whole network again. It also gives the maximum power transfer condition directly: maximum power is delivered when RL = Rth.
2. **Find the Value of I_{ab} using Norton's Theorem.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*


   Answer: Norton's theorem states that any linear two-terminal network can be replaced, as seen from those two terminals, by a single current source IN in parallel with a single resistance RN.

   The specific circuit is not reproduced here, so the complete standard procedure is given and then applied to a worked example.

   Procedure:

   Step 1 - Remove the branch whose current is required, that is the branch a-b, leaving terminals a and b open.

   Step 2 - Find IN, the Norton current. Place a short circuit directly across a and b, and find the current that flows through that short. Mesh or nodal analysis is normally used, because the short changes the topology of the network.

   Step 3 - Find RN, the Norton resistance. This is exactly the same as Rth:
   - Replace every independent voltage source by a short circuit.
   - Replace every independent current source by an open circuit.
   - Reduce the remaining resistor network as seen from a-b.
   - So RN = Rth.

   Step 4 - Draw the Norton equivalent: IN in parallel with RN, and reconnect the load between a and b.

   Step 5 - Find the load current by the current divider rule:
   Iab = IN x RN / (RN + RL)

   Worked example with typical values:
   - Suppose a 12 V source is in series with 4 ohm, that node feeds a 6 ohm resistor to ground, and a 2 ohm load is connected between a and b at that node.
   - Step 2: short a-b. The 6 ohm resistor is then shorted out, so the entire source current flows through the short
     IN = 12 / 4 = 3 A
   - Step 3: short the 12 V source. The 4 ohm and 6 ohm appear in parallel
     RN = (4 x 6) / (4 + 6) = 2.4 ohm
   - Step 5: reconnect the 2 ohm load and apply the current divider
     Iab = 3 x 2.4 / (2.4 + 2) = 7.2 / 4.4 = 1.636 A

   Equivalent circuit:

   ```
        +---------+---------+------o a
        |         |         |
      ( ^ ) 3 A  [2.4 ohm] [2 ohm load]
        |         |         |
        +---------+---------+------o b
   ```

   Relation between the two theorems (source transformation):
   - Vth = IN x RN
   - IN = Vth / Rth
   - Rth = RN
   - Check with the numbers above: Vth = 3 x 2.4 = 7.2 V, which matches the Thevenin result exactly, and both give Iab = 1.636 A.

   Norton's form is preferred when the network is driven mainly by current sources or when several branches are in parallel, because a parallel combination is then handled directly.
