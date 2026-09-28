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

**[Claim comment](https://github.com/codepath/pathreview-ai301-fa26-s3/issues/58#issuecomment-5880127115)**

Hello, I'd like to take a stab at this. I think the fix involves some modifications or additions to the regex rules in bias_detector.py.

**[Reproduction comment](https://github.com/codepath/pathreview-ai301-fa26-s3/issues/58#issuecomment-5880681266)**

I started up a local copy of the most recent commit (`2f4e82f`) using `Python3.11`. I can confirm that nine test cases from `tests/unit/test_bias_detector.py` currently fail.

### Spinning up local copy per `README.md`

```bash
cd pathreview-ai301-fa26-s3
cp .env.example .env
docker compose up -d
make setup
```

### Running unit tests

```bash
make test-unit
```

### Relevant test output (modified for brevity)

```
...::...::test_dismissive_bootcamp_language_detected XFAIL
...::...::test_bootcamp_lacks_rigor_detected XFAIL
...::...::test_bootcamp_inadequate_training_detected PASSED
...::...::test_self_taught_comparison_detected PASSED
...::...::test_positive_bootcamp_mention_not_flagged PASSED
...::...::test_neutral_bootcamp_mention_not_flagged PASSED
...::...::test_educational_background_positive_not_flagged PASSED
...::...::test_demographic_assumption_age_detected XFAIL
...::...::test_demographic_assumption_old_detected PASSED
...::...::test_demographic_assumption_background_detected PASSED
...::...::test_immigrant_developer_assumption_detected PASSED
...::...::test_international_developer_assumption_detected PASSED
...::...::test_clean_feedback_not_flagged PASSED
...::...::test_technical_feedback_not_flagged PASSED
...::...::test_development_suggestion_not_flagged PASSED
...::...::test_case_insensitive_detection PASSED
...::...::test_return_value_structure PASSED
...::...::test_unbiased_returns_empty_reason PASSED
...::...::test_biased_returns_reason PASSED
...::...::test_empty_text PASSED
...::...::test_whitespace_only PASSED
...::...::test_coding_bootcamp_variant XFAIL
...::...::test_online_course_bias_detected PASSED
...::...::test_developer_vs_programmer_distinction XFAIL
...::...::test_multiple_bias_indicators XFAIL
...::...::test_negative_educational_claim XFAIL
...::...::test_working_class_assumption PASSED
...::...::test_rich_poor_assumption XFAIL
...::...::test_foreign_developer_struggle_assumption PASSED
...::...::test_skill_assessment_not_biased PASSED
...::...::test_comparative_without_bias PASSED
...::...::test_assumption_vs_observation XFAIL
```

### Specific failing tests are as follows:

- test_dismissive_bootcamp_language_detected
- test_bootcamp_lacks_rigor_detected
- test_demographic_assumption_age_detected
- test_coding_bootcamp_variant
- test_developer_vs_programmer_distinction
- test_multiple_bias_indicators
- test_negative_educational_claim
- test_rich_poor_assumption
- test_assumption_vs_observation

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

`pkg-19` was one of the packages I had an initial discrepancy with. It is the sole reason for the check mentioned directly above "No hard timelines" existing.
In a similar vein, `pkg-20` was the only issue requiring a checking of the repo's disclosure requirements. We need at least one passing in each category and it is the only one in it's category and thus we must pass it. It is the sole issue for which another one of my checks "Disclosure adherence" exists.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
