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


   Answer: A PN junction diode is formed by joining a p-type semiconductor and an n-type semiconductor. It lets current pass in one direction only.

   Working principle:
   - The p-side has holes as its majority carriers. The n-side has electrons.
   - As soon as the two are joined, electrons near the junction cross into the p-side and holes cross into the n-side, and they recombine.
   - This leaves a thin region near the junction with no free carriers, only fixed charged ions. It is called the depletion region.
   - The fixed ions set up an internal electric field that opposes any further crossing. The voltage across this region is the barrier potential: about 0.7 V for silicon and about 0.3 V for germanium.

   Symbol:

   ```
        Anode (P)          Cathode (N)
           ----|>|----
                bar
   ```

   The triangle points in the direction of conventional current flow. The bar is the cathode, and on a real diode it is marked with a painted ring.

   Forward bias against reverse bias:

   | Point | Forward bias | Reverse bias |
   |---|---|---|
   | Connection | Positive terminal to P, negative to N | Positive terminal to N, negative to P |
   | Effect on the depletion region | It becomes narrower | It becomes wider |
   | Barrier potential | Reduced, so carriers can cross | Increased, so carriers cannot cross |
   | Current | Large, in milliamperes. It flows freely once the applied voltage exceeds about 0.7 V | Almost zero. Only a tiny leakage current in microamperes, from the minority carriers |
   | Resistance offered | Very low, a few ohms | Very high, in megohms |
   | Behaviour | Acts like a closed switch | Acts like an open switch |

   Breakdown: if the reverse voltage is raised too far, the diode reaches its breakdown voltage and a large reverse current suddenly flows. An ordinary diode is destroyed by this. A Zener diode is built to work there safely, and that is how it regulates voltage.

2. **Determine the current passing through a 10\text{ k}\Omega resistor. Assume a forward voltage drop of 0.75\text{ V} across the diode.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*


   Answer:

   Given: a diode in series with a 10 kΩ resistor. The forward voltage drop across the diode is 0.75 V.

   Method: in a series circuit the same current flows through every element. The diode simply drops a fixed 0.75 V, so the rest of the source voltage appears across the resistor.

   Formula:

   I = (V_source − V_diode) / R

   Taking a 5 V source, which is the standard value for this problem:

   I = (5 − 0.75) / 10,000
   = 4.25 / 10,000
   = 0.000425 A

   Final answer: I = 0.425 mA

   If the source were 10 V instead, the same method gives I = (10 − 0.75)/10,000 = 0.925 mA.

   Note: the source voltage was not printed in the collected question, so 5 V is assumed. The method does not change; only the number does. The key idea to show is that a forward biased diode is treated as a constant 0.75 V drop, not as a resistance. <!-- verify -->

3. **What is Diode and Inductor?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*


   Answer:

   Diode:
   - A diode is a two terminal semiconductor device, made from a p-n junction, that allows current to flow in one direction only.
   - Its two terminals are the anode, on the p-side, and the cathode, on the n-side.
   - In forward bias, that is anode positive, it conducts once the voltage passes about 0.7 V for silicon. In reverse bias it blocks, passing only a tiny leakage current.
   - Main use: rectification, that is turning AC into DC.
   - Types: rectifier diode, Zener diode for voltage regulation, LED, photodiode, and Schottky diode for fast switching.

   Inductor:
   - An inductor is a passive two terminal component, usually a coil of wire, that stores energy in a magnetic field when current flows through it.
   - Its property is inductance, measured in henry (H).
   - Its defining equation is V = L (di/dt). So the voltage across it depends on how fast the current is changing, not on the current itself.
   - It opposes any change in current. So it passes DC easily, because DC does not change, but it opposes AC. Its reactance is X_L = 2πfL, which rises with frequency.
   - Energy stored: E = ½LI².
   - Uses: filters, tuned circuits, transformers, chokes and relays.

   The essential difference: a diode is an active, non-linear device that controls the direction of current. An inductor is a passive, linear device that stores energy and opposes change in current.

4. **How does LED differ from Laser Diod? What are the function of Diode?** *[BTRC Assistant Director (Technical) 2021 compact it 808 (ET: IBA)]*


   Answer:

   How an LED differs from a laser diode:

   | Point | LED, Light Emitting Diode | Laser Diode |
   |---|---|---|
   | How light is produced | Spontaneous emission. The electrons fall back and emit photons at random | Stimulated emission. One photon triggers others, so the photons are all identical |
   | Coherence | Incoherent. The photons are out of step with each other | Coherent. All the photons are in step, in phase |
   | Spectral width | Wide, about 25 to 100 nm, so the colour is not pure | Very narrow, about 1 to 5 nm, so it is nearly a single wavelength |
   | Beam | Spreads out widely, about 60 degrees | A very narrow, tightly focused beam, about 5 to 10 degrees |
   | Optical cavity | None | It has a resonant cavity, with mirrors at the two ends |
   | Threshold current | None. It emits light as soon as any current flows | It has a threshold. Below that current it behaves like an LED, and only above it does it lase |
   | Output power | Low, in milliwatts | High, up to watts |
   | Modulation speed | Slower, up to a few hundred MHz | Much faster, in GHz |
   | Cost and lifetime | Cheap, long life, and not sensitive to temperature | Expensive, shorter life, and it needs temperature control |
   | Use in fibre optics | Multimode fibre, short distance | Single mode fibre, long distance |
   | Common uses | Indicators, displays, lighting, TV remotes | Optical fibre communication, CD and DVD drives, barcode scanners, surgery |

   Functions of a diode:
   - Rectification: converting AC to DC. This is the most common use, in half wave, full wave and bridge rectifiers.
   - Voltage regulation: a Zener diode holds a constant voltage across a load, working in its reverse breakdown region.
   - Clipping: cutting off part of a waveform, to protect a circuit from an over-voltage.
   - Clamping: shifting a waveform up or down to a required DC level.
   - Switching: turning a circuit on and off very fast in digital and logic circuits.
   - Light emission: an LED converts current into light.
   - Light detection: a photodiode converts light into current, used in solar cells and optical receivers.
   - Protection: a freewheeling diode across a relay coil safely absorbs the reverse voltage spike when the coil is switched off.
   - Frequency mixing and demodulation in radio receivers.

## Digital-to-Analog & Analog-to-Digital Converters (DAC/ADC) (4)

1. **You are required to convert a 12-bit digital number to an analogue voltage over the voltage range of 0 to 3.3V with a Digital-to-Analogue Converter (DAC). What is the resolution of the analogue output?** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 419 (ET: BIBM)]*


   Answer:

   Given: a 12-bit DAC, output range 0 to 3.3 V.

   Resolution means the smallest change in output voltage that the DAC can produce. It is one step of the output.

   Step 1: find the number of levels

   Number of levels = 2ⁿ = 2¹² = 4096

   So the output can take 4096 different values, from 0 up to full scale.

   Step 2: find the number of steps

   Number of steps = 2ⁿ − 1 = 4095

   There are 4096 levels, so there are 4095 gaps between them.

   Step 3: find the resolution

   Resolution = Full scale voltage / (2ⁿ − 1)
   = 3.3 / 4095
   = 0.000806 V

   Final answer: resolution = 0.806 mV, that is about 0.81 mV per step.

   Notes:
   - Some textbooks divide by 2ⁿ instead of 2ⁿ − 1, giving 3.3/4096 = 0.0008057 V. The two differ by only 0.02 percent, so either is acceptable, provided we state which definition we used.
   - As a percentage: 1/4095 × 100 = 0.0244 percent of full scale.
   - Meaning of the answer: the DAC output can only move in jumps of about 0.81 mV. It cannot produce any voltage between two neighbouring steps.

2. **An 8 bit (Analog to Digital Converter) = 2.56v. Let the minimum analog voltage = 0v. Calculate binary data output if analog input=1.7** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)]*


   Answer:

   Given: an 8-bit ADC, reference voltage V_ref = 2.56 V, minimum analog voltage = 0 V, analog input V_in = 1.7 V.

   Step 1: find the number of levels

   Levels = 2⁸ = 256

   Step 2: find the step size, that is the resolution

   Step size = V_ref / 2ⁿ
   = 2.56 / 256
   = 0.01 V, that is 10 mV per step

   This is a convenient value, and it is why 2.56 V was chosen as the reference.

   Step 3: find the digital output

   Digital value D = V_in / step size
   = 1.7 / 0.01
   = 170

   Step 4: convert 170 to 8-bit binary

   170 ÷ 2 = 85 remainder 0
   85 ÷ 2 = 42 remainder 1
   42 ÷ 2 = 21 remainder 0
   21 ÷ 2 = 10 remainder 1
   10 ÷ 2 = 5 remainder 0
   5 ÷ 2 = 2 remainder 1
   2 ÷ 2 = 1 remainder 0
   1 ÷ 2 = 0 remainder 1

   Reading the remainders from the bottom upwards: 10101010

   Final answer: the binary data output is 10101010, that is decimal 170, or AA in hexadecimal.

   Verification: 170 × 0.01 = 1.70 V, which is exactly the input. So the quantisation error here is zero, because 1.7 V falls precisely on a step boundary.

3. **Draw an ADC converter circuit which convert an analog signal to digital signal.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 714 (ET: BUET)]*


   Answer: An ADC converts a continuous analog signal into a discrete digital number.

   The four steps of analog to digital conversion:

   ```
   Analog in --> [Sampling] --> [Quantisation] --> [Encoding] --> Digital out
                  take values     round to the      write each
                  at fixed        nearest level     level as bits
                  time intervals
   ```

   - Sampling: we measure the analog signal at fixed intervals of time. A sample and hold circuit grabs the value and holds it steady while the converter works on it.
     - Nyquist criterion: the sampling rate must be at least twice the highest frequency in the signal, f_s ≥ 2f_max. If we sample slower, different frequencies become indistinguishable, which is called aliasing, and the original signal can never be recovered.
     - Example: human speech goes up to about 4 kHz, so telephone systems sample at 8 kHz.
   - Quantisation: each sampled value is rounded to the nearest of the available levels. An n-bit converter has 2ⁿ levels.
     - The rounding error is called quantisation error, and its maximum is half a step.
     - More bits means more levels, smaller steps and less error.
   - Encoding: each level is written as an n-bit binary number, which is the digital output.
   - Anti-aliasing filter: before sampling, a low pass filter removes any frequency above half the sampling rate, so aliasing cannot occur.

   Circuit: a Successive Approximation Register (SAR) ADC, which is the type most commonly used.

   ```
                    +-------------------+
   Analog in ------>| Sample & Hold     |
                    +---------+---------+
                              | V_in (held steady)
                              v
                         +----+----+
                         | Compar- |<-------- V_DAC
                         |  ator   |
                         +----+----+
                              | 1 if V_in > V_DAC, else 0
                              v
                    +-------------------+
   Clock ---------->| Successive        |------> Digital output
                    | Approximation Reg |        (n bits)
                    +---------+---------+
                              |
                              v
                    +-------------------+
                    |       DAC         |
                    +-------------------+
                              |
                              +----------> back to comparator as V_DAC
   ```

   How the SAR ADC works, for 8 bits:
   - Set the most significant bit to 1 and all the rest to 0, giving 10000000. The DAC turns this into half of the full scale voltage.
   - The comparator checks whether V_in is greater than that. If yes, keep the bit as 1. If no, clear it to 0.
   - Move to the next bit and repeat. Each step halves the remaining range, exactly like a binary search.
   - After n comparisons, one per bit, the register holds the final digital value.
   - So an n-bit SAR ADC needs exactly n clock cycles, whatever the input value is.

   Other types of ADC:
   - Flash ADC: it uses 2ⁿ − 1 comparators all working at once, so it converts in a single clock cycle. It is the fastest, but also the most expensive and power hungry. Used for video and radar.
   - Dual slope ADC: it charges and discharges a capacitor and measures the time. Very slow but very accurate, and it rejects mains hum well. Used in digital multimeters.
   - Sigma-delta ADC: it samples far above the Nyquist rate and filters digitally. It gives very high resolution at low speed. Used in audio.

4. **(ক) A/D Converter দ্বারা কিভাবে একটি Analog signal Digital signal এ রূপান্তরিত করা হয়। ডায়াগ্রাম সহ লিখুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 776 (ET: N/A)]*


   Answer: An A/D converter changes a continuous analog signal, such as sound or temperature, into a digital number that a computer can store and process.

   The four steps of analog to digital conversion:

   ```
   Analog in --> [Sampling] --> [Quantisation] --> [Encoding] --> Digital out
                  take values     round to the      write each
                  at fixed        nearest level     level as bits
                  time intervals
   ```

   - Sampling: we measure the analog signal at fixed intervals of time. A sample and hold circuit grabs the value and holds it steady while the converter works on it.
     - Nyquist criterion: the sampling rate must be at least twice the highest frequency in the signal, f_s ≥ 2f_max. If we sample slower, different frequencies become indistinguishable, which is called aliasing, and the original signal can never be recovered.
     - Example: human speech goes up to about 4 kHz, so telephone systems sample at 8 kHz.
   - Quantisation: each sampled value is rounded to the nearest of the available levels. An n-bit converter has 2ⁿ levels.
     - The rounding error is called quantisation error, and its maximum is half a step.
     - More bits means more levels, smaller steps and less error.
   - Encoding: each level is written as an n-bit binary number, which is the digital output.
   - Anti-aliasing filter: before sampling, a low pass filter removes any frequency above half the sampling rate, so aliasing cannot occur.

   Worked example, an 8-bit ADC with V_ref = 5 V:
   - Step size = 5 / 256 = 0.0195 V, that is about 19.5 mV.
   - If the input is 2.5 V, then D = 2.5 / 0.0195 = 128, which is 10000000 in binary.
   - If the input is 0 V, the output is 00000000. If the input is 5 V, the output is 11111111.

   Diagram of the complete conversion:

   ```
      Analog signal                Sampled                Quantised           Digital
      (continuous)                 (discrete in time)     (discrete in value)  output

        /\      /\                  |  |  |  |             _ _ _ _            0110
       /  \    /  \        --->      |  |  |  |     --->   | | | | |    --->  1010
      /    \  /    \                 |  |  |  |            |_|_|_|_|          1101
     /      \/      \                |  |  |  |                              0011
   ```

   Why we need A/D conversion: the real world is analog, that is sound, light, temperature and pressure all vary continuously. But a computer can only work with numbers. So every sensor, microphone and camera needs an ADC at its input. The reverse device, a DAC, is needed at the output, for example to drive a loudspeaker.

## AC Circuits & Power Analysis (2)

1. **A two-element series circuit has an average power of 940\text{W} and a power factor of 0.707 (leading). Determine the circuit elements if the applied voltage is V = 99\cos(600t + 30^\circ)\text{V}.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*


   Answer:

   Given: average power P = 940 W, power factor pf = 0.707 leading, applied voltage V = 99cos(600t + 30°) V.

   A leading power factor means the current leads the voltage, so the reactive element is a capacitor. The circuit is therefore a series R-C circuit.

   Step 1: find the RMS voltage and the angular frequency

   V_rms = V_m / √2 = 99 / 1.414 = 70 V
   ω = 600 rad/s

   Step 2: find the phase angle

   pf = cos θ = 0.707
   θ = cos⁻¹(0.707) = 45°, and it is leading

   Step 3: find the apparent power and the current

   P = S × pf, so S = P / pf = 940 / 0.707 = 1329.6 VA

   S = V_rms × I_rms, so

   I_rms = S / V_rms = 1329.6 / 70 = 18.99 A

   Step 4: find the impedance

   |Z| = V_rms / I_rms = 70 / 18.99 = 3.686 Ω

   Step 5: split the impedance into R and X_C

   R = |Z| cos θ = 3.686 × 0.707 = 2.606 Ω
   X_C = |Z| sin θ = 3.686 × 0.707 = 2.607 Ω

   Step 6: find the capacitance from the reactance

   X_C = 1 / (ωC), so

   C = 1 / (ω X_C)
   = 1 / (600 × 2.607)
   = 1 / 1564.2
   = 6.394 × 10⁻⁴ F

   Final answer: the circuit is a resistor R = 2.61 Ω in series with a capacitor C = 639.4 µF.

   Verification: P = I²R = (18.99)² × 2.606 = 360.6 × 2.606 = 940 W. This matches the given power, so the answer is correct.

2. **RLC সার্কিট কী? বৈদ্যুতিক সার্কিটে ট্রানজিস্টরের ভূমিকা কী?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 809-810 (ET: IBA)]*


   Answer:

   What an RLC circuit is:
   - An RLC circuit is an electrical circuit containing a resistor (R), an inductor (L) and a capacitor (C), connected either in series or in parallel.
   - Each element behaves differently towards AC. The resistor opposes current with plain resistance R. The inductor opposes a change in current, with reactance X_L = 2πfL. The capacitor opposes a change in voltage, with reactance X_C = 1/(2πfC).
   - The total opposition is called impedance. For a series RLC circuit:

     Z = √( R² + (X_L − X_C)² )

   - Phase angle: θ = tan⁻¹((X_L − X_C)/R). If X_L > X_C the circuit is inductive and the current lags. If X_C > X_L it is capacitive and the current leads.

   Resonance, which is the most important property:
   - At one particular frequency X_L equals X_C, and the two cancel each other out. That frequency is called the resonant frequency.

     f_r = 1 / (2π√(LC))

   - At resonance in a series RLC circuit, Z = R, which is its minimum value. So the current is maximum and the power factor is 1.
   - In a parallel RLC circuit the opposite happens: the impedance is maximum and the current is minimum at resonance.
   - Uses: tuning a radio or television to one station, filters, and oscillators. Turning the tuning knob changes C, which changes f_r, so a different station is selected.

   Role of a transistor in an electrical circuit:
   - Amplification: a small input signal controls a much larger output. A tiny base current controls a large collector current, so a weak microphone signal can drive a loudspeaker. This is the main analog use.
   - Switching: the transistor works only in cut off, which is fully OFF, and saturation, which is fully ON. It becomes an electronic switch with no moving parts, which can operate millions of times a second. This is the main digital use, and it is the basis of every logic gate.
   - Building logic gates and memory: all AND, OR and NOT gates are built from transistors. A modern processor contains billions of them.
   - Voltage regulation: a series pass transistor in a regulator holds the output voltage steady.
   - Oscillation: with feedback, a transistor circuit generates a continuous waveform, used for clocks and radio carriers.
   - Signal modulation and demodulation in communication circuits.
   - Impedance matching, using the emitter follower or common collector configuration.

   In one line: a transistor is the device that lets a small electrical signal control a large one, and that single property gives us both amplification and switching.

## Operational Amplifiers (Op-Amp) (2)

1. **Assuming Ideal Op Amps, Find The Voltage Gain V_o/V_i of the following circuit.** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*


   Answer:

   The circuit diagram was not reproduced in the collected question, so the standard op-amp gain results are derived and given. The two ideal op-amp rules are used throughout.

   The two ideal op-amp assumptions:
   - Infinite open loop gain, so the two input terminals sit at the same voltage. This is the virtual short.
   - Infinite input resistance, so no current enters either input terminal.

   Inverting amplifier:

   ```
        Rf
     +--///--+
     |       |
   Vi--///---+---|-\
        R1       |  >--- Vo
              +--|+/
              |
             GND
   ```

   - The + input is grounded, so by the virtual short the − input is also at 0 V. That node is called a virtual ground.
   - Current through R1: I = (Vi − 0)/R1 = Vi/R1
   - No current enters the op-amp, so all of it flows on through Rf: I = (0 − Vo)/Rf
   - Setting the two equal: Vi/R1 = −Vo/Rf

   Voltage gain: Vo/Vi = − Rf/R1

   The minus sign means the output is inverted, that is 180 degrees out of phase with the input.

   Non-inverting amplifier:

   - Here the input goes to the + terminal, and the feedback network R1 and Rf sits between the output, the − terminal and ground.
   - By the virtual short, the − terminal is also at Vi.
   - That node is the output of a voltage divider: Vi = Vo × R1/(R1 + Rf)

   Voltage gain: Vo/Vi = 1 + Rf/R1

   This gain is always greater than or equal to 1, and the output is in phase with the input.

   Voltage follower: a non-inverting amplifier with Rf = 0 and R1 = infinity gives Vo/Vi = 1. It is used as a buffer, because it has very high input impedance and very low output impedance. <!-- verify -->

2. **একটি Operational Amplifier এর প্রধান বৈশিষ্ট কী কী? AC Power কিভাবে DC পাওয়ারে রূপান্তরিত হয়?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 809 (ET: IBA)]*


   Answer:

   Main characteristics of an operational amplifier:
   - It is a high gain, direct coupled, differential amplifier. It amplifies the difference between its two inputs: Vo = A(V⁺ − V⁻).
   - It has two inputs, the inverting input marked − and the non-inverting input marked +, and one output.

   Characteristics of an ideal op-amp, against a real one:

   | Characteristic | Ideal value | Typical real value, 741 |
   |---|---|---|
   | Open loop voltage gain | Infinite | About 200,000 |
   | Input impedance | Infinite, so no input current | About 2 MΩ |
   | Output impedance | Zero | About 75 Ω |
   | Bandwidth | Infinite | About 1 MHz gain-bandwidth product |
   | CMRR, common mode rejection ratio | Infinite | About 90 dB |
   | Slew rate | Infinite | About 0.5 V/µs |
   | Offset voltage | Zero | A few millivolts |

   Two rules that follow, used to solve every op-amp circuit:
   - Virtual short: with negative feedback, the two input terminals stay at the same voltage.
   - No input current: no current flows into either input terminal.

   Uses: inverting and non-inverting amplifiers, summing amplifier, difference amplifier, integrator, differentiator, comparator, filters and oscillators.

   How AC power is converted into DC power:

   The process has four stages.

   ```
   AC mains --> [Transformer] --> [Rectifier] --> [Filter] --> [Regulator] --> steady DC
                  step down        AC to pulsating   smooth      constant
                                        DC                        output
   ```

   - Step 1, Transformer: it steps the 220 V AC mains down to a low voltage, such as 12 V AC. It also isolates the circuit from the mains, which is a safety requirement.
   - Step 2, Rectifier: diodes convert the AC into pulsating DC, that is DC that flows in one direction but still rises and falls.
     - Half wave rectifier: one diode. It passes only the positive half cycles, so half the power is wasted.
     - Full wave centre tap: two diodes and a centre tapped transformer. It uses both half cycles.
     - Full wave bridge: four diodes in a bridge, and no centre tap needed. This is the arrangement used in practice.
   - Step 3, Filter: a large capacitor across the output charges at the peaks and discharges between them, which smooths the pulses into an almost flat DC. What is left of the variation is called ripple. A bigger capacitor gives less ripple.
   - Step 4, Regulator: an IC such as the 7805, or a Zener diode, holds the output at a fixed voltage even when the mains voltage or the load current changes.

   The complete unit is called a DC power supply, and it is what sits inside every phone charger and computer power supply.

## Sensor Circuits & Automated Control Systems (2)

1. **Design and implement an automated street light control system. The system should ensure that the street lights remain off during the presence of sunlight and automatically turn on in the absence of sunlight (i.e., during nighttime or low ambient light conditions).** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1365 (ET: BUET)]*


   Answer: The system must switch the street light OFF in daylight and ON in darkness. We do this with a light sensor driving a relay.

   Components:
   - LDR, Light Dependent Resistor: its resistance falls when light falls on it. In bright daylight it is about 1 kΩ; in darkness it rises to several hundred kΩ. This is the sensor.
   - A fixed resistor, about 10 kΩ, to form a voltage divider with the LDR.
   - A comparator, such as an LM358 or LM393 op-amp, or a transistor.
   - A relay, to switch the 220 V lamp, since the control circuit is only 5 V.
   - A transistor, such as BC547, to drive the relay coil.
   - A freewheeling diode, 1N4007, across the relay coil.
   - A preset, that is a variable resistor, to set the darkness level at which the light comes on.

   Circuit:

   ```
      +5V
       |
      LDR
       |
       +----------------+
       |                |          +5V
      R1 10k        [ - IN ]        |
       |            Comparator --- Relay coil
      GND           [ + IN ]        |    (with 1N4007 across it)
                        |          Collector
                     preset       BC547
                        |          Emitter
                       GND          |
                                   GND
   ```

   Working:
   - The LDR and R1 form a voltage divider. The voltage at their junction is the sensor output.
   - Daytime: light falls on the LDR, so its resistance is low. The junction voltage is high. The comparator output goes LOW, the transistor is off, the relay stays open, and the lamp is OFF.
   - Night: no light, so the LDR resistance is high. The junction voltage falls below the reference set on the preset. The comparator output goes HIGH, the transistor turns on, the relay closes, and the lamp is ON.
   - The preset sets the exact light level at which the switching happens, so we can decide how dark it must be before the light comes on.

   Why each part is needed:
   - The comparator is used rather than feeding the LDR straight to the transistor, because it gives a clean, sharp switch. Without it the lamp would flicker at dusk, when the light level hovers near the threshold.
   - Hysteresis, added with a feedback resistor on the comparator, makes the ON threshold and the OFF threshold slightly different. This stops the lamp from chattering when a cloud passes.
   - The relay is essential, because the 5 V control circuit cannot switch 220 V directly. The relay also gives electrical isolation between the two.
   - The freewheeling diode is essential. When the relay coil is switched off, its collapsing magnetic field produces a large reverse voltage spike that would destroy the transistor. The diode gives that current a safe path.

   Microcontroller version, which is what is used in practice:
   - Feed the LDR divider into an ADC pin of an Arduino or similar board.
   - Read the value, compare it with a threshold in software, and drive the relay pin accordingly.
   - Advantages: the threshold can be changed in software, we can add a real time clock so the light never comes on in daytime even under a dark cloud, we can dim the lamp with PWM after midnight to save power, and we can log faults.

2. **Which signal a sensor could to send the signal to microcontroller if the sensor finds any gas leakage point?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 861 (ET: N/A)]*


   Answer: A gas sensor sends an analog voltage signal to the microcontroller. That signal must then be converted to digital by the ADC inside the microcontroller.

   How a gas sensor works:
   - The common type is the MQ series, such as MQ-2 for LPG and smoke, MQ-4 for methane, or MQ-7 for carbon monoxide.
   - Inside is a tin dioxide (SnO₂) sensing layer with a heater. In clean air its resistance is high.
   - When a combustible gas touches the hot surface, it reacts and the resistance falls.
   - The sensor is wired with a load resistor as a voltage divider, so the falling resistance produces a rising output voltage.

   The signals available from such a sensor:
   - Analog output (AO): a continuous voltage, typically 0 to 5 V, proportional to the gas concentration. This is the main signal. We feed it to an ADC pin, and the microcontroller can then tell how much gas is present, not merely that some is present.
   - Digital output (DO): many modules also carry an on-board comparator and a preset. It gives a simple HIGH or LOW when the concentration crosses the set threshold. We feed this to an ordinary digital input pin, or better to an interrupt pin.

   Which to use, and why:
   - For a leak detection and alarm system, the analog signal is the correct choice, because the microcontroller can then distinguish a small trace from a dangerous concentration, raise different alarm levels, and log the trend over time.
   - The digital output is useful in addition, wired to an external interrupt pin, so that a sudden dangerous level wakes the microcontroller immediately instead of waiting for the next scheduled ADC reading.

   Complete detection chain:

   ```
   Gas --> [MQ sensor] --AO: analog voltage--> [ADC in MCU] --> compare with threshold
                        --DO: digital HIGH/LOW--> [interrupt pin]
                                                        |
                                                        v
                                        Buzzer + LED + SMS alert + shut off valve
   ```

   Practical points worth stating:
   - The sensor needs a warm-up time, typically 20 seconds to a few minutes, before its reading is trustworthy.
   - It must be calibrated in clean air first, and the reading drifts with temperature and humidity, so a compensation table is used.
   - The sensor is not selective. It responds to several gases at once, so a specific gas cannot be identified from one sensor alone.

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
