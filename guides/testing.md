# Testing

Make sure that the tests in the codebase are correct, sensible, and useful.
Tests do not test themselves, and we rarely write tests for our tests—a human
must ensure that tests are valid.

Will the tests actually fail when the code is broken? If the code changes
beneath them, will they start producing false positives? Does each test make
simple and useful assertions? Are the tests separated appropriately between
different test methods?

Remember that tests are also code that has to be maintained. Don’t accept
complexity in tests just because they are not part of the main product/binary.
If there are ways to compartmentalise behaviour into smaller and more
predictable chunks, it is advised to do so as it makes it easier for product
maintainers to understand expected behaviour.
