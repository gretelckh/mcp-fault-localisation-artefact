# Artefact — *Why Is It So Hard to Localize Bugs in MCP Pipelines?*

Artefact package accompanying the manuscript *Why Is It So Hard to Localize Bugs in MCP
Pipelines? An Empirical Study with a Reproducible Fault-Injection Benchmark*. It contains the five
things the manuscript promises in its data-availability statement, and nothing else:

| # | What the paper promises | Where it is |
|---|---|---|
| 1 | Issue-screening workbook over all 1,343 pure issues | `data/screening_1343.csv`, `data/screening_funnel.csv` |
| 1a | The same pull, raw, exactly as the GitHub API returned it (1,373 issues, 14 API fields, no analysis columns) | `data/gh_issues_raw_2026-11-09.xlsx` |
| 2 | The live dataset: 339 rows | `data/active_bugs_339.csv`, `data/evidence_class_339.csv` |
| 3 | The 72 capture records and associated runner sources | `repro/runner/`, `repro/captures/`, `repro/transcripts/` |
| 4 | Per-bug evidence classification | `data/evidence_class_339.csv`, `repro/evidence_matrix.csv`, `data/blocking_gaps_83.csv` |
| 5 | LLM prompts and raw answers | `llm/prompts.md`, `llm/outputs/` |
| 6 | A script that checks the released counts and scores | `scripts/verify_numbers.py` |
| 7 | Expert Annotation Record Form | `Expert 1.csv`, `Expert 2.xlsx` |

Nothing here is synthetic. Every row is traceable to a public GitHub issue in
`modelcontextprotocol/python-sdk`, a run that was actually executed, or a model response that was
actually returned.

---

## 1. Quick start (60 seconds)

You need Python 3.9+. No third-party package is required for verification.

```bash
git clone <this-repo> mcp-artefacts && cd mcp-artefacts
python scripts/verify_numbers.py
```

The verifier checks counts and model scores from the released tables. It also checks capture metadata, referenced runner symbols, and arithmetic in the archived census figure. See the linked provenance notes for the scope of these checks.

If you only want to look at one thing, open `data/active_bugs_339.csv` in Excel or pandas and
filter the column `reproduction_status`.

---

## 2. Study A serverInfo experiment

The [serverInfo experiment](llm/serverinfo_ablation/README.md) includes the exact Study A input text, the baseline prompt, the 648 archived responses, and an offline verifier.

## 3. Census figure and reproduction provenance

See [census aggregate provenance](data/FIGURE_CENSUS.md) and [capture and runner provenance](repro/PROVENANCE.md).
