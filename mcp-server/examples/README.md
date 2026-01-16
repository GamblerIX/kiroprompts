# Kiro MCP 服务器示例

此目录包含 Kiro MCP 服务器的示例配置和使用模式。

## 配置示例

### 基本配置 (mcp-config.json)

将此添加到你的 MCP 客户端配置文件（例如 `~/.kiro/settings/mcp.json` 或 Claude Desktop 的配置）：

```json
{
  "mcpServers": {
    "kiro-prompts": {
      "command": "uvx",
      "args": ["kiro-mcp-server"],
      "disabled": false,
      "autoApprove": ["list_instructions", "get_system_instruction"]
    }
  }
}
```

### 本地开发配置

如果从源代码运行：

```json
{
  "mcpServers": {
    "kiro-prompts": {
      "command": "python",
      "args": ["-m", "kiro_mcp_server.server"],
      "disabled": false,
      "env": {
        "KIRO_SYSTEM_PATH": "/path/to/kiro/.kiro/system"
      }
    }
  }
}
```

## 使用示例

配置完成后，你可以在 MCP 客户端中使用服务器：

### 列出可用指令

使用 `list_instructions` 工具查看可用的内容：

```
使用 list_instructions 工具
```

### 获取特定系统指令

```
使用 get_system_instruction 工具，参数为 instruction_type: "complete-instructions"
```

### 搜索指令

```
使用 search_instructions 工具，参数为 query: "MCP"
```

### 使用提示

服务器提供预配置的提示：

1. **kiro_assistant** - 完整的 Kiro 助手配置
2. **code_review** - 使用 Kiro 标准进行代码审查
3. **feature_development** - 功能开发工作流程

## 测试服务器

你可以通过以下方式测试服务器是否正常工作：

1. 在客户端中检查 MCP 服务器视图
2. 尝试列出指令
3. 检索系统指令文档

## 故障排除

### 服务器无法启动

- 检查是否安装了 `uvx` 或 `uv`：`uv --version`
- 尝试直接运行：`uvx kiro-mcp-server`（这会因 stdio 错误而失败，但确认包可访问）

### 找不到系统文件

- 将 `KIRO_SYSTEM_PATH` 环境变量设置为指向你的 `.kiro/system` 目录
- 确保你在 Kiro 仓库内运行或已正确安装包

### 资源未显示

- 检查 MCP 客户端日志中的错误
- 验证服务器在 MCP 配置中已列出并启用
- 尝试从 MCP 服务器视图重新连接服务器
