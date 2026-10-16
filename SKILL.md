---
name: "github-urdf-checker"
description: "Checks whether a GitHub repository contains URDF files and reports their paths. Invoke when the user asks if a GitHub repo has URDF, or wants to find robot description files in a repository."
---

# GitHub URDF Checker

Quickly determines whether a given GitHub repository contains URDF (Unified Robot Description Format) files and summarizes their locations.

## When to Invoke

- User asks "Does [repo URL] have URDF?" or similar phrasing.
- User wants to find robot model / description files in a GitHub repository.
- User is comparing robot arms / platforms and needs to know URDF availability.

## Workflow

1. **Fetch the repo root page** with `WebFetch` to confirm the repo exists and get an overview.
   - If the repo URL returns 404 or is under a different org (e.g. user typed `Seeed-Studio` but the repo is under `Seeed-Projects`), search for the correct repo using `WebSearch`.

2. **Search the file tree** using `WebFetch` on the repo's file listing (e.g. `https://github.com/<owner>/<repo>/find/main` or `tree/main` for key subdirectories).
   - Common URDF locations to check: `urdf/`, `description/`, `robots/`, `meshes/`, `Simulation/`, `*_description/`, `ros/`, `ros2/`.
   - Also check for `.xacro`, `.urdf.xacro`, `.urdf` file extensions.

3. **Use WebSearch as backup** if the file tree view is incomplete or the repo is large.
   - Query pattern: `github <owner> <repo> urdf file`
   - Look for ROS index pages, wiki docs, or community repos that host the URDF.

4. **Report findings clearly:**
   - State **yes / no** directly.
   - List each URDF file with its **full path** inside the repo.
   - Note the robot model variant (e.g. 5DOF / 6DOF, RS / DM, old calibration / new calibration).
   - Mention related resources: mesh files, MJCF / MuJoCo models, xacro files, MoveIt configs, ROS packages.
   - If the URDF lives in a **different repo** (e.g. a separate `*_description` repo), state that explicitly and link to it.
   - Cite sources using `[$TRAE_REF](url)` format.

## Common Patterns

| Repository Type | Typical URDF Path |
|---|---|
| ROS workspace | `<pkg>_description/urdf/<robot>.urdf.xacro` |
| Hardware project | `Simulation/<model>/<robot>.urdf` |
| Description package | `urdf/`, `meshes/` siblings |
| Isaac / MuJoCo project | may be in `assets/` or alongside MJCF |

## Reminders

- URDF files may use `.urdf` or `.urdf.xacro` extensions.
- Some projects only provide xacro source files — the URDF is generated at build time.
- Always distinguish between the **main repo** and **related repos** that contain URDF.
