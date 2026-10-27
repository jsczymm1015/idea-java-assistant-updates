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

## 当前版本：0.3.0

**无需截图即可检查当前文件的黄线，新增全项目代码 Agent。**

- 打开/激活文件，输入 `/review 检查当前文件的黄线`。插件自动读取整个活动文件的 IDEA 警告原文、行列和检查类型，无需圈选或选中代码。可继续查找项目相关文件并分析。
- “问题 / 定位”页可直接刷新本地检查结果，不调用模型；双击或回车跳转。IDEA 仍在索引/分析时显示不完整，不误报为没有问题。仅读取已有缓存，不保证未打开文件或顶部文件级通知的覆盖。
- `/agent 具体代码目标` 自主查找、读取、修改源文件和 Maven/Gradle 配置，运行终端命令与测试、联网获取技术资料。读取 IDEA 未保存文字；写入任务开始前保存当前项目文档。
- “执行”页显示输出、计划、修改及额外权限请求；允许本次、拒绝或停止均由用户选择。已完成的修改保留，结束后可查看补丁差异；终端造成的其他变化需在 Git 中审阅，不提供通用回滚。
- 仅面向代码开发，未加入桌面、鼠标键盘或浏览器界面操控。独立网页搜索取决于 CLI/账号，当前验证了终端 HTTP 获取官方技术资料，未验证原生搜索工具。
- 检查与 Agent 使用项目独立会话并可恢复；源会话只读，需求计划仍需预览确认。旧版模块内受控流程及最近一轮撤销可通过 `/module-agent` 使用。

保留已实现的功能：Codex 路径记忆和自动连接、账号每周剩余额度、Enter 发送与 Command+Enter 换行、紧凑引用标签、已打开文件优先/全项目文件搜索、图片粘贴与文件附件拖放、按项目 Java 版本限制的本地建议，以及需求讨论、局部测试、注释和阶段文档。

原生 Agent 需要支持动态工具实验协议的本机已登录 Codex CLI；自动连接和额度读取不调用模型。源码、私人附件及聊天记录不会发布到本仓库。

下载：[java-codex-assistant-0.3.0.zip](https://github.com/jsczymm1015/idea-java-assistant-updates/releases/download/java-codex-assistant-v0.3.0/java-codex-assistant-0.3.0.zip)。校验值见 [checksums.sha256](checksums.sha256)。ZIP 不需解压。

验证：15 个独立测试入口、最终安装包结构/schema/内容审计、隔离 IDEA 的 Java/XML 黄线缓存读取、未保存文本、精确定位及原有界面回归通过。真实 Codex 在合成项目完成代码及 pom.xml 修改、javac/java 验证成功、下载官方技术文档。原生 IDEA 和真实模型分别联调；未完成跨平台人工整体验收、业务项目测试或用户日常 IDEA 更新。兼容范围维持 261.*。

## 发布约定

公开仓库仅保留更新索引、校验值和必要使用说明；编译 ZIP 放在 GitHub Releases。先发布并验证 ZIP，再更新 `updatePlugins.xml`。索引中的 ID、版本和兼容范围必须来自实际 ZIP 内的 `META-INF/plugin.xml`，已发布版本的安装包不覆盖。
