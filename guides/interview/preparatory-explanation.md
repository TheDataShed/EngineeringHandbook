# Engineer Interview Preparatory Explanation

## Technical Assessment

### Prerequisites

Before the interview there should be an initial contact wherein we should aim
to:

- contact the candidate on a video call using Teams;
- demonstrate GitPod to the candidate.

This will allow us to avoid any initial setup issues with Teams and provide at
least a passing familiarity with the format of the technical assessment.

## Explanatory Notes

The below must be shared with the candidate prior to the interview itself:

- The technical assessment will take place using
  [GitPod](https://www.gitpod.io/), a web-based IDE similar in appearance and
  functionality to [Visual Studio Code](https://code.visualstudio.com/). If they
  are familiar with GitHub's
  [github.dev web-based editor](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor)
  then this is very similar.
- the GitPod environment will be configured to run a series of tests,
  implemented in a language agreed with the candidate.
- the tests will initially be failing and the aim of the assessment is to add or
  update the existing code such that the tests pass.

## Tech Test Example

The first question on our tech-test is the following (if taking the test in
`python`):

If you choose to research our company and read through our guides on the
handbook we think that you should be allowed to see what kind of questions to
expect on the test. There are four more questions beyond this one (with a bonus
one if you get that far) and they get more challenging as they go along.

```python
def test_01_can_count_number_of_males():
    """
    Count of the number of males in the rows of data from
    the provided records object below by changing the logic in the function
    get_count() found in app.py

    Hint: Make sure the function gets something to count!
    """

    records: Records = [
        Record(first_name="mitchell", surname="clausson", dob="21/01/1980", sex="m"),
        Record(first_name="thomas", surname="skindstad", dob="18/06/1988", sex="m"),
        Record(first_name="susan", surname="boyle", dob="01/04/1961", sex="f"),
    ]

    actual_value_1 = get_count()

    assert actual_value_1 == 2
```

In this test we are looking to test your knowledge of classes and their
attributes, as well as the ability to search a list by some criteria.
