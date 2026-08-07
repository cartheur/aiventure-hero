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
- install the accessories and liason with group regarding issues
- verified memory expansion
- working serial path
- a tiny repeatable sensor-to-action experiment with logged observations

## Can a program designed to run on a RB5X be ported to the ETW-18?

Yes—**in principle**, but only with **substantial porting work**, because the RB5X and the Heathkit HERO 1/ETW-18 (commonly associated with ET-18) run on **different CPUs**, have **different memory/IO layouts**, and use **different programming environments/command sets**.

## What “porting” would realistically mean
- **Re-implement the robot behavior**, not just recompile the code.
  - RB5X: your logic likely targets its specific sensors/actuators and its RB5X I/O/memory model.
  - ETW-18/HERO 1: you’d map that logic onto HERO’s own sensor interfaces and motor/actuator control, and onto the way HERO programs are structured (monitor/robot command language/BASIC options, etc.).
- **Translate the low-level parts**
  - Any code that directly does things like “read sensor X at address Y” or “drive motor Z with timing T” will need to be rewritten.
- **Translate the high-level parts (sometimes)**
  - If your RB5X program is mostly “behavioral” (finite state machines, “if obstacle then turn,” etc.), that logic can often be reused after rewriting the hardware calls.

## Key practical difference: programming target
HERO 1 is described as having a **Motorola 6808 CPU** with **4 kB RAM** and a **monitor ROM (2 kB)**, plus robot-specific programming via its monitor/robot command language. That’s a fundamentally different platform from RB5X’s INS8073/4 MHz + its own software interface.

## Straight answer
- If you mean **“Can I take an RB5X program binary and run it on the ETW-18?”**
  - **No.**
- If you mean **“Can I create an equivalent program for the ETW-18 using the same overall robot behaviors?”**
  - **Yes**, usually by rewriting the program for the HERO’s environment and hardware interfaces.

## Quick next step (to estimate effort)
If you tell me what RB5X program type you have (e.g., wander with sonar, line follower, bump-avoidance, etc.) and whether it uses low-level memory-mapped sensor/motor I/O, I can suggest what parts are likely reusable vs what must be rewritten.
