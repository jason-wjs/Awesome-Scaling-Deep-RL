# Awesome Scaling Deep RL Design

## Goal

Create an independent GitHub awesome-list repository named `Awesome-Scaling-Deep-RL`.
The repository curates a small, source-backed v1 paper list about how deep RL agents scale under RL objectives with model size, data, replay, compute, component capacity, and why that scaling succeeds or fails.

The v1 list should be deliberately selective: around 20 core papers, not a comprehensive survey.

## Research Questions

The repository is organized around four questions:

1. Does deep RL exhibit predictable scaling behavior similar to supervised learning?
2. When do larger models, more data, or more compute improve RL performance?
3. What RL-specific mechanisms prevent stable scaling?
4. Which remedies make scaling more reliable under RL objectives?

## Repository Boundary

`Awesome-Scaling-Deep-RL/` is an independent Git repository located beside `Awesome-Human-Interaction-Motion-Generation/`.
It may borrow the existing repository's README style, badges, and table presentation, but it has no code or git dependency on that repository.

## Scope

### In Scope

Papers are in scope when their main evidence concerns scaling under an RL objective:

- online deep RL
- offline RL when value or policy improvement under an RL objective is central
- value-based RL
- actor-critic RL
- self-play RL
- robot or embodied RL only when the paper explicitly studies RL-objective scaling
- model size, depth, width, representation capacity, critic capacity, actor capacity, update-to-data ratio, replay, data scale, distributed compute, and remedies for scaling failures

### Out of Scope

The v1 repository excludes:

- LLM-RL, RLHF, RLVR, and reasoning RL
- pure imitation learning
- behavior cloning scaling
- VLA or robot foundation model pretraining scaling
- Decision Transformer, Trajectory Transformer, Gato, and similar supervised trajectory-modeling papers
- model-based RL and world-model scaling
- papers that only use "large-scale" as an engineering descriptor without analyzing scaling behavior or RL-specific bottlenecks

## README Architecture

`README.md` should contain:

1. Title and badges.
2. One-sentence scope statement.
3. Core research questions.
4. Explicit scope boundary with `In Scope` and `Out of Scope`.
5. A short problem map named `Why RL Scaling Is Hard`.
6. Tag legend.
7. News.
8. Citation placeholder.
9. Table of contents.
10. Five paper sections with markdown tables.
11. A brief contribution note.

The README should remain an awesome list, not a long survey. Explanatory prose should be compact and used to make the taxonomy clear.

## Problem Map

The `Why RL Scaling Is Hard` section should identify RL-specific obstacles:

- non-stationary targets
- bootstrapping and critic error amplification
- exploration and data distribution shift
- actor-critic capacity mismatch
- plasticity loss and primacy bias
- unstable optimization and normalization sensitivity

This section should be short and should not overclaim beyond the listed papers.

## Paper Sections

### 1. Scaling Laws & Predictability

Papers that directly ask whether RL performance predictably improves with scale.
Strong entries include systematic scaling sweeps, fitted scaling trends, cross-scale prediction, or explicit scaling-law claims.

### 2. Network and Representation Capacity

Papers about network capacity itself: parameter count, depth, width, backbone, representation learning, and feature collapse under RL objectives.
Transformer or MoE entries may appear here only if trained or evaluated under an RL objective.

### 3. Actor-Critic Capacity and Update Ratios

Papers about RL component capacity and update dynamics: critic ensembles, value distribution, actor-vs-critic bottlenecks, update-to-data ratio, replay ratio, critic overfitting, and policy improvement speed versus value learning speed.

### 4. Data, Replay and Compute

Papers about environment steps, dataset scale under RL objectives, replay buffers, distributed actors, throughput, self-play compute, and large-scale training systems.
This section should not include large systems unless the paper provides evidence about scaling behavior or scaling bottlenecks.

### 5. Barriers and Remedies

Papers that explain or address why scaling fails: plasticity loss, primacy bias, dormant neurons, policy churn, instability, normalization, regularization, bootstrapping, and overestimation.
This section is the main diagnostic section for why RL scaling differs from supervised learning.

## Table Schema

Each paper table uses:

```markdown
| Title | Venue | Year | Axis / Finding | Code | Project |
|:------|:-----:|:----:|:---------------|:----:|:-------:|
```

The title cell may include a GitHub stars badge when an official repository exists:

```markdown
![Star](https://img.shields.io/github/stars/<owner>/<repo>.svg?style=social&label=Star) <br>[**Title**](paper-link) <br>
```

If code or project pages do not exist, use `-`.

## Tags

Use lightweight tags inside `Axis / Finding`, not separate columns.
Initial tags:

- `[scaling-law]`
- `[model-size]`
- `[depth]`
- `[width]`
- `[representation]`
- `[critic]`
- `[actor]`
- `[utd]`
- `[replay]`
- `[data]`
- `[compute]`
- `[distributed]`
- `[offline-rl]`
- `[self-play]`
- `[robotics]`
- `[transformer]`
- `[moe]`
- `[plasticity]`
- `[normalization]`
- `[instability]`

Each finding must state a concrete, conservative claim supported by the paper.
Do not write generic findings such as "studies scaling in RL."

## V1 Paper Strategy

The initial README should contain about 20 papers, with quality prioritized over coverage:

- Scaling Laws & Predictability: 4-5 papers
- Network and Representation Capacity: 3-4 papers
- Actor-Critic Capacity and Update Ratios: 4-5 papers
- Data, Replay and Compute: 4-5 papers
- Barriers and Remedies: 5-6 papers

These ranges are guidance, not quotas. If a section has fewer truly central papers, keep it smaller.

## Source-Backed Collection Workflow

Do not fill entries from memory.
For each paper entry:

1. Search primary sources first: arXiv, OpenReview, conference proceedings, official project pages, and official GitHub repositories.
2. Verify title, venue or source, year, paper link, code link, project link, and relevance to the strict RL-objective boundary.
3. Confirm that the paper directly studies a scaling axis, a scaling failure mechanism, or a remedy for scaling under RL objectives.
4. Write the `Axis / Finding` sentence conservatively.
5. Keep weaker or borderline candidates out of v1.

## Files

The v1 repository should contain:

- `README.md`
- `docs/superpowers/specs/2026-06-18-awesome-scaling-deep-rl-design.md`
- `docs/superpowers/plans/2026-06-18-awesome-scaling-deep-rl-v1.md`

No `CONTRIBUTING.md` is needed for v1.
Figures are optional and should not block v1.

## Acceptance Criteria

The v1 is complete when:

1. The repository is initialized as an independent git repository.
2. The design spec exists and reflects the agreed scope.
3. The implementation plan exists and covers the v1 build.
4. `README.md` implements the hybrid problem-map plus table structure.
5. The README contains a small, verified, high-signal paper set.
6. Entries follow the table schema and use conservative source-backed findings.
7. The scope boundary clearly excludes imitation, VLA, LLM-RL, supervised trajectory modeling, and world-model scaling.
8. Basic markdown/link sanity checks run successfully or any failures are reported.
