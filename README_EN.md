# Anti-Defensive Writing · Tutorial

**Remove repetitive justifications and disclaimers. Explain mechanisms and conditions clearly.**

An Agent Skill for reviewing and revising defensive language in tutorials, technical explanations, and learning materials.

[中文 README](README.md) · [中文 Skill](skills/anti-defensive-writing-tutorial/SKILL.md) · [English Skill](skills/anti-defensive-writing-tutorial-en/SKILL.md)

## Install the Codex plugin

The plugin includes Chinese and English skills with no additional runtime dependencies.

To install from a local checkout, run these commands from the repository root:

```bash
codex plugin marketplace add .
codex plugin add anti-defensive-writing-tutorial@tutorial-writing
```

To install from GitHub:

```bash
codex plugin marketplace add zhu-chen/anti-defensive-writing-tutorial
codex plugin add anti-defensive-writing-tutorial@tutorial-writing
```

After installation, select **Anti-Defensive Writing · Tutorial** in a new conversation and use the skill for your preferred language.

## What problem does it solve?

As more people use language models to learn, defensive writing from GPT models also appears in tutorials, technical explanations, and learning materials. Existing anti-defensive writing skills primarily address academic papers. This skill provides rules tailored to teaching and learning.

Some technical explanations rush to tell readers what something “does not mean” before explaining the mechanism:

> This does not mean that tools execute automatically.

Readers need to know who requests the call and who executes the tool. State the process directly:

> The model returns a tool-call request, and the application executes the corresponding function.

The revision explains the responsibilities of the model and the application. The core principle is: **Use the text to explain knowledge, mechanisms, and conditions. Make every sentence advance understanding.**

## Rules at a glance

| Pattern | Revision approach |
| --- | --- |
| Preemptive rebuttals | Explain the mechanism and what actually happens. |
| Repeated disclaimers | Specify conditions, consequences, and how to respond. |
| Self-deprecation | Replace vague labels such as “crude” or “incomplete” with observable behavior. |
| Scope justifications | Explain how the current choice helps readers understand. |
| Unnecessary negative contrasts | State meanings, responsibilities, and differences directly. |
| Premature lists of shortcomings | Explain relevant limitations where readers need to decide or act. |

Preserve technical facts, necessary conditions, and the original teaching scope. Judge each sentence in context and retain negation that supports technical corrections, conceptual distinctions, or safe operation.

## Revision examples

These are manually written examples illustrating the rules.

| Context | Before | After |
| --- | --- | --- |
| Coding tutorial | It must be emphasized that retries do not guarantee success. | Retries can recover from temporary network failures; credential errors require configuration changes. |
| Concept explanation | An iterable is not an iterator; the two must not be confused. | An iterable provides an iterator through `iter()`; an iterator returns elements one at a time through `next()`. |
| Agent tutorial | Saving history is not the same as resuming execution. | History records past interactions; resuming execution also requires saving the execution position, such as whether to request a model response or execute a tool next. |

## When to use it

- **Revise tutorial passages:** replace repeated justifications, disclaimers, and self-deprecation with concrete explanations.
- **Review technical explanations:** identify preemptive rebuttals and unnecessary negative contrasts, with suggested revisions and reasons.
- **Organize learning materials:** merge repeated statements and place necessary conditions beside the relevant knowledge or action.

## Install a skill separately

You can also copy the skill folder for your preferred language into your project's `.agents/skills/` directory. Both languages can be installed together:

```text
your-project/
└── .agents/
    └── skills/
        ├── anti-defensive-writing-tutorial/
        │   └── SKILL.md
        └── anti-defensive-writing-tutorial-en/
            └── SKILL.md
```

Codex discovers skills in the project's `.agents/skills/` directory and supports symlinks to skill directories. If a newly added skill does not appear, restart Codex. See the [official skill documentation](https://learn.chatgpt.com/docs/build-skills).

## Usage

After installation, name the skill and provide the text:

```text
$anti-defensive-writing-tutorial-en
Revise the defensive language in this tutorial passage. Preserve technical facts and necessary conditions:

[Paste the text]
```

You can also request a review first:

```text
$anti-defensive-writing-tutorial-en
Review this technical explanation for defensive language. List the original sentences, suggested revisions, and reasons.
```

For the Chinese version, use `$anti-defensive-writing-tutorial`. See the [Chinese skill](skills/anti-defensive-writing-tutorial/SKILL.md) and [English skill](skills/anti-defensive-writing-tutorial-en/SKILL.md) for the complete rules.

## Distribute the plugin

Push this repository to GitHub to distribute it through the marketplace commands above. The marketplace is named `tutorial-writing`, and the plugin is named `anti-defensive-writing-tutorial`.

```text
anti-defensive-writing-tutorial/
├── .agents/plugins/marketplace.json  # Repository marketplace
├── .codex-plugin/plugin.json         # Codex compatibility manifest and presentation
├── plugin.json                       # Portable plugin manifest
├── skills/
│   ├── anti-defensive-writing-tutorial/
│   │   └── SKILL.md                  # Chinese
│   └── anti-defensive-writing-tutorial-en/
│       └── SKILL.md                  # English
└── README.md / README_EN.md
```

For subsequent releases, update the version in both plugin manifests. Users can run `codex plugin marketplace upgrade tutorial-writing` to refresh the source, then run the plugin installation command again to update their installation.

A repository marketplace supports GitHub distribution. Listing in the OpenAI public plugin directory requires a separate submission and review. See the official [packaging documentation](https://developers.openai.com/plugins/build/plugins) and [submission process](https://developers.openai.com/plugins/deploy/submission).

## Attribution and license

Inspired by Adkid-Zephyr's [Anti-Defensive Writing](https://github.com/Adkid-Zephyr/anti-defensive-writing-Skill), applying direct statements and the removal of self-undermining language to tutorials, technical explanations, and learning materials.

Released under the [MIT License](LICENSE), retaining the original author's copyright notice.
