# Test Driven Development (TDD)

It is expected that where feasible and appropriate, all projects will have
relevant tests and test automation to accompany the functional elements of the
project.

One great way to ensure this practice is adhered to is through the medium of
**Test Driven Development**, commonly referred to as **TDD**.

## What is TDD?

TDD is a method of development whereby (in an _ideal_ world) unit tests are
written before the application code of the project.

The ideal flow of TDD is as follows:

1. Write a failing test
2. Write functional code to make the test pass
3. Yay, we have passing tests!

## Why TDD?

The advantage of writing code in a TDD way is that one can set out exactly what
should make a test pass and what shouldn't.

Writing the application code after the test means that the bare minimum code is
written to fulfil the requirement for a particular test. Additionally, the
theory goes that writing the test beforehand means the test shouldn't be forced
to pass by writing complex test logic.

This helps to reduce the complexity of individual methods and can reduce scope
creep for particular requirements.

TDD also helps to reduce bugs in the code as individual methods are tested only
for what they are written to achieve. This is great because the testing is
low-level, meaning that differing conditions at runtime _probably_ won't hide
other issues.

## Example (in Python 🐍)

_Assume the relevant `unittest` packages are imported and setup._

1. Write a test that should pass, but fails because the method isn't implemented
   yet.

   `test_calculator.py`

   ```python
   import unittest

   class TestCalculator(unittest.TestCase):
       def test_calculator_add(self):
           self.assertEquals(Calculator.add(2, 2), 4)
   ```

2. Write the method to make the test pass.

   `calculator.py`

   ```python
   class Calculator:
       def add(self, a, b):
           return a + b
   ```

You can see in the above that we start by writing a test which asserts that
`2 + 2 = 4`. We then write our application method that will return `4` when `2`
is passed to both parameter `a` and parameter `b`.

## Useful Tools

The tools which can be used will depend upon which languages and technology you
are working with. Below are a few examples:

### Python

- [unittest (Standard Library)](https://docs.python.org/3/library/unittest.html)
- [pytest](https://docs.pytest.org/en/7.1.x/) (and optionally
  [pytest-cov](https://pypi.org/project/pytest-cov/) for ensuring test coverage)

### SQL Server

- [tSQLt](https://tsqlt.org/)
- [Visual Studio Test Explorer](https://docs.microsoft.com/en-us/sql/ssdt/walkthrough-creating-and-running-a-sql-server-unit-test?view=sql-server-ver16)

### C\#

- [NUnit](https://nunit.org/)
- [xUnit](https://xunit.net/)
- [SpecFlow](https://specflow.org/) **NB:** This is a
  [BDD](https://medium.com/javascript-scene/behavior-driven-development-bdd-and-functional-testing-62084ad7f1f2)
  framework but can be used for TDD.

### SSIS (Yes, even SSIS)

- [ssisUnit](https://github.com/johnwelch/ssisUnit)

There are many more tools out there which are language and technology dependent
but these are some common ones. Generally speaking, if it supports unit testing,
you can TDD it.

## Things to remember

- Test code needs to be maintained as well
- TDD isn't appropriate for all situations (Developing MVC or GUI's for example)
- Make sure you automate your tests
- TDD doesn't remove the need for regression, integration or other types of
  testing
