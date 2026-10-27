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

## 当前版本：0.1.3

- 项目搜索浮层锚定输入区的＋/回形针，在按钮上方展开（空间不足时改为下方），不再居中显示在代码区。
- 输入框使用紧凑图标和引用标签，随内容收缩，支持明暗主题及窄侧栏滚动。
- 默认只引用 IDEA 当前活动文件；＋搜索项目代码引用，回形针搜索项目附件，不再弹出系统文件选择器。
- 在输入框按 Ctrl/⌘ + V 粘贴图片，或把图片、MD 等支持的文件拖到输入框/对话区，成为附件并参与本次请求。
- 普通文本复制/粘贴保留；移除附件不删除原始文件，粘贴图片产生的临时 PNG 会清理。
- Java 提示依据项目的语言级别与编译目标限制。
- Codex 需求讨论、代码建议、局部测试、注释及阶段总结由用户主动触发。
- 本地提示无需连接 Codex；AI 功能需本机已登录的 Codex CLI。

下载：[java-codex-assistant-0.1.3.zip](https://github.com/jsczymm1015/idea-java-assistant-updates/releases/download/java-codex-assistant-v0.1.3/java-codex-assistant-0.1.3.zip)。校验值见 [checksums.sha256](checksums.sha256)。ZIP 不需解压。

验证范围：本版构建、8 组独立检查、原生包结构，以及 macOS ARM64 / IDEA 2026.1.5 隔离真实窗口中的搜索浮层位置、文件搜索、Enter 添加和关闭已通过。0.1.2 的合成剪贴板/文件列表接入和明暗主题组件渲染验证继续作为相关功能记录。系统剪贴板与真实鼠标拖拽的跨平台完整人工验收尚未完成；本次未重新调用真实模型。Windows/Linux 完整流程与其他 IDEA 分支尚未验证。

## 发布约定

公开仓库仅保留更新索引、校验值和必要使用说明；编译 ZIP 放在 GitHub Releases。先发布并验证 ZIP，再更新 `updatePlugins.xml`。索引中的 ID、版本和兼容范围必须来自实际 ZIP 内的 `META-INF/plugin.xml`，已发布版本的安装包不覆盖。
