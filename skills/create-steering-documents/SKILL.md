---
name: create-steering-documents
description: 为开发项目创建全面的指导文档。在 .kiro/steering/ 目录中生成特定于项目的标准、Git 工作流和技术指南。
version: 1.0.0
license: MIT
compatibility:
  - Claude Code
  - Cursor
  - VS Code Copilot
  - Windsurf
metadata:
  category: project-setup
  complexity: intermediate
  triggers:
    - create steering documents
    - setup project standards
    - initialize kiro steering
    - project guidelines
---

# 创建指导文档 (Create Steering Documents)

根据项目类型和需求，为开发项目创建全面的指导文档。

## 用法

```
Create steering documents for [project description]
```
（为 [项目描述] 创建指导文档）

## 示例

- `Create steering documents for a React TypeScript e-commerce application`
- `Create steering documents for a Python Django REST API with PostgreSQL`
- `Create steering documents for a Node.js microservices architecture`
- `Create steering documents for a Vue.js component library`

## 什么是指导文档？

指导文档是影响 AI 助手如何处理开发任务的上下文指南。它们包含特定于项目的标准、惯例和最佳实践，有助于提供更相关和一致的帮助。

### 它们如何工作

1. **始终包含（默认）**：没有 front-matter 的文档包含在每次交互中
2. **文件匹配条件**：带有 `inclusion: fileMatch` 的文档在上下文中有特定文件时包含
3. **手动包含**：带有 `inclusion: manual` 的文档仅在明确引用时包含

## 流程

### 1. 项目分析

首先，分析项目需求并确定的需要哪些指导文档：

**对于前端项目 (React, Vue, Angular):**
- 包含：project-standards.md, git-workflow.md, frontend-standards.md, development-environment.md
- 考虑：component-library.md, testing-strategy.md

**对于后端/API 项目 (Node.js, Python, Java):**
- 包含：project-standards.md, git-workflow.md, api-design.md, development-environment.md
- 考虑：database-standards.md, security-guidelines.md

**对于全栈项目：**
- 包含：所有核心文档加上技术特定的文档
- 考虑：deployment-standards.md, monitoring-guidelines.md

**对于库/包项目：**
- 包含：project-standards.md, git-workflow.md, documentation-standards.md
- 考虑：versioning-strategy.md, publishing-guidelines.md

### 2. 核心文档模板

#### project-standards.md

```markdown
# 项目标准和指南

## 代码质量标准
- 遵循特定于语言的风格指南（JS/TS 用 ESLint，Python 用 Black 等）
- 在整个代码库中保持一致的命名约定
- 编写具有清晰变量和函数名称的自文档化代码
- 为复杂的业务逻辑包含有意义的注释
- 保持函数小巧并专注于单一职责

## 测试需求
- 为所有业务逻辑函数编写单元测试
- 保持至少 80% 的代码覆盖率
- 为 API 端点包含集成测试
- 为关键用户流程编写端到端测试
- 使用描述性测试名称来解释正在测试的场景

## 文档标准
- 重大更改更新 README.md
- 用清晰的示例记录 API 端点
- 包含设置和部署说明
- 维护版本发布的变更日志
- 以 ADR 格式记录架构决策

## 安全实践
- 永远不要提交机密、API 密钥或密码
- 使用环境变量进行配置
- 验证所有用户输入
- 实施适当的认证和授权
- 遵循 OWASP 安全指南

## 性能指南
- 优化数据库查询并避免 N+1 问题
- 在适当的地方实施缓存
- 为大数据集使用延迟加载
- 定期监控和分析性能
- 在架构决策中考虑可扩展性
```

#### git-workflow.md

```markdown
# Git 工作流和分支策略

## 分支命名约定
- 功能分支：`feature/description-of-feature`
- Bug 修复：`fix/description-of-bug`
- 热修复：`hotfix/critical-issue-description`
- 发布：`release/version-number`

## 提交消息格式
遵循 conventional commits 格式：
```
type(scope): description

[optional body]

[optional footer]
```

类型：feat, fix, docs, style, refactor, test, chore

## Pull Request 指南
- 从功能分支创建 PR 到 main/develop
- 包含清晰的更改描述
- 使用关键字链接相关问题 (fixes #123)
- 请求审查前确所有测试通过
- 合并时压缩提交以保持历史记录清洁

## 代码审查流程
- 合并前至少需要一次批准
- 审查代码质量、安全性和性能
- 检查测试是否覆盖新功能
- 如果需要，验证文档是否已更新
- 确保没有未进行适当版本控制的破坏性更改
```

#### frontend-standards.md

```markdown
---
inclusion: fileMatch
fileMatchPattern: '*.tsx|*.jsx|*.vue|*.svelte'
---
# 前端开发标准

## 组件架构
- 使用带钩子的函数组件 (React)
- 保持组件小巧且专注
- 实施适当的属性验证
- 使用 TypeScript 进行类型安全
- 遵循组件组合模式

## 状态管理
- 将本地状态用于特定于组件的数据
- 为共享应用程序数据实施全局状态
- 使用适当的状态管理库 (Redux, Zustand, Pinia)
- 使用上下文或状态管理避免属性钻取

## 样式指南
- 为组件样式使用 CSS 模块或 styled-components
- 遵循 CSS 类命名的 BEM 方法论
- 使用移动优先方法实施响应式设计
- 使用 CSS 自定义属性进行主题化
- 保持一致的间距和排版比例

## 性能优化
- 实施代码拆分和延迟加载
- 对昂贵的组件使用 React.memo 或类似物
- 优化图像和资产
- 实施适当的缓存策略
- 监控捆绑包大小和性能指标

## 无障碍标准
- 使用语义化 HTML 元素
- 实施适当的 ARIA 属性
- 确保键盘导航支持
- 保持适当的颜色对比度
- 使用屏幕阅读器进行测试
```

#### api-design.md

```markdown
---
inclusion: manual
---

# API 设计指南

## RESTful API 标准
- 恰当使用 HTTP 方法 (GET, POST, PUT, DELETE, PATCH)
- 遵循基于资源的 URL 模式：`/api/v1/users/{id}`
- 为资源集合使用复数名词
- 实施适当的 HTTP 状态代码
- 在 URL 路径中包含 API 版本控制

## 请求/响应格式
- 对于请求和响应体使用 JSON
- 遵循一致的命名约定（camelCase 或 snake_case）
- 为列表端点包含分页
- 实施适当的错误响应格式：

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input provided",
    "details": ["Email is required", "Password too short"]
  }
}
```

## 认证和授权
- 使用 JWT 令牌进行无状态认证
- 实施适当的令牌刷新机制
- 使用基于角色的访问控制 (RBAC)
- 对 API 端点进行速率限制以防止滥用

## 文档
- 使用 OpenAPI/Swagger 进行 API 文档
- 包含请求/响应示例
- 记录所有可能的错误响应
- 提供 SDK 或客户端库示例
```

#### development-environment.md

```markdown
---
inclusion: fileMatch
fileMatchPattern: 'package.json|requirements.txt|Dockerfile|docker-compose.yml'
---

# 开发环境设置

## 本地开发
- 使用 .nvmrc 文件中指定的 Node.js 版本
- 使用 `npm ci` 安装依赖项以获得一致的构建
- 使用 Docker 获取本地数据库和服务依赖项
- 在提交更改之前运行 linting 和格式化

## 环境变量
- 为本地开发复制 `.env.example` 到 `.env`
- 永远不要提交实际的环境文件
- 在 README 中记录所有需要的环境变量
- 为不同环境使用不同的前缀 (DEV_, PROD_ 等)

## 数据库管理
- 为所有模式更改使用迁移
- 包含迁移的回滚脚本
- 种子数据应是幂等的
- 在重大更改之前备份数据库

## 构建和部署
- 确保构建在环境中可重复
- 使用多阶段 Android Docker 构建进行优化
- 在容器化应用程序中包含健康检查
- 记录部署程序和回滚步骤

## 调试和日志记录
- 使用带有适当日志级别的结构化日志记录
- 包含用于请求跟踪的相关 ID
- 设置适当的错误监控和警报
- 使用调试器而不是 console.log 进行开发
```

### 3. 内容定制

**语言/框架特定适应：**
- **JavaScript/TypeScript**: ESLint, Prettier, Jest, package.json scripts
- **Python**: Black, flake8, pytest, requirements.txt, virtual environments
- **Java**: Checkstyle, Maven/Gradle, JUnit, Spring Boot conventions
- **Go**: gofmt, go mod, testing patterns, project structure
- **Rust**: rustfmt, Cargo.toml, cargo test, clippy

**项目规模适应：**
- **小型项目：** 轻量级流程，最少工具
- **团队项目：** 代码审查需求，共享标准
- **企业：** 全面的安全、合规、文档

**领域特定考虑：**
- **电子商务：** PCI 合规，性能，安全
- **医疗保健：** HIPAA 合规，数据隐私，审计跟踪
- **金融：** 安全标准，监管合规
- **开源：** 贡献指南，许可，社区标准

### 4. 文件参考集成

使用 `#[[file:path]]` 语法包含相关的外部文件：
- API 项目的 OpenAPI 规范
- 后端项目的数据库模式
- 前端项目的设计系统令牌
- 环境设置的配置文件

### 5. 质量检查清单

在最终确定指导文档之前，确保：
- [ ] 所有文档都有适当的包含逻辑 front-matter
- [ ] 指南具体且可操作，而非通用的
- [ ] 为复杂概念提供了示例
- [ ] 文档之间没有冲突的标准
- [ ] 包含了安全和性能考虑
- [ ] 文档覆盖了完整的开发生命周期
- [ ] 文件引用格式正确且有效

## 输出结构

在 `.kiro/steering/` 目录下创建指导文档：

```
.kiro/steering/
├── project-standards.md      (always included)
├── git-workflow.md           (always included)
├── frontend-standards.md     (fileMatch: *.tsx,*.jsx)
├── api-design.md             (manual inclusion)
└── development-environment.md (fileMatch: package.json)
```

## Front-matter 选项

```yaml
---
inclusion: always|fileMatch|manual
fileMatchPattern: 'glob-pattern'  # 仅用于 fileMatch
---
```

## 最佳实践

### 做：
- 保持文档专注和具体
- 使用清晰、可操作的语言
- 包含具体示例
- 引用外部规范
- 随着项目发展定期更新
- 使用适当的包含机制

### 不做：
- 创建过于宽泛或通用的指南
- 在多个文档中重复信息
- 包含敏感信息或机密
- 创建冲突的标准
- 使文档太长或太复杂
