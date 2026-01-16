# Kiro MCP 服务器

一个 MCP（模型上下文协议）服务器，暴露 Kiro 的系统提示和指令。

## 概述

此服务器通过模型上下文协议提供对 Kiro 全面系统指令、能力、指南和质量标准的访问。它允许 AI 助手和其他 MCP 客户端访问和利用 Kiro 的提示工程最佳实践。

## 功能

- **资源**：访问所有 Kiro 系统文档文件
- **工具**：查询和检索特定系统指令
- **提示**：常见 Kiro 工作流程的预配置提示

## 安装

### 使用 uvx（推荐）

```bash
uvx kiro-mcp-server
```

### 使用 pip

```bash
pip install kiro-mcp-server
```

### 从源代码

```bash
cd mcp-server
pip install -e .
```

## 使用

### 配置

添加到你的 MCP 客户端配置（例如 Claude Desktop、Kiro）：

```json
{
  "mcpServers": {
    "kiro-prompts": {
      "command": "uvx",
      "args": ["kiro-mcp-server"],
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

或者如果本地安装：

```json
{
  "mcpServers": {
    "kiro-prompts": {
      "command": "python",
      "args": ["-m", "kiro_mcp_server.server"],
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

### 可用资源

服务器暴露以下 Kiro 系统文档：

- `kiro://system/complete-instructions` - 完整的 Kiro 系统指令
- `kiro://system/capabilities` - Kiro 能力和特性
- `kiro://system/guidelines` - 开发指南
- `kiro://system/quality-standards` - 质量标准
- `kiro://system/response-style` - 响应风格指南
- `kiro://system/workflow-patterns` - 常见工作流程模式

### 可用工具

- `get_system_instruction` - 按类型检索特定系统指令
- `search_instructions` - 在所有系统指令中搜索
- `list_instructions` - 列出所有可用的指令类型

### 可用提示

- `kiro_assistant` - 使用 Kiro 系统指令设置 AI 助手
- `code_review` - 使用 Kiro 标准配置代码审查
- `feature_development` - 配置功能开发工作流程

## 开发

```bash
# 安装开发依赖
pip install -e ".[dev]"

# 运行测试
pytest

# 本地运行服务器
python -m kiro_mcp_server.server
```

## 许可证

请参阅主 Kiro 仓库获取许可证信息。

## 贡献

欢迎贡献！请参阅主 Kiro 仓库获取贡献指南。
