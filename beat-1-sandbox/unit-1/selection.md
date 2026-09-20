# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/58

**Verdict output**

"1. #58 — Bias detector patterns too narrow (bug, safety, tier-1). Best fit: Python regex work in one file (safety/bias_detector.py), and 9 existing failing tests in tests/unit/test_bias_detector.py pin the expected behavior exactly, so there's nothing to design. It's also the only tier-1 of the four, and the fairness/bias subject matter lines up with your civic-tech and public-policy interest."

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
{
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/58",
    "checks": [
      {"name": "Recent default-branch commits", "grade": "pass", "evidence": "Last 5 commits: 2026-09-16 (x3), 2026-08-24 (x2) — all within 30 days of 2026-09-20."},
      {"name": "Recent human-contributions", "grade": "pass", "evidence": "Repo has 0 PRs ever; all 5 default-branch commits are authored by Aburke225 (Andrew Burke), not a [bot]."},
      {"name": "Repo isn't archived", "grade": "pass", "evidence": "GitHub API repo object: \"archived\": false."},
      {"name": "Not an epic issue", "grade": "pass", "evidence": "Labels are [bug, safety, tier-1]; body describes one regex-coverage defect, no sub-item list."},
      {"name": "Issue is unclaimed", "grade": "pass", "evidence": "\"assignees\": [] and 0 comments on the issue."},
      {"name": "Issue has no outstanding PRs", "grade": "pass", "evidence": "Repository-wide PR list (state=all) returns 0 PRs; issue timeline shows only 3 'labeled' events, no cross-references."},
      {"name": "No product decisions", "grade": "pass", "evidence": "\"Nine unit tests specifying the intended coverage fail\" in tests/unit/test_bias_detector.py — expected behavior is pinned by tests."},
      {"name": "Repo allows AI contributions", "grade": "pass", "evidence": "docs/CONTRIBUTING.md states workflow conditions only; no AI ban, and no AI_POLICY.md/AGENTS.md in the repo."},
      {"name": "Comments don't include unresolved debate", "grade": "pass", "evidence": "Issue comment count is 0."}
    ],
    "verdict": "accept"
  }
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

14/20
17/20
16/20
19/20
20/20

**Issue analysis**

Issue 15, my rubric says reject which is in accordance with the gold label. The specific reason my rubric rejects it is that the comments contain unresolved debate regarding design.

**Check rationale**

| Comments don't include unresolved debate | The issue comments | Issue does not have unresolved design/implementation/etc debate | Required |

Issues in which the right decision on how to actually handle it hasn't been decided are not good candidates. You won't know what specifically to do and may result in wasted work.

**Trade-offs**

This check was necessary in my case to get a correct rejection of issue 15. An issue can appear well-scoped in the original description and be within a well-maintained repository but if the organization hasn't made a decision on something, it generally isn't in an outsider's purview to make that decision for them.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
