## Diagnosis

Regex in `safety/bias_detector.py` needs additional rules to detect further wordings of different biases.

## Plan

On a new branch `fix/58-expand-bias-detection`, I'm going to go into `safety/bias_detector.py`. In the file, I'm going to go to the current regex patterns `lines 14-19 and lines 22-26` and add new regex patterns that will detect the phrasings identified in the original issue and the phrasings tested in `tests/unit/test_bias_detector.py`. I'm not going to remove any existing regex patterns. Per `docs/CONTRIBUTING.md`, once I get the tests passing, I will remove the XFAIL markers in `/test_bias_detector.py`.

## Test Confirmation

I will judge my work complete when the existing `tests/unit/test_bias_detector.py` suite passes fully with no XFAIL markers, with no regressions in the number of currently passing (non-XFAIL) tests.

## Deviations

Nothing changed; the plan held.
