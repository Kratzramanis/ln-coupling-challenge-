# ln-coupling-challenge
Goal: test whether rapid pressure pulses in dense ceramics produce a logarithmic temperature rise  ΔT  Δρ  ≈  κ1 ln⁡(ρ)   ΔTΔρ≈κ1​ln(ρ)​
    One-liner
    – Squeeze a piezo (PZT) pellet with millisecond pressure pulses.
    – Record the accompanying temperature jump ΔT and force/pressure Δρ.
    – Upload CSV + photo → auto-script evaluates the ln-fit.
    – R² ≥ 0.80? → co-author credit in the Finja & Dimi preprint!

1 · Low-budget hardware (≈ €60)
Part	Purpose	Cost
PZT pellet (Ø 10 mm)	dense ceramic lattice	€5
Small press / vise	short pressure pulse	€20
K-thermocouple (+ MAX31855) or NTC	millisecond ΔT read-out	€3
Load cell + HX711	force → Δρ proxy	€7
Arduino / ESP32 + SD logger	timestamp & CSV log	€10
Smartphone macro / USB microscope	crystal photo (before/after)	€0–15
2 · Measurement procedure

    Mount pellet, thermocouple and load cell in a line.

    Produce 25 pressure pulses – press in, release immediately.

    Log per pulse: timestamp (ms), force (N), temperature (°C).

    Take one photo before and one after the run.

3 · Data format

# ms,ΔT_C,ΔF_N
0,0.00,0.00
17,0.35,42.7
...


    ΔT_C = temperature rise vs. start value

    ΔF_N = force change (acts as Δρ proxy)

4 · Upload steps

    Fork this repo.

    Create /data/<your_name>/

        run.csv – raw log

        before_after.jpg – pellet photo

        setup.txt – sensors & sampling rate

    Open a pull request.

5 · Auto-scoring

Notebook score_ln.ipynb

    loads run.csv

    detects peaks, computes ΔT and Δρ

    performs ln regression → returns κ₁ and R²

    appends your result to scores.md

    Thresholds

        R² ≥ 0.80 → Hall of Fame + co-author in the paper

        0.50 ≤ R² < 0.80 → listed in the supplementary dataset
6 · Timeline
| Phase                        | Date                   |
| ---------------------------- | ---------------------- |
| Call opens                   | **T₀ (today + 1 day)** |
| Data collection              | T₀ → T₀ + 28 days      |
| Scoring & feedback (Discord) | week 5                 |
| Preprint submission          | week 6                 |


7 · License & contribution

All contributions under CC-BY 4.0.
By submitting a PR you consent to publication of your data in the Finja & Dimi preprint (with full name acknowledgement).
## Community & Support  
Join the live discussion on Discord → **https://discord.gg/s5kNa2ng**  
Channel: **#ln-coupling**

We troubleshoot hardware, share partial results and keep the scoreboard up-to-date.
