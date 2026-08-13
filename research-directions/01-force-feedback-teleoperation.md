# 1. Force-Feedback Teleoperation for Humanoid Robots

## 1.1 Research Problem

Teleoperation is a primary paradigm for collecting human demonstrations and enabling remote manipulation of humanoid robots. Current whole-body humanoid teleoperation systems predominantly use **position/velocity control without force feedback**. This is insufficient for **contact-rich tasks**, where the human operator must perceive forces/torques to act appropriately:

- **Shaving**: excessive force causes injury; the blade must follow the skin surface with gentle, compliant force.
- **Egg grasping**: the operator must feel the shell to avoid crushing.
- **Precision insertion / assembly**: contact forces guide correction.

Force feedback (rendering interaction forces to the operator) is distinct from tactile feedback (pressure/vibration), and force-controlled teleoperation remains immature.

## 1.2 Related Work

| System | Source | Feedback Scope | Force Feedback |
|--------|--------|----------------|----------------|
| UME | arXiv:2606.14218 (2026) | Upper limb, via OpenArm exoskeleton | ✅ torque |
| Glovity | arXiv:2510.09229 (2025) | Hand, haptic glove | ✅ wrench |
| OmniH2O | CoRL 2025 | Whole body | ❌ |
| TWIST2 | ICRA 2026 (Oral) | Whole body + neck | ❌ |
| FACTR 2 | arXiv:2606.12406 (2026) | — | — |
| WT-UMI | arXiv:2606.13232 (2026) | — | — |
| DexTeleop-0 | arXiv:2606.23431 (2026) | — | — |

A cluster of force-feedback teleoperation works appeared around mid-2026 (FACTR 2, WT-UMI, DexTeleop-0). UME demonstrates upper-limb torque feedback; Glovity demonstrates hand-level wrench feedback; whole-body systems (OmniH2O, TWIST2) exist but without force feedback.

## 1.3 Gap / Novelty

- **No system combines whole-body teleoperation with force feedback.** Upper-limb and hand-level feedback exist independently; whole-body motion and force feedback have not been unified.
- **Low-cost force-feedback rendering** (6-axis F/T sensor + a commodity haptic device) has not been systematically benchmarked on contact-rich humanoid tasks.

## 1.4 Proposed Research Directions

### A. End-effector force-feedback rendering (primary)
1. Integrate a **6-axis force/torque (F/T) sensor** at the end-effector of an existing teleoperation platform.
2. Render forces/torques to the operator through an arm/wrist haptic device.
3. Benchmark **contact-rich tasks with vs. without force feedback** (ablation).
   - Reference improvement: Glovity reports page-turning success improving from 48% to 78% with feedback.

### B. Foot force feedback (whole-body coupling)
- Integrate foot-ground contact force feedback to support locomotion-contact coupling during whole-body tasks.

### C. Whole-body force-sensing dataset
- Collect synchronized whole-body motion + end-effector/contact force/torque data as a new dataset resource.

### D. Bilateral control theory
- Stability and transparency analysis of bilateral teleoperation extended to whole-body, multi-limb systems.

## 1.5 Evaluation Design

- **Task suite** (contact-rich): page turning, shaving, egg grasping, precision insertion.
- **Metrics**: task success rate, completion time, force accuracy / force error, peak contact force, operator workload (validated questionnaire), ablation with vs. without feedback.

## 1.6 Open Problems

- Hardware maturity / cost / durability of force-feedback devices.
- F/T sensor noise, calibration drift, and mounting compliance.
- Rendering realism vs. stability trade-off (transparency, passivity / Z-width).
- Communication latency and its effect on force transparency.
- Sim-to-real of force feedback (rendering in simulation for training).

## 1.7 References

- UME — arXiv:2606.14218
- Glovity — arXiv:2510.09229
- OmniH2O — CoRL 2025
- TWIST2 — ICRA 2026 Oral
- FACTR 2 — arXiv:2606.12406; WT-UMI — arXiv:2606.13232; DexTeleop-0 — arXiv:2606.23431
