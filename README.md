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

## 当前版本：0.1.1

- 输入框上方显示文件引用标签，可打开、移除和添加项目文件或附件。
- Java 提示依据项目的语言级别与编译目标限制。
- Codex 需求讨论、代码建议、局部测试、注释及阶段总结由用户主动触发。
- 本地提示无需连接 Codex；AI 功能需本机已登录的 Codex CLI。

下载：[java-codex-assistant-0.1.1.zip](https://github.com/jsczymm1015/idea-java-assistant-updates/releases/download/java-codex-assistant-v0.1.1/java-codex-assistant-0.1.1.zip)。校验值见 [checksums.sha256](checksums.sha256)。ZIP 不需解压。

验证范围：此版本已通过构建、独立检查及 macOS ARM64 上 IDEA 2026.1.5 的隔离加载与相关交互冒烟检查；不等同于完整人工业务端到端验收。Windows/Linux 完整流程与其他 IDEA 分支尚未验证。

## 发布约定

公开仓库仅保留更新索引、校验值和必要使用说明；编译 ZIP 放在 GitHub Releases。先发布并验证 ZIP，再更新 `updatePlugins.xml`。索引中的 ID、版本和兼容范围必须来自实际 ZIP 内的 `META-INF/plugin.xml`，已发布版本的安装包不覆盖。
