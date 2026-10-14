# Anti-Defensive Writing · Tutorial

**去掉教程中反复的辩解与免责，把机制和条件讲清楚。**

一个用于教程、技术讲解和学习材料的 Agent Skill，帮助审阅和修改防御性表述。

[English README](README_EN.md) · [中文 Skill](skills/anti-defensive-writing-tutorial/SKILL.md) · [English Skill](skills/anti-defensive-writing-tutorial-en/SKILL.md)

## Codex 插件安装

本插件包含中文和英文两份 Skill，无额外运行依赖。

从本地仓库安装，在仓库根目录执行：

```bash
codex plugin marketplace add .
codex plugin add anti-defensive-writing-tutorial@tutorial-writing
```

从 GitHub 安装：

```bash
codex plugin marketplace add zhu-chen/anti-defensive-writing-tutorial
codex plugin add anti-defensive-writing-tutorial@tutorial-writing
```

安装后，在新对话中选择 **Anti-Defensive Writing · Tutorial** 插件，使用对应语言的 Skill。

## 它解决什么问题

利用大模型辅助学习愈加普遍，但gpt系列的防御性写作风格写出的东西不仅在论文中出现，也在教程、技术讲解和学习材料中出现。现有的反防御性写作 Skill 主要针对论文等内容，缺少针对教程、技术讲解和学习材料的规则。这个 Skill 解决了这个问题。

技术讲解中，有些句子急于提醒读者“这不意味着什么”，却没有解释机制本身：

> 这并不意味着工具会自动执行。

读者需要知道的是：谁发起调用，谁执行工具。直接写清这个过程：

> 模型返回工具调用请求，应用程序根据请求执行对应函数。

改写后，读者可以理解模型与应用程序各自的职责。这个 Skill 的核心原则是：**把篇幅用于解释知识、机制与条件，让每句话推进理解。**

## 规则速览

| 表达问题 | 修改方向 |
| --- | --- |
| 预设反驳 | 直接解释机制，说明实际发生什么。 |
| 反复免责 | 写清具体条件、后果与处理方式。 |
| 自我贬低 | 用可观察的行为替换“简陋”“不完善”等笼统评价。 |
| 范围辩解 | 说明当前选择如何帮助读者理解。 |
| 无必要的否定对照 | 直接说明概念的含义、职责与差异。 |
| 提前堆叠不足 | 在读者需要作出判断或操作的位置说明相关限制。 |

修改时保留技术事实、必要条件和原有教学范围。根据句子在上下文中的作用判断，保留有助于技术纠错、概念辨析和安全操作的否定表述。

## 修改示例

以下为手工编写的规则示例。

| 场景 | 修改前 | 修改后 |
| --- | --- | --- |
| 代码教学 | 需要强调，重试并不意味着能够保证成功。 | 临时网络故障可以通过重试恢复；凭据错误需要修正配置。 |
| 概念讲解 | 可迭代对象不等于迭代器，不能把两者混为一谈。 | 可迭代对象可以通过 `iter()` 获取迭代器；迭代器通过 `next()` 逐项返回元素。 |
| Agent 教程 | 保存历史不等于恢复运行。 | 历史记录保存已发生的交互；恢复运行还需要保存执行位置，例如下一步应请求模型还是执行工具。 |

## 适用场景

- **修改教程段落**：将反复的辩解、免责和自我贬低改为具体说明。
- **审阅技术讲解**：找出预设反驳和无必要的否定对照，给出修改建议与理由。
- **整理学习材料**：合并重复声明，把必要条件放到相关知识或操作旁边。

## 单独安装 Skill

也可以将所需语言的 Skill 目录复制到目标项目的 `.agents/skills/` 下；两种语言可同时安装：

```text
你的项目/
└── .agents/
    └── skills/
        ├── anti-defensive-writing-tutorial/
        │   └── SKILL.md
        └── anti-defensive-writing-tutorial-en/
            └── SKILL.md
```

Codex 支持从项目的 `.agents/skills/` 发现 Skill，也支持链接到实际目录的软链接。新增 Skill 未出现在列表时，重启 Codex。参见 [官方 Skill 文档](https://learn.chatgpt.com/docs/build-skills)。

## 使用

安装后，在对话中指定 Skill 和待修改的内容：

```text
$anti-defensive-writing-tutorial
请修改下面这段教程中的防御性表述，保留技术事实与必要条件：

[粘贴正文]
```

也可以要求先审阅：

```text
$anti-defensive-writing-tutorial
请检查这篇技术讲解中的防御性表述，列出原句、修改建议和理由。
```

使用英文版时，将 Skill 名称替换为 `$anti-defensive-writing-tutorial-en`。完整规则见[中文 Skill](skills/anti-defensive-writing-tutorial/SKILL.md) 和 [English Skill](skills/anti-defensive-writing-tutorial-en/SKILL.md)。

## 插件分发

将本仓库推送到 GitHub，即可通过上面的 marketplace 命令分发。市场名为 `tutorial-writing`，插件名为 `anti-defensive-writing-tutorial`。

```text
anti-defensive-writing-tutorial/
├── .agents/plugins/marketplace.json  # 仓库 marketplace
├── .codex-plugin/plugin.json         # Codex 兼容清单与展示信息
├── plugin.json                       # 通用插件清单
├── skills/
│   ├── anti-defensive-writing-tutorial/
│   │   └── SKILL.md                  # 中文版
│   └── anti-defensive-writing-tutorial-en/
│       └── SKILL.md                  # 英文版
└── README.md / README_EN.md
```

后续发布时同步更新两份插件清单中的版本号。安装用户可以执行 `codex plugin marketplace upgrade tutorial-writing` 刷新来源，再执行插件安装命令更新安装。

仓库 marketplace 用于 GitHub 分发；如需进入 OpenAI 公共插件目录，还需单独提交审核。参见官方[插件打包文档](https://developers.openai.com/plugins/build/plugins)与[发布流程](https://developers.openai.com/plugins/deploy/submission)。

## 来源与许可

本 Skill 受 Adkid-Zephyr 的 [Anti-Defensive Writing](https://github.com/Adkid-Zephyr/anti-defensive-writing-Skill) 启发，将直接陈述、避免自我削弱等思想用于教程、技术讲解和学习材料。

采用 [MIT 许可证](LICENSE)，保留原作者版权声明。
