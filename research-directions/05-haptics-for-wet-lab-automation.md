# 5. Haptics for Wet-Lab Automation

## 5.1 Research Problem

Automating bio-wet-lab operations (pipetting, cell culture, sample handling, micro-injection) requires **force-sensitive, dexterous manipulation**. Teleoperated robots with **force feedback** can preserve human dexterity while scaling throughput and reducing human error. This direction applies whole-body force-feedback teleoperation (see Direction 01) to the wet-lab domain.

## 5.2 Related Work

| Work | Source | Contribution |
|------|--------|--------------|
| Pipette | arXiv:2606.12936 (Tencent + Shanghai AI Lab) | Simulation + benchmark + data augmentation for wet-lab robotics |
| BioProVLA-Agent | arXiv:2605.07306 | Agentic framework for bio experiments |
| AutoBio | ICLR 2026 | New track for bio-automation |

## 5.3 Gap

Existing wet-lab robotics work focuses on **simulation + data**, not on real **force-feedback teleoperation** for delicate wet-lab manipulations. Force feedback × wet-lab automation is an unexplored intersection.

## 5.4 Research Direction

Combine whole-body force-feedback teleoperation (Direction 01) with wet-lab manipulation as an application domain:

- **Candidate tasks**: pipetting, delicate sample handling, micro-injection, cell manipulation.
- **Core capability**: force-sensitive manipulation with operator-in-the-loop feedback.

## 5.5 Open Problems

- **Sterilization / contamination constraints** on hardware design.
- **Sub-mN force-feedback requirements** for delicate biological manipulation.
- **Teleoperation → autonomy transfer**: using teleop demonstrations to bootstrap autonomous policies in the wet-lab.
- **Benchmark design** for wet-lab manipulation success.

## 5.6 References

- Pipette — arXiv:2606.12936
- BioProVLA-Agent — arXiv:2605.07306
