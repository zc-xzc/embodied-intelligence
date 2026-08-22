# 4. Humanoid Whole-Body Control Datasets

> Survey date: 2026-06 (refined 2026-08). Sources: arXiv + Semantic Scholar + CrossRef, covering 40+ papers/systems.

## 4.1 Survey Scope

Overview of open datasets for whole-body humanoid control, focusing on platform, scale, task coverage, and teleoperation availability.

## 4.2 Tier-1 Datasets

| Dataset | Date | Venue | Platform | Scale | Core Limitation |
|---------|------|-------|----------|-------|-----------------|
| UniFolm WBT (Unitree) | 2026.03 | — | G1 (41 joints) | ~340 h / 1.89 M trajectories | Tens of seconds per episode; teleoperation not open-sourced |
| TWIST2 (Stanford) | 2025.11 | ICRA 2026 Oral | G1 + custom neck | ~100 days / 15 min | Few task types (3–4) |
| Humanoid Everyday (USC + TRI) | 2025.10 | arXiv | G1 / H1 | 10.3 k / 260 tasks | No long-horizon tasks |
| Fourier ActionNet | 2025.03 | — | GRx series | 30 k+ / 200 tasks | Non-G1, non-whole-body |
| SENTINEL | 2025.11 | CVPR 2026 | G1 (simulation) | 200 k trajectories | Simulation only |
| Dexora | 2026 | ICRA 2026 | 36-DoF dual arm | 12.2 k / 40.5 h | No lower body, non-G1 |

## 4.3 Tier-2 Datasets

CLONE (CoRL 2025), ZeroWBC, DemoHLM, HumanoidMimicGen (ICRA 2026 Workshop Best Paper), RoboMIND 2.0, OpenLET, 10KhRealOmni, ALMI-X (NeurIPS 2025), WholeBodyVLA, GRAIL.

## 4.4 Publication Verification

- TWIST2 → ICRA 2026 Oral
- CLONE → CoRL 2025 (PMLR)
- SENTINEL → CVPR 2026
- ALMI → NeurIPS 2025
- TWIST → CoRL 2025
- OmniH2O → CoRL 2025
- Dexora → ICRA 2026
- HumanoidMimicGen → ICRA 2026 Workshop Best Paper

## 4.5 Gap Analysis

1. **Long-horizon composite tasks (2–5 minutes) are missing.** Existing datasets are "short and many"; none are "long and focused".
2. **One-stop open-source kit** — teleoperation suite + long-horizon dataset + training baseline — is missing. Unitree has data without teleoperation; TWIST2 has teleoperation but few tasks.
3. **Whole-body motion-chain gap (2026-08).** A cross-dataset comparison of full-body teleoperation datasets reveals a common blind spot: almost all are *standing, upper-body hand-operation* records without locomotion:

| Dataset | Task volume | Strength | Missing motion |
|---------|-------------|----------|----------------|
| Humanoid Everyday | 260 tasks | large task count, precise standing manipulation | no locomotion; standing, upper-body only |
| UniFolm WBT | ~340 h / 1.89 M trajectories | large scale, real-robot | tens of seconds per episode; no continuous motion chain |
| OmniH2O | 6 tasks | first whole-body dataset | fixed base, no walking |
| HumanPlus | — | open hardware, shadow-mode teleoperation | upper-body focus; no lower-body coordination |
| TWIST2 | — | very high collection throughput (ICRA 2026 Oral) | only 3–4 task types; not released as a dataset |
| CLONE | — | long-horizon teleoperation with closed-loop correction | method paper; no dataset release |
| BifrostUMI | — | operator-free collection (5 keypoints) | qualitative results only; no quantitative evaluation |
| SENTINEL | 200 k trajectories | end-to-end language→action (CVPR 2026) | simulation-only; no teleoperation |
| DemoHLM | — | single-demonstration generalization | simulation-only |

   **No existing dataset combines walking + squatting + overhead reach + kneeling into a continuous full-body motion chain.** The differentiation lever is therefore motion diversity (complete whole-body motion chains) rather than cognitive complexity.

## 4.6 Proposed Data-Collection Tasks

Design principle (refined 2026-08): each task has few steps (2–5) and minimal cognitive judgment; the emphasis is on motion-chain completeness and variety — full-height coverage (floor → desk → high shelf) and mixed locomotion (walk / squat / kneel / pivot). Task count is expanded by *scene × motion-mode* combinations instead of cognitive difficulty, keeping collection reliable while enriching scene coverage.

18 tasks across four motion modes (2–4 min per episode):

- **Ground interaction G1–G5**: squat-to-pick from floor → walk → place at desk / low shelf / high shelf; includes a push-sweep task and a box-lid closing task.
- **Height transition H1–H5**: full vertical transfer inside a rack — low→high, high→low, and layer-by-layer descent.
- **Mobile operation L1–L4**: short round-trip, obstacle-avoidance walking, walk→stop→squat→continue, triangular multi-station path.
- **Kneeling K1–K2**: kneel→pick→stand and kneel→organize→stand; **domain-first** (no published dataset covers kneeling); success samples capped at ≤5 per task to limit hardware wear.

Motion coverage in the core 14-task set: squat in 8/14 (57%), walking in 10/14 (71%), overhead reach above 1.5 m in 5/14, kneeling in 2/14.

## 4.7 Evaluation Design & Collection Spec

- Per task: 5 recorded groups, each a complete 2–4 min closed-loop episode, including success and failure samples (failures kept in full, not truncated).
- Per-trajectory annotation: success/failure binary label, failure sub-reason, natural-language task description.
- Dual-view capture: head-fixed camera baseline (640×480) + active-vision gimbal head (experimental group; per-task count downgraded on hardware instability).
- Third-person side camera for demonstration footage.
- Gripper capability boundary: grasp / carry / push–pull / flip only — no fine manipulation (screwing, peg-in-hole, key press).
- Collection priority: a first batch of 10 core tasks.

## 4.8 Data Format & Scale

- Format: LeRobot / HDF5.
- Total scale: 500–1500 trajectories, 50–80 hours.

## 4.9 References

- UniFolm WBT; TWIST2; Humanoid Everyday; Fourier ActionNet; SENTINEL; Dexora; CLONE; HumanoidMimicGen; RoboMIND 2.0; ALMI-X; OmniH2O; TWIST; ZeroWBC; DemoHLM; OpenLET; WholeBodyVLA; GRAIL.
