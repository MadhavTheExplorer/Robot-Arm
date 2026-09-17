# Robotic Charging Challenge

A six-degree-of-freedom robotic charging-station prototype developed for an Inter IIT preparation challenge. The project combines robot kinematics and trajectory planning, charging-port detection, CAD, and MATLAB/Simscape simulation.

## Outcomes

- Characterizes the arm workspace, plans joint-space and Cartesian trajectories, and evaluates motion and torque.
- Uses an LED-marked charging socket and vision pipelines to estimate charging-port keypoints and pose.
- Includes a Simscape/Simulink model for executing planned trajectories and visualizing the charging sequence.
- Contains CAD assemblies, component geometry, and manufacturing-oriented assets for the charging-station concept.

The design assumes a custom charging socket, servo actuation, negligible friction in torque calculations, and four LEDs at the charging socket corners. The documented estimated charging-cycle energy is approximately 70 J.

## Repository Map

| Area | Location | Contents |
| --- | --- | --- |
| Motion planning and kinematics | `Robot-Arm-Control/` | MATLAB scripts for DH modeling, forward/inverse kinematics, collision checks, trajectories, torque calculations, and plots. Start with `main.m`. |
| Vision | `CV/` | Charging-port detection, monocular/stereo estimation, and the trained YOLO weight file `best.pt`. |
| Simulation | `Simscape Simulation/` | Simscape/Simulink models and supporting geometry for trajectory execution and visualization. |
| Robot model and assets | `Robot-Arm/` | Robot description, planning data, and MATLAB support files. |
| ROS integration | `ros packages/` | ROS-oriented copies of the robot-control assets and geometry. |
| Analysis | `Final_torque/`, `Joint Torque/` | Torque-related calculations and outputs. |

## Setup

The project was developed as a multi-tool prototype. Run the parts relevant to your goal rather than expecting a single end-to-end command.

### Planning and Simulation

1. Install MATLAB with Simulink and Simscape Multibody.
2. Open `Robot-Arm-Control/main.m` and set MATLAB's current folder to `Robot-Arm-Control/`.
3. Run `main.m` to initialize robot parameters, collision boxes, and planning dependencies.
4. For the Simscape workflow, set the initial and target poses in the waypoint-generation script within `Simscape Simulation/`, then open the corresponding `.slx` model.

### Computer Vision

1. Use Python with PyTorch and the Ultralytics YOLOv5 dependencies.
2. Load `CV/best.pt` as a custom YOLOv5 model.
3. Use the vision scripts in `CV/` for keypoint detection and the monocular or stereo estimation experiments.

## Assets And Storage

CAD, simulation geometry, MATLAB data, and model weights are included because they are required to reproduce or inspect the prototype. Future versions of `.mat`, `.pt`, `.stl`, `.step`, SolidWorks, Simulink, `.wrl`, `.x3d`, and video files are configured for Git LFS through `.gitattributes`.

Existing assets remain in the repository's historical Git objects. Moving them to LFS would rewrite published history, so it is intentionally deferred until a separate migration and release plan is approved. Large release-ready models, videos, and generated result bundles should be published as GitHub Release assets instead of committed as new Git blobs.

## Project Metadata

The machine-readable portfolio entry is in `.explorer/project.yml`. It classifies this as an archived hardware project in the `robotics-and-autonomy` family, with robotics, motion planning, computer vision, and control as its fields.

