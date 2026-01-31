# Obsidian Sample Plugin Plus

[![许可证: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[English](../README.md)

这是一个为 [Obsidian](https://obsidian.md) 设计的增强型插件示例模板，集成了 AI 辅助开发工具和最佳实践。

本项目使用 TypeScript 提供类型检查和文档。仓库依赖于最新的 TypeScript 定义格式的插件 API (obsidian.d.ts)，其中包含描述其功能的 TSDoc 注释。

此示例插件演示了插件 API 可以实现的一些基本功能：
- 添加功能图标，点击时显示通知。
- 添加命令 "Open modal (simple)"，打开一个模态框。
- 在设置页面中添加插件设置选项卡。

## 为什么选择 Plus 版本？

此模板包含额外的工具和文档，旨在提升您的开发体验：

### AI 辅助开发系统

此模板使用 OpenSkills 系统，技能可通过 npm 包获取。

**设置：**
```bash  
# 1. 安装依赖（包含 obsidian-dev-skills）
pnpm install

# 2. 初始化本地技能组 (.agent/skills/)
pnpm obsidian-dev-skills

# 3. 设置参考资料（链接到核心 Obsidian 仓库）
.\scripts\setup-ref-links.bat  # Windows  
# 或
bash scripts/setup-ref-links.sh  # macOS/Linux
```

**包含内容：**
- **`AGENTS.md`** - AI Agent 指导的 OpenSkills 入口点
- **`.agent/skills/` 文件夹** - 链接到集中技能仓库的符号链接
- **插件开发技能** - TypeScript、API 模式、生命周期管理
- **操作技能** - 构建、发布和维护流程
- **技术参考** - API 文档、清单规则、文件格式
- **项目特定技能** - 您的自定义模式和约定

### 参考资料系统 (`.ref` 文件夹)

- **符号链接到 Obsidian 仓库** - 轻松查看 API 文档、示例代码和案例。
- **集中存储** - 所有项目共享相同的参考仓库（无重复占用空间）。
- **6 个核心 Obsidian 项目** - API 定义、文档、示例插件、ESLint 规则。

### ESLint 9 与 Obsidian 规则

- **与官方审核机器人一致** - 使用相同的 `obsidianmd.configs.recommended` 配置。
- **自动迁移** - 自动从 ESLint 8 升级到 ESLint 9。
- **智能检测** - 自动处理根目录或 `src/` 文件夹下的 `main.ts`。

## 快速开始

### 开发新插件（以此为模板）

1. **使用此模板** - 点击 GitHub 上的 "Use this template" 或克隆此仓库。
2. **安装依赖**：`pnpm install`
3. **初始化技能**：`pnpm obsidian-dev-skills`
4. **可选：设置参考资料**（推荐）：
   - **Windows**: `scripts\setup-ref-links.bat`
   - **macOS/Linux**: `./scripts/setup-ref-links.sh`
5. **开始开发**：`pnpm dev`
6. **使用 Chrome MCP 调试**：（可选）使用 [Chrome DevTools MCP](https://github.com/ChromeDevTools/chrome-devtools-mcp) 直接从 IDE 的 AI 助手调试插件。

### 🔍 使用 Chrome DevTools MCP 调试

现在你可以使用 [Chrome DevTools MCP](https://github.com/ChromeDevTools/chrome-devtools-mcp) 来调试 Obsidian。这允许 AI 检查 DOM、查看控制台并与 Obsidian 界面交互。

#### 设置

1. **安装 MCP**：按照 [官方文档](https://github.com/ChromeDevTools/chrome-devtools-mcp) 在你的 IDE（如 Cursor, VS Code）中安装 Chrome DevTools MCP。
2. **用远程调试模式启动 Obsidian**：
   
   - **macOS**: `open -a Obsidian --args --remote-debugging-port=9222`
   - **Linux**: `obsidian --remote-debugging-port=9222`
   - **Windows (PowerShell)**: `& "$env:LOCALAPPDATA\Obsidian\Obsidian.exe" --remote-debugging-port=9222`

   > **提示**: 将其别名设置为简短的内容，比如 `obsdev`。

#### 为什么使用它？
启用后，您的 AI 助手可以：
- **获取快照**：获取当前 Obsidian 的状态。
- **检查 DOM**：辅助编写 CSS 或定位元素。
- **查看控制台日志**：实时调试错误。
- **模拟交互**：模拟点击按钮或执行命令。

## 如何使用

### 基础开发

- 克隆此仓库。
- 确保 NodeJS 版本至少为 v16 (`node --version`)。
- `pnpm install` 安装依赖（或使用 `npm install`，会自动代理到 pnpm）。
- **开发**: `pnpm dev` - 编译到根目录的 `main.js`（带监听模式）。
- **生产构建**: `pnpm build` - 编译到根目录的 `main.js`（单次构建）。
- **部署**: `pnpm deploy` - 构建并自动复制到您的 Obsidian 测试库。

#### 设置部署 (Deploy)

`deploy` 命令帮助您自动将构建产物复制到本地 Obsidian 库进行测试。

1. 在项目根目录创建 `deploy.config.local.json`：
   ```json
   {
       "targetDir": "C:\\你的路径\\.obsidian\\plugins\\你的插件ID"
   }
   ```
2. 运行 `pnpm deploy`。此文件已被 git 忽略，以保护您的本地路径隐私。

**注意**: 本项目优先使用 pnpm，但为了兼容性，`npm install`, `npm run build`, `npm run dev`, `npm run deploy`, 和 `npm run lint` 依然有效。
