# Experiment Agent

![Version](https://img.shields.io/badge/version-1.0-blue)
![License](https://img.shields.io/badge/license-CC--BY--NC--4.0-green)

A Claude Code skill for executing, monitoring, interpreting, and verifying experiments in academic research.

## What It Does

- **Runs code experiments** — executes scripts (Python, R, etc.), monitors for stalls/crashes in real-time, collects results
- **Manages human studies** — plans protocols, checks IRB ethics, tracks data collection progress
- **Interprets statistics** — reads p-values, effect sizes, CIs; checks 11 types of statistical fallacies (Simpson's Paradox, survivorship bias, etc.)
- **Verifies reproducibility** — re-runs experiments and compares results

## Why It Exists

Lu et al. (2026, *Nature*) demonstrated an Experiment Progress Manager for autonomous AI research. This skill brings the same execute-and-monitor capability to human-in-the-loop academic workflows — without the risks of full automation.

## Modes

| Mode | What It Does |
|------|-------------|
| `run` | Execute code + monitor process |
| `manage` | Plan + track human studies |
| `validate` | Statistical interpretation + reproducibility check |
| `plan` | Socratic dialogue to design experiments |

## Quick Start

1. Clone this repo into your project or `.claude/skills/`
2. Start a Claude Code session
3. Try: "Run my analysis: `Rscript analysis.R`"

## ARS Compatibility

This skill works independently. It also integrates optionally with [Academic Research Skills (ARS)](https://github.com/Imbad0202/academic-research-skills):

- Reads ARS Stage 1 output (RQ Brief, Methodology Blueprint) to pre-populate experiment design
- Produces Material Passport-compatible output for ARS Stage 2 consumption
- ARS requires zero modification — the user bridges manually

## Safety

- Only executes commands you specify — never auto-generates or modifies your code
- Never auto-retries crashed experiments
- Never touches raw participant data
- Statistical interpretation describes, never concludes
- Full list: see SKILL.md Safety Rules

## License

CC-BY-NC 4.0

## Author

Cheng-I Wu

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md)
