# Codexian

AI 聊天助手 Obsidian 插件，底层走 [Codex CLI](https://www.npmjs.com/package/@openai/codex)。

不限 GPT，不限 Claude——你本机 Codex CLI 后端是什么模型，它就是什么模型（通常是 DeepSeek）。

## 功能

- 右侧面板聊天，问知识库里的问题，直接回答
- Enter 发送 / Shift+Enter 换行
- 消息区文字可选中复制
- 配置 CLI 路径，上下文行数

## 安装

```bash
git clone git@github.com:tingyu220/codexian.git
cd codexian
npm install
npm run build
```

然后把项目文件夹复制到 Obsidian vault 的 `.obsidian/plugins/codexian/`，在「设置 → 第三方插件」中启用。

## 依赖

- [Codex CLI](https://www.npmjs.com/package/@openai/codex)（本机必须已安装）
- 本插件不绑定任何 AI 提供商，模型走你本机 Codex CLI 的配置

## 开发

```bash
npm install
npm run dev     # watch 构建
npm run build   # 生产构建
```

## 架构

```
src/
├── main.ts          # 插件入口，注册视图和设置
├── CodexianView.ts  # 右侧面板聊天 UI
├── CodexCli.ts      # Codex CLI 调用适配层
├── SettingTab.ts    # 设置页
└── types.ts         # 类型定义
```

Codex CLI 调用方式：`codex exec --skip-git-repo-check --json "<prompt>"`，从 JSONL 输出中提取 `agent_message.text`。
