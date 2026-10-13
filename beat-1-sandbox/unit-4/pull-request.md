# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

[Link to the pull request you opened. It must be the pull request's own page on the Path
Review repo, not your fork's branch page.]

**Branch**

[The name of the branch the pull request comes from, exactly as it appears in your fork.
The naming shape is a type prefix, then the issue number, then a short description. **The
issue number in the branch name must be the number of the issue the pull request fixes** —
a name carrying any other number does not satisfy this field.]

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

20/20

**Package analysis**

`pkg-01`: My rubric decided it should be rejected, in alignment with the gold label. The PR does not comply with the repository's PR template/checklist which means it was not in compliance per the `standards-wall` category.

**Check rationale**

| PR follows existing template | repo's PR templates, PR description | Reject if the PR doesn't follow a provided PR template, if one such exists. Following meaning to fill out all required sections, properly, unless good reason is given. | required |

The PRs need to follow existing PR standards (PR templates + AI policy). This check rejects the PR if it doesn't comply with the repo's PR template specifically. This check is the same as when I first wrote it, no revisions, and no real debate on its inclusion.

**Trade-offs**

The check above is responsible for the rejections of `pkg-01` (only). Without that check, the PR is otherwise solid and thus would've passed the rubric. This check is necessary to enforce compliance with repo PR standards.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
