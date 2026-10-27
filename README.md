# Java Codex Assistant 更新源

这是 Java Codex Assistant 的公开安装包与 IntelliJ IDEA 自定义更新索引仓库。源码仓库保持私有。本仓库不包含源码、聊天资料或用户附件。

## 在 IDEA 中安装与更新

适用于 **IntelliJ IDEA 2026.1（build 261.*）**，插件 ID：`dev.jsc.idea.java-codex-assistant`。

1. 打开 **Settings / Preferences → Plugins → 齿轮 → Manage Plugin Repositories**。
2. 点击 **＋**，添加下面的地址并保存：

```text
https://raw.githubusercontent.com/jsczymm1015/idea-java-assistant-updates/main/updatePlugins.xml
```

3. 已安装的用户可在 Plugins 的 Installed 页检查更新；新用户可在 Plugins 中搜索 **Java Codex Assistant**，或从 [Releases](https://github.com/jsczymm1015/idea-java-assistant-updates/releases) 下载 ZIP，通过 **Install Plugin from Disk** 安装。
4. 后续发布兼容的新版本后，IDEA 可提示更新，按提示点击 Update；可能需要重启 IDEA。同版本不会重复显示更新。

这是自定义插件仓库，并非 JetBrains Marketplace 官方上架。访问更新源和安装包均无需登录；IDEA 需要能够访问 GitHub、raw.githubusercontent.com 及 GitHub 的下载域名。

## 当前版本：0.2.2

新增 **周额度显示与回车发送**：

- 插件顶部显示当前 Codex 账号的周额度剩余百分比，悬停可查看重置时间及其他额度桶；这是账号共享额度，不是当前项目 token 统计。
- 连接后、操作完成后和约每分钟刷新；也可使用 **⋯ → 刷新额度**。没有有效周数据或请求失败时显示暂不可用，不显示虚假百分比。
- **Enter 发送，macOS Command+Enter 换行**；Windows/Linux 使用 Ctrl+Enter 换行。多行粘贴保持原样，加入中文输入法确认候选时的误发送保护。
- 额度读取不会启动模型推理；API Key 账号或旧 CLI 可能不提供周额度。

继续支持 **记住 Codex 路径与自动连接**：连接成功一次后，打开插件面板时自动连接，并恢复该项目自己的工作会话。

- 成功路径保存在 IDEA 应用级设置，新项目也能复用；对话、来源和需求继续按项目隔离。
- 旧版已有工作会话的项目会尝试原路径，成功后自动迁移，无需重复填写。
- **⋯ → 启动时自动连接** 可关闭；**⋯ → 连接 / 设置 Codex** 可修改路径。
- 失败保留手动重试/设置入口，不循环重试或自动弹窗；失败的新路径不覆盖原来的成功配置。
- 自动连接不调用模型、不发送代码或附件；登录仍由本机 Codex CLI 管理。

支持 **Agent 模式**：连接 Codex 后，从输入框下拉菜单选择 Agent，输入目标并发送；也可输入 `/agent 具体目标`。

- 自动在当前模块内搜索和读取文件、制定执行计划、应用多文件修改。
- 每次修改后自动运行模块 Maven/Gradle test，根据失败结果继续修复；最多 16 步 / 4 次测试。
- “执行”页显示过程；可以停止，结束后查看本轮差异或撤销本轮。遇到用户后续修改会拒绝覆盖。
- Agent 不自动改构建脚本/隐藏配置、不删除文件、不运行任意命令或部署；环境缺失、无测试或验证失败会报告未完成。
- 撤销快照仅保存当前面板最近一轮，重启后不恢复；对话模式继续通过预览确认应用修改。

- 项目搜索浮层锚定输入区的＋/回形针，在按钮上方展开（空间不足时改为下方），不再居中显示在代码区。
- 输入框使用紧凑图标和引用标签，随内容收缩，支持明暗主题及窄侧栏滚动。
- 活动文件默认显示为灰色未选中候选，点击后才作为引用参与请求；切换编辑器保留已选引用，移除已选活动文件后恢复为候选。
- ＋和回形针打开时先列符合条件的已打开文件（活动文件优先），输入关键词搜索整个项目，清空后返回已打开列表。
- 侧栏参考 Copilot 的紧凑布局：顶部连接和更多菜单、对话主区、底部圆角输入框；引用、附件、命令和发送集中在输入区。
- 在输入框按 Ctrl/⌘ + V 粘贴图片，或把图片、MD 等支持的文件拖到输入框/对话区，成为附件并参与本次请求。
- 普通文本复制/粘贴保留；移除附件不删除原始文件，粘贴图片产生的临时 PNG 会清理。
- Java 提示依据项目的语言级别与编译目标限制。
- Codex 需求讨论、代码建议、局部测试、注释及阶段总结由用户主动触发。
- 本地提示无需连接 Codex；AI 功能需本机已登录的 Codex CLI。

下载：[java-codex-assistant-0.2.2.zip](https://github.com/jsczymm1015/idea-java-assistant-updates/releases/download/java-codex-assistant-v0.2.2/java-codex-assistant-0.2.2.zip)。校验值见 [checksums.sha256](checksums.sha256)。ZIP 不需解压。

验证范围：JDK 21 构建、13 组独立检查、安装包结构/schema 校验与包审计通过。真实 Codex 周额度接口只读联调通过，没有创建会话或启动模型。实际隔离 IDEA 中验证额度显示、刷新、失败状态、实际输入框快捷键动作、两次启动后的自动重连及原有组件回归。输入法保护使用合成事件测试，未完成人工跨平台、各中文输入法验收；未重新执行 Agent/真实模型全循环，也未操作用户日常 IDEA 更新。

## 发布约定

公开仓库仅保留更新索引、校验值和必要使用说明；编译 ZIP 放在 GitHub Releases。先发布并验证 ZIP，再更新 `updatePlugins.xml`。索引中的 ID、版本和兼容范围必须来自实际 ZIP 内的 `META-INF/plugin.xml`，已发布版本的安装包不覆盖。
