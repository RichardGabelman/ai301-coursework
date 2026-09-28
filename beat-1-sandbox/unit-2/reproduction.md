# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**RichardGabelman**

---

## Posted upstream

**Claim comment**

[Link to the comment where you claimed the issue. Use the comment's own permalink, not the
issue page on its own. **Then paste the text of that comment underneath the link** — the
pasted text is what this field is graded on, so copy across what you actually posted.]

**Reproduction comment**

[Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.]

## Eval iterations

**Run history**

17/20
19/20

**Package analysis**

`pkg-20`
My rubric (after adding new rules) believes it to be a reject, in agreement with the gold label. The repository has AI-disclosure requirements in it's contributing/AI-policy files. I specifically communicated in my skill documents that all claim comments + repro reports it will look at will have made use of AI in some way, and thus, all claim comments/repro reports need to disclose AI usage if required by the repository rules. The claim comment and repro report in question did not.

**Check rationale**

| No hard timelines | claim comment body, repro report body | Pass if the comment and/or repro report don't contain hard (specific) timelines | Required |

I originally had this stipulation in my voice guide document as a preference moreso than a rejectable offense. Running my first eval_run surfaced a discrepancy, `pkg-19`, which should've been a reject according to the gold label which my original rubric deemed acceptable. Providing a hard timeline like this is too specific and potentially dishonest. We can't gurantee how long a fix will take, and frankly we might not even have the skillset to provide a reasonable estimate, either. Our claim comments shouldn't make promises we can't keep.

**Trade-offs**

[Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

`pkg-19` was one of the packages I had an initial discrepancy with. It is the sole reason for the check mentioned directly above "No hard timelines" existing.
In a similar vein, `pkg-20` was the only issue requiring a checking of the repo's disclosure requirements. We need at least one passing in each category and it is the only one in it's category and thus we must pass it. It is the sole issue for which another one of my checks "Disclosure adherence" exists.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
