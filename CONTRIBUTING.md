<a id="contributing-to-the-wazuh-documentation"></a>
Contributing to the Wazuh documentation

This document explains how to report issues, set up a local environment, and submit a pull request to the Wazuh documentation repository.

<a id="reporting-issues"></a>
Reporting issues

We value feedback from the community. When reporting an issue, include the URL or section where the problem occurs and provide all relevant details.

If something in the documentation seems inaccurate, unclear, or confusing, open an issue in this repository.

If you encounter bugs or unexpected behavior when using Wazuh itself, report it in the corresponding component repository:

[All Wazuh repositories](https://github.com/wazuh)

Every pull request must be associated with an open issue. If one does not exist yet, please create it before submitting your PR.

<a id="branching"></a>
Branching

Refer to the [branch model in README.md](README.md#branches) for an overview of how branches map to Wazuh versions.

Target the branch that corresponds to the Wazuh version you are updating. For example, a fix for the 4.14 documentation should be submitted against the `4.14` branch. Don't use `main` to update published documentation, this branch has the documentation for  latest version currently in development.

A release still in development may not have a plain `X.Y` branch yet. For example, a fix for the 5.0 documentation before it publishes should target the `5.0.0` (or later `5.0.Z`) branch instead of `5.0`.

Long-lived branches (`main` and version branches) are protected. Only authorized members of the documentation team can merge changes into them.

<a id="setting-up-a-local-environment"></a>
Setting up a local environment

<a id="prerequisites"></a>
Prerequisites

Python 3 and `pip`

`git`

`make`

<a id="build-the-documentation"></a>
Build the documentation

With a virtual environment created and activated:

```shell
# Clone your fork
git clone https://github.com/wazuh/wazuh-documentation.git
cd wazuh-documentation

# Install dependencies
pip install -r requirements.txt

# Build the HTML documentation
make html #or `make html-quick`
```

The generated documentation will be at `build/html/index.html`. Open it in your browser to preview your changes.

To remove previous builds:

```shell
make clean
```

<a id="submitting-a-contribution"></a>
Submitting a contribution

<a id="1-fork-and-create-a-branch"></a>
1. Fork and create a branch

Fork the repository and create a branch from the appropriate base branch. Follow this naming convention:

Bug fix: `bug/<issueID>-short-description`

New content or enhancement: `enhancement/<issueID>-short-description`

Test-related: `test/<issueID>-short-description`

Other changes (e.g. rollbacks): `change/<issueID>-short-description`


Use lowercase letters, numbers, and hyphens. Avoid spaces and special characters. Replace `<issueID>` with the corresponding issue number.

Example: `bug/1234-fix-agent-installation-steps`

<a id="2-make-your-changes"></a>
2. Make your changes

Follow the writing and formatting guidelines below before committing.

<a id="3-commit-your-changes"></a>
3. Commit your changes

Write clear commit messages that describe what changed and why. Feel free to make as many commits as needed while working on your branch.

Every commit must be signed and show as verified on GitHub. This repository's branches enforce required commit signatures, so a PR containing unsigned commits cannot be merged, no matter how many approvals it has.

To sign your commits:

1. Set up a GPG or SSH signing key and [add it to your GitHub account](https://docs.github.com/en/authentication/managing-commit-signature-verification).
2. Configure Git to sign automatically:

```shell
git config commit.gpgsign true
```

If you already made unsigned commits, sign them retroactively, for example with an interactive rebase (`git rebase --exec 'git commit --amend --no-edit -S' -i <base-commit>`), then force-push the branch.

<a id="4-open-a-pull-request"></a>
4. Open a pull request

Open a pull request against the appropriate base branch. In your PR description:

Explain what the PR changes and why.

Link to the related issue. You can use the `closes #<issueID>` keyword.

Add links to any relevant external resources or related PRs.

Resolve any merge conflicts before requesting review.

The documentation team will review your PR. At least one approval from a team member is required before merging.

Before submitting, make sure your PR meets the checklist in the pull request template.

<a id="updating-changelogmd"></a>
Updating CHANGELOG.md

Add an entry under the corresponding version header using the following format:

```markdown
## [vX.Y.Z]

### Added

- Description of the new content. ([#PR](https://github.com/wazuh/wazuh-documentation/pull/PR))

### Changed

- Description of the change. ([#PR](https://github.com/wazuh/wazuh-documentation/pull/PR))

### Fixed

- Description of the fix. ([#PR](https://github.com/wazuh/wazuh-documentation/pull/PR))
```

Use Post-release: as a prefix for entries that apply to an already published version. Link every entry to its corresponding pull request.

<a id="writing-and-formatting-guidelines"></a>
Writing and formatting guidelines

<a id="indentation"></a>
Indentation

Use three-space indentation in `.rst` files. For example:

```rst
#. Access the Wazuh web interface with ``https://<wazuh-dashboard-ip>`` and
   your credentials:

   -  Username: admin
   -  Password: <ADMIN_PASSWORD>
```

<a id="links"></a>
Links

Use the `:ref:` role to link to sections within the same page.

Use the `:doc:` role to link to other documentation pages. Do not use

  `:ref:` to link to a full page.
Use `:api-ref:` to link to the Wazuh API reference.

Use anonymous hyperlinks (double underscores) for external links:

```rst
  `https://example.com`__

  `Example site <https://example.com>`__
```

To prevent Sphinx from converting a URL into a link, prepend `\`:

```rst
  This is the sample URL \https://example.com used as an example.
```

<a id="headings"></a>
Headings

Use the following underline characters consistently:

H1: `=`

H2: `-`

H3: `^`

H4: `~`

H5: `.`


Thank you for contributing to the Wazuh documentation.
