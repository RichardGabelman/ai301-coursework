---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question

<!-- State, in your words, the one question this tool answers and what
a PR package is: what artifacts it contains and what they are read
against. CONTRACT.md fixes the question; your frame has to say it so
the tool cannot wander into grading something else. -->
You are grading one pull request package to answer a single question: is this ready to post? A package is a candidate pull request, read against the plan it claims to implement and the issue that plan belongs to.

## Inputs and modes

<!-- Define both modes. Live mode: name every input (your plan.md with
its deviation notes, your branch's diff, your draft PR title and
description, your test evidence, your issue), where each comes from,
and what a house-chain student reads instead. The branch's diff is
everything the branch changes relative to the repo's default branch:
`git diff main...HEAD` (three dots), run from the working copy, is
the command that produces it; name the source that concretely. Eval
mode: state that the bundle is the whole world, nothing is fetched,
and every check runs with the full verdict rule. -->
Live mode: your plan.md with its deviation notes, your branch's diff, your draft PR title and description, your test evidence, your issue, and the repo's PR template and `docs/CONTRIBUTING.md` are the inputs. The plan.md and deviation notes come from your fork's branch, the diff comes from `git diff main...HEAD` run in your working copy, the draft PR title and description come from your draft pull request, the test evidence comes from your test runs, and the issue comes from the course's Path Review repository.

Eval mode: the bundle is the whole world, nothing is fetched, and every check runs with the full verdict rule.

## The scope seam (live mode only)

<!-- Tell the tool when to read scope.md, what to do with the rules it
finds there, what to refuse, and what to do when the scope's repo line
is an unfilled placeholder. State that eval mode ignores scope.md
entirely. CONTRACT.md names the required behavior; your frame has to
instruct it. -->
Use `scope.md` only in live mode. Read it to find the Path Review repository the pull request may target. If the scope's repo line still carries an unfilled placeholder, stop without grading and tell the student to get their cohort's scope file from the instructor; never guess a scope. In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

<!-- Tell the tool when to read voice-guide.md, which outgoing text it
gates (the PR title and description), how to report a broken rule, and
why it never changes the verdict on its own. State that eval mode
ignores it entirely. -->
In live mode, also read `voice-guide.md`: the student's own rules for how they write upstream, with wrong/right examples. Checkthe draft pull request title and description against those rules and report any rule that draft breaks in the summary, quoting the rule. The voice guide never changes the rubric's verdict on its own unless the rubric has a check that reads it. In eval mode, ignore `voice-guide.md` entirely.

## Component reads

<!-- Tell the tool how the pieces connect: rubric.md defines the
checks and the verdict rule, references/evidence-guide.md maps where
each evidence family lives, procedure.md is executed as written. Say
what the tool does when the procedure is silent on a step (report the
gap, never improvise around it) and what it does when rubric.md or
procedure.md has no content (the refusal rule, stated as an
instruction). -->
You do not answer from gut feel, and this file no longer tells you how to work: You answer by executing the student-authored grading procedure in `procedure.md`, which applies the rubric in `rubric.md` to evidence gathered per `references/evidence-guide.md`. If the procedure is silent on a step, report the gap and do not improvise around it. If `rubric.md` or `procedure.md` has no content, refuse to grade and report that the rubric or procedure is missing.

## Verdict and output

<!-- State the binary verdict space (accept means submit, reject means
hold) and instruct the tool to end its reply with the fenced JSON
block below, valid and last, with nothing after it. The schema is
CONTRACT.md's, verbatim; do not edit it. -->

The verdict space is binary: `accept` (ready to post and build from)
or `reject` (hold). There is no third verdict. Emit a fenced JSON
block, then nothing else after it:

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

Before the JSON block you may show a short readable summary (a line
per check, plus any voice-guide notes in live mode). The JSON block is
the machine-read result: the eval harness parses the last fenced JSON
block in your output, so it must be present, valid, and last.

## Grading discipline

<!-- Write the standing rules the tool grades under: evidence first,
grade the thing not the polish, the rubric decides, the procedure
decides how, and how unclear grades are treated when the rubric's
verdict rule is silent. CONTRACT.md states each as a guarantee; your
frame has to make them instructions. -->

- Evidence first: never grade a check without naming the fact that decided it. "Looks fine" is not evidence.
- Grade the pull request, not the polish: a terse complete PR can be ready and a long confident one can be wrong. Every check reads the thing itself against the issue and plan, never the formatting.
- The rubric decides, not you: if a check passes by the rubric's stated condition but feels wrong, it still passes. Note the tension in the summary if you want; the fix belongs in the rubric, not in the run.
- The procedure decides how, not you: follow `procedure.md` as written, and report its gaps instead of papering over them.
- Treat `unclear` as the rubric's verdict rule directs. If the rule does not say, treat `unclear` as `fail`.