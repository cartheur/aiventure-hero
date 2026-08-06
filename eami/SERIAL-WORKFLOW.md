# Hero-1 Serial Workflow

This is the intended host-side loop for `eami` experiments once the robot hardware is verified.

## Goal

Use serial access to shorten the experiment cycle:

- write source on the host
- transfer or enter code on the robot
- run a constrained test
- dump memory or observations back to the host
- revise and repeat

## Prerequisites

- memory expansion installed and working
- serial interface present and stable
- known-good ROM and clock pairing
- a terminal connection from the host to the robot

## Workflow

1. Record the robot configuration in [HERO1-LAB-INVENTORY.md](/eami/HERO1-LAB-INVENTORY.md).
2. Choose the experiment target:
   `monitor`, `assembly`, or `BASIC`.
3. Keep source and notes in git on the host.
4. Run the smallest possible motion or sensing test on the robot.
5. Capture observations, memory dumps, or parameter values back into the repo.
6. Only expand scope after the previous step is repeatable.

## First things to validate

- terminal settings that reliably talk to the robot
- a successful memory inspection or dump
- one upload or manual entry cycle with repeatable results
- one safe motion test with the drive wheel constrained or elevated if needed

## Suggested repo usage

- `eami/` for plans, inventories, and experiment logs
- `src/` for active source files
- `monitor/` for historical host tooling and references
- `repairs/` for anything that blocks reliable experiments

## Early warning signs

- inconsistent serial timing
- behavior changes after power cycles
- motion tests that depend on unstable wheel geometry
- ROM assumptions that do not match installed hardware
