
Under Construction - ANP - 08/2026
## title: Instrument Tuning Annotations — Aurora Scientific Azizi

# Instrument Tuning Annotations — Aurora Scientific Azizi

> Companion to the [factory manual](attachments/300C_305C_309C_310C.Manual.pdf) (Section 6.0, pp. 12–21).
> These notes are specific to the **310C** unit in the Azizi Lab **(PC board AS300b-2 Rev 3. ASSY # 20010-6500b-2)** and supplement or override the generic factory procedure where noted.

**Caution carried forward from manual:** Lethal voltages are exposed when the electronics box cover is removed. The cover must be removed for all PCB-level adjustments in sections 6.1 and 6.2.

---

## 6.0 General Setup (Manual p. 12)

Equipment required per manual: dual-trace oscilloscope, 3½-digit DVM, function generator, Phillips and flat-tip screwdrivers, BNC cables.

**Lab-specific notes:**

- *[e.g. Which oscilloscope/function generator is used in our setup?]*
- *[Any quirks with our bench wiring or BNC routing?]*



### Initial connections (steps 1–3)

- Scope CH1 → LENGTH OUT
- Scope CH2 → jumper R67 (motor current)
- Function generator → LENGTH IN
- Voltmeter → FORCE OUT

**Lab-specific notes:**
- *Be sure to set the motor arm pointing directly upwards, this is what "centerline" refers to.*
- *[e.g. Note on cable labeling, connector location, etc.]*

---



## 6.1 Length Control Setup — AS30004 PCB (Manual pp. 13–19)

> Skip steps 4–9 and go directly to step 10 if only minor tuning adjustments are needed.


### Full reset (steps 4–9)

Starting pot positions before re-tuning from scratch:

- R25, R28, R31, R59 → CCW 30 turns (or until click)
- R13, R107 → center (15 turns from either stop)
### Step 4 — Reset pots
> [!note] "R107"
> R107 does not excist on this board and has essentially been replaced by the length offset dial on the front of the control box. Make sure the length offset is set to "5.0" and the gain is set to 1x.
- R78 → fully CCW
- Front panel FORCE OFFSET → fully CW; LENGTH OFFSET → center (5 turns)

Null offset (step 7): adjust R13 until voltage at R14 pin (front-panel side) = **0.000 V**.

**Lab-specific notes:**

- *[e.g. Our R13 tends to settle around X turns — note any drift behavior]*



### Dynamic tuning (steps 10–11)

Drive LENGTH IN with a **1 V p-p square wave** at:


| Model          | Frequency |
| -------------- | --------- |
| 300C / 300C-LR | 30 Hz     |
| 305C / 305C-LR | 25 Hz     |
| 309C           | 10 Hz     |
| 310C / 310C-LR | 5 Hz      |


Target: critically damped step response (no overshoot/undershoot, no ringing) at:


| Model              | Step response time |
| ------------------ | ------------------ |
| 300C with 2 cm arm | 1 ms               |
| 300C / 300C-LR     | 1.3 ms             |
| 305C / 305C-LR     | 2 ms               |
| 309C               | 4 ms               |
| 310C / 310C-LR     | 8 ms               |


**Pot roles (from manual):**

- **R31** — error integrator; controls servo gain / speed. Turn CW to speed up response.
- **R28** — error amplifier; electrical restoring spring. Turn CW to reduce overshoot.
- **R25** — position differentiator; low-frequency damping. Use early; loses effectiveness at higher gains.
- **R59** — current integrator; high-frequency damping. Use with R25 once R25 alone is insufficient.

**Standard tuning sequence:** R31 ↑ (gain) → R28 ↑ (kill overshoot) → R59 ↑ (kill 2nd-order bump) → R25 ↑ (kill 3rd-order bump) → R28 ↑ again → R31 ↑ again → repeat until critically damped at target rise time.

**Lab-specific notes:**

- *[e.g. Our unit required more R59 than typical — starting point for next tuning session: R59 ≈ X turns]*
- *[e.g. Any load inertia changes — arm length, added mass — that required re-tuning?]*



### Verify tuned state (step 12)

- No overshoot/undershoot on LENGTH OUT
- No ringing on position or current traces (if ringing, loop gain too high)
- No audible ringing from motor (faint hissing is normal and increases with gain)
- Use the minimum loop gain that meets spec

**Lab-specific notes:**

- *[e.g. Our unit has a slight hiss at our operating gain — confirmed normal by ASI]*



### Input/output amplitude match — R93 (step 13)

Split function generator output to both LENGTH IN and scope CH2. Compare LENGTH OUT (CH1) to LENGTH IN (CH2). Adjust **R93** until amplitudes are identical.

**Lab-specific notes:**

- *[e.g. Our R93 was X turns from CCW when matched — record after each re-tune]*



### Slew rate limiting — R78 (step 14)

Monitor +MOTOR current (connect scope to either side of the on-board fuse). Increase LENGTH IN amplitude toward ±10 V. Adjust **R78 CCW** to remove distortion at +MOTOR signal peaks.

**Lab-specific notes:**

- *[e.g. At what LENGTH IN amplitude did distortion first appear on our unit?]*



### Field size calibration — R13 (step 15)

Drive LENGTH IN with a **6 V p-p square wave** at the frequency from Chart #1 above. Adjust **R13** until lever arm tip moves:


| Model          | Peak-to-peak motion |
| -------------- | ------------------- |
| 300C / 300C-LR | 3 mm                |
| 305C / 305C-LR | 6 mm                |
| 309C           | 7.5 mm              |
| 310C / 310C-LR | 12 mm               |


After R13 adjustment, re-check dynamic tuning (step 11).

**Lab-specific notes:**

- *[e.g. Measurement method used — optical reticule, traveling stage microscope, etc.]*



### Scanner voltage check (step 16)

Measure voltage at **U2, pin 14**. Should be **+5.0 to +11.5 VDC**. Outside this range indicates a scanner problem — contact ASI.

**Lab-specific notes:**

- *[e.g. Our last measured value: X.X V on date YYYY-MM-DD]*

---



## 6.2 Force Control Setup — AS30005 PCB (Manual pp. 19–21)



### Force scale zero (steps 1–2)

- Motor arm horizontal, hanging over table edge
- Voltmeter to FORCE OUT; adjust **R18** (accessible via ZERO hole on front panel) → **0.000 VDC**

**Lab-specific notes:**

- *[e.g. Any drift in our zero between sessions?]*



### Force scale gain — R11 (step 3)

Hang specified weight via rubber band (compliant link — mandatory; rigid link causes oscillation). Adjust **R11** until FORCE OUT matches:


| Model   | Weight | FORCE OUT target |
| ------- | ------ | ---------------- |
| 300C    | 20 g   | 4.000 V          |
| 300C-LR | 50 g   | 5.000 V          |
| 305C    | 200 g  | 4.000 V          |
| 305C-LR | 500 g  | 5.000 V          |
| 309C    | 1000 g | 5.000 V          |
| 310C    | 2000 g | 4.000 V          |
| 310C-LR | 2000 g | 2.000 V          |


**Lab-specific notes:**

- *[e.g. What calibration weights are available in the lab? Where are they stored?]*



### Re-zero with arm pointing down (step 4)

Orient motor arm pointing toward floor. Adjust **R18** → FORCE OUT = **0.000 VDC**.

### Inertia and mechanical spring cancellation (step 5)

Drive LENGTH IN with a **6 V p-p triangle wave** (not square) at:


| Model          | Frequency |
| -------------- | --------- |
| 300C / 300C-LR | 20 Hz     |
| 305C / 305C-LR | 5 Hz      |
| 309C           | 5 Hz      |
| 310C / 310C-LR | 3 Hz      |


- **R9** (inertia canceling) — minimize transients at triangle wave peaks/troughs. ~90% cancellation is achievable.
- **R34** (mechanical spring canceling) — eliminate the triangular component of FORCE OUT. Residual should look like an "ugly square wave" with amplitude < **30 mV p-p** (this amplitude = friction).

**Lab-specific notes:**

- *[e.g. Our unit's friction amplitude after cancellation: X mV p-p — record date]*
- *[e.g. Any difficulty getting R9/R34 to null? Starting pot positions that worked?]*



### Electrical spring cancellation — R24 (step 6)

Function generator OFF. FORCE OFFSET → ¼ turn from CCW stop. LENGTH OFFSET → fully CW. Push lever arm CCW slowly through normal range and back. Adjust **R24** until FORCE OUT stays constant (within a few mV) throughout the range.

**Lab-specific notes:**

- *[e.g. Our R24 setting: X turns from CCW]*



### Force input scale factor — R23 (step 7)

FORCE OFFSET → 3 turns CW. LENGTH OFFSET → center. Apply **1 V p-p square wave** to FORCE IN at Chart #1 frequency. Push lever arm CCW into constant force mode. Adjust **R23** until FORCE OUT = **1.0 V p-p**.

**Lab-specific notes:**

- *[e.g. Note any interaction between R23 and the zero offset after adjustment]*



### Force mode "dead" adjustment — R30 (step 8)

Function generator OFF. FORCE OFFSET → fully CCW. LENGTH OFFSET → fully CW. Push lever arm back and forth. Adjust **R30** until the arm stays wherever it is pushed ("dead" feel). Slight negative spring outside center is acceptable.

**Lab-specific notes:**

- *[e.g. Our R30 setting: X turns from CCW. Behavior in our setup: ...]*



### Final force offset check (step 9)

Push lever arm CCW into constant force mode. Turn FORCE OFFSET CW. Confirm force corresponds to **≥ 1 V/turn** of FORCE OFFSET knob. If not, contact ASI.

**Lab-specific notes:**

- *[e.g. Our measured sensitivity: X V/turn]*

---

