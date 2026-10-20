---
name: "github-urdf-checker"
description: "Checks whether a GitHub repository contains URDF files and reports their paths. Invoke when the user asks if a GitHub repo has URDF, or wants to find robot description files in a repository."
---

# 🔍 GitHub URDF 检测器

> 快速检测指定 GitHub 仓库中是否包含 URDF 文件，并汇总所有文件路径

---

## 触发条件

当用户询问以下话题时激活本技能：

- 🔍 "这个 GitHub 仓库有 URDF 文件吗？" / "Does [repo] have URDF files?"
- 🤖 想在 GitHub 仓库中查找机器人模型 / 描述文件
- 🦾 对比机械臂 / 机器人平台，需要确认是否有 URDF
- 📦 查找 xacro、MJCF、MoveIt 配置等机器人相关资源
- 🌐 查询关联仓库（如独立的 `*_description` 仓库）中的 URDF

---

## 工作流程

### 第 1 步：确认仓库存在
使用 `WebFetch` 访问仓库主页，确认仓库存在并获取概览信息。
- 如果返回 404 或组织名不对（比如用户写的是 `Seeed-Studio` 但实际仓库在 `Seeed-Projects` 下），用 `WebSearch` 搜索正确的仓库地址。

### 第 2 步：搜索文件树
使用 `WebFetch` 访问仓库文件列表页面，检查常见 URDF 位置。

**自动检查的路径**：

| 路径模式 | 说明 |
|---------|------|
| `urdf/` | 最常见的 URDF 目录 |
| `*_description/` | ROS 风格的描述包 |
| `description/` | 通用描述目录 |
| `robots/` | 机器人模型目录 |
| `meshes/` | 网格模型（通常和 URDF 一起） |
| `Simulation/` | 仿真相关目录 |
| `ros/` / `ros2/` | ROS 相关目录 |
| `assets/` | 资源目录（Isaac/MuJoCo 常见） |

**检查的文件扩展名**：
- `.urdf` — 标准 URDF 文件
- `.urdf.xacro` — URDF Xacro 文件
- `.xacro` — Xacro 源文件

### 第 3 步：WebSearch 兜底
如果文件树视图不完整或仓库太大，使用 `WebSearch` 作为补充。
- 搜索格式：`github <owner> <repo> urdf file`
- 查找 ROS 索引页、wiki 文档或社区仓库中是否托管了 URDF

### 第 4 步：清晰汇报结果
按照以下结构输出：

```
🔍 URDF 文件检测结果
━━━━━━━━━━━━━━━━━━━━

📦 仓库：<owner>/<repo>

✅ 检测结果：找到 N 个 URDF 相关文件

📄 URDF 文件列表：
  • path/to/robot1.urdf
  • path/to/robot2.urdf.xacro

📎 关联资源：
  • 网格模型（meshes）：path/to/meshes/
  • MJCF / MuJoCo：path/to/model.xml
  • MoveIt 配置：path/to/moveit_config/
  • ROS 包：path/to/package.xml

🔗 关联仓库：
  • 如果 URDF 在独立的 *_description 仓库中，在此列出并附链接

💡 备注：
  • 机器人型号变体信息（5DOF/6DOF、RS/DM、新旧校准等）
```

---

## 常见路径模式速查表

| 仓库类型 | 典型 URDF 路径 |
|---------|---------------|
| ROS 工作区 | `<pkg>_description/urdf/<robot>.urdf.xacro` |
| 硬件项目 | `Simulation/<model>/<robot>.urdf` |
| 独立描述包 | `urdf/` 和 `meshes/` 并列 |
| Isaac / MuJoCo 项目 | `assets/` 或与 MJCF 文件同目录 |
| 通用项目 | `description/`、`robots/`、`ros/` |

---

## 注意事项

> 💡 URDF 文件可能使用 `.urdf` 或 `.urdf.xacro` 扩展名
>
> 💡 有些项目只提供 xacro 源文件——URDF 在构建时才生成
>
> 💡 注意区分**主仓库**和包含 URDF 的**关联仓库**
>
> 💡 引用来源时使用 `[$TRAE_REF](url)` 格式

---

## 技能元信息

- **技能名称**：github-urdf-checker
- **适用平台**：全平台（通过网页访问）
- **支持文件**：.urdf / .urdf.xacro / .xacro / MJCF / MoveIt
- **作者**：monicaffy108-alt
- **协议**：MIT
