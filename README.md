# Codexian Plus

AI 聊天助手 Obsidian 插件，底层走 [Codex CLI](https://www.npmjs.com/package/@openai/codex)。
**Codexian 模型层不锁死**——内置 DeepSeek V4 Pro / V3 / R1，支持自定义添加任何模型。

## 功能

- 右侧面板聊天，Enter 发送 / Shift+Enter 换行
- 启动时全量扫描知识库，事件驱动增量更新——不重复扫描
- 每次提问自动搜索知识库，把最相关的 5 篇笔记注入 prompt
- 对话记忆：最近 10 轮对话作为上下文
- 模型选择器：标题栏下拉切模型
- **MCP Server 长连接**：`codex mcp-server` 常驻，复用 threadId，大幅减少等待
- 文字可选中复制
- 设置页：CLI 路径、默认模型、自定义模型、上下文轮数

## 架构

```
src/
├── main.ts              # 插件入口，注册视图 + KnowledgeIndex
├── types.ts             # 类型定义
├── providers/
│   └── CodexianProvider.ts  # 动态模型列表
├── runtime/
│   └── CodexianRuntime.ts   # MCP server 长连接（cmd.exe /c 包装）
├── ui/
│   └── CodexianView.ts      # 聊天面板 + 知识库搜索结果注入
├── knowledge/
│   └── KnowledgeIndex.ts    # 全量扫描 + 事件驱动增量更新
└── settings/
    └── SettingTab.ts        # 设置页
```

## 安装

```bash
git clone git@github.com:tingyu220/codexian.git
cd codexian
npm install
npm run build
```

复制到 Obsidian vault 的 `.obsidian/plugins/codexian/`，启用。

## 开发

```bash
npm install
npm run dev     # watch
npm run build   # 生产
```
