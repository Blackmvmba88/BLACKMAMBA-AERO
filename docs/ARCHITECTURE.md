# BLACKMAMBA-AERO Architecture

## 1. System layers

### Airframe model
Geometry, mass properties, control surfaces and configuration live behind an airframe identifier. The rest of the stack consumes a normalized contract instead of hard-coding one vehicle.

### Environment model
Atmosphere, wind, disturbances and terrain are explicit inputs. Simulations must record the environment used for every run.

### Sensing
Raw sensor streams are transformed into timestamped observations with provenance, confidence and calibration metadata.

### State estimation
A state estimator produces a bounded state vector such as position, orientation, velocity and selected aerodynamic estimates. Estimation and control remain separate modules.

### Control
Controllers consume state + mission intent and emit bounded actuator commands. Every controller must declare:
- input contract;
- output contract;
- valid operating envelope;
- failsafe behavior;
- simulator used for validation.

### Safety supervisor
The supervisor can clamp, reject or neutralize commands that exceed the configured envelope. Human emergency override always outranks autonomy.

### Evidence
Every simulation or hardware-in-the-loop run should emit:
- configuration;
- git revision;
- airframe id;
- environment;
- controller version;
- events;
- metrics;
- pass/fail result.

## 2. Canonical loop

```text
Sensors → Normalize → Estimate State → Mission / AI Advice
                                      ↓
                               Safety Supervisor
                                      ↓
                                   Control
                                      ↓
                                  Actuators
                                      ↓
                         Plant / Simulator / Vehicle
                                      ↺
```

AI may propose, classify or optimize. Safety-critical actuation must remain constrained by deterministic rules.

## 3. Simulation-first contract

A feature is not considered physically validated because it works in UI or animation.

Validation levels:

- **L0 — Concept**: written model and assumptions.
- **L1 — Software**: unit/invariant checks.
- **L2 — Simulation**: reproducible closed-loop scenario.
- **L3 — HIL/SIL**: hardware/software-in-the-loop evidence.
- **L4 — Low-energy physical test**: bounded real system with emergency stop.
- **L5 — Expanded test envelope**: requires explicit engineering review.

## 4. Airframe registry

The machine-readable starting registry lives in `specs/airframes.json`. Unknown values remain `null`; they must not be invented merely to complete the schema.

## 5. Initial boundaries

This foundation intentionally does **not** define propulsion sizing, structural loads, flight envelopes, life-safety tolerances or manufacturing dimensions. Those require evidence and dedicated engineering work.
