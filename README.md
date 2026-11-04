# 单词变考题 · vocab-to-exam

把今天背过的英语单词，变成可以直接作答的原创考试练习。

一个以中文交互的 Agent Skill，面向四级、六级、考研英语一和英语二。输入词表后，按指定考试和题型生成试题；交卷后提供答案、定位解析、词汇覆盖明细和复习建议。

## 快速体验

安装后，在 Codex 中输入：

```text
请使用 $vocab-to-exam。
今天背的词：adapt, challenge, maintain, benefit, contribute,
efficient, resource, sustainable, approach, significant。
生成一篇四级仔细阅读，5道选择题。先不要给答案，等我做完再批改。
```

作答时回复 `1A 2C 3B 4D 5A` 即可。以上字母仅为提交格式示例，不是试题答案。

## 支持什么

| 考试 | 练习类型 |
| --- | --- |
| 四级、六级 | 仔细阅读、长篇阅读段落匹配、选词填空、汉译英 |
| 考研英语一 | 传统阅读、新题型、划线部分英译汉 |
| 考研英语二 | 传统阅读、新题型、段落英译汉 |

- 接受换行、逗号分隔、含中文释义的词表，也接受词组。
- 可指定篇数、题量、主题、篇幅和难度；只给词表时，默认四级仔细阅读1篇、5道题。
- 默认先给试题；要求“附答案／学习版”时，答案解析集中放在题后。
- 词汇覆盖按正文核查，区分屈折形式与派生词，明确列出未覆盖词。
- 批改包含答案证据与错误原因；翻译允许合理的不同译法。

更多可复制提示见 [使用示例](docs/examples.md)。

## 安装到 Codex

本仓库提供技能源文件，无需运行服务、安装 Python 依赖或配置额外 API 密钥。使用时需要可正常工作的 Codex 环境。

1. 下载仓库：在 GitHub 点击 **Code → Download ZIP**，然后解压。
2. 将仓库内的整个 `vocab-to-exam` 文件夹复制到以下任一位置：
   - 当前用户使用：`~/.agents/skills/vocab-to-exam/`（Windows 对应 `%USERPROFILE%\.agents\skills\vocab-to-exam\`）。
   - 当前项目使用：`<项目根目录>/.agents/skills/vocab-to-exam/`。
3. 确认 `SKILL.md` 直接位于该文件夹内，避免多嵌套一层。
4. 在对话中输入 `$vocab-to-exam` 和词表；若技能未出现，重启 Codex 后再试。

这些路径和发现方式依据 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。其他支持 Agent Skills 的工具需要按其说明安装，本仓库未逐一验证兼容性。

## 仓库结构

```text
.
├── README.md
├── .gitignore
├── .gitattributes
├── docs/
│   ├── examples.md            # 使用提示示例
│   ├── github-upload.md       # 手动上传步骤
│   └── syllabus-audit.md      # 已有考纲核查记录与限制
└── vocab-to-exam/             # 安装时复制整个文件夹
    ├── SKILL.md               # 技能入口与出题、批改规则
    ├── agents/openai.yaml     # 显示名称与默认提示
    └── references/exam-formats.md
## 维护

反馈题目问题时，请附考试类型、词表、完整试题和有疑问的题号，便于复现。更新规则时，同时检查题型参考、答案展示方式和覆盖统计是否一致。

如何把这份仓库上传到 GitHub，见 [上传指南](docs/github-upload.md)。
