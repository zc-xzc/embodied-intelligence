# 4. Humanoid Whole-Body Control Datasets

> Survey date: 2026-06. Sources: arXiv + Semantic Scholar + CrossRef, covering 40+ papers/systems.

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

## 4.6 Proposed Data-Collection Tasks

5–6 composite tasks, each 2–5 minutes, 3–5 scene variants, 30–50 episodes per variant:

1. Enter → pick → return → place (localization benchmark)
2. Open/close cabinet door, pick and place
3. Push/pull heavy object transport
4. Pick from ground → turn → place
5. Dynamic human-robot object handover

## 4.7 Data Format & Scale

- Format: LeRobot / HDF5.
- Total scale: 500–1500 trajectories, 50–80 hours.

## 4.8 References

- UniFolm WBT; TWIST2; Humanoid Everyday; Fourier ActionNet; SENTINEL; Dexora; CLONE; HumanoidMimicGen; RoboMIND 2.0; ALMI-X; OmniH2O; TWIST; ZeroWBC; DemoHLM; OpenLET; WholeBodyVLA; GRAIL.
