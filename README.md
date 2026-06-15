# Codexian

AI 聊天助手 Obsidian 插件，底层走 Codex CLI，不限 GPT，不限 Claude——只要你本机跑的 Codex 是什么模型，它就是什么模型。

## 功能

- 右侧面板聊天界面，问知识库里的问题，直接回答
- Ctrl+Enter 发送，支持多轮对话
- 配置 CLI 路径和上下文行数
- 点击 ribbon 图标或命令面板打开

## 安装

```bash
git clone https://github.com/TianYu-00/codexian.git
cd codexian
npm install
npm run build
```

然后把项目文件夹复制到你的 Obsidian vault 的 `.obsidian/plugins/codexian/`。

## 依赖

- [Codex CLI](https://www.npmjs.com/package/@openai/codex)（必须本机已安装）
- 本插件本身不提供模型，模型走你本机 Codex CLI 的配置

## 开发

```bash
npm install
npm run dev     # watch 模式
npm run build   # 生产构建
```
