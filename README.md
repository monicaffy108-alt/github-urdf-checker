# github-urdf-checker

A TraeWork skill that checks whether a GitHub repository contains URDF (Unified Robot Description Format) files and reports their paths.

## Description

This skill automatically guides the query process when you ask whether a GitHub repository has URDF files — including visiting the repository page, searching the file tree, checking common URDF paths (`urdf/`, `*_description/`, `Simulation/`, etc.), and handling cases where URDF files are in other associated repositories. Finally, it summarizes all URDF file paths and related information (xacro, MJCF, MoveIt configs, etc.).

## Features

- Quickly determines if a GitHub repo contains URDF files
- Searches common URDF locations automatically
- Detects `.urdf`, `.urdf.xacro`, and `.xacro` files
- Identifies related resources (meshes, MJCF/MuJoCo models, MoveIt configs, ROS packages)
- Handles URDF files in separate associated repositories

## Usage

This skill is designed for use with TraeWork. Install it by placing the `SKILL.md` file in your TraeWork skills directory.

Once installed, simply ask questions like:
- "Does this GitHub repo have URDF files?"
- "Find robot description files in [repo URL]"
- "Check if [repo] has URDF for robot arm models"

## File Structure

```
github-urdf-checker/
├── SKILL.md      # Skill definition for TraeWork
└── README.md     # This file
```

## License

MIT
