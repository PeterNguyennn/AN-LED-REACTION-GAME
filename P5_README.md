# Reaction Time Game

A hardware arcade game built from three ICs — no microcontroller, no code. A bouncing LED tests your reaction time: stop it on the centre light to score.

![TinkerCAD Circuit](
)
> 🔗 [View on TinkerCAD](https://www.tinkercad.com/your-link-here) · 🎥 [Demo Video](https://your-video-link-here)

---

## How It Works

A **555 timer** generates a ~7 Hz clock that drives a **4017 decade counter**, which advances one LED per pulse — creating a light that bounces back and forth across 5 LEDs. A **4011 NAND SR latch** handles the Start/Stop buttons: pressing Start enables the counter, pressing Stop freezes it. Whatever LED is lit at that exact moment is your result.

---

## Specs

| Property | Value |
|---|---|
| Clock IC | 555 Timer (astable) |
| Sequencer IC | 4017 Decade Counter |
| Latch IC | 4011 NAND (SR latch) |
| Clock frequency | ~7 Hz |
| Supply | 9V battery |
| LEDs | 2× red, 2× blue, 1× green (centre) |

---

## Scoring

| Position | Points |
|---|---|
| Centre green LED | 10 pts |
| Adjacent blue LEDs | 5 pts |
| Outer red LEDs | 0 pts |

First to 50 wins. Swap R1/R2 values to adjust difficulty.

---

## Components

- 555 Timer IC (NE555)
- 4017 Decade Counter IC (CD4017)
- 4011 NAND Gate IC (CD4011)
- Resistors: 100kΩ, 10kΩ, 1kΩ ×2, 100Ω ×10
- Capacitor: 1µF electrolytic
- LEDs: 2× red, 2× blue, 1× green
- 2× push-buttons
- Full-size breadboard (60+ rows), jumper wires, 9V battery

---

## Lessons Learned

- Testing each subsystem in isolation (555 → 4017 → latch) saved a lot of debugging time
- The 4017 notch orientation is easy to get wrong — always double-check before powering up
- SR latch needs pull-up resistors on button inputs, otherwise it triggers randomly from noise
- A full-size 60-row breadboard is not optional — 3 ICs + 5 LEDs + 2 buttons won't fit on smaller ones

---

## Future Improvements

- Replace R2 with a potentiometer for real-time speed control
- Add a 7-segment display to track score automatically
- Extend to 7–9 LEDs for more scoring zones
- Port to PCB for a permanent build
