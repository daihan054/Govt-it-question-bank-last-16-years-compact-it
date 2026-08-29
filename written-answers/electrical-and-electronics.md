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


   Answer: BJT stands for Bipolar Junction Transistor. It is called bipolar because both carriers, electrons and holes, take part in conduction, unlike a FET where only one type of carrier conducts.
2. **How many terminals does a BJT have?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: A BJT has three terminals: Emitter (E), Base (B) and Collector (C).

   - Emitter: heavily doped, injects the majority carriers into the base.
   - Base: very thin and lightly doped, controls the flow of carriers.
   - Collector: moderately doped and physically the largest, collects the carriers and dissipates the heat.

   The current relation between them is IE = IB + IC.
3. **In an NPN transistor, the current flows from _____** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: In an NPN transistor the conventional current flows from the collector to the emitter, and a small control current flows from the base to the emitter.

   - Electron flow is the opposite: electrons are injected from the emitter into the base and are collected by the collector.
   - Terminal currents: IE = IB + IC, with IC being about 98 to 99 percent of IE.
   - Bias condition for normal (active) operation: the base-emitter junction is forward biased and the base-collector junction is reverse biased.
   - The arrow on the emitter of an NPN symbol points outwards, showing the direction of conventional current out of the emitter.

   Final answer: current flows from collector to emitter (with the base current entering at the base and also leaving through the emitter).
4. **Which BJT configuration gives maximum voltage gain?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: The common-emitter (CE) configuration gives the maximum voltage gain.

   Comparison of the three configurations:

   | Parameter | Common Base (CB) | Common Emitter (CE) | Common Collector (CC) |
   |---|---|---|---|
   | Voltage gain | High | High | Less than 1 (about 0.99) |
   | Current gain | Less than 1 (alpha) | High (beta) | High (1 + beta) |
   | Power gain | Moderate | Highest | Moderate |
   | Input resistance | Very low (about 50 ohm) | Medium (about 1 k ohm) | Very high (about 500 k ohm) |
   | Output resistance | Very high | High | Very low |
   | Phase shift | 0 degree | 180 degree | 0 degree |
   | Main use | High-frequency amplifier | General purpose amplifier | Impedance matching, buffer, emitter follower |

   Note: common base also gives a high voltage gain, but its current gain is less than 1, so its power gain is much lower. The common emitter is the only configuration that gives both a high voltage gain and a high current gain, so it gives the highest power gain and is the standard amplifier stage.
5. **Collector current (Ic) is related to base current (Ib) by _____** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: The collector current is related to the base current by the current gain beta:

   IC = beta x IB

   where beta (also written hFE) is the common-emitter current gain, typically 20 to 500.

   Related relations:
   - Emitter current: IE = IB + IC
   - Common-base current gain: alpha = IC / IE, typically 0.95 to 0.995
   - Link between the two gains: beta = alpha / (1 - alpha) and alpha = beta / (1 + beta)
   - Emitter current in terms of base current: IE = (1 + beta) IB

   Example: if IB = 50 microampere and beta = 100, then IC = 100 x 50 microampere = 5 mA and IE = 5.05 mA.
6. **N-Channel MOS operating in the linear region. Calculate the current passing through the channel of the transistor. Given: \mu_n C_{ox} (W/L) = 1.3\text{ mA/V}^2, V_{GS} = 2.5\text{ V}, V_t = 0.95\text{ V}. Assume reasonable values for missing parameters if necessary.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*


   Answer: In the linear (triode) region of an NMOS transistor the drain current is given by

   ID = mu_n.Cox.(W/L).[(VGS - Vt).VDS - (VDS^2)/2]

   Given:
   - mu_n.Cox.(W/L) = 1.3 mA/V^2
   - VGS = 2.5 V
   - Vt = 0.95 V
   - VDS is not given, so a reasonable value is assumed: VDS = 0.5 V

   Step 1 - check the region of operation:
   - Overdrive voltage VOV = VGS - Vt = 2.5 - 0.95 = 1.55 V
   - VGS = 2.5 V is greater than Vt = 0.95 V, so the channel is formed.
   - VDS = 0.5 V is less than VOV = 1.55 V, so the device is indeed in the linear (triode) region. The assumption is valid.

   Step 2 - substitute the values:
   - ID = 1.3 x 10^-3 x [(1.55 x 0.5) - (0.5^2)/2]
   - ID = 1.3 x 10^-3 x [0.775 - 0.125]
   - ID = 1.3 x 10^-3 x 0.650

   Step 3 - compute:
   - ID = 0.845 x 10^-3 A

   Final answer: ID = 0.845 mA (for the assumed VDS = 0.5 V).

   Note: if VDS were raised to or above VOV = 1.55 V the device would enter saturation and the current would become
   ID = (1/2).mu_n.Cox.(W/L).VOV^2 = 0.5 x 1.3 x 1.55^2 = 1.561 mA, after which it stays almost constant.
7. **Describe cut off, saturation and active region of operation of a transistor with diagram. Explain the working principal of ab n-channel JFET with various values of V_{GS} and V_{DS}.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 445 (ET: BIBM)]*


   Answer:

   Part 1 - Regions of operation of a BJT

   The region is decided by how the two junctions are biased.

   | Region | Base-Emitter junction | Base-Collector junction | Behaviour |
   |---|---|---|---|
   | Cut-off | Reverse biased | Reverse biased | Transistor OFF, IC almost 0, acts as an open switch |
   | Active | Forward biased | Reverse biased | Linear amplification, IC = beta.IB |
   | Saturation | Forward biased | Forward biased | Transistor fully ON, VCE about 0.2 V, acts as a closed switch |

   Cut-off region:
   - VBE is less than the cut-in voltage (about 0.7 V for silicon), so no carriers are injected into the base.
   - IB = 0, IC = ICEO which is only a few nanoamperes, and VCE is approximately equal to VCC.
   - Used as the OFF state of a switch.

   Active region:
   - VBE is about 0.7 V and VCE is greater than VCE(sat).
   - IC = beta.IB, so the collector current is controlled linearly by the base current and the transistor works as an amplifier.
   - The output characteristic curves are almost flat and horizontal here, showing that IC depends on IB and not on VCE.

   Saturation region:
   - Both junctions are forward biased, so the collector can no longer collect all the injected carriers.
   - IC stops following beta.IB and becomes limited by the external circuit: IC(sat) = (VCC - VCE(sat)) / RC, with VCE(sat) about 0.2 V.
   - Used as the ON state of a switch.

   Output characteristic diagram:

   ```
     IC
      |          saturation
      |         |
      |         |______________ IB4  <- active region
      |        /|______________ IB3
      |       / |______________ IB2
      |      /  |______________ IB1
      |     /   |
      |____/____|______________ IB = 0  <- cut-off
      +--------------------------------- VCE
        0.2 V
   ```

   Load line: the operating point Q is the intersection of the load line VCE = VCC - IC.RC with the curve for the chosen IB. For an amplifier Q is placed in the middle of the active region; for a switch it is driven between cut-off and saturation.

   Part 2 - Working principle of an n-channel JFET

   Structure: a bar of n-type silicon forms the channel, with the Drain at one end and the Source at the other. Two heavily doped p-type regions on the sides form the Gate. The gate-channel junction is always kept reverse biased, so the gate draws almost no current and the input resistance is very high (about 10^9 ohm).

   Control mechanism: reverse biasing the gate widens the depletion layer on both sides, which narrows the conducting channel and reduces the current. The JFET is therefore a voltage-controlled, depletion-mode device: it conducts fully at VGS = 0 and is turned off by a negative VGS.

   Effect of VGS (with VDS small and fixed):
   - VGS = 0 V: the depletion layer is thinnest, the channel is widest, and the current is maximum. This value is called IDSS (drain-source current with the gate shorted).
   - VGS made more negative: the depletion layer widens, the channel narrows, and ID falls.
   - VGS = VP (the pinch-off or cut-off voltage, for example -4 V): the depletion layers meet, the channel is completely closed and ID = 0. The device is OFF.

   Effect of VDS (with VGS fixed):
   - Ohmic region (VDS less than VGS - VP): the channel behaves as a resistor whose value is set by VGS, and ID rises almost linearly with VDS. The JFET is used as a voltage-controlled resistor here.
   - Pinch-off point (VDS = VGS - VP): the depletion layer at the drain end just touches, and the channel pinches off at that end.
   - Saturation (active) region (VDS greater than VGS - VP): ID stays almost constant even though VDS rises further, because any extra voltage is dropped across the widened depletion region. This is the amplifying region, and the current follows Shockley's equation
     ID = IDSS.(1 - VGS/VP)^2
   - Breakdown region: at a very large VDS the reverse-biased gate junction breaks down and ID rises sharply. The device must not be operated here.

   Drain characteristic diagram:

   ```
     ID
      |     ohmic |  saturation region
   IDSS|_____ ____|_________________ VGS = 0 V
      |    /      |_________________ VGS = -1 V
      |   /       |_________________ VGS = -2 V
      |  /        |_________________ VGS = -3 V
      | /         |
      |/__________|_________________ VGS = VP = -4 V (cut-off)
      +---------------------------------- VDS
   ```

   Key parameters: transconductance gm = change in ID / change in VGS, drain resistance rd, and amplification factor mu = gm x rd.

   Main advantage over a BJT: very high input impedance, low noise, and no thermal runaway, which is why the JFET is used in the first stage of sensitive amplifiers and measuring instruments.
8. **(a) Draw and explain the operation of NMOS transistor.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*


   Answer: An NMOS transistor (n-channel Metal-Oxide-Semiconductor FET) is a voltage-controlled device in which a positive gate voltage creates a conducting channel of electrons between two n-type regions in a p-type substrate.

   Structure:
   - A lightly doped p-type substrate (body).
   - Two heavily doped n+ regions diffused into it, forming the Source (S) and the Drain (D).
   - A thin layer of silicon dioxide (SiO2) grown over the region between them, and a metal or polysilicon Gate (G) on top of that oxide.
   - The gate is insulated from the channel by the oxide, so the gate current is essentially zero and the input resistance is about 10^14 ohm.
   - The body is normally tied to the source or to the most negative supply.

   ```
            G (Gate)
             |
        =====|=====        <- metal / polysilicon
        ~~~~~~~~~~~        <- SiO2 insulating layer
      +---------------+
   S--| n+ |     | n+ |--D
      +---------------+
      |   p-substrate  |
      +---------------+
             |
             B (Body)
   ```

   Working principle (enhancement type):

   1. VGS = 0:
      - The two n+ regions and the p-substrate form two back-to-back pn junctions, so no current flows from drain to source. The device is OFF.

   2. VGS positive but less than Vt:
      - The positive gate voltage pushes holes away from the surface of the substrate and leaves a depletion region. Still no conducting path, so ID is almost zero.

   3. VGS greater than Vt (threshold voltage, typically 0.4 to 1 V):
      - The field is strong enough to attract minority electrons from the substrate to the surface. A thin n-type inversion layer forms, which connects the source to the drain. This is the channel.
      - The channel is created (enhanced) by the gate voltage, which is why it is called an enhancement-mode device.
      - The overdrive voltage VOV = VGS - Vt controls how thick and how conductive the channel is.

   4. Small VDS applied (linear or triode region, VDS less than VOV):
      - Electrons drift from source to drain, so conventional current flows from drain to source.
      - The channel behaves as a resistance controlled by VGS:
        ID = mu_n.Cox.(W/L).[(VGS - Vt).VDS - (VDS^2)/2]
      - ID rises almost linearly with VDS, so the device works as a voltage-controlled resistor.

   5. VDS increased to VOV (pinch-off):
      - The voltage across the oxide at the drain end falls to Vt, so the channel just vanishes at that end.

   6. VDS greater than VOV (saturation or active region):
      - The pinch-off point moves slightly towards the source and any extra VDS is dropped across the pinched-off part.
      - The current becomes almost independent of VDS:
        ID = (1/2).mu_n.Cox.(W/L).(VGS - Vt)^2
      - This is the amplifying region, used for analog gain.

   Summary of the regions:

   | Condition | Region | Drain current |
   |---|---|---|
   | VGS less than Vt | Cut-off | ID = 0 |
   | VGS greater than Vt and VDS less than VOV | Linear / triode | ID = k[(VOV)VDS - VDS^2/2] |
   | VGS greater than Vt and VDS greater than or equal to VOV | Saturation | ID = (k/2)(VOV)^2 |

   where k = mu_n.Cox.(W/L).

   Applications:
   - As a switch in CMOS logic: cut-off gives logic 1 at the drain and saturation/triode gives logic 0. Combined with a PMOS it forms the CMOS inverter, which draws almost no static power.
   - As an amplifier when biased in saturation.
   - As a memory cell transistor in DRAM and flash.
9. **ইমিটার কারেন্টের মান 1 Amp, কালেক্টর কারেন্ট 0.95 A হলে বেইস (Base) কারেন্টের মান কত? একটি চিত্র দেওয়া ছিল!!** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*


   Answer: In a transistor the emitter current divides into the base current and the collector current.

   Given:
   - Emitter current, IE = 1 A
   - Collector current, IC = 0.95 A

   Step 1 - apply the fundamental current relation of a BJT:
   IE = IB + IC

   Step 2 - rearrange for the base current:
   IB = IE - IC

   Step 3 - substitute the values:
   - IB = 1 - 0.95
   - IB = 0.05 A

   Final answer: Base current IB = 0.05 A = 50 mA.

   Additional parameters from the same data:
   - Common-base current gain: alpha = IC / IE = 0.95 / 1 = 0.95
   - Common-emitter current gain: beta = IC / IB = 0.95 / 0.05 = 19
   - Cross-check: beta = alpha / (1 - alpha) = 0.95 / 0.05 = 19. Both agree.

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
