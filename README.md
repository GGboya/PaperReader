<h1 align="center">PaperReader 论文伴读</h1>

<p align="center">
  <strong>一键安装的 AI 论文伴读桌面应用：选中即问、页码引用、原地翻译、教练式带读。</strong>
</p>

<p align="center"><sub>中文 · <a href="README.en.md">English</a></sub></p>

<p align="center">
  <img src="assets/paperreader/demo.gif" alt="PaperReader：选中即问 → 页码引用 → 跳回高亮" width="100%">
</p>

<p align="center">
  <a href="https://github.com/GGboya/PaperReader/releases/latest"><img src="https://img.shields.io/github/v/release/GGboya/PaperReader?style=flat&label=release&color=4D6BFE" alt="Latest release"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-2EA44F?style=flat" alt="MIT License"></a>
  <img src="https://img.shields.io/badge/macOS-Universal-4493F8?style=flat-square" alt="macOS Universal">
</p>

## 这是什么

PaperReader 是一个开箱即用的论文阅读桌面应用：左边文献库、中间 PDF 阅读器、右边 AI 对话。选中一句话就能问，回答里带页码、点页码跳回原文高亮，还能一键生成全文中文对照。

它不是从零写的——**PaperReader = [DSH Desktop](https://github.com/anywhere-labs/deepseek-harness-desktop)（桌面外壳）+ [dsh-paper-reader](https://github.com/GGboya/dsh-paper-reader)（论文伴读插件，预装）**。本仓库是 DSH Desktop 的 fork，做了三件事：换品牌、预装插件、关掉上游更新通道，其余原样保留（含全部提交历史与 MIT LICENSE）。

## 下载与安装

| 平台 | 下载 | 安装方式 |
| --- | --- | --- |
| macOS Universal（Intel + Apple Silicon） | [下载 DMG](https://github.com/GGboya/PaperReader/releases/latest/download/PaperReader-0.1.0-universal.dmg) | 打开 DMG，把 PaperReader 拖进「应用程序」 |
| Windows | 打包中，敬请期待 | — |

两点说明：

- **免签名发布**：没有买 Apple 开发者证书，首次打开需要 右键 → 打开（或 系统设置 → 隐私与安全性 → 仍要打开）。只弹这一次。
- **首次启动较慢**：第一次运行有几分钟的一次性初始化（插件环境组装，风扇可能会转），之后就正常了。

## 功能

- 📚 **文献库侧栏**：专题 → 论文两级管理，拖 PDF 进去就是一篇文献
- 💬 **选中即问**：阅读器里选中文字 → 弹出提问框 → 右侧对话实时回答
- 📍 **页码引用**：回答里的「第 N 页」可点击，平滑跳回 PDF 对应页并高亮
- 🤖 **教练式伴读**：专用 agent preset，像老师一样带读——制定分步阅读计划（带页码和思考题）→ 逐节讲解点评 → 出题检验批改 → 成绩与薄弱点记入学习档案，跨会话累积
- 🀄 **中英切换**：顶栏一键切换原文 ↔ 纯中文译文；首次生成译文时自动下载安装 [BabelDOC](https://github.com/funstory-ai/BabelDOC) 翻译环境（uv + 托管 Python，全程落在用户目录，**无需自己装 Python**）
- 🔍 **全文转录检索**：本地提取 PDF 文本（页眉页脚剔除、断词愈合、段落重排），回答基于真实页码

## 站在这些开源项目的肩膀上

PaperReader 能做的，绝大部分来自下面这些项目的成果。真诚感谢：

| 项目 | 它提供了什么 |
| --- | --- |
| [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | AI agent 运行时：对话、流式输出、工具调用、插件系统。PaperReader 的全部 AI 能力由它驱动 |
| [anywhere-labs/deepseek-harness-desktop](https://github.com/anywhere-labs/deepseek-harness-desktop)（DSH Desktop） | 桌面外壳：窗口、托盘、终端、零环境安装。PaperReader 直接 fork 自它的 v2.0.13 |
| [GGboya/dsh-paper-reader](https://github.com/GGboya/dsh-paper-reader) | 论文伴读插件（本项目预装的核心功能），也以独立插件形式发布在 npm |
| [funstory-ai/BabelDOC](https://github.com/funstory-ai/BabelDOC) | PDF 全文翻译引擎（中英切换功能在背后调用它，首次使用时自动安装） |
| [mozilla/pdf.js](https://github.com/mozilla/pdf.js) | PDF 渲染与文本提取 |
| [Electron](https://github.com/electron/electron) | 跨平台桌面运行时 |

以及 [uv](https://github.com/astral-sh/uv)（Python 环境引导）等依赖生态里的众多项目。

**License 说明**：本仓库代码沿用 fork 来源的 [MIT LICENSE](LICENSE)。BabelDOC 为 AGPL-3.0，以独立进程方式在首次使用翻译时下载安装，不包含在本安装包内。

## 数据与隐私

- 所有数据存在本地用户目录 `~/.paperreader`（文献、会话、学习档案、翻译缓存）
- 对话能力需要按界面提示完成登录（DeepSeek Harness 账号体系），提问内容会发送给你配置的模型服务
- 翻译功能默认使用你自己配置的 `translate` 端点，译文缓存在本地

## 免责说明

独立的社区开源项目，与深度求索（DeepSeek）不存在隶属、合作、授权或背书关系；与 DSH Desktop 团队亦无隶属关系。GitHub Contributors 中显示的贡献者来自 fork 继承的提交历史。

## 反馈

Bug 和建议请提 [Issue](https://github.com/GGboya/PaperReader/issues)。
