# Artemis II: Trajectory Analysis

**English** | [Bahasa Indonesia](README.id.md)

> *"We choose to go to the Moon not because it is easy, but because it is hard."* (John F. Kennedy)

On April 1, 2026, people headed for the Moon again for the first time since Apollo. They weren't going to land. The point of this trip was to show that the spacecraft and crew were ready for the next mission, the one that will.

Artemis II carried four astronauts around the Moon and back in about nine days, aboard an Orion capsule the crew named *"Integrity"*. I wanted to see that trip for myself, so this repo rebuilds the path Orion flew using real ephemeris data from **NASA JPL Horizons** and turns it into plots.

![Trajectory 2D](trajectory_2d.png)

---

## About the mission

Artemis II is the first crewed flight of the Artemis program, NASA's follow-up to Apollo. Artemis I in 2022 flew with nobody on board. This time there were four people, flying a *free-return trajectory*. That path is shaped so that if every system failed after leaving Earth orbit, the gravity of the Moon and Earth would still bring the capsule home without a single extra engine burn.

**Crew:**
- **Reid Wiseman**, Commander (NASA)
- **Victor Glover**, Pilot (NASA)
- **Christina Koch**, Mission Specialist (NASA)
- **Jeremy Hansen**, Mission Specialist (CSA, Canada)

**Quick timeline:**

| Day | What happened |
|-----|---------------|
| 1 | Launch from Kennedy Space Center, solar arrays deployed, first orbit adjustments |
| 2 | **Translunar Injection (TLI)**: a 5 min 55 s burn adding 388 m/s, pointing Orion at the Moon |
| 5–6 | Enters the Moon's sphere of influence, closest approach **8,282 km** above the surface |
| 6 | Farthest point from Earth: **413,146 km** |
| 7–9 | Heading home, with three small correction burns |
| 10 | Atmospheric entry at 122 km, splashdown in the Pacific Ocean |

---

## What the plots show

![Distance Profile](distance_profile.png)

The two curves mirror each other. As Orion gets farther from Earth, it gets closer to the Moon. Both peak on day 6, when Orion was 413 thousand km from Earth and only about 8 thousand km above the lunar surface.

![Speed Profile](speed_profile.png)

The speed plot is gravity at work. Orion slows down as it climbs away from Earth, speeds up as the Moon pulls it in, and speeds up again on the fall back home. Each vertical line marks an engine burn that changed the path.

![Trajectory 3D](trajectory_3d.png)

---

## Data

Everything comes straight from the NASA JPL Horizons System, the same ephemeris service NASA scientists and mission engineers use.

| File | Contents |
|------|----------|
| `artemis_ephemeris.txt` | Position and velocity of Orion "Integrity" (body ID `-1024`), updated April 10, 2026 |
| `moon_ephemeris.txt` | Position of the Moon (body ID `301`, DE441), 5-minute steps |

Every line between `$$SOE` and `$$EOE` holds a Julian Date, a timestamp, an XYZ position (km), and a VxVyVz velocity (km/s), in the Earth-centered Ecliptic J2000.0 frame.

---

## How to run it

```bash
pip install -r requirements.txt
jupyter notebook artemis_ii_analysis.ipynb
```

The notebook is saved with its outputs, so you can open it and read through without running anything.

---

## Source

NASA JPL Horizons System: [ssd.jpl.nasa.gov](https://ssd.jpl.nasa.gov/horizons/)
