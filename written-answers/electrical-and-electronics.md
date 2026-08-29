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
