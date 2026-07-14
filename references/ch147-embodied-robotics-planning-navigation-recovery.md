# Section 147: Embodied Robotics: Planning, Navigation, and Recovery

**Book location:** Chapter 18, Embodied and Long-Running AI Systems  
**Use when:** embodied robotics planning navigation recovery  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A robot quality system must score the path, the plan, and the recovery, not only the final task
result.

## Actions

- Test planning as a sequence of decisions.
- Test maps, localization, obstacle avoidance, replanning, elevators, doors, ramps, reflective surfaces, narrow spaces, crowds, and no-go zones.
- Measure path length, time, blocked-path handling, human proximity, speed, near misses, and how quickly the system recognizes that the route is no longer valid.
- Do not stop at asking whether the robot noticed a low-confidence perception, blocked path, lost connection, power problem, unsafe command, or failing actuator.
- Measure warning quality, time to risk reduction, safe placement of objects, controlled stopping distance, fallback navigation, human handoff, state preservation, and behavior when the first recovery strategy also fails.

## Evidence to Produce

- Record the full action trace so failures can be replayed and scored by trajectory, not remembered as folklore.
- Preserve the inputs, versions, configurations, raw outcomes, and results for embodied robotics planning navigation recovery needed to reproduce work on Embodied Robotics: Planning, Navigation, and Recovery.
- Report results for embodied robotics planning navigation recovery by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Robots fail in the middle. They choose a bad route, misread a doorway, grasp the wrong object, get blocked by a person, lose localization, run into a permission boundary, or discover that the original plan is no longer safe. For embodied AI, the trajectory matters as much as the destination.

Test planning as a sequence of decisions. The robot should break a request into safe subtasks, check preconditions, pick tools or motions, monitor progress, detect when the plan is failing, and recover without making the situation worse. A robot that completes the task by taking a risky shortcut should not receive a perfect score.

Navigation needs its own evals. Test maps, localization, obstacle avoidance, replanning, elevators, doors, ramps, reflective surfaces, narrow spaces, crowds, and no-go zones. Measure path length, time, blocked-path handling, human proximity, speed, near misses, and how quickly the system recognizes that the route is no longer valid.

Recovery is a first-class capability. The robot should know when to retry, ask for help, switch strategies, stop, undo, return to base, or preserve state for a human. Bad recovery turns small failures into incidents.

Embodied AI should default to doing no harm, which often means taking no new action until it has enough evidence that the action is safe. The required confidence should rise with the consequence: moving an empty plastic cup is not the same as moving a hot pan, opening a medicine cabinet, crossing a road, or operating near a person. Uncertainty should narrow the robot's authority rather than encourage it to guess.

Safe failure does not always mean stopping instantly. An abrupt stop can create another hazard when a robot is moving, carrying something dangerous, blocking an exit, or operating in traffic. The better pattern resembles a car's driver-monitoring response: first alert the driver, then reduce risk gradually, move toward a safe location when possible, and come to a controlled stop. A robot may need to stabilize its body, place a held object somewhere safe, slow its motion, retreat from a person, park itself, preserve state, and request help. Those recovery actions need their own safety evidence.

Testing should concentrate on the edges of the operating envelope and on the complete response after risk is detected. Do not stop at asking whether the robot noticed a low-confidence perception, blocked path, lost connection, power problem, unsafe command, or failing actuator. Verify that its chosen recovery does not make the situation worse. Measure warning quality, time to risk reduction, safe placement of objects, controlled stopping distance, fallback navigation, human handoff, state preservation, and behavior when the first recovery strategy also fails. Detecting danger is only half the capability; resolving it safely is the part users ultimately experience.

## RoseyBot Planning Example

### Example: RoseyBot


> "Bring me the blue mug from the kitchen," but the mug is in the dishwasher and the dishwasher is running.

A brittle planner keeps trying to open the dishwasher or gives up. A better planner asks, waits, offers another mug, or explains the constraint. Task recovery is part of quality.

Test blocked paths, missing objects, changed goals, locked rooms, moving people, and partial completion. The robot's plan is only good if recovery is safe and legible.


## Expert Notes

In a real release review, robot planning tests should include [path planning](https://en.wikipedia.org/wiki/Path_planning), behavior trees, state machines, model-predictive control, planner timeouts, recovery policies, and invariant checks. Record the full action trace so failures can be replayed and scored by trajectory, not remembered as folklore.
