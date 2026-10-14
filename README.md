# Anti-Defensive Writing · Tutorial

**让教程直接讲清知识、机制与条件。**

受 [Anti-Defensive Writing](https://github.com/Adkid-Zephyr/anti-defensive-writing-Skill) 启发的教程版 Agent Skill，聚焦教程、技术讲解和学习材料中的反防御性表达。

当前为初稿，正在补充实际使用案例与安装验证。

## 它解决什么问题

技术讲解中常见这样的句子：

> 为了避免教程过于复杂，这里暂时不考虑并发，但这不代表并发不重要。

直接说明选择理由后，可以写成：

> 本节采用串行执行，便于逐步观察每次调用及其结果。

这个 Skill 帮助识别和修改六类表达：预设反驳、反复免责、自我贬低、范围辩解、无必要的否定对照，以及提前堆叠不足。修改时保留技术事实、必要条件和原有教学范围。

## 修改示例

以下为手工编写的规则示例。

| 修改前 | 修改后 |
| --- | --- |
| 这并不意味着工具会自动执行。 | 模型返回工具调用请求，应用程序根据请求执行对应函数。 |
| 需要强调，重试并不意味着能够保证成功。 | 临时网络故障可以通过重试恢复；凭据错误需要修正配置。 |
| 保存历史不等于恢复运行。 | 历史记录保存已发生的交互；恢复运行还需要保存执行位置，例如下一步应请求模型还是执行工具。 |

## 安装到 Codex 项目

将本仓库中的 `skills/anti-defensive-writing-tutorial/` 整个目录复制到目标项目的 `.agents/skills/` 下：

```text
你的项目/
└── .agents/
    └── skills/
        └── anti-defensive-writing-tutorial/
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

完整规则见 [SKILL.md](skills/anti-defensive-writing-tutorial/SKILL.md)。

## 来源与许可

本 Skill 借鉴 Adkid-Zephyr 的 [anti-defensive-writing-Skill](https://github.com/Adkid-Zephyr/anti-defensive-writing-Skill)，将直接陈述、避免自我削弱等思想用于教程表达。本文保留原有教学目标、事实精度及必要的技术条件。

采用 [MIT 许可证](LICENSE)，保留原作者版权声明。

## 待完善

- 补充实际调用产生的修改前后案例。
- 试用含必要限制的段落，以及本来就表达清楚的段落。
- 在独立环境中验证 README 的安装与调用步骤。
