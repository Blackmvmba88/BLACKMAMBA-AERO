# BLACKMAMBA-AERO Roadmap

## Phase A0 — Foundation
- [x] Canonical repository selected.
- [x] Architecture layers documented.
- [x] Airframe registry created.
- [x] Simulation-first validation ladder defined.

## Phase A1 — Simulation contracts
- [ ] Define normalized vehicle state.
- [ ] Define sensor observation schema.
- [ ] Define actuator command schema.
- [ ] Define scenario/replay format.
- [ ] Define safety-envelope configuration.

## Phase A2 — M-RAY baseline
- [ ] Establish a deliberately simplified M-RAY dynamics model.
- [ ] Add deterministic test scenarios.
- [ ] Integrate visualization through Avion / Avion-Unity where useful.
- [ ] Record repeatable simulation evidence.

## Phase A3 — Control and observer integration
- [ ] Connect flight-simu experiments through adapters.
- [ ] Add supervisor / emergency-stop state machine.
- [ ] Export machine-readable run reports.
- [ ] Connect controlled execution to Observer / WARPBLACK.

## Phase A4 — Sensing research
- [ ] Flow-sensing interface contract.
- [ ] Smart-skin sensor topology experiments.
- [ ] Sensor fusion experiments with synthetic data.
- [ ] Failure injection and degraded-mode behavior.

## Phase A5 — Physical validation gate
Only after A1–A4 provide reproducible evidence:
- [ ] select low-energy bench hardware;
- [ ] define physical limits and test enclosure;
- [ ] human emergency stop;
- [ ] pre-test checklist and abort conditions;
- [ ] compare measured data with simulator predictions.
