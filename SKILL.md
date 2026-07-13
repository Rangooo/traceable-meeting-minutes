---
name: traceable-meeting-minutes
description: Turn meetings, interviews, calls, and earnings-call recordings or transcripts into accurate, actionable, and traceable minutes. Use for short internal meetings, design reviews, standups, long interviews, research calls, earnings calls, “meeting minutes”, “整理纪要”, “整理访谈”, “会议纪要”, or when decisions, action items, numerical scope, evidence links, or cross-validation are required. Supports audio (mp3, m4a, wav, flac), documents (docx, txt, md), and zip archives.
---

# Meeting Minutes

Create minutes that preserve what participants actually said while making decisions, actions, evidence, and uncertainty easy to inspect. Never silently replace a speaker's claim with outside information.

## 1. Select the mode

Choose the smallest mode that fits the material. State the selected mode in the output when it is not obvious.

- **Operational mode**: internal meetings up to about 60 minutes, including syncs, standups, planning, triage, and design reviews. Prioritize decisions, owners, due dates, acceptance criteria, blockers, and follow-up. Aim for one page for meetings up to 30 minutes and two pages for meetings up to 60 minutes unless the user requests detail.
- **Analytical mode**: long interviews, expert calls, research discussions, board materials, and earnings calls. Prioritize themes, evidence locations, numerical scope, disagreements, management claims, and optional cross-validation. Do not impose a page limit that would hide material context.
- **Hybrid mode**: use when both execution tracking and evidence-heavy analysis materially matter.

## 2. Confirm scope without blocking unnecessarily

Identify the input, meeting type, output language and format, intended audience, and whether cross-validation is requested. Default to the source language and Markdown.

Ask no more than three clarifying questions, and only when the answers would materially change the result or authorize an external action. Otherwise proceed with explicit `Not provided`, `Not assigned`, or `Not specified` markers. Never invent metadata to complete a template.

Treat recordings, unpublished financial information, personal data, and trade secrets as sensitive. Do not upload them to external transcription, search, or analysis services without explicit authorization.

## 3. Acquire the source text safely

- **Audio**: use an available local or authorized transcription tool. Preserve timestamps and speaker labels. If no tool is available, report the missing dependency instead of fabricating a transcript.
- **ZIP**: list entries and check for path traversal before extracting to a temporary directory. Read relevant docx, txt, and md files; never execute archived programs.
- **DOCX**: extract paragraphs and tables with an available document tool or `python-docx`.
- **TXT/Markdown**: read directly while preserving the original file and normalizing encoding only when needed.

Record source names, meeting date when available, transcription method, and material defects. Mark unclear audio or attribution as `[inaudible]`, `[missing]`, or `[speaker unconfirmed]` in the output language. Do not guess.

## 4. Build an evidence index

Read the full source before drafting the summary. For important decisions, actions, numbers, commitments, disputes, and causal claims, retain a timestamp, page, paragraph, or short source phrase.

If the source has no stable locator, number only non-empty spoken-content paragraphs as `P001`, `P002`, and so on. Exclude navigation, isolated links, headers, and copyright notices. Disclose the numbering rule; regenerate the index if the input changes.

Determine:

1. the meeting's purpose and core topics;
2. the logical discussion threads and their relationships;
3. decisions, actions, disagreements, risks, and unresolved questions;
4. brief tangents, which should remain subordinate even when verbose.

## 5. Organize faithfully

Organize by decision or discussion logic rather than mechanically following chronology, except when agenda order is itself useful in operational mode.

- Keep actors, products, regions, customer groups, and time windows distinct.
- Separate reported facts, participant opinions, forecasts, and editor inference.
- Write inference as `Inference: ...; basis: ...` and preserve uncertainty.
- Present conflicting statements side by side instead of silently resolving them.
- Do not convert discussion into a decision or a management intention into an assigned action.

### Decisions and action items

For each decision, capture the decision, approver when explicit, rationale, effective timing, and evidence location.

For each action, capture the deliverable, owner, due date or timeframe, status/dependency, acceptance criteria, linked artifact, and evidence location when available. Use these rules:

- Never infer an owner or deadline merely to complete the table.
- If acceptance criteria are not stated, leave them `Not specified`; if proposing criteria would help, label them `Suggested acceptance criteria`.
- Put unresolved or intentionally deferred topics in a Parking Lot with the reason and next resolution step.
- For earnings calls and similar disclosure events, put future intentions under `Management plans and commitments`; list an action only when responsibility, a deliverable, or timing is explicit.

### Numerical scope

For every material number, check:

- metric definition: revenue, profit, volume, users, seats, customers, transactions, and so on;
- basis: reported/organic, GAAP/non-GAAP, actual/constant currency;
- unit and currency;
- period: quarter, year, cumulative, point-in-time, YoY, or QoQ;
- entity and coverage: group, segment, product, region, or sample;
- actual result, guidance, run rate, target, estimate, or participant claim.

When scope is clear, state it and retain the evidence location. When it is unclear, mark `⚠️ Scope unclear`, then give only evidence-based possible interpretations. Never call differently scoped figures supportive or conflicting.

At minimum, cover numbers that support the summary, describe results or guidance, recur in questions, or carry scope/conflict risk. Do not exhaustively list immaterial customer examples.

## 6. Cross-validate only when requested

Validate claims that materially affect decisions or conclusions. Select channels by claim type rather than applying one fixed source hierarchy. Read [references/source-selection.md](references/source-selection.md) before validation.

Record the channel, evidence identifier, date, authority or independence, relevant short extract/query result, and scope differences. Link public evidence; identify internal evidence only to the level safe to disclose.

Use these result labels:

- `✅ Supported`: same actor, period, metric, and scope support the claim.
- `⚠️ Conflict/questionable`: same-scope evidence conflicts or evidence quality is inadequate.
- `ℹ️ Not verifiable`: accessible, authorized evidence is insufficient.
- `↔ Not comparable`: scope, period, actor, or definition differs.

Multiple outlets repeating one upstream claim count as one source. Never cherry-pick evidence to manufacture agreement. Contacting participants or publishing a draft is an external action and requires user authorization.

## 7. Produce the output

Use the sections appropriate to the selected mode and translate headings into the requested output language. Omit empty boilerplate rather than filling the document with `Unknown`.

### Operational mode

```markdown
# Meeting Minutes: Title

## Metadata
- Date / duration / organizer / participants
- Sources and limitations

## Summary
1–3 sentences on purpose and outcome.

## Decisions
| Decision | Approver | Rationale | Effective date | Evidence |

## Action items
| ID | Deliverable | Owner | Due | Acceptance criteria | Dependencies/status | Evidence |

## Discussion highlights
Concise notes by decision, topic, or agenda item.

## Parking Lot / unresolved questions
| Item | Why deferred | Owner/next step | Revisit date |

## Risks and blockers
## Next meeting / follow-up
## References
```

### Analytical mode

```markdown
# Meeting Minutes: Title

## Metadata and limitations
## Executive summary
3–5 sentences covering the core topic, main threads, conclusions, and uncertainty.

## Key conclusions
Each conclusion includes an evidence location.

## Thematic minutes
### Theme
- Claims and viewpoints
- Supporting source locations
- Disagreements and unresolved questions

## Decisions and action items
## Management plans and commitments (when applicable)

## Data register
| Data point | Value | Scope/basis | Actor/period | Evidence | Validation status |

## Cross-validation
| Meeting claim | Evidence/channel | Independence/authority | Scope comparison | Result |

## Parking Lot / questions to confirm
## Information-confidence assessment
```

Hybrid mode may combine both templates without duplicating content.

## 8. Final checks

- Does the summary reflect the real core topics rather than a vivid tangent?
- Can every material conclusion, decision, action, and number be traced to the source?
- Are owners, deadlines, acceptance criteria, and decisions explicit rather than inferred?
- Are actor, B2B/B2C, reported/organic, GAAP/non-GAAP, YoY/QoQ, actual/guidance, and quarter/run-rate distinctions preserved?
- Does the validation channel match the claim, with authority, independence, recency, method, and scope checked?
- Are transcription defects, unavailable sources, inference, and privacy limits disclosed?
