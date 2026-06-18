# WdArpgFramework

基于 **Godot 4.6** 的 ARPG 游戏框架项目，采用**组件式架构**与**数据驱动**设计理念，提供灵活可扩展的游戏开发基础。

## 特性

- **组件式架构**: 基于 Godot 节点系统，将游戏逻辑拆分为独立的可组合组件
- **数据驱动**: 通过配置数据驱动游戏行为，实现逻辑与数据分离
- **完整功能模块**: 包含角色、战斗、任务、装备、AI等核心系统
- **类型安全**: 使用 GDScript 的类型系统，提供良好的开发体验
- **模块化设计**: 各模块低耦合，易于扩展和替换

## 技术栈

- **引擎**: Godot Engine 4.6 (GDScript)
- **数据格式**: JSON / YAML (配置数据)
- **状态管理**: 状态机模式
- **渲染**: Godot 4.x 渲染管线

## 核心模块

### 角色系统 (Character System)
- 角色属性管理（生命值、法力值、攻击力等）
- 组件化角色能力（移动、攻击、技能）
- 角色状态机（待机、移动、攻击、受伤、死亡）

### 战斗系统 (Combat System)
- 伤害计算与减免
- 命中与暴击机制
- 技能冷却与消耗
- 战斗日志与反馈

### 任务系统 (Quest System)
- 任务条件与目标
- 任务状态管理
- 任务奖励系统
- 任务对话与剧情

### 装备系统 (Equipment System)
- 装备属性与插槽
- 装备强化与镶嵌
- 装备掉落与收集
- 背包管理

### AI系统 (AI System)
- 行为树框架
- 巡逻与追击
- 仇恨系统
- 智能决策

### 数据管理 (Data Management)
- 配置数据加载
- 数据持久化（存档）
- 对象池管理
- 资源加载优化

## 项目结构

```
WdArpgFramework/
├── addons/                    # 插件目录
│   └── ...
├── assets/                    # 资源目录
│   ├── animations/            # 动画资源
│   ├── audio/                 # 音频资源
│   ├── materials/             # 材质资源
│   ├── scenes/                # 场景文件
│   ├── textures/              # 纹理资源
│   └── ...
├── components/                # 组件目录
│   ├── character/             # 角色组件
│   │   ├── CharacterAttribute.gd
│   │   ├── CharacterMovement.gd
│   │   └── ...
│   ├── combat/                # 战斗组件
│   │   ├── CombatController.gd
│   │   ├── DamageSystem.gd
│   │   └── ...
│   ├── ai/                    # AI组件
│   │   ├── BehaviorTree.gd
│   │   ├── AIController.gd
│   │   └── ...
│   └── ...
├── data/                      # 配置数据目录
│   ├── characters/            # 角色配置
│   ├── skills/                # 技能配置
│   ├── items/                 # 物品配置
│   ├── quests/                # 任务配置
│   └── ...
├── systems/                   # 系统目录
│   ├── GameManager.gd         # 游戏管理器
│   ├── InputSystem.gd         # 输入系统
│   ├── UISystem.gd            # UI系统
│   ├── EventSystem.gd         # 事件系统
│   └── ...
├── utils/                     # 工具目录
│   ├── DataLoader.gd          # 数据加载器
│   ├── MathUtils.gd           # 数学工具
│   ├── EventBus.gd            # 事件总线
│   └── ...
├── scenes/                    # 场景目录
│   ├── Main.tscn              # 主场景
│   ├── Game.tscn              # 游戏场景
│   ├── UI/                    # UI场景
│   └── ...
└── project.godot              # 项目配置
```

## 快速开始

### 环境要求

- Godot Engine 4.6 或更高版本
- Git (版本控制)

### 安装步骤

1. 克隆项目到本地：
   ```bash
   git clone https://github.com/your-username/WdArpgFramework.git
   ```

2. 使用 Godot 4.6 打开项目：
   - 启动 Godot Engine
   - 点击 "Import" 选择项目目录
   - 选择 `project.godot` 文件

3. 运行项目：
   - 点击 "Play" 按钮或按 `F5` 键

## 设计理念

### 组件式架构

框架采用基于 Godot 节点系统的组件化设计，每个功能模块作为独立组件存在，可自由组合和替换。

```gdscript
# 角色节点结构示例
extends CharacterBody3D

@onready var attribute = $Attribute
@onready var movement = $Movement
@onready var combat = $Combat
@onready var animation = $AnimationPlayer
```

### 数据驱动

游戏数据通过配置文件管理，逻辑层只负责读取和处理数据，实现数据与逻辑的解耦。

```json
{
  "id": "warrior",
  "name": "战士",
  "base_attributes": {
    "max_hp": 1000,
    "max_mp": 200,
    "attack": 50,
    "defense": 30
  },
  "skills": ["slash", "shield_bash", "rage"]
}
```

## 使用指南

### 创建角色

1. 在 `data/characters/` 目录下创建角色配置文件
2. 使用 `CharacterFactory` 创建角色实例
3. 添加所需组件（属性、移动、战斗等）

### 创建技能

1. 在 `data/skills/` 目录下创建技能配置文件
2. 实现技能逻辑组件
3. 注册到技能系统

### 添加任务

1. 在 `data/quests/` 目录下创建任务配置文件
2. 设置任务目标和条件
3. 绑定任务奖励

## 开发规范

- **命名规范**: 使用 PascalCase 命名类和节点，使用 snake_case 命名变量和方法
- **代码风格**: 遵循 Godot 官方 GDScript 风格指南
- **组件设计**: 每个组件职责单一，避免跨组件直接调用
- **数据管理**: 配置数据统一存放在 `data/` 目录，使用 `DataLoader` 加载

## 贡献

欢迎提交 Issue 和 Pull Request！

### 开发流程

1. Fork 项目
2. 创建功能分支 (`git checkout -b feature/your-feature`)
3. 提交代码 (`git commit -m 'Add some feature'`)
4. 推送到分支 (`git push origin feature/your-feature`)
5. 创建 Pull Request

## 许可证

MIT License - 详见 [LICENSE](LICENSE)

## 联系方式

如有问题或建议，欢迎通过以下方式联系：

- GitHub Issues: [https://github.com/your-username/WdArpgFramework/issues](https://github.com/your-username/WdArpgFramework/issues)

---

*Built with Godot Engine 4.6*
