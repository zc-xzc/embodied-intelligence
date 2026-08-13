# 3. Active Vision for Humanoid Teleoperation

## 3.1 Research Problem

Humanoid teleoperation suffers from **limited camera field of view (FOV)**. A fixed camera cannot simultaneously observe the workspace, the manipulated object, and the operator's own body (e.g., the feet or the table below the field of view), causing collisions during teleoperation.

**Active vision** — mounting the camera on a head-like gimbal driven by the operator's head motion — provides **immersive, natural viewpoint control** ("head moves, view moves"), a lightweight alternative to multi-camera rigs.

## 3.2 System Overview

| Component | Specification |
|-----------|---------------|
| Head tracking | PICO 4 (6DoF) |
| Active head mechanism | **2-DoF** gimbal: yaw/pan + pitch/tilt, dual-axis STS3032 servos |
| Camera | Intel RealSense D415 |
| Mapping | VR head pose → gimbal joint commands (view mapping) |

All active-vision head mechanisms are **2-DoF**. (Historical STL filenames containing "3dof" are non-standard naming only, not three-degree-of-freedom mechanisms.)

## 3.3 Technical Components

- **Head-to-gimbal mapping and calibration**: mapping operator head pose to gimbal yaw/pitch with correct reference frames.
- **Servo control & tuning**: STS3032 servo control, smooth trajectory following.
- **Latency budget**: end-to-end latency between head motion and rendered view — a key immersion factor.
- **Viewpoint selection**: how the active view contributes to whole-body awareness.

## 3.4 Applications

- **Teleoperated manipulation** with natural, operator-driven viewpoint.
- **Whole-body collision avoidance**: observe feet/table/workspace on demand.
- **Active perception**: attention-driven viewpoint for inspection or grasp.

## 3.5 Open Problems

- **End-to-end latency optimization** (head tracking → control → video loopback).
- **Gaze/attention-based active vision**, beyond head motion.
- **Viewpoint control in occluded / confined spaces**.
- **Integration with force feedback**: haptic + active vision combined feedback.
- **Active vision in autonomous (non-teleop) settings** as a perception modality.

## 3.6 References

- Platform assets and hardware documentation are maintained in the `robot_platform` repository.
