# Alpha-Hero Roadmap

`Alpha-Hero` is the first practical `eami` milestone for this robot: a minimal closed-loop behavior layer that senses the environment and chooses safe motion responses.

## Objective

Build a tiny adaptive core around real `Hero-1` primitives instead of a screen-only simulation.

Motion work starts only after the front caster or steering assembly is mechanically trustworthy.

## Phase 1

- verify safe bench testing conditions
- confirm at least one reliable sensor input
- confirm at least one reliable motion output
- establish a repeatable test script

## Phase 2

- define a compact condition table
- map each condition to a small response set
- log observed outcomes after each response
- adjust response preference from prior success

## Candidate condition inputs

- obstacle near via sonar threshold
- bright or dark light threshold
- sound trigger present
- motion detector event
- timeout or idle state

## Candidate response outputs

- stop
- forward short burst
- reverse short burst
- pivot left
- pivot right
- arm posture change

## Success criteria

- the robot completes repeated short trials safely
- at least one condition changes action selection over time
- state can be inspected or dumped through the host workflow

## Do not optimize yet

Avoid large behavior trees, multi-feature learning, or complex data structures before:

- repair blockers are cleared
- serial access is dependable
- the memory map is based on the real installed hardware
