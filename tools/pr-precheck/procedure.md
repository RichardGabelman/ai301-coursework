# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

1. Look for/read the repository's PR templates and AI policies.
2. Read the plan the PR claims to implement.
3. Read the PR description.
4. Read the PR diffs.
5. Look for departures between the structure of the PR description and any existing PR templates.
6. Look for a lack of disclosure of AI-usage, if such a disclosure is required by repo's policies.
5. Look for undisclosed departures from the plan in terms of what files are changed and in what way.
6. Look for proof of that testing occurred of the new changes.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

Plan / Plan comment: A top-level `plan.md` file, if live, else the plan_context_markdown in thread_highlights.
PR description: the candidate PR, if live, else the description field of the pr object.
PR diffs: the PR diffs, if live, else the diff field of the pr object.
Repo's AI policy: Various potential documentation files (docs/CONTRIBUTING.md), if live, else raw_markdown in repo_facts.
Repo's PR templates: The repo's pull request templates, if live, else raw_markdown in repo_facts.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->
Check compliance with PR templates/AI policy first.
Check for undisclosed file changes.
Check for disclosed but non-existent changes.
Check for proof that testing of the new changes exists.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->
All required checks must pass. List failing checks and why.