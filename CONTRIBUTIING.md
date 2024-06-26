# Contribution Guidelines

First and foremost, we’d like to express our gratitude to you for taking the time to contribute. 
We welcome and appreciate any and all contributions via 
[Pull Requests](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests)
along the [GitHub Flow](https://guides.github.com/introduction/flow/).  

1. [Open a GitHub issue](#open-a-github-issue)
1. [Fork the repository on GitHub](#fork-the-repository-on-github)
1. [Install the pre-commit hooks](#install-the-pre-commit-hooks)
1. [Update the documentation](#update-the-documentation)
1. [Update the tests](#update-the-tests)
1. [Update the code](#update-the-code)
1. [Create a pull request](#create-a-pull-request)
1. [Merge and release](#merge-and-release)

## Open a GitHub issue

For bug reports or requests, please submit your issue in the appropriate repository.

We advise that you open an issue and ask the
[CODEOWNERS](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/about-code-owners) and
community prior to starting a contribution. This is your chance to ask questions and receive feedback before you start
writing ( potentially wrong ) code. We value the direct contact to our community a lot, so don't hesitate to ask any
questions. 

## Fork the repository on GitHub

[Fork](https://help.github.com/en/github/getting-started-with-github/fork-a-repo) the repository into your own GitHub
account and [create a new branch](https://guides.github.com/introduction/flow/) as described in the
[GitHub Flow](https://guides.github.com/introduction/flow/).

## Install the pre-commit hooks

If the repository you're working on ships with a `.pre-commit-config.yaml,` make sure the necessary hooks have been
installed before you begin working (e.g. a `pre-commit install`). 

## Update the documentation

We encourage you to update the documentation before writing any code (please see
[Readme Driven Development](https://tom.preston-werner.com/2010/08/23/readme-driven-development.html). This ensures the
documentation stays up to date and allows you to think through the problem fully before you begin implementing any
changes.

## Update the tests

We also recommend updating the automated tests before updating any code
(see [Test Driven Development](https://en.wikipedia.org/wiki/Test-driven_development)).

That means that you should add or update a test case, run all tests and verify that the new test fails with a clear
error message and then start implementing the code changes to get that test to pass.

The test folder in every repository will have documentation on how to run the tests locally.

## Update the code

At this point, make your code changes and constantly test again your new test case to make sure that everything working
properly. Do [commit](https://help.github.com/en/desktop/contributing-to-projects/committing-and-reviewing-changes-to-your-project)
early and often and make useful commit messages.

If a backwards incompatible change cannot be avoided, please make sure to call that out when you submit a pull request,
explaining why the change is absolutely necessary. 

## Create a pull request

[Create a pull request](https://help.github.com/articles/creating-a-pull-request/) with your changes.
Please make sure to include the following:

1. A description of the change, including a link to your GitHub issue.
1. Any notes on backwards incompatibility or downtime.

## Merge and release

The [CODEOWNERS](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/about-code-owners)
of the repository will review your code and provide feedback. If everything looks good, they will merge the code and
release a new version while following the principles of [Semantic Versioning (SemVer)](https://semver.org/).