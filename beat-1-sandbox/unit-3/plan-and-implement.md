# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**RichardGabelman**

**[Plan comment](https://github.com/codepath/pathreview-ai301-fa26-s3/issues/58#issuecomment-5990791971)**

Hello, I've looked into the issue further and I think I have a plan ready for execution.

## Root cause

I believe the core issue is that the existing regex patterns in `safety/bias_detector.py` need additional rules to detect further wordings of different biases.

## Plan

On a new branch `fix/58-expand-bias-detection`, I'm going to go into `safety/bias_detector.py`. In the file, I'm going to go to the current regex patterns `lines 14-19 and lines 22-26` and add new regex patterns that will detect the phrasings identified in the original issue (and thus the phrasings tested in `/tests/unit/test_bias_detector.py`). I'm not going to remove any existing regex patterns. Per `docs/CONTRIBUTING.md`, once I get the tests passing, I will remove the XFAIL markers in `/test_bias_detector.py`.

## Test

I'm going to aim to have all the tests in `tests/unit/test_bias_detector.py` passing fully with no XFAIL markers (and no removal of any tests), and with no regressions in the number of currently passing (non-XFAIL) tests.

---

## Your branch

**fix/58-expand-bias-detection**

**Evidence**

### Before

I started up a local copy of the most recent commit (`2f4e82f`) using `Python3.11`. I can confirm that nine test cases from `tests/unit/test_bias_detector.py` currently fail.

#### Spinning up local copy per `README.md`
```bash
cd pathreview-ai301-fa26-s3
cp .env.example .env
docker compose up -d
make setup
```

#### Running unit tests
```bash
make test-unit
```

#### Relevant test output (modified for brevity)
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

#### Specific failing tests are as follows:
- test_dismissive_bootcamp_language_detected
- test_bootcamp_lacks_rigor_detected
- test_demographic_assumption_age_detected
- test_coding_bootcamp_variant
- test_developer_vs_programmer_distinction
- test_multiple_bias_indicators
- test_negative_educational_claim
- test_rich_poor_assumption
- test_assumption_vs_observation

### After

#### Spinning up local copy per `README.md`
```bash
cd pathreview-ai301-fa26-s3
cp .env.example .env
docker compose up -d
make setup
```

#### Running unit tests
```bash
make test-unit
```

#### Relevant test output (modified for brevity)
...::...::test_dismissive_bootcamp_language_detected PASSED
...::...::test_bootcamp_lacks_rigor_detected PASSED
...::...::test_bootcamp_inadequate_training_detected PASSED
...::...::test_self_taught_comparison_detected PASSED
...::...::test_positive_bootcamp_mention_not_flagged PASSED
...::...::test_neutral_bootcamp_mention_not_flagged PASSED
...::...::test_educational_background_positive_not_flagged PASSED
...::...::test_demographic_assumption_age_detected PASSED
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
...::...::test_coding_bootcamp_variant PASSED
...::...::test_online_course_bias_detected PASSED
...::...::test_developer_vs_programmer_distinction PASSED
...::...::test_multiple_bias_indicators PASSED
...::...::test_negative_educational_claim PASSED
...::...::test_working_class_assumption PASSED
...::...::test_rich_poor_assumption PASSED
...::...::test_foreign_developer_struggle_assumption PASSED
...::...::test_skill_assessment_not_biased PASSED
...::...::test_comparative_without_bias PASSED
...::...::test_assumption_vs_observation PASSED


## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

18/20
19/20

**Package analysis**

`pkg-20`, my rubric agreed with the gold label in rejecting it. The repository has a stated policy requiring disclosure of all AI usage. My rubric understood that all content it would be judging would have some AI usage and thus, would require an AI disclosure if the repo required it. The comment did not disclose it, thus it was rejected.

**Check rationale**

| conventions | the plan comment, the original issue post, the thread, repo's AI policy | Pass if the comment follows any explicit maintainer direction present in the thread. Every single plan you read will have used AI in some way, pass if either there is no repo AI disclosure policy, or if the plan discloses AI usage per the repo's AI policy | required |

The skill needed to check if the repository has an AI disclosure policy (dictated in a specific file or by a maintainer in the thread). If one such exists, the plan comment it is judging should abide by that disclosure policy and well... disclose. I needed to explicitly tell the skill that anything it is judging will have some AI usage and thus require disclosure if the repo calls for it, otherwise it wasn't sure if disclosure was necessary.

**Trade-offs**

[Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]
The check as pasted above was necessary to achieve a "correct" rejection on `pkg-20`. Without that check, and especially the wording reinforcing the usage of AI in all content reviewed, the AI would've approved that plan despite it's contravening of repository policy.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
