# Environments

When not dictated to by a client the following environment definitions should be
applied:

- `local` - your local machine
- `dev`
- `staging`
- `production`

The environment can be controlled through environmental variables and loaded in
respect to the product that needs them. They can be listed in Github Actions,
Dockerfiles, or even can be loaded within the code (which is very common).

An example of how one may do this in python for example:

```python
import os

ENV = os.environ.get("ENV") # Load the environment variable from the machine it's on
```

Because the code above is referencing the variable `ENV`, this variable will
need to be set on the machine that the code is running on. This can be stored in
a `.envrc` variable if you are using `direnv` on your local machine. Or added to
the Databricks cluster that you are deploying (For example). Environment
variables are used in all of our projects, and they should be used to ensure
that the code running pertains to the correct environment that it is suited for.

## Development Stages/Environments

The four different environments are generally self explanatory and splitting out
dev and staging may be overkill for certain projects but in general:

### Dev

A safe deployment that allows for experimentation and should be used for
testing, debugging and ensuring that code is ready for deployments. Initial
feature development will be easiest in this environment.

### Testing

A deployment that is to run ahead of the production release by x amount of
days/weeks to ensure that UAT testing by QA (Quality Assurance) engineers on new
features can be accepted before deployment to production.

### Pre-Production/Staging

The battle tested and thoroughly safeguarded deployment that is the one that can
be treated as a beta environment to do any final checks and testing. It is an
exact mirror of production apart from the incremental change that will be going
forward. The focus is to test the application from start to finish and ensure
behaviour of the entire product.

### Production

The battle tested and thoroughly safeguarded deployment that is the one that is
used by the client/customers.
