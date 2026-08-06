# HERO-1 Step-By-Step Workplan

This is the practical workplan for getting the lab `Hero-1` ready for `eami` experiments.

This is the main file to use at the bench.

Use it in order. Do not skip ahead to software or serial work until the steering and drive repair is stable.

## Start here

If you only open one file, use this one.

Only use this other file while working:

- [HERO1-LAB-INVENTORY.md](/eami/HERO1-LAB-INVENTORY.md) for recording what you actually find

Related output file:

- [HERO1-PODCAST-OUTPUT.md](/eami/HERO1-PODCAST-OUTPUT.md) for the podcast outline and script draft

## Steering and drive fault summary

This is the first repair priority for the lab `Hero-1`.

Current reported condition:

- the steering and drive assembly runs to the extreme left stop
- the robot needs to be tilted or supported to test the wheel safely

Why it comes first:

- safe drive testing depends on it
- repeatable motion control depends on it
- `eami` behavior experiments depend on it
- serial-guided movement tests depend on it

Current evidence:

- [repairs/images/left-pivot-drive.png](/repairs/images/left-pivot-drive.png)
- [repairs/images/training-wand.png](/repairs/images/training-wand.png)

Likely fault classes:

1. Mechanical binding
   Wheel fork, steering linkage, drive train, gearbox, or mounting hardware may be binding before the control system sees a valid centered position.
2. Feedback or stop-sensing fault
   A switch, potentiometer, or equivalent steering reference element may be dirty, open, misaligned, or disconnected.
3. Drive electronics fault
   The steering motor or drive command path may be forcing continuous travel in one direction.
4. Contamination and age-related failure
   Oxidation, dried lubricant, hardened rubber, or brittle wiring may be contributing.

## Repair checklist from the ET-18 documents

Use this short checklist before making changes. It pulls together the most useful repair guidance from the local Heathkit manuals.

### Document-based checks

- [ ] Check battery condition first. The `User's Guide` warns that low logic voltage can cause false motor behavior, and low drive voltage stops normal motion. See [ET-18 Robot - User's Guide.pdf](/docs/heathkit-ET(W)-18-complete/ET-18%20Robot%20-%20User%27s%20Guide.pdf:1).
- [ ] Do not add oil or grease as a first step. The `User's Guide` says the motors and gearcases are permanently lubricated; clean exposed mechanism areas instead.
- [ ] Expect the robot to home the drive wheel by sending it left to a limit and then back to center. If it goes left and does not recover, suspect centering adjustment or steering-limit sensing. See [ET-18 Robot Technical Manual ET-18A.pdf](/docs/heathkit-ET(W)-18-complete/ET-18%20Robot%20Technical%20Manual%20ET-18A.pdf:1).
- [ ] Check the steering adjustment on the `drive wheel bracket`. The `User's Guide` says straight-ahead travel depends on an adjustable spring there, and shipping can misadjust it.
- [ ] Check the `limit switch spring` adjustment on the main drive assembly. The `Technical Manual` steering adjustment section identifies this as the steering centering adjustment.
- [ ] Check the `drive wheel sensor` alignment. The `Technical Manual` says the optical pickup and encoder disk may need adjustment if sensing is inconsistent.
- [ ] Use the teaching pendant as a diagnostic tool. With the wheel unloaded, confirm left, right, hold, and return behavior before deeper disassembly. See [ET-18 Robot Assembly Manual ET-18A.pdf](/docs/heathkit-ET(W)-18-complete/ET-18%20Robot%20Assembly%20Manual%20ET-18A.pdf:1).
- [ ] Be careful with connectors and board removal. The `Technical Manual` warns to pry boards and reconnect plugs carefully and exactly.

### Best repair order from the manuals

1. Check batteries and power symptoms.
2. Clean and visually inspect the steering and drive assembly.
3. Test steering response with the teaching pendant and the wheel unloaded.
4. Adjust the steering centering spring or limit switch spring if needed.
5. Check drive wheel sensor pickup alignment if behavior is still inconsistent.
6. Only then move into deeper wiring or board-level diagnosis.

## Phase 1: Make the robot safe to inspect

Goal: create a safe bench setup for front wheel diagnosis.

- [ ] Clear a stable work area with good lighting.
- [ ] Gather blocks, supports, or a stand so the front wheel can hang free.
- [ ] Keep the robot stable enough that it cannot roll or tip during testing.
- [ ] Place the programming or training unit nearby.
- [ ] Have a camera or phone ready for documentation.

Stop if:

- the robot cannot be supported safely
- the wheel is carrying weight during diagnosis
- the body rocks or slips under light handling

## Phase 2: Capture the starting state

Goal: document the machine before changing anything.

- [ ] Fill in the top of [HERO1-LAB-INVENTORY.md](/eami/HERO1-LAB-INVENTORY.md).
- [ ] Photograph the steering and drive assembly from front, left, right, and underside views.
- [ ] Note the current wheel position at power-off.
- [ ] Record any visible damage, missing fasteners, cracked parts, bent metal, or loose wires.
- [ ] Add image filenames and notes to the inventory file.

Done when:

- you can describe the starting condition without relying on memory

## Phase 3: Perform a power-off mechanical check

Goal: decide whether the fault is obviously mechanical.

- [ ] Move the front wheel assembly gently by hand through its range.
- [ ] Check for rough spots, sticking, rubbing, or hard stops.
- [ ] See whether the wheel can return to a sensible center position.
- [ ] Inspect linkage, fork, gearbox area, and mounting points for binding.
- [ ] Look for dried grease, corrosion, dirt, or aged wiring around the assembly.

Record:

- [ ] Does the wheel move freely by hand?
- [ ] Does it bind only near one side?
- [ ] Can it be centered manually?
- [ ] Is there play, backlash, or looseness?

If the answer is clearly mechanical:

- [ ] Pause powered testing until the binding source is identified

## Phase 4: Perform a short powered steering check

Goal: confirm whether the wheel runs away electrically or under control logic.

- [ ] Keep the front wheel unloaded.
- [ ] Power on only for short test windows.
- [ ] Use the programming or training unit to command left, right, and neutral behavior.
- [ ] Observe whether the wheel always drives left regardless of command.
- [ ] Listen for changes near the ends of travel: motor tone, switch click, relay sound, or stall behavior.
- [ ] Power off immediately if the wheel drives hard into the stop.

Record:

- [ ] Does powered behavior differ from hand movement?
- [ ] Do left and right commands behave differently?
- [ ] Does the wheel always seek the same extreme?
- [ ] Is there evidence of a limit or feedback device not being recognized?

## Phase 5: Identify the most likely fault class

Goal: classify the problem before attempting repair.

Choose the best current fit:

- [ ] Mechanical binding
- [ ] Feedback or limit-sensing fault
- [ ] Steering motor drive or control fault
- [ ] Wiring or connector fault
- [ ] Mixed fault, not yet isolated

Write the current best guess in:

- [ ] [HERO1-LAB-INVENTORY.md](/eami/HERO1-LAB-INVENTORY.md)

## Phase 6: Do the smallest repair or cleanup first

Goal: make the least risky change that could restore normal behavior.

Examples:

- [ ] Clean and reseat steering-related connectors
- [ ] Remove visible debris or hardened residue
- [ ] Tighten loose mounting hardware
- [ ] Correct obvious misalignment
- [ ] Repair or secure damaged wiring

Rules:

- [ ] Change one thing at a time
- [ ] Re-test after each change
- [ ] Take another photo after each meaningful intervention

Avoid:

- [ ] multiple simultaneous changes
- [ ] free-floor movement tests before unloaded steering is repeatable

## Phase 7: Re-test until steering is repeatable

Goal: prove the repair is stable enough for the next stage.

- [ ] Repeat the unloaded steering test across multiple power cycles.
- [ ] Confirm the wheel no longer runs away to the extreme left stop.
- [ ] Confirm left and right commands both respond predictably.
- [ ] Confirm the wheel can hold or return to a useful center state.
- [ ] Update the repair notes with what fixed the issue.

Exit criteria:

- [ ] Steering no longer runs away
- [ ] Steering response is repeatable
- [ ] No immediate sign of binding or overstress

## Phase 8: Verify the rest of the motion path

Goal: make sure steering repair did not hide other drive problems.

- [ ] Re-check drive motion status in [HERO1-LAB-INVENTORY.md](/eami/HERO1-LAB-INVENTORY.md).
- [ ] Confirm bench-safe forward and reverse response.
- [ ] Confirm pivot behavior matches command direction.
- [ ] Watch for intermittent startup or connector issues.

Only proceed if:

- [ ] motion behavior is predictable enough for controlled experiments

## Phase 9: Inventory expansion and serial hardware

Goal: prepare for host-assisted software work.

- [ ] Confirm memory expansion board presence and chip population.
- [ ] Confirm serial interface presence and connection path.
- [ ] Record ROM labels, jumper positions, and clock details.
- [ ] Note Utility ROM and BASIC ROM status if present.
- [ ] Update [HERO1-LAB-INVENTORY.md](/eami/HERO1-LAB-INVENTORY.md) completely.

## Phase 10: Start the first software path

Goal: choose the easiest reliable development loop.

Start with one:

- [ ] Monitor-driven `6800` assembly
- [ ] `HERO-1 BASIC`
- [ ] Host-side cross-development over serial

Pick based on:

- [ ] what hardware is confirmed installed
- [ ] what serial path is working
- [ ] what gives the shortest repeatable test loop

## Phase 11: Run the first tiny EAMI experiment

Goal: prove a minimal sense-to-action loop on stable hardware.

- [ ] Choose one sensor condition.
- [ ] Choose one safe response.
- [ ] Run a tiny controlled trial.
- [ ] Record observations and any dumped state.
- [ ] Repeat until behavior is predictable.

Good first targets:

- [ ] obstacle-near to stop
- [ ] timeout to pivot
- [ ] light-threshold to short motion response

## Documentation capture

Goal: make future writing or recording easier while the details are fresh.

- [ ] Save clear before and after photos for each repair step.
- [ ] Record exact observed symptoms in plain language, not just conclusions.
- [ ] Note each intervention, however small, and whether it helped.
- [ ] Keep dates on bench sessions, tests, and changes.
- [ ] Save any surprising behavior, false starts, and dead ends.
- [ ] Write one short paragraph after each session: what we thought, what we tried, what changed.

Useful future output angles:

- a repair paper on reviving an ET-18 steering and drive system
- a methods note on document-guided restoration from original manuals
- a podcast episode on debugging vintage embodied AI hardware
- a broader piece connecting `Hero-1`, `eami`, and adaptive behavior experiments

## Quick decision guide

If the wheel binds by hand:

- treat it as mechanical first

If the wheel moves freely by hand but runs left under power:

- suspect feedback, limit, wiring, or drive control

If behavior changes after connector movement:

- suspect contact, oxidation, or cable strain

If behavior changes across power cycles:

- document power and timing conditions carefully

## Minimum success definition

This workplan is successful when:

- the steering and drive assembly is reliable
- the robot is safe for controlled motion testing
- the machine inventory is documented
- the serial and memory path is known
- one tiny `eami` experiment can be run on purpose
