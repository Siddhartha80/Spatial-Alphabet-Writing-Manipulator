# Spatial Alphabet Writing Manipulator

A MATLAB simulation of a spatial robotic manipulator that traces the characters **A, T, H, L, E, and F**. Enter a character at the command prompt and the selected model computes joint-space motion for the character's Cartesian waypoints, then visualizes the motion and drawing path.

> **Scope:** This repository contains simulation scripts. It does not provide a hardware driver or a safety-rated controller.

## Features

- Select a supported character interactively; uppercase and lowercase input are accepted.
- Explore two manipulator configurations:
  - `FinalMain.m` — a 3-link revolute (`RRR`) model.
  - `FinalPrism.m` — a 4-joint prismatic (`PPPP`) model.
- Use inverse kinematics to map Cartesian waypoints to joint configurations.
- Use `jtraj` to generate trajectories between successive configurations and visualize them with Robotics Toolbox for MATLAB.

## Architecture

The scripts follow the same high-level flow: select a manipulator model, enter a character, map its predefined waypoints to joint configurations, generate motion, and view the result. The two MATLAB files are independent entry points and use different robot configurations and coordinate ranges.

See the [architecture diagram and component notes](docs/architecture.md).

## Requirements

- MATLAB.
- Peter Corke's Robotics Toolbox for MATLAB, including the `Link`, `SerialLink`, `transl`, `jtraj`, and plotting/kinematics functions used by the scripts.

The toolbox must be installed and available on the MATLAB path before running either script.

## Run

1. Clone or download this repository and open its directory in MATLAB.
2. Make sure Robotics Toolbox for MATLAB is on the MATLAB path.
3. Run one of the scripts:

   ```matlab
   FinalMain
   ```

   or

   ```matlab
   FinalPrism
   ```

4. At the prompt, enter `A`, `T`, `H`, `L`, `E`, or `F`. Lowercase letters are also accepted. Enter any other response to exit.

`FinalMain.m` opens the revolute model's teaching interface before accepting input. Both scripts visualize the robot motion; the character strokes are plotted in MATLAB figures.

## Repository contents

| Path | Description |
| --- | --- |
| `FinalMain.m` | Interactive character drawing using a three-revolute-joint serial manipulator. |
| `FinalPrism.m` | Interactive character drawing using a four-prismatic-joint serial manipulator. |
| `docs/architecture.md` | Architecture diagram and a description of the simulation flow. |

## Notes and limitations

- The character paths are predefined waypoint sequences in the MATLAB scripts; this is not a general font-rendering system.
- The two scripts model different mechanisms and use different coordinate conventions and workspace scales. Choose the entry point you want to explore.
- Results depend on the installed MATLAB and Robotics Toolbox versions and on the target points being reachable by the selected model.
- Review and validate all motion before adapting the simulation to physical hardware. No physical robot interface is included.

## Contributing

For changes, please keep the entry-point instructions and character support list in sync with the MATLAB scripts. Include the MATLAB/toolbox versions and any reproducible steps when reporting a problem.

