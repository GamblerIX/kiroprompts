# Kiro 技能

遵循 [agentskills.io](https://agentskills.io) 规范的 Claude Code 技能集合，用于规范驱动开发。

## 可用技能

| 技能 | 描述 | 复杂度 |
|------|------|--------|
| [spec-driven-development](./spec-driven-development/) | 结合所有三个阶段的主方法论 | 中级 |
| [requirements-engineering](./requirements-engineering/) | EARS 格式需求和验收标准 | 初级 |
| [design-documentation](./design-documentation/) | 技术架构和组件设计 | 中级 |
| [task-breakdown](./task-breakdown/) | 顺序实施任务规划 | 中级 |
| [ai-prompting](./ai-prompting/) | 有效的 AI 沟通策略 | 初级 |
| [quality-assurance](./quality-assurance/) | 测试和验证技术 | 中级 |
| [troubleshooting](./troubleshooting/) | 诊断和解决常见问题 | 中级 |
| [create-steering-documents](./create-steering-documents/) | 生成 .kiro/steering/ 项目指南 | 中级 |

## 安装

### Claude Code

可以直接从仓库引用技能：

```bash
# 克隆仓库
git clone https://github.com/jasonkneen/kiro.git

# 在你的项目中引用技能
# 技能位于 /skills 目录
```

### 手动安装

将所需的技能文件夹复制到项目的 `.claude/skills/` 目录：

```bash
cp -r kiro/skills/spec-driven-development .claude/skills/
```

## 技能格式

每个技能遵循 agentskills.io 的 SKILL.md 格式：

```yaml
---
name: skill-name
description: 此技能的作用（最多 1024 个字符）
license: MIT
compatibility: Claude Code, Cursor, VS Code
metadata:
  category: methodology
  complexity: beginner|intermediate|advanced
---

# 技能名称

[代理要遵循的指令]
```

## 快速开始

1. **规范新手？** 从 [spec-driven-development](./spec-driven-development/) 开始
2. **只需要需求？** 使用 [requirements-engineering](./requirements-engineering/)
3. **改善 AI 结果？** 尝试 [ai-prompting](./ai-prompting/)
4. **遇到问题？** 查看 [troubleshooting](./troubleshooting/)

## 验证

运行验证脚本检查所有技能：

```bash
./scripts/validate-skills.sh
```

## 贡献

要添加新技能：

1. 在 `skills/` 下创建新目录
2. 添加具有正确 frontmatter 的 `SKILL.md` 文件
3. 运行验证以确保格式符合要求
4. 提交拉取请求

## 许可证

MIT - 参见 [LICENSE](../LICENSE)
