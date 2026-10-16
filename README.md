# Academic PPT Workflow

[English](README.en.md) | 简体中文

**让内容先讲清楚，再把设计还原成可编辑的 PPT。**

面向 Codex 的学术与教学演示制作技能：从材料分析、大纲与逻辑检查出发，使用图像生成工具设计页面，再忠实重建为可编辑演示文稿。适用于课程教学、研究介绍与工作汇报，也支持从现有图片/PDF/PPT直接重建。

| 水墨课堂 · 声乐入门 | 艺术纹理 · 图像风格迁移 |
| :---: | :---: |
| [![声乐基础教学封面](examples/05-vocal-basics/cover.png)](examples/05-vocal-basics/README.md) | [![风格迁移教学封面](examples/04-style-transfer-with-reference/cover.png)](examples/04-style-transfer-with-reference/README.md) |

*两张封面均从可编辑成品的配套PDF导出。点击进入案例，查看原始指令与两个阶段的PDF效果。*

[技能正文](skills/zh-CN/academic-ppt-workflow/SKILL.md) · [五个完整案例](#案例与下载) · [17张参考风格图](style-references/README.md) · [MIT 许可](LICENSE)

## 核心思路

- **逻辑清晰：** 检查章节间、章节内与页面内容三个层次的逻辑，将叙述结构与衔接关系记录于大纲，确保内容合理、讲述流畅。
- **视觉美观：** 以完整大纲为依据，通过图像生成模型设计页面，将内容与关系转化为清晰、美观的视觉表达。
- **输出可编辑：** 分析页面图像，区分可矢量化重建的元素与难以重建的复杂图案，分别重建或保留为图像，交付可编辑 PPTX 与 PDF 预览。

## 九步工作流

| 阶段 | 主要工作 |
| --- | --- |
| 1. 分析要求与材料 | 明确受众、目的、内容、比例与交付范围 |
| 2. 按需调研 | 只补齐必要信息缺口，保存事实来源 |
| 3. 完整大纲 | 规划章节、逐页文案、图形关系与备注 |
| 4. 大纲自查 | 核对内容覆盖与三个层次的叙述逻辑 |
| 5. 确定风格 | 通常生成A/B/C方案；参考图作为真实输入 |
| 6. 全套缩略图 | 覆盖全稿，检查结构、角色与视觉节奏 |
| 7. 图片版 | 独立生成单页、检查、组装并确认 |
| 8. 可编辑重建 | 对照图片基准拆解对象，完成第一轮检查修正 |
| 9. 逐页精查 | 第二轮完整检查，修正并核对最终交付 |

默认在完整图片版检查通过后、可编辑重建前确认一次。已有直接重建或全自动授权时按授权继续；可编辑重建已包含后续精查，不额外增加例行审批。细则以[技能正文](skills/zh-CN/academic-ppt-workflow/SKILL.md)为准。

## 安装与调用

技能按语言分为两个独立目录，每个目录都有完整的 `SKILL.md`、`references/`、`agents/openai.yaml` 和许可证，内部只引用本语言的文档。

| 版本 | 安装源目录 | 技能正文 |
| --- | --- | --- |
| 中文 | `skills/zh-CN/academic-ppt-workflow/` | [中文说明](skills/zh-CN/academic-ppt-workflow/SKILL.md) |
| English | `skills/en/academic-ppt-workflow/` | [English instructions](skills/en/academic-ppt-workflow/SKILL.md) |

两版的工作流与能力一致，仅指令和界面描述的语言不同；演示文稿的语言仍由任务要求决定。**选择一个版本安装即可**，调用名称均为 `$academic-ppt-workflow`。不要同时安装两版，也不要把整个 `skills/` 目录复制到技能发现目录，以免出现同名技能。

当前官方文档列出的用户级位置为 `~/.agents/skills/`，仓库级位置为 `.agents/skills/`；也可以通过 `$skill-installer` 指定上述某一个语言版本的目录安装。详见 [OpenAI 技能文档](https://learn.chatgpt.com/docs/build-skills)。如果现有环境使用不同技能目录，请沿用该环境实际配置。

从本仓库根目录执行下列命令之一（Bash）。如果已有同名技能，先将旧的 `academic-ppt-workflow` 文件夹移出技能发现目录并备份，再复制新版本，避免合并目录后遗留旧文件。切换语言时也按此方式整体替换。

**安装中文版：**

```bash
mkdir -p "$HOME/.agents/skills"
cp -R skills/zh-CN/academic-ppt-workflow "$HOME/.agents/skills/"
```

**或安装英文版：**

```bash
mkdir -p "$HOME/.agents/skills"
cp -R skills/en/academic-ppt-workflow "$HOME/.agents/skills/"
```

复制时保留整个 `academic-ppt-workflow/` 文件夹，无需重命名文件或手动切换入口。若未发现新技能，重启客户端后再试。仓库的 README、案例说明等仍保留中英文切换，案例 PDF 和参考图维持原语言。

新建演示的提示词示例：

```text
请使用 $academic-ppt-workflow，为只学过基础图像处理的本科生，制作一份介绍图像风格迁移的教学PPT。先规划内容与讲解顺序，必要时调研；默认16:9。PPT 的风格可以参考我上传的参考图。
```

直接重建的提示词示例：

```text
我有一个图片版 PPT，现在请用 $academic-ppt-workflow 这个技能来帮我将它进行可编辑化重建吧。
```

执行完整流程需要可用的图像生成、文件读写、PPT构建与渲染能力；有信息缺口时还需要检索能力。具体工具不锁定到某一库，能力不足时应明确未完成阶段。

## 案例与下载

五组展示案例，涵盖 **120页内容**，保留两个制作阶段的 **10份PDF**，附用户提示词和参考风格图。

| 案例 | 页数 | 风格参考 | 图片审阅版 PDF | 可编辑重建效果 PDF | 提示词 |
| --- | ---: | --- | --- | --- | --- |
| [1 · 越狱攻击教学](examples/01-jailbreak-teaching/README.md) | 22 | S0 | [PDF](examples/01-jailbreak-teaching/image-review.pdf) | [PDF](examples/01-jailbreak-teaching/editable.pdf) | [查看](examples/01-jailbreak-teaching/prompt.md) |
| [2 · 工作进度汇报](examples/02-work-progress/README.md) | 18 | S10 | [PDF](examples/02-work-progress/image-review.pdf) | [PDF](examples/02-work-progress/editable.pdf) | [查看](examples/02-work-progress/prompt.md) |
| [3 · 风格迁移，无参考图](examples/03-style-transfer-no-reference/README.md) | 32 | 无 | [PDF](examples/03-style-transfer-no-reference/image-review.pdf) | [PDF](examples/03-style-transfer-no-reference/editable.pdf) | [查看](examples/03-style-transfer-no-reference/prompt.md) |
| [4 · 风格迁移，有参考图](examples/04-style-transfer-with-reference/README.md) | 30 | S9 | [PDF](examples/04-style-transfer-with-reference/image-review.pdf) | [PDF](examples/04-style-transfer-with-reference/editable.pdf) | [查看](examples/04-style-transfer-with-reference/prompt.md) |
| [5 · 声乐基础教学](examples/05-vocal-basics/README.md) | 18 | S1 | [PDF](examples/05-vocal-basics/image-review.pdf) | [PDF](examples/05-vocal-basics/editable.pdf) | [查看](examples/05-vocal-basics/prompt.md) |

本包用于案例展示，不含PPTX源文件或字体安装包。“可编辑重建效果PDF”是从可编辑PPT导出的展示副本，PDF本身不提供PPT对象编辑能力。

## 文件结构

```text
academic-ppt-workflow/
├── README.md / README.en.md
├── LICENSE / LICENSE-SCOPE.md / LICENSE-SCOPE.en.md / LICENSES/
├── skills/
│   ├── zh-CN/academic-ppt-workflow/  # 独立中文版技能
│   └── en/academic-ppt-workflow/     # 独立英文版技能
├── examples/                     # 五组案例PDF、提示词、两张封面
└── style-references/             # S0–S16参考风格原图
```

参考图统一放在图库中，各案例通过链接对应。技能与案例分开，安装时只需复制所选语言下的 `academic-ppt-workflow/` 目录。

## 发布与许可

解压后将本目录内容作为GitHub仓库根目录，通过Git或GitHub Desktop提交。技能与本仓库贡献者享有权利的内容采用 [MIT许可](LICENSE)，要求保留版权声明与许可文本；第三方素材适用[许可范围说明](LICENSE-SCOPE.md)。
