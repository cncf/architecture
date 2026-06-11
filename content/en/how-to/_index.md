---
title: How to submit
toc_hide: true
menu:
  main:
    weight: 30
---

## Welcome

Welcome to the Cloud Native Reference Architecture contributing guide, and thank you for your interest.

The goal of this site is to show real-life examples of successful cloud native architectures in order to make good choices easier to find.

The Cloud Native Reference Architecture content is stored in [this GitHub repo](https://github.com/cncf/architecture)
where you'll find a list of [issues](https://github.com/cncf/architecture/issues), and pull requests ([PRs](https://github.com/cncf/architecture/pulls)) for the site.

### Join the Reference Architectures community! {#join-the-reference-architectures-community}

If you want to contribute to the project or want to get in discussion with the maintainers and other contributors, you can join our [#reference-architectures](https://cloud-native.slack.com/archives/C07JCV4CQD9) channel on the CNCF Slack
— we'd love to meet you!

## Add new architecture {#add-new-architecture}

### Who can contribute?

Given the nature of the content we are only accepting PRs from CNCF members at this time. This will be verified during the PR approval process.

### Before you start

Before beginning your Reference Architecture contributor journey, be sure to complete the following steps:

1. Create a [GitHub account](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account), if you don't have one already.
2. Sign the [Contributor License Agreement](https://docs.linuxfoundation.org/lfx/easycla/v2-current/contributors) (CLA).
3. [Verify your commit signature](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification)
4. Enable [vigilant mode](https://docs.github.com/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits#about-vigilant-mode) in your GitHub account to display the "Verified" status on your commits.

### Submitting a new architecture {#submitting-a-new-architecture}

By raising a PR, you can submit a new architecture to the CNCF Reference Architecture site.

There are two template markdown files available which you can follow to see how you might build your story.

* [refarch.md](https://github.com/cncf/architecture/tree/main/archetypes/refarch.md) is a very common architecture template.
* [refarch-platform-engineering.md](https://github.com/cncf/architecture/tree/main/archetypes/refarch-platform-engineering.md) is based on the common architecture template but includes an additional section to highlight the Platform Engineering team.

The architecture should go in the `content/en/architectures` folder.
For each architecture, you should create a new folder with the name of the company.
Images should be stored in the `content/en/architectures/<company-name>/images` folder.
It's also possible to include diagrams in the architecture.
These can be included as Markdown code blocks, written in [mermaid.js](https://mermaid.js.org/) (also see the hugo documentation about [Mermaid diagrams](https://gohugo.io/content-management/diagrams/#mermaid-diagrams)).

### Best practices {#best-practices}

To facilitate the reviewing process, please use [semantic line breaks](https://sembr.org/) (e.g., one line per sentence).
We recommend checking out this [markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/)
to correctly format Markdown text in GitHub (e.g., hyperlink, bold, italic).
And when naming .md files, please use lowercase letters and hyphens instead of spaces to separate words and avoid parenthesis.

## Update an existing architecture {#update-an-existing-architecture}

To update an existing architecture, you can request changes by creating an issue or, if you are from the organization that submitted the architecture, work on the changes yourself and submit a PR.

### Request a change via an issue {#request-a-change-via-an-issue}

If you want to flag a problem with an architecture, you can use the "Report issue" option of the CNCF Reference Architecture webpage.
Locate yourself in the CNCF page of the architecture you'd like to flag and click on "Report issue".
This will automatically open an issue for you.

**We updated this guide based on templates from [The Good Docs Project](https://thegooddocsproject.dev/).**
