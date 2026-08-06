# EAMI Workspace

This directory collects the repo pieces needed to turn the `Hero-1` into a usable `eami` research platform.

## What is here

- [HERO1-M6808-EXPANSION-ASSESSMENT.md](/eami/HERO1-M6808-EXPANSION-ASSESSMENT.md)
  Summary of why memory expansion, serial access, and host-side tooling matter.
- [HERO1-LAB-INVENTORY.md](/eami/HERO1-LAB-INVENTORY.md)
  Working inventory sheet for the exact robot in the lab.
- [SERIAL-WORKFLOW.md](/eami/SERIAL-WORKFLOW.md)
  Host-to-robot workflow for loading, testing, and dumping experiments.
- [ALPHA-HERO-ROADMAP.md](/eami/ALPHA-HERO-ROADMAP.md)
  First-stage adaptive behavior plan for the Hero-1 embodiment.

## How to use this folder

1. Fill in the machine inventory from physical inspection.
2. Update repair blockers that prevent safe drive testing.
3. Confirm serial access and memory expansion status.
4. Choose the first implementation path:
   `6800` assembly, `HERO-1 BASIC`, or a mixed workflow.
5. Define and test the smallest closed-loop behavior from the roadmap.

## Immediate objective

The shortest path to meaningful `eami` work is:

- repaired front caster or steering assembly
- stable drive and pivot behavior
- verified memory expansion
- working serial path
- a tiny repeatable sensor-to-action experiment with logged observations
