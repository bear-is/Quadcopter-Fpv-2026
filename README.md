# Summer Project 2026 Peregrine — High Speed FPV Quad

> *A Peregrine-inspired speed quadcopter designed to fly fast, look cinematic, and be built from scratch.*

---

## What We're Building

A compact, high-speed FPV quadcopter 3D printed, and built entirely by our team: custom SolidWorks frame, hand-soldered electronics stack, and tuned Betaflight firmware.

The goal is a drone that:
- Flies nearly horizontal at full throttle
- Looks great on FPV footage
- Is small, light, and relatively simple to build
- Is fully documented so anyone on the team can pick up where someone left off

## ***This is just a starter roadmap everything here is subject to change***

---

## Project Status

- [ ] Team roles assigned
- [ ] SolidWorks frame design started
- [ ] BOM finalized and parts ordered
- [ ] Electronics bench test complete
- [ ] First print iteration done
- [ ] Betaflight configured and armed
- [ ] First hover test
- [ ] First full-speed flight
- [ ] Demo video captured

---

## Repo Structure

```
/peregrine
├── /cad                  ← SolidWorks parts + assemblies + exported STLs
├── /stl                  ← Print-ready STL exports (named with version)
├── /firmware             ← Betaflight config dumps, ELRS bind phrases, BLHeli settings
├── /software             ← Python scripts, MAVLink/DroneKit, SITL configs
├── /docs                 ← Wiring diagrams, BOM, build notes, tuning logs
├── /media                ← Flight footage, photos, renders
└── README.md             ← Roadmap + documentation
```

> **Note:** SolidWorks and STL files are large binaries. The repo uses **Git LFS**
---

## Electronics Stack (Target Spec / tbd)

| Component | Part | Notes |
|---|---|---|
| Motors | 2004 / 1606, 3000–3500KV | 4S optimized |
| ESC | 4-in-1, 25–30A, BLHeli_32 | Enable bidirectional DSHOT |
| Flight Controller | F7 stack, 20×20 | Betaflight firmware |
| Receiver | ExpressLRS (ELRS) 2.4GHz | Match TX firmware version |
| Radio | RadioMaster Boxer or TX16S | ELRS module required |
| VTX | 200mW 5.8GHz | MSP OSD enabled |
| Camera |  |
| Battery |  |
| Props | 5" tri-blade (HQ or Gemfan) | Check motor direction before flying |

---

## Software & Tools

### Everyone
- [Git](https://git-scm.com/) + [Git LFS](https://git-lfs.com/)
- [SolidWorks](https://www.solidworks.com/) (education license)

### Electronics / Firmware
- [Betaflight Configurator](https://github.com/betaflight/betaflight-configurator/releases)
- [BLHeli_32 Suite](https://github.com/bitdump/BLHeli)
- [ELRS Configurator](https://github.com/ExpressLRS/ExpressLRS-Configurator/releases)
- [Betaflight Blackbox Explorer](https://github.com/betaflight/blackbox-log-viewer/releases)

### Software / Simulation
- [Python 3.10+](https://python.org)
- [DroneKit Python](https://dronekit.io/) — `pip install dronekit`
- [ArduPilot SITL](https://ardupilot.org/dev/docs/sitl-simulator-software-in-the-loop.html) — simulate flights before real ones
- [QGroundControl](http://qgroundcontrol.com/) — ground station / mission planner

---

## Build Order


1. **Finalize CAD** — lock in motor spacing, then design everything else around it
2. **Export STLs + DXF** for carbon plate, add to `/stl`
3. **Order parts** — budget 2–3 weeks shipping, order early
4. **Print test arms** — crash test them before printing the full frame
5. **Bench test electronics** — FC + ESC + motors spinning on the bench, no props, no frame
6. **Flash firmware** — Betaflight on FC, BLHeli_32 on ESC, ELRS on RX and TX
7. **Assemble frame** — wire everything through the arms, no exposed cables
8. **Betaflight config** — ports, protocols, motor directions, failsafe
9. **Props-off arm test** — verify all motors spin correct direction


---

## Wiring Rules

- Use **silicone wire** rated to 200°C — PETG softens at ~80°C and PVC-insulated wire will melt against the frame at high current
- Route motor wires **through the arms** — nothing dangling underneath
- All components share a **common ground** — never power the FC from a separate source
- Solder XT30 or XT60 battery connectors — do not use JST for anything above 10A

---

## Git Workflow

```bash
# Clone the repo (first time)
git lfs install
git clone <repo-url>

# Before starting work
git pull origin main

# Create a branch for your changes
git checkout -b feature/your-name-description
# e.g. git checkout -b cad/nose-cone-v2

# Commit and push
git add .
git commit -m "short description of what you changed"
git push origin feature/your-name-description

# Open a pull request on GitHub — don't push directly to main
```

**Branch naming:**
- `cad/` — SolidWorks changes
- `firmware/` — Betaflight / ELRS configs
- `software/` — Python / simulation
- `docs/` — documentation updates
- `media/` — footage and photos

---

## Resources & References

- [Peregrine 2 build video — Luke Bell (YouTube)](https://www.youtube.com/watch?v=wThmg8Ezm9w)
- [Betaflight docs](https://betaflight.com/docs/)
- [ExpressLRS docs](https://www.expresslrs.org/)
- [BLHeli_32 manual](https://github.com/bitdump/BLHeli/blob/master/BLHeli_32%20ARM/BLHeli_32%20manual%20ARM%20Rev32.x.pdf)
- [ArduPilot SITL setup](https://ardupilot.org/dev/docs/sitl-simulator-software-in-the-loop.html)
- [Joshua Bardwell — Betaflight tuning (YouTube)](https://www.youtube.com/@JoshuaBardwell)

---

*Built by DTCC Engineers — 2026
