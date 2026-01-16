# Kiro 规范驱动开发指南 – Web 应用程序

这是一个现代化的 Web 应用程序，旨在展示和使用 Kiro 规范驱动开发指南的内容。

## 功能

### 📚 完整内容展示
- 方法论概述 – 规范驱动开发的核心概念和理念
- 流程指南 – 三阶段开发流程的详细步骤
- AI 推理 – AI 决策框架和思维过程的分析
- 提示策略 – 与 AI 协作的有效沟通技巧
- 执行指南 – 从规范到实施的实用指导
- 资源库 – 标准、工具和学习材料
- 示例和案例 – 真实案例和完整的规范样本
- 模板库 – 即用型模板和检查清单

### 🔧 系统文档
- 系统能力 – Kiro AI 助手的核心功能和特性
- 响应风格 – 沟通风格和交互指南
- 工作流程模式 – 执行方法和最佳实践
- 质量标准 – 代码质量和输出标准

### 📋 项目指导
- 项目标准 – 代码质量和测试要求
- Git 工作流程 – 分支策略和提交约定
- 前端标准 – React/TypeScript 开发规范
- API 设计 – RESTful API 设计标准
- 开发环境 – 配置和工具

### ⚡ 命令和自动化
- 创建指导文档 – 自动生成项目指导文档
- 上下文命令 – 检索文件、文件夹、问题等上下文
- MCP 集成 – 模型上下文协议支持

## 技术栈

- React 18 – 用户界面框架
- TypeScript – 类型安全
- Tailwind CSS – 样式框架
- React Router – 路由管理
- Lucide React – 图标库
- Vite – 构建工具

## 快速开始

### 安装依赖
```bash
npm install
```

### 启动开发服务器
```bash
npm run dev
```
应用将在 http://localhost:3000 启动

### 构建生产版本
```bash
npm run build
```

### 预览生产构建
```bash
npm run preview
```

## 项目结构

```
src/
├── components/          # 可重用组件
│   └── Layout.tsx      # 主布局组件
├── pages/              # 页面组件
│   ├── Home.tsx        # 首页
│   ├── Methodology.tsx # 方法论
│   ├── Process.tsx     # 流程指南
│   ├── AIReasoning.tsx # AI 推理
│   ├── Prompting.tsx   # 提示策略

```

MIT 许可证 – 参见 LICENSE 文件
