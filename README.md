# Traceable Meeting Minutes

[![skills.sh](https://skills.sh/b/Rangooo/traceable-meeting-minutes)](https://skills.sh/Rangooo/traceable-meeting-minutes)

A general-purpose Agent Skill for turning meetings, interviews, research calls, and earnings calls into accurate, actionable, and traceable minutes.

Unlike a fixed meeting template, this skill selects between:

- **Operational mode** for short internal meetings: decisions, action owners, due dates, acceptance criteria, blockers, parking-lot items, and follow-up.
- **Analytical mode** for long interviews and earnings calls: themes, evidence locations, numerical scope, disagreements, management claims, and optional cross-validation.
- **Hybrid mode** when both execution tracking and evidence-heavy analysis matter.

The core workflow follows the open `SKILL.md` format and does not depend on a specific model vendor. `agents/openai.yaml` is optional interface metadata for compatible OpenAI/Codex clients.

## Install

Install with the open `skills` CLI:

```bash
npx skills add Rangooo/traceable-meeting-minutes --skill traceable-meeting-minutes
```

Or clone/copy this repository into the skills directory used by your Agent. The entry point is the root [`SKILL.md`](SKILL.md).

## Use

```text
Use $traceable-meeting-minutes to turn this 45-minute design review into concise minutes.
Capture explicit decisions and action items, but do not infer owners or deadlines.
```

```text
Use $traceable-meeting-minutes to structure this earnings-call transcript.
Organize by theme, distinguish actual results from guidance and run rate,
annotate numerical scope, and cross-validate material claims with suitable sources.
```

```text
使用 $traceable-meeting-minutes 整理这份会议录音。提取决策、行动项、负责人和截止时间；
原文没有明确的信息不要猜测。
```

Common inputs include `.mp3`, `.m4a`, `.wav`, `.flac`, `.docx`, `.txt`, `.md`, and `.zip`. Audio transcription depends on a local tool or a service explicitly authorized by the user; no speech model is bundled.

## What it adds

- Evidence locations for material conclusions, decisions, actions, and numbers
- Explicit separation of facts, opinions, forecasts, and inference
- Numerical-scope checks such as GAAP/non-GAAP, reported/organic, YoY/QoQ, and actual/guidance/run rate
- Action-item acceptance criteria without fabricating owners or deadlines
- Claim-specific cross-validation using original records, participants, internal systems, official sources, research, databases, media, or customer evidence
- Privacy boundaries for external transcription, search, communication, and publishing

## 中文说明

这是一个面向通用 AI Agent 的会议纪要技能，适用于内部短会、访谈、专家电话会及 earnings call。它不仅整理摘要和行动项，还会保留原文定位、检查数字口径，并在用户要求时根据说法类型选择合适渠道交叉验证。

## Privacy and limitations

- Confirm that you have the right to process and retain non-public meeting material.
- Do not upload internal recordings or transcripts to external services without explicit authorization.
- Automated transcription may misidentify speakers, numbers, and proper nouns; material conclusions should be checked against the source.
- Cross-validation can establish support, conflict, or non-comparability between evidence; it cannot guarantee that an internal claim is true.

## License

MIT License. See [`LICENSE`](LICENSE).
