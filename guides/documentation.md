# Documentation

## Summary

Documentation is central to the development work that we do at the Data Shed.
Every project should contain enough information to allow for new engineers
joining the project to understand what is occurring in a given section of the
code. That said, it does come with the caveat that the documentation should be
scoped to meet the expectations of the consumer reading the documentation.

### The Audience

The audience is key for all levels of documentation. Links to more detailed
implementations should be linked to from higher level instruction not the other
way around. Allow people to get into the details if they choose but do not
overburden someone with too much information.

## High Level Operational Guides

As a project starts off, we should define high level architectural diagrams of
how the project is structured. We have used
[mermaid](https://openbase.com/js/mermaid/documentation) successfully in the
past on some projects as it integrates well with markdown files which is our
recommended medium for technical documentation. The reason for this is that:

1. It is plaintext and easy to search for using common cli tools
2. It is a standard commonly used in spaces like confluence and being able to
   copy and paste from your project into confluence for other users to be able
   to read is quite handy. _(There are tools available that you can use to
   update confluence automatically with documentation from a git repo but that
   is something that will not be covered in this guide.)_
3. It can easily be transformed into PDF documentation using a tool called
   [pandoc](https://pandoc.org/).

High level operational guides should depict a general overview of how the
project is structured as well as simple use cases around how to use the software
being developed. Just as many reading this likely go to the README.md of a git
repo to see how to use it, our guides should reflect the architecture _(if
relevant)_ as well as examples to get you started, setup, test, etc...

To generate a straightforward README file for a project, I recommend using
[readme.so](https://readme.so/editor). It allows us to pick and choose sections
that are applicable for a project.

## Technical Operation

Run books for long term support should be detailed to handle not only for happy
path but keep continued logs around common errors and how issues were rectified
in the past. There is no need to feel embarrassed or hide mistakes that may
arise during these cases so documenting these situations can be incredibly
helpful for the long term maintainability for the project. One needs to be
consistently asking themselves whether they are taking anything for granted and
if they are needs to consider the **audience** of the documentation.

The audience for technical documentation should be catered towards someone who
is unfamiliar with the exact implenentation of how you did something. Take for
example a situation in which we are defining a regular expression to verify that
a user has first name that doesn't contain any numbers or special characters in
it, and starts with a capital letter.

```python
import re

def is_valid_first_name(name):
    """
    Validate that the first name contains only A-Z.

    This function is used to ensure the first name
    of a person is capitalised, contains only letters,
    and may sometimes contain a space or hyphen if
    double barrelled.

    Args:
        name (str): The indivudual's name

    Returns:
        bool: Whether the first name is valid
    """
    pattern = re.compile(r"^[A-Z][a-zA-Z ]+$")
    if re.match(pattern, name):
        return True
    return False
```

Now whether this function handles all cases is irrelevant to the point, what we
want to orchestrate is that we should be describing what the function does and
give general hints as to how the logic in the function is carried out. What we
do not want to do or mandate is that we explain how regular expressions work,
what the re library is, explain the difference between a raw string and a
standard string, etc...

Technical documentation should be used for the entire `src` equivalent directory
and all it's contents. Unit and integration tests are also incredibly useful to
newcomers to a project, so if your test does not immediately infer what is being
tested, we expect the test to contain some documentation.

## Comments

Comments in code should be used when the length of a particular function or loop
is unclear from the documentation. It should be used as a means of assisting
other engineers with an explanation as to how something is working, and is
especially useful for explaining logic in terms of business logic that is not
immediately intuitable from the function. They should be able to fit on one line
and any desire to have long winded paragraphs of comments should be used
incredibly rarely and are not encouraged as they suggest that there may be
better places to store this information as well as encourage some refactoring so
that the code is more clear on what is occurring.

## Recordings

If you wish to demonstrate how the application works visually, instead of doing
screen records, if you are using a terminal to demonstrate the project, the use
of private [asciinema recordings](https://asciinema.org/) are very handy to link
to and embed in markdown files. They take up far less space than a screen
record.
