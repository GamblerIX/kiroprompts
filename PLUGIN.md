# Kiro 的 Claude Code 插件

一个 Claude Code 插件，提供遵循 [agentskills.io](https://agentskills.io) 规范的规格驱动开发（Spec-driven Development）技能。

## 安装

### 方法 1：从 GitHub 安装（推荐）

```bash
# 在 Claude Code 中
/plugin marketplace add https://github.com/jasonkneen/kiro
/plugin install kiro-spec-driven@kiro-marketplace
```

### 方法 2：从本地克隆安装

```bash
# 克隆仓库
git clone https://github.com/jasonkneen/kiro.git
cd kiro

# 在 Claude Code 中（从父目录执行）
/plugin marketplace add ./kiro
/plugin install kiro-spec-driven@kiro-marketplace
```

### 安装范围

```bash
# 用户范围（默认）- 在所有项目中可用
/plugin install kiro-spec-driven@kiro-marketplace

# 项目范围 - 通过 git 与团队共享
/plugin install kiro-spec-driven@kiro-marketplace --scope project

# 本地范围 - 项目特定，已加入 gitignored
/plugin install kiro-spec-driven@kiro-marketplace --scope local
```

## 包含的技能

安装后，Claude 将在相关时自动使用这些技能：

| 技能 | 描述 | 触发词 |
|-------|-------------|----------|
| **spec-driven-development** | 完整的三个阶段方法论 | "create a spec"（创建规格）, "plan this feature"（规划此功能）, "spec-driven"（规格驱动） |
| **requirements-engineering** | EARS 格式的需求项 | "requirements"（需求）, "acceptance criteria"（验收标准）, "user stories"（用户故事） |
| **design-documentation** | 技术架构文档 | "design document"（设计文档）, "architecture"（架构）, "technical design"（技术设计） |
| **task-breakdown** | 实施规划 | "break down tasks"（分解任务）, "implementation plan"（实施计划）, "task list"（任务列表） |
| **ai-prompting** | AI 沟通策略 | "prompt better"（更好地提示）, "AI communication"（AI 沟通）, "improve prompts"（改进提示） |
| **quality-assurance** | 测试和验证 | "quality"（质量）, "testing strategy"（测试策略）, "validation"（验证） |
| **troubleshooting** | 问题解决与调试 | "debug"（调试）, "troubleshoot"（故障排除）, "issue with"（...的问题） |
| **create-steering-documents** | 项目指南与规范设置 | "steering documents"（指导文档）, "project standards"（项目标准）, "setup guidelines"（设置指南） |

## 使用示例

### 开始一个新的规格 (Spec)

```
为支持 OAuth 的用户身份验证创建一个规格 (spec)
```

Claude 将自动调用 `spec-driven-development` 技能。

### 编写需求

```
帮助我使用 EARS 格式编写文件上传功能的需求
```

Claude 将使用 `requirements-engineering` 技能。

### 创建技术设计

```
为一个通知系统设计架构
```

Claude 将使用 `design-documentation` 技能。

### 分解任务

```
将此设计分解为实施任务
```

Claude 将使用 `task-breakdown` 技能。

## 验证安装

```bash
# 列出已安装的插件
/plugin

# 检查插件状态
/plugin info kiro-spec-driven
```

## 更新

```bash
# 更新到最新版本
/plugin update kiro-spec-driven@kiro-marketplace
```

## 卸载

```bash
# 卸载插件
/plugin uninstall kiro-spec-driven
```

## 插件内容结构

```
kiro/
├── .claude-plugin/
│   ├── plugin.json          # 插件清单 (Manifest)
│   └── marketplace.json     # 市场配置
├── skills/
│   ├── spec-driven-development/
│   │   └── SKILL.md
│   ├── requirements-engineering/
│   │   └── SKILL.md
│   ├── design-documentation/
│   │   └── SKILL.md
│   ├── task-breakdown/
│   │   └── SKILL.md
│   ├── ai-prompting/
│   │   └── SKILL.md
│   ├── quality-assurance/
│   │   └── SKILL.md
│   └── troubleshooting/
│       └── SKILL.md
├── mcp-server/              # 可选的 MCP 服务器
└── spec-process-guide/      # 完整文档指南
```

## 许可证

MIT - 参见 [LICENSE](LICENSE)
