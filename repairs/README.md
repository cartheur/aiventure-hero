## Repairs to the ETW-18

A series of repairs to bring an old robot back to everyday life. And to help study [Heiserman](https://github.com/cartheur/aiventure-rodney)'s concept of self-programming, given a new embodiment criteria in [ideal](https://github.com/cartheur/ideal).

-----

## First repair priority

The first subsystem to attend to is the front caster or driven steering wheel assembly.

From the current repair evidence, the practical symptom appears to be that the steering drive runs the front wheel assembly to the extreme left until it hits the stop shaft.

This must be treated as the first blocker before general motion testing, serial-guided movement experiments, or `Alpha-Hero` behavior work.

## Known symptom

* The extreme position of the drive wheel.
    - ![image](/repairs/images/left-pivot-drive.png)
* The current dilemma is to pivot the robot on its back wheels, keeping the drive wheel elevated so it can be tested with the training/programming unit
    - ![image](/repairs/images/training-wand.png)

## Working interpretation

- The affected part is the front wheel steering or caster assembly rather than a rear support wheel.
- The current failure mode may be electrical, mechanical, or both:
  steering feedback, limit detection, linkage binding, motor control, or contamination in the assembly.
- Bench testing should keep the front wheel unloaded until the fault is understood.

## Repair workflow

1. Secure the robot so the front wheel assembly can move freely without floor loading.
2. Inspect the caster or steering linkage for binding, bent parts, cracked plastic, or loose hardware.
3. Inspect wiring, switches, and connectors associated with steering feedback or stop detection.
4. Use the training or programming unit to verify whether left, right, and centered behavior can be commanded distinctly.
5. Document the observed behavior and only then proceed to cleaning, adjustment, or part repair.

### Next steps

* Secure the robot for unloaded front caster testing.
* Record whether the wheel can be centered manually and whether it returns to the extreme left under power.
* Identify whether the fault is primarily mechanical binding or runaway steering control.

This repair remains a direct blocker for `eami` motion experiments and should be cleared before free-movement testing.
