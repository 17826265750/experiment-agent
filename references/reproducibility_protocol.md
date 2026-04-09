# Reproducibility Protocol

Defines how validate mode verifies reproducibility of code experiments by re-running and comparing.

## Applicability

- **Applicable**: Any experiment with an executable command and recorded original results
- **Not applicable**: Human studies, external API calls with non-deterministic responses, hardware-dependent benchmarks
- If not applicable, skip reproducibility verification and report: "Reproducibility: N/A — [reason]"

## Procedure

### Step 1: Classify Experiment Determinism

| Type | Criteria | Expected Outcome |
|------|----------|-----------------|
| **Deterministic** | Same seed, same data, same code, same environment | Exact match required |
| **Stochastic** | Random elements (different seed, dropout, data augmentation) | Statistical equivalence |
| **Environment-sensitive** | Results depend on hardware, OS, or library version | Document environment, allow wider tolerance |

Ask user: "Is this experiment deterministic (same seed/data = same result) or stochastic (involves randomness)?"

### Step 2: Re-Run

1. Delegate to code_runner_agent with the same command and working directory
2. code_runner_agent runs full EXECUTE → MONITOR → COLLECT cycle
3. Collect new experiment_result

### Step 3: Compare

**Deterministic comparison:**
- For each numeric metric: `abs(original - rerun)` must be exactly 0
- For output files: byte-for-byte comparison (`diff` or hash)
- Any difference = `MISMATCH`

**Stochastic comparison:**
- For each numeric metric: `abs(original - rerun) / original` must be < threshold
- Default threshold: 5% relative difference
- User can override with `reproducibility_threshold`
- For distributions: compare summary statistics (mean, std, min, max)

**File comparison:**
- Size within 10% tolerance (stochastic outputs may vary)
- Structure match (same columns, same row count for CSV)
- Content: spot-check first/last 5 rows

### Step 4: Verdict

| Verdict | Criteria |
|---------|---------|
| `REPRODUCIBLE` | All metrics within tolerance; all output files match |
| `PARTIALLY_REPRODUCIBLE` | Some metrics match, some don't; or files differ in non-critical ways |
| `NOT_REPRODUCIBLE` | Significant differences in primary metrics |

## Tolerance Defaults

| Comparison | Deterministic | Stochastic |
|-----------|--------------|------------|
| Numeric metrics | Exact (0 diff) | < 5% relative |
| Output file size | Exact | < 10% |
| Output file content | Byte-for-byte | Structure + spot check |
| Timing metrics | Not compared (always varies) | Not compared |

## Edge Cases

- **Missing original results**: Cannot compare → report "Reproducibility: CANNOT_VERIFY — original results not provided"
- **Environment changed**: Warn "environment may differ from original run — results may not match even if code is correct"
- **Partial output**: If original has 5 output files but re-run produces 4 → `PARTIALLY_REPRODUCIBLE` + flag missing file
