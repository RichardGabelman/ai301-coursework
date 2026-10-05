# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

Plan should indicate the root cause of the issue pretty early on.
The issue will generally be near the command or step taken in the repro evidence where the output or behavior will be deemed wrong or unexpected.
If the repro evidence indicates certain things were attempted with no positive improvement, those cannot be the root diagnoses.
<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

## Scope

Scope will be indicated by a specific file, or better, specific lines in that file. Specific files indicated for each file touched. No files touched that aren't core to the issue and the fix.
<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

## Executability

Steps that will be taken should be in chronological order, with specific files, directories, and commands shown.
<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

## Test plan

A mechanism for verifying the success of the plan should be present, either in the form of a (new) automated test, or specific and detailed steps that, when taken, verify that the original issue no longer exists.
<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

## Honesty

Uncertainty about diagnosis should be explicit (in that case, finding the root cause should be explicitly part of the plan). Impacts to non-issue related things should be mentioned (if such exist).
<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

## Comms

The plan comment structure and content should follow maintainer direction, if such exists within the repo facts (like any templates or guides given) or the issue thread. The plan should disclose AI usage in accordance with any repo AI policy.
<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->
