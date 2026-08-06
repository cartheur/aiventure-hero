# HERO-1 M6808 Expansion Assessment

This note summarizes how to get maximum practical value from the onboard Motorola `6808` in the lab `ETW-18`, using only the evidence currently present in this repository.

## Executive view

The `HERO-1` is already a strong host for Heiserman-style adaptive control because it combines:

- an onboard `6808` CPU
- built-in sensing for light, sound, ultrasonic range, motion, and time
- a motorized mobile base and articulated arm
- a user-accessible experimental board with direct CPU-facing access

The single most important expansion path is:

1. memory expansion
2. serial interface
3. Utility ROM and/or BASIC ROM
4. cross-development from a modern host

That stack turns the robot from a sealed educational machine into a real experimental platform for adaptive behavior, logging, and iterative software development.

## Confirmed base machine capabilities

From the local technical manual [ET-18 Robot Technical Manual ET-18A.pdf](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/docs/heathkit-ET(W)-18-complete/ET-18%20Robot%20Technical%20Manual%20ET-18A.pdf:1):

- CPU: `6808` microprocessor
- Base memory: `4K RAM` plus `8K ROM`
- Sensors: sound, light, ultrasonic ranging, motion, and calendar clock
- Head: `Experimental Board` with user I/O, user-defined interrupt, CPU control lines, `+5V`, and `+12V`
- Built-in monitor and robot interpreter

This means the stock platform is already enough for:

- assembly-language control experiments
- direct sensor polling and reflexive motor control
- interrupt-driven add-ons through the experimental board

## High-value expansion path

### 1. Memory expansion

From [ET-18 Robot Memory Expansion Accessory ET-18-6.pdf](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/docs/heathkit-ET(W)-18-complete/ET-18%20Robot%20Memory%20Expansion%20Accessory%20ET-18-6.pdf:1):

- base memory can be expanded from `12K` total to as much as `56K`
- supported devices include `6116` and `6264` RAM, plus `2716`, `2532`, `2732`, `2764`, and `68764` EPROM-family parts
- the board relocates the CPU onto the expansion card and opens six memory sockets `U102`-`U107`

Why this matters:

- more RAM allows behavior tables, sensor histories, and learned response maps
- more ROM/EPROM space allows custom monitor, control, or experiment images
- standby-powered RAM can preserve learned state through sleep cycles if configured correctly

### 2. Serial interface

From [ET-18 Robot HERO-1 BASIC Manual ET-18-9.pdf](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/docs/heathkit-ET(W)-18-complete/ET-18%20Robot%20HERO-1%20BASIC%20Manual%20ET-18-9.pdf:1):

`HERO-1 BASIC` requires:

- `ET-18-6` Memory Expansion
- at least one `6264` RAM
- `ETW-18-10` Serial Interface
- a terminal or a host with terminal emulation

Why this matters:

- serial is the cleanest path for loading programs, debugging, dumping memory, and collecting experimental traces
- it makes the robot much more usable as a research platform than front-panel-only entry

### 3. Utility ROM and BASIC ROM

From [ET-18-4 Utility ROM Accessory](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/docs/heathkit-ET(W)-18-complete/ET-18%20Robot%20Utility%20ROM%20Accessory%20ET-18-4.pdf:1) and the BASIC manual:

- Utility ROM gives quick-access demonstrations, speech features, editing aids, and host-assisted workflows
- BASIC ROM adds a higher-level programming path for fast behavioral iteration

Why this matters:

- Utility ROM is useful for inspection, demos, and some operator-facing workflows
- BASIC is useful for quick behavioral prototyping
- assembly remains the best fit for deterministic low-level control or tight memory work

### 4. Cross-development on a modern machine

This repo already includes historical toolchain artifacts:

- [monitor/Assember.zip](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/monitor/Assember.zip:1)
- [monitor/C-compiler.zip](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/monitor/C-compiler.zip:1)
- [monitor/MemoryDump.bas](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/monitor/MemoryDump.bas:1)

That means the right modern workflow is probably:

- write and version source on the host
- assemble or compile offboard
- transfer over serial
- validate behavior on the robot
- dump memory or state back to the host

## What the lab robot appears to have already

From the local photos in [media/myne](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/media/myne/README.md:1) and development images:

- the arm assembly is present
- a head-top expansion board is visible
- side-mounted internal boards are visible
- a remote/power/manuals bundle was included with the purchase

Most important visual inference:

- the board shown in [upgrades/images/hero-memory-expanse.png](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/upgrades/images/hero-memory-expanse.png:1) matches the memory expansion hardware family
- the robot photos strongly suggest that your lab unit already has a substantial add-on stack installed

What cannot yet be confirmed from photos alone:

- whether the serial interface board is installed and working
- whether the Utility ROM is installed
- whether the BASIC ROM is installed
- how much RAM is actually populated on the memory board
- whether the clock/ROM pairing is correct for the installed ROM revision

## Important timing and compatibility note

From [Hero Robot Frequently Asked Questions.pdf](/home/cartheur/ame/aiventure/aiventure-github/cartheur/aiventure-hero/development/hero-faq/Hero%20Robot%20Frequently%20Asked%20Questions.pdf:1):

- some ROM revisions depend on a `4.00 MHz` clock
- the memory expansion card carries a `4.00 MHz` crystal
- mixing ROM revision and crystal frequency incorrectly can distort timing, especially serial timing

This is one of the first things to verify in the lab before doing serious software work.

## Best use of the M6808 for a Heiserman-style port

The strongest way to exploit the onboard `6808` is not to imitate the TRS-80 screen world literally, but to map the Heiserman behavior hierarchy onto real robot primitives.

Recommended progression:

### Alpha-Hero

- condition inputs: bumper/contact, sonar threshold, light threshold, motion, sound
- response outputs: forward, reverse, pivot left, pivot right, stop, arm posture change
- policy: random or semi-random response under constraint of self-preservation

### Beta-Hero

- add remembered response tables keyed by sensed conditions
- reward successful escape, obstacle avoidance, or nest-return behavior
- persist or periodically dump memory tables through serial

### Gamma-Hero

- generalize from one successful condition to nearby conditions
- bias future action selection using confidence values
- use more RAM for condition clusters or response scores

This is a much better hardware instantiation of the Heiserman idea than a screen-only recreation, because the Hero already has real sensing, motion, and onboard timing.

## Recommended lab inspection checklist

For the exact robot in the laboratory, confirm these items physically:

1. CPU board ROMs
   Check `U417` and `U418` and record installed labels and jumper positions.

2. Memory expansion board population
   Record which of `U102`-`U107` are populated and with what device types.

3. Clock source
   Verify whether the active configuration is using the expansion-board `4.00 MHz` timing path or stock CPU timing.

4. Serial interface
   Verify presence of the `ETW-18-10` board on the experimental board or connected serial hardware path.

5. Utility/BASIC ROM status
   Determine whether `ET-18-4` Utility ROM or `ET-18-9` BASIC ROM is physically installed.

6. Voice hardware
   Confirm whether the speech board/accessory is present and functioning, since this helps with demo and interaction workflows.

7. Battery and sleep-retention behavior
   If RAM is configured for standby retention, verify that learned or entered state survives sleep cycles as expected.

## Practical maximum-capability configuration

If the goal is to push this unit toward a serious adaptive robotics platform, the best target configuration is:

- memory expansion board installed and verified
- maximum practical RAM population for experiment storage
- serial interface installed and stable
- known-good ROM/clock pairing
- Utility ROM available for operator workflows
- BASIC ROM available for quick prototyping
- assembly-based core experiments for high-performance control
- host-side source control plus serial transfer/dump tooling

That gives you:

- interactive development
- state inspection
- persistent experiment logs
- room for learned tables and confidence structures
- a credible path from Alpha to Beta and then Gamma-class behavior

## Recommendation

The next best step is not yet writing behavior code. The next best step is to create a machine inventory for the exact lab robot:

- installed boards
- installed ROM labels
- installed RAM population
- jumper positions
- crystal/clock configuration
- serial-access status

Once that is documented, we can design the first `Alpha-Hero` memory map and choose whether to start in:

- monitor-driven `6800` assembly
- `HERO-1 BASIC`
- or a host-side cross-compiled workflow

For a historically faithful but practical Heiserman port, `assembly core + serial tooling + optional BASIC for rapid experiments` is the strongest path.
