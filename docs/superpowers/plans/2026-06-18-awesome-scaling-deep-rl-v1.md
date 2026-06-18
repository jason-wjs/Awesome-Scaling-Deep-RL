# Awesome Scaling Deep RL V1 Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build the complete v1 of `Awesome-Scaling-Deep-RL` as a small, source-backed awesome-list repository about scaling under deep RL objectives.

**Architecture:** The repository is documentation-first: one README is the user-facing artifact, while the spec and plan live under `docs/superpowers/`. Subagents perform independent source-backed paper discovery; the main agent integrates and verifies the final README to avoid write conflicts.

**Tech Stack:** Markdown, Git, shell sanity checks, internet search with primary sources.

---

## File Structure

- Create: `README.md`
  - Public awesome-list entry point.
  - Contains scope, problem map, tag legend, news, citation placeholder, table of contents, five paper tables, and contribution note.
- Already created: `docs/superpowers/specs/2026-06-18-awesome-scaling-deep-rl-design.md`
  - Design source of truth.
- Create: `docs/superpowers/plans/2026-06-18-awesome-scaling-deep-rl-v1.md`
  - This implementation plan.

## Execution Mode

The user explicitly requested subagents.
Use subagents only for independent source-backed paper research.
Do not let subagents edit `README.md`, because all paper entries converge into the same file.

## Task 1: Confirm Baseline

**Files:**
- Read: `docs/superpowers/specs/2026-06-18-awesome-scaling-deep-rl-design.md`

- [x] **Step 1: Initialize the independent repository**

Run:

```bash
git init
```

Expected: a new `.git/` directory exists inside `Awesome-Scaling-Deep-RL/`.

- [x] **Step 2: Write the design spec**

Create `docs/superpowers/specs/2026-06-18-awesome-scaling-deep-rl-design.md` with the agreed hybrid structure, strict RL-objective boundary, five-section taxonomy, and source-backed workflow.

- [x] **Step 3: Commit the design spec**

Run:

```bash
git add docs/superpowers/specs/2026-06-18-awesome-scaling-deep-rl-design.md
git commit -m "docs: add awesome scaling deep rl design"
```

Expected: initial commit records the spec.

## Task 2: Run Source-Backed Paper Discovery

**Files:**
- No direct file writes.

- [x] **Step 1: Dispatch five independent research agents**

Dispatch one agent for each section:

1. `Scaling Laws & Predictability`
2. `Network and Representation Capacity`
3. `Actor-Critic Capacity and Update Ratios`
4. `Data, Replay and Compute`
5. `Barriers and Remedies`

Each agent must return candidate papers with title, year, venue/source, paper URL, official code URL if any, official project URL if any, a conservative tagged finding, and why the paper satisfies the RL-objective boundary.

- [x] **Step 2: Independently verify candidates with primary sources**

Use internet search and source pages to verify:

- title
- year
- venue or source
- paper URL
- official code URL
- official project URL
- whether the paper is truly about RL-objective scaling

Expected: reject pure imitation, VLA, LLM-RL, supervised trajectory modeling, model-based/world-model scaling, and papers that are only "large-scale" without scaling analysis.

- [x] **Step 3: Select around 20 core papers**

Use this target distribution without forcing quotas:

- Scaling Laws & Predictability: 4-5 papers
- Network and Representation Capacity: 3-4 papers
- Actor-Critic Capacity and Update Ratios: 4-5 papers
- Data, Replay and Compute: 4-5 papers
- Barriers and Remedies: 5-6 papers

Expected: a smaller list is acceptable when candidates are not central enough.

## Task 3: Create README Scaffold

**Files:**
- Create: `README.md`

- [x] **Step 1: Add title and badges**

Use:

```markdown
# Awesome Scaling Deep RL

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
[![PR's Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](http://makeapullrequest.com)
```

- [x] **Step 2: Add scope and research questions**

Add the one-sentence scope and four core questions from the design spec.

- [x] **Step 3: Add explicit scope boundary**

Add `In Scope` and `Out of Scope` subsections matching the design spec.

- [x] **Step 4: Add problem map and tag legend**

Add compact `Why RL Scaling Is Hard` and `Tag Legend` sections.

- [x] **Step 5: Add News, Citation, and Table of Contents**

Use a placeholder citation block that says no survey citation is available yet.

- [x] **Step 6: Add five empty paper tables**

For each section, use:

```markdown
| Title | Venue | Year | Axis / Finding | Code | Project |
|:------|:-----:|:----:|:---------------|:----:|:-------:|
```

## Task 4: Populate README With Verified Core Papers

**Files:**
- Modify: `README.md`

- [x] **Step 1: Insert verified entries section by section**

For each accepted paper, write an entry in this form:

```markdown
| ![Star](https://img.shields.io/github/stars/<owner>/<repo>.svg?style=social&label=Star) <br>[**Paper Title**](paper-url) <br> | Venue | Year | `[tag] [tag]` Conservative source-backed finding. | [Github](code-url) | [Project](project-url) |
```

If no official code or project exists, use `-`.

- [x] **Step 2: Sort each table**

Sort each section by year descending.
Within the same year, put the most directly relevant scaling papers first.

- [x] **Step 3: Remove weak or borderline entries**

Reject entries that only weakly match scaling RL or violate the out-of-scope boundary.
Do not pad sections to reach a quota.

## Task 5: Verify README Quality

**Files:**
- Read: `README.md`
- Read: `docs/superpowers/specs/2026-06-18-awesome-scaling-deep-rl-design.md`

- [x] **Step 1: Check markdown tables**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
text = Path('README.md').read_text()
assert '# Awesome Scaling Deep RL' in text
for heading in [
    'Scaling Laws & Predictability',
    'Network and Representation Capacity',
    'Actor-Critic Capacity and Update Ratios',
    'Data, Replay and Compute',
    'Barriers and Remedies',
]:
    assert heading in text, heading
assert text.count('| Title | Venue | Year | Axis / Finding | Code | Project |') == 5
print('README structure check passed')
PY
```

Expected: `README structure check passed`.

- [x] **Step 2: Check hard exclusions**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
text = Path('README.md').read_text().lower()
blocked = [
    'decision transformer',
    'trajectory transformer',
    'gato',
    'rlhf',
    'rlvr',
    'vision-language-action',
    'vla pretraining',
    'world model scaling',
]
violations = [term for term in blocked if term in text and 'out of scope' not in text[text.find(term)-200:text.find(term)+200]]
if violations:
    raise SystemExit(f'blocked terms need manual review: {violations}')
print('scope exclusion check passed')
PY
```

Expected: `scope exclusion check passed`, or a specific list of terms to manually inspect.

- [x] **Step 3: Check link shapes**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
import re
text = Path('README.md').read_text()
links = re.findall(r'\]\(([^)]+)\)', text)
bad = [u for u in links if not (u.startswith('http://') or u.startswith('https://') or u.startswith('#'))]
if bad:
    raise SystemExit(f'non-web links found: {bad}')
print(f'link shape check passed for {len(links)} links')
PY
```

Expected: all markdown links are HTTP(S) links or anchors.

- [x] **Step 4: Review source-backed findings manually**

Read every `Axis / Finding` sentence and confirm it is conservative, tagged, and not broader than the verified sources.

## Task 6: Final Git Commit and Goal Completion

**Files:**
- Add: `README.md`
- Add: `docs/superpowers/plans/2026-06-18-awesome-scaling-deep-rl-v1.md`

- [x] **Step 1: Inspect git status and diff**

Run:

```bash
git status --short
git diff -- README.md docs/superpowers/plans/2026-06-18-awesome-scaling-deep-rl-v1.md
```

Expected: only v1 README and plan changes are pending.

- [x] **Step 2: Commit v1**

Run:

```bash
git add README.md docs/superpowers/plans/2026-06-18-awesome-scaling-deep-rl-v1.md
git commit -m "docs: build curated scaling deep rl v1"
```

Expected: commit succeeds.

- [x] **Step 3: Final verification**

Run:

```bash
git status --short
git log --oneline -2
```

Expected: clean worktree and two commits: design spec, then v1 README/plan.
