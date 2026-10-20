<div align="center">

# 🔍 GitHub URDF Checker

> **一键检测 GitHub 仓库中的 URDF 机器人模型文件**
>
> _A TRAE Skill that finds URDF files in any GitHub repository in seconds_

[![URDF](https://img.shields.io/badge/URDF-Robot%20Description-blue?style=for-the-badge&logo=ros)](http://wiki.ros.org/urdf)
[![GitHub](https://img.shields.io/badge/GitHub-Repo%20Scanner-lightgrey?style=for-the-badge&logo=github)](https://github.com/monicaffy108-alt/github-urdf-checker)
[![TRAE Skill](https://img.shields.io/badge/TRAE-Skill-orange?style=for-the-badge)](https://github.com/monicaffy108-alt)
[![License](https://img.shields.io/github/license/monicaffy108-alt/github-urdf-checker?style=for-the-badge)](LICENSE)

[English](#-what-it-does) · [中文说明](#-功能介绍)

</div>

---

## ✨ What It Does

Tired of manually browsing GitHub repos looking for URDF files? This skill automates the entire process — just give it a repo URL, and it finds all robot description files for you.

| | Feature | Description |
|---|---|---|
| 🔍 | **Smart Detection** | Scans common URDF locations automatically |
| 📁 | **Multi-format** | Supports `.urdf`, `.urdf.xacro`, `.xacro` files |
| 🔗 | **Related Resources** | Finds meshes, MJCF/MuJoCo models, MoveIt configs, ROS packages |
| 🗂️ | **Cross-repo** | Handles URDF files in separate `*_description` repos |
| ⚡ | **Instant Results** | No cloning needed — works entirely via web |

---

## 🎯 Supported File Types

| File Type | Extension | Detected |
|-----------|-----------|:--------:|
| URDF | `.urdf` | ✅ |
| URDF Xacro | `.urdf.xacro` | ✅ |
| Xacro | `.xacro` | ✅ |
| Mesh files | `.stl`, `.dae`, `.obj` | ✅ |
| MJCF / MuJoCo | `.xml`, `.mjcf` | ✅ |
| MoveIt config | `moveit_config/` | ✅ |
| ROS packages | `package.xml` | ✅ |

---

## 📂 Common URDF Locations

The skill checks these typical paths automatically:

| Repository Type | Typical URDF Path |
|---|---|
| ROS workspace | `<pkg>_description/urdf/<robot>.urdf.xacro` |
| Hardware project | `Simulation/<model>/<robot>.urdf` |
| Description package | `urdf/`, `meshes/` siblings |
| Isaac / MuJoCo project | `assets/` or alongside MJCF files |
| General | `description/`, `robots/`, `ros/`, `ros2/` |

---

## 🚀 Quick Start

### Prerequisites
- TRAE Workspace with web access enabled

### Installation
1. Clone or download this skill
2. Place it under `.trae/skills/github-urdf-checker/` in your workspace
3. Restart TRAE or reload skills

### Usage
Just ask TRAE:
```
"这个 GitHub 仓库里有 URDF 文件吗？"
"帮我找找 [repo URL] 里的机器人描述文件"
"检查一下 [repo] 有没有机械臂的 URDF"
"Does this repo have URDF files?"
"Find robot description files in [repo URL]"
```

---

## 📁 File Structure

```
github-urdf-checker/
├── 📄 README.md      # This file — you're reading it!
└── 📄 SKILL.md       # Skill definition for TRAE platform
```

---

## 🌟 Why This Skill?

> Finding URDF files in a GitHub repo shouldn't require cloning the entire thing.
> This skill saves you minutes per repo —
> **paste a URL, get all robot model paths instantly.**

---

## 📄 License

[MIT](LICENSE) © monicaffy108-alt

---
---

# 🔍 GitHub URDF 检测器

> **一键扫描 GitHub 仓库，快速定位 URDF 机器人模型文件**
>
> _一款能在任意 GitHub 仓库中自动查找 URDF 文件的 TRAE 技能_

---

## ✨ 功能介绍

还在手动翻 GitHub 仓库找 URDF 文件？这个技能帮你全自动搞定——给个仓库链接，所有机器人描述文件立刻出现在你面前。

| | 功能 | 说明 |
|---|---|---|
| 🔍 | **智能检测** | 自动扫描常见 URDF 存放路径 |
| 📁 | **多格式支持** | 支持 `.urdf`、`.urdf.xacro`、`.xacro` 文件 |
| 🔗 | **关联资源识别** | 自动发现 mesh、MJCF/MuJoCo 模型、MoveIt 配置、ROS 包 |
| 🗂️ | **跨仓库检测** | 能找到独立 `*_description` 仓库中的 URDF |
| ⚡ | **秒出结果** | 无需克隆仓库，纯网页方式工作 |

---

## 🎯 支持的文件类型

| 文件类型 | 扩展名 | 支持检测 |
|---------|--------|:--------:|
| URDF | `.urdf` | ✅ |
| URDF Xacro | `.urdf.xacro` | ✅ |
| Xacro | `.xacro` | ✅ |
| 网格模型 | `.stl`、`.dae`、`.obj` | ✅ |
| MJCF / MuJoCo | `.xml`、`.mjcf` | ✅ |
| MoveIt 配置 | `moveit_config/` | ✅ |
| ROS 包 | `package.xml` | ✅ |

---

## 📂 常见 URDF 路径

技能会自动检查这些典型路径：

| 仓库类型 | 典型 URDF 路径 |
|---------|---------------|
| ROS 工作区 | `<pkg>_description/urdf/<robot>.urdf.xacro` |
| 硬件项目 | `Simulation/<model>/<robot>.urdf` |
| 描述包 | `urdf/` 和 `meshes/` 并列 |
| Isaac / MuJoCo 项目 | `assets/` 或与 MJCF 文件同目录 |
| 通用项目 | `description/`、`robots/`、`ros/`、`ros2/` |

---

## 🚀 快速开始

### 前置条件
- TRAE 工作区（已开启网页访问权限）

### 安装方法
1. 克隆或下载本技能
2. 放入工作区的 `.trae/skills/github-urdf-checker/` 目录下
3. 重启 TRAE 或重新加载技能

### 使用方式
直接问 TRAE 就行：
```
"这个 GitHub 仓库里有 URDF 文件吗？"
"帮我找找 [repo URL] 里的机器人描述文件"
"检查一下 [repo] 有没有机械臂的 URDF"
"Does this repo have URDF files?"
"Find robot description files in [repo URL]"
```

---

## 📁 文件结构

```
github-urdf-checker/
├── 📄 README.md      # 本文件 —— 你正在看的就是！
└── 📄 SKILL.md       # TRAE 平台技能定义文件
```

---

## 🌟 为什么做这个技能？

> 找 URDF 文件不该把整个仓库都 clone 下来。
> 这个技能帮你每个仓库省下好几分钟——
> **贴个链接，所有机器人模型路径立刻到手。**

---

## 📄 开源协议

[MIT](LICENSE) © monicaffy108-alt

---

<div align="center">

**如果对你有帮助，别忘了给个 ⭐ Star 哦！**

Made with 🤖 by monicaffy108-alt

</div>
