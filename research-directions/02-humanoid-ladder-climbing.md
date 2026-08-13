# 2. Humanoid Ladder Climbing

## 2.1 Research Problem

Ladder climbing is a challenging whole-body locomotion task requiring **coordinated hand-foot coupling, high contact forces, and precise contact placement**. It serves as a strong benchmark for humanoid control beyond flat-ground or staircase locomotion.

**Task taxonomy** (difficulty increases):

- Inclined ladders (55°–75°)
- Vertical ladders (90°)
- Stairs (distinct task, not the core target here)

**Key observation**: vertical-ladder climbing with vision-based full autonomy on real hardware has **no published precedent**.

## 2.2 Related Work

### LadderMan
- arXiv:2606.05873 (2026-06), Amazon FAR + UC Berkeley / Stanford / CMU / USC, platform Unitree G1.
- Achieves **autonomous vision-closed-loop climbing of 55°–75° inclined ladders**, zero-shot sim2real.
- Method: mixed action tracking → multiple climbing experts → distillation into a unified depth-vision-based motion policy (imitation + RL).
- **Explicitly does not extend to vertical ladders.**

### Industrial / research humanoids
- Industrial humanoids (Tiangong, Xingdong, Fourier, Unitree, etc.) demonstrate **staircase** climbing, not ladder climbing.

## 2.3 Gap / Novelty

Vertical ladder (90°) + vision + full autonomy + real hardware = **no public precedent** → the differentiation opportunity.

## 2.4 Technical Approach

### Route A (main): human-demonstration-driven
Human demonstration (VR + motion capture) → motion retargeting → imitation learning + RL.

- **Stage 2**: explicit rung / grasp-point detection module for contact placement.
- **Excluded**: pure end-to-end vision RL (Route C); pure contact-planned MPC (Route B).

### Data collection
- **Devices**: Pico VR headset + Xsens MVN motion-capture suit (17+ IMU nodes + 6DoF head + optional hand tactile), 60–240 Hz.
- **Calibration / sync**: time synchronization (NTP/PTP, <10 ms), T-pose calibration, GMR-type IK retargeting, hand-grasp-specific retargeting rules.
- **Storage**: BVH / NPZ.
- **Three usages**:
  1. Reward shaping only (MVP, most robust)
  2. Policy input (not recommended for MVP)
  3. Behavior-cloning initialization (to accelerate)

### MVP
- Reproduce **75° inclined ladder**.
- Simulation state ground truth (not vision); fixed ladder parameters; safety tether.
- Vision / parameter randomization / vertical-ladder extension deferred to later stages.

## 2.5 System Architecture

```
Simulation training (domain randomization)
  → Perception & state estimation (point cloud / image)
    → Learned whole-body control (policy distillation / training)
      → Optimized joint commands
        → Safety & actuation
          → Real environment
```

**Teacher–student distillation**: human demo → reward shaping → teacher policy (privileged-state RL) → student policy (onboard vision only) → real deployment with safety tether.

## 2.6 Challenges / Open Problems

1. **Hand-grasping sim-to-real gap**: friction, compliance, and grasp-force simplification in simulation.
2. **Dexterous-hand hardware reliability**.
3. **Failure recovery and safety** in the 75° → 90° transition.
4. **Is a human reference trajectory necessary?** RL + reward shaping + curriculum may learn without an explicit reference — an open scientific question.

## 2.7 References

- LadderMan — arXiv:2606.05873
