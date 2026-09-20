# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Recent default-branch commits | The dates of the last 5 default-branch commits | Last 5 commits are from within the last 30 days | Required |
| Recent human-contributions | The authors of the last 5 merged PRs commits | At least one of the authors has a name not ending in [bot] | Required |
| Repo isn't archived | Archived flag | Repo is not archived | Required |
| Not an epic issue | The issue labels and issue description | Labels do not contain "epic" | Required |
| Issue is unclaimed | The issue assignees | Nobody is assigned to the issue | Required |
| Issue has no outstanding PRs | The issue's associated PRs | No open PRs addressing the issue | Required |
| No product decisions | Issue description | Issue resolution should not involve making a product decision | Required |
| Repo allows AI contributions | Repo's CONTRIBUTING.md and any contributor docs it links | No ban on AI-generated/assisted contributions | Required |
| Comments don't include unresolved debate | The issue comments | Issue does not have unresolved design/implementation/etc debate | Required |


## Verdict rule

Accept if every required check passes, preferred checks are only used to rank accepted issues, an unclear determination on a required check counts as a fail.

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->
