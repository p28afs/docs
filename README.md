# R2D2 Knowledge Extraction

Extracts everything needed to rebuild R2D2 (acquisition → obligation → generation) from the legacy code. The code is the source of truth; no human in the loop. Method: `knowledge-extraction-playbook.md`.

## Run

Single model (Claude):

```
/ke-run <github-url> [<github-url> …]
```

Cross-model (Claude and Codex, then curated):

```
/ke-run-cross <github-url> [<github-url> …]
```

Refine the curated blueprint with another round:

```
/ke-curate
```

Optional: add `exclude: <scope>` to narrow the scope.

## Results

| File | What |
|---|---|
| `fields_matrix.csv` | Full lineage of every reportable field |
| `rules_matrix.csv` | Every rule with all its dependencies |
| `scorecard.md` | Completeness, agreement and proof scores |
| `digest.md` | Summary, what was auto-resolved, and any assumptions where the code itself has no answer |

Every gap is auto-resolved from the code. Nothing is left open and nothing waits for a person.

Single model: matrices in `ke/outputs/`, scorecard in `ke/eval/`, digest in `ke/`. Cross-model: all in `ke/blueprint/`. Repos are checked out to `legacy/`.
