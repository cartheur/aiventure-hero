# Front Caster Repair Plan

This note tracks the first repair priority for the lab `Hero-1`: the front caster or driven steering wheel assembly.

## Why this comes first

The robot cannot be trusted for motion experiments while the front steering assembly drives to an extreme stop or behaves unpredictably under power.

That makes this repair a prerequisite for:

- safe drive testing
- repeatable motion control
- `eami` behavior experiments
- serial-guided movement tests

## Current evidence

- [repairs/images/left-pivot-drive.png](/repairs/images/left-pivot-drive.png)
- [repairs/images/training-wand.png](/repairs/images/training-wand.png)
- existing note in [repairs/README.md](/repairs/README.md)

## Problem statement

Observed or reported condition:

- the front wheel steering assembly runs to the extreme left stop
- the robot needs to be tilted or supported to test the wheel safely

## Likely fault classes

1. Mechanical binding
   Wheel fork, linkage, gearbox, or mounting hardware may be binding before the control system sees a valid centered position.
2. Feedback or stop-sensing fault
   A switch, potentiometer, or equivalent steering reference element may be dirty, open, misaligned, or disconnected.
3. Drive electronics fault
   The steering motor command path may be forcing continuous travel in one direction.
4. Contamination and age-related failure
   Oxidation, dried lubricant, hardened rubber, or brittle wiring may be contributing.

## Bench procedure

1. Support the robot so the front wheel hangs free.
2. Photograph the assembly from left, right, front, and underside views.
3. Check whether the wheel can be moved smoothly by hand through its range with power off.
4. Observe stop points, spring behavior, backlash, and any rubbing.
5. Power the robot only for short controlled tests.
6. Use the programming unit to command steering changes and record exactly what the assembly does.

## What to record

- Can the wheel rotate freely by hand?
- Does it center mechanically?
- Does powered steering always force left?
- Is there any audible relay, switch, or motor change near the end of travel?
- Are there visible damaged wires, cracked mounts, or missing fasteners?

## Exit criteria

This repair is considered ready enough for motion work when:

- the front caster assembly no longer runs away to the left stop
- left and right steering commands both respond predictably
- the wheel can hold or return to a sensible center state
- unloaded testing is repeatable across multiple power cycles
