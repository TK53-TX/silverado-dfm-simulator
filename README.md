# Silverado L84 DFM Cluster Simulator

Two interactive browser simulations of the GM 5.3L **L84** engine's **Dynamic Fuel Management (DFM)** cylinder-deactivation logic, styled as the **2025 Chevrolet Silverado 1500** 12.3-inch digital instrument cluster.

## Live demo

Enable **GitHub Pages** (Settings → Pages → Deploy from branch → `main` / root), then open:

- `index.html` — landing page
- `dfm_cluster_option2_drivecycle.html` — Option 2, scripted drive cycle
- `dfm_cluster_option3_accelproxy.html` — Option 3, interactive accel proxy

## The two builds

| | Option 2 — Drive Cycle | Option 3 — Accel Proxy |
|---|---|---|
| Input | Scripted 88s trip (play/pause/scrub) | Speed slider + grade slider |
| Engine load | Derived from speed, acceleration, grade | Derived from rate of speed change + grade |
| Best for | Watching DFM behave on its own | Probing a specific speed/grade case |

## Features

- **Cluster layout** — tachometer left, speedometer right, Driver Information Center center (GM Classic config).
- **Continuous DFM model** — cylinder count slides 8 → 6 → 4 → 2 on engine load; no artificial speed window. Active at all speeds, locks V8 only on real torque demand or near-idle.
- **10-speed gear strip** — P R N D plus gears 1–10, live highlight, load-based downshift (10L80-style).
- **Aero-drag load model** — load rises with the square of speed, so 75–80 mph cruise holds a shallow deactivation (6-cyl) rather than locking V8.
- **Boost OBD module** — models the real device: arms only after the truck first reaches **40 mph**, then locks V8 for the rest of the session.
- **Instant MPG gauge** — green when V8 is locked by the module, amber while DFM is active.

## Tech

Single self-contained HTML files. [D3.js](https://d3js.org) (CDN) for the radial gauges. No build step, no dependencies to install.

## Accuracy note

This is an **educational model**, not a GM engineering tool. Cylinder thresholds, load curves, RPM, MPG values, and shift points are informed approximations of AFM/DFM behavior. The Boost OBD module's 40 mph arming behavior reflects the manufacturer's published spec. Real DFM also weighs coolant temp, gear, transmission state, and lifter oil pressure, which are not modeled.

## License

MIT — see `LICENSE`.
