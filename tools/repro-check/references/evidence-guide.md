# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->
Where it lives:
  - Live
    - the issue thread, the repo's docs, and the draft comment
  - Eval bundle
    - the issue context, the repo-facts block, the claim comment, the repro report and its parts

What "good" looks like:
  - The environment/versions mentioned in the comment should match the environment/versions mentioned in the original comment, if the environment/versions are relevant to the original issue.
  - A failure to reproduce is not relevant if the comment's environment/versions are not the same as mentioned in the original issue.
  - A successful reproduction on a different environment/issue is fine.


## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->
Where it lives:
  - Live
    - the issue thread and the draft comment
  - Eval bundle
    - the claim comment and/or the repro report and its parts

What is "followable":
  - Steps outline ALL specific actions taken.
  - File names, commands, etc... are explicitly identified in a non-ambiguous way.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->
Where it lives:
  - Live
      - The repro report
  - Eval bundle
      - The repro report markdown

What is good:
  - Either output logs/behavior matches the output logs/behavior described in the original issue
  - Or the discrepancy is explicitly highlighted in the claim comment/repro report.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->
How to tell:
  - A successful reproduction must include the relevant logs/output proof.
  - A lack of relevant logs/output proof or logs and output proof that show a different outcome should result in a disclosure of an inability to reproduce.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

- Comments should match the form of a repo's template, if the repo has such a template.
- All claim comments and/or repro reports you will look at utilize AI in some way. The claim comment and/or repro report should contain an AI-usage disclosure if required by the repo's contributing/AI-policy requirements.
