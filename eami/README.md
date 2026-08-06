# EAMI Workspace

This directory collects the repo pieces needed to turn the `Hero-1` into a usable `eami` research platform.

## What is here

- [HERO1-STEP-BY-STEP-WORKPLAN.md](/eami/HERO1-STEP-BY-STEP-WORKPLAN.md)
  Main bench file with the integrated repair checklist, steering-and-drive fault summary, and step-by-step sequence.
- [HERO1-PODCAST-OUTPUT.md](/eami/HERO1-PODCAST-OUTPUT.md)
  Podcast-ready outline and script draft for the restoration and `eami` story.
- [HERO1-M6808-EXPANSION-ASSESSMENT.md](/eami/HERO1-M6808-EXPANSION-ASSESSMENT.md)
  Summary of why memory expansion, serial access, and host-side tooling matter.
- [HERO1-LAB-INVENTORY.md](/eami/HERO1-LAB-INVENTORY.md)
  Working inventory sheet for the exact robot in the lab.
- [SERIAL-WORKFLOW.md](/eami/SERIAL-WORKFLOW.md)
  Host-to-robot workflow for loading, testing, and dumping experiments.
- [ALPHA-HERO-ROADMAP.md](/eami/ALPHA-HERO-ROADMAP.md)
  First-stage adaptive behavior plan for the Hero-1 embodiment.

## How to use this folder

1. Start with [HERO1-STEP-BY-STEP-WORKPLAN.md](/eami/HERO1-STEP-BY-STEP-WORKPLAN.md).
2. Use [HERO1-LAB-INVENTORY.md](/eami/HERO1-LAB-INVENTORY.md) only to record findings from the bench.
3. Confirm serial access and memory expansion status.
4. Choose the first implementation path:
   `6800` assembly, `HERO-1 BASIC`, or a mixed workflow.
5. Define and test the smallest closed-loop behavior from the roadmap.

## Immediate objective

The shortest path to meaningful `eami` work is:

- repaired steering and drive assembly
- stable drive and pivot behavior
- verified memory expansion
- working serial path
- a tiny repeatable sensor-to-action experiment with logged observations
