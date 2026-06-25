# Experiment Agent

A Claude Code skill for executing, monitoring, interpreting, and verifying experiments in academic research.

## Available Modes

| Mode | Purpose | Trigger Keywords |
|------|---------|-----------------|
| `run` | Execute code + monitor process | run experiment, execute code, train model, benchmark, 跑實驗, 執行程式 |
| `manage` | Plan + track human studies | manage study, track participants, field study, survey, 管理研究, 追蹤參與者 |
| `validate` | Statistical interpretation + reproducibility | validate results, check statistics, reproduce, 驗證結果, 檢查統計 |
| `plan` | Socratic experiment design | plan experiment, design study, what should I test, 規劃實驗, 設計研究 |

## Quick Start

```
Run my training: python train.py --epochs 50
Help me manage my survey study
Validate these regression results
Help me design an experiment
```

## Slash Commands

| Command | Mode |
|---------|------|
| `/exp-run` | run — code execution + monitoring |
| `/exp-manage` | manage — human study tracking |
| `/exp-validate` | validate — statistical interpretation |
| `/exp-plan` | plan — Socratic experiment design |

## ARS Integration

Fits between ARS Stage 1 (RESEARCH) and Stage 2 (WRITE):

```
ARS Stage 1 RESEARCH  →  RQ Brief + Methodology Blueprint
        ↓
  experiment-agent     →  plan → run/manage → validate → verified results
        ↓
ARS Stage 2 WRITE     →  write paper with experiment results
```

## Safety Rules

1. Only executes user-specified commands — never auto-generates or modifies code
2. Never auto-retries crashed experiments
3. Never touches raw participant data
4. Statistical interpretation is descriptive — never concludes

## Version Info

- Version: 1.0.0
- License: CC-BY-NC 4.0
- Author: Cheng-I Wu
