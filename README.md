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

## 当前版本：0.2.0

新增 **Agent 模式**：连接 Codex 后，从输入框下拉菜单选择 Agent，输入目标并发送；也可输入 `/agent 具体目标`。

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

下载：[java-codex-assistant-0.2.0.zip](https://github.com/jsczymm1015/idea-java-assistant-updates/releases/download/java-codex-assistant-v0.2.0/java-codex-assistant-0.2.0.zip)。校验值见 [checksums.sha256](checksums.sha256)。ZIP 不需解压。

验证范围：JDK 21 构建、10 组独立检查和安装包结构校验通过。实际隔离 IDEA 中完成合成 Java/Maven 模块的测试失败→修复→通过、多文件撤销、冲突保护和停止检查；真实 Codex 自主查找、读取、修改并通过实际 Maven/JUnit 测试。引用、附件和模式入口界面检查通过。没有读取业务项目或私人附件；未操作用户日常 IDEA 更新。真实模型验证仅覆盖小型合成模块，Gradle Agent 全流程、Windows/Linux、跨模块与外部服务集成尚未端到端验证。IDEA 启动的测试属于本机构建，可能下载依赖。

## 发布约定

公开仓库仅保留更新索引、校验值和必要使用说明；编译 ZIP 放在 GitHub Releases。先发布并验证 ZIP，再更新 `updatePlugins.xml`。索引中的 ID、版本和兼容范围必须来自实际 ZIP 内的 `META-INF/plugin.xml`，已发布版本的安装包不覆盖。
