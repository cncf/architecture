---
title: How to submit
toc_hide: true
menu:
  main:
    weight: 30
---

## Welcome 

Welcome to the Cloud Native Reference Architecture contributing guide, and thank you for your interest. 

## CNCF Reference Architecture overview 

The goal of this site is to show real-life examples of successful cloud native architectures in order to make good choices easier to find. 

The Cloud Native Reference Architecture content is stored in [this GitHub repo](https://github.com/cncf/architecture) 
where you'll find a list of [issues](https://github.com/cncf/architecture/issues), pull requests ([PRs](https://github.com/cncf/architecture/pulls)), and 
[discussions](https://github.com/cncf/architecture/discussions) about the site. 

## Who can contribute?

Given the nature of the content we are only accepting PRs from CNCF members at this time. This will be verified during the PR approval process.


## Before you start

Before beginning your Glossary contributor journey, be sure to complete the following steps:

1. Create a [GitHub account](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account), if you don't have one already. 
2. Sign the [Contributor License Agreement](https://docs.linuxfoundation.org/lfx/easycla/v2-current/contributors) (CLA). 
3. [Verify your commit signature](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification)
4. Enable [vigilant mode](https://docs.github.com/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits#about-vigilant-mode) in your GitHub account to display the "Verified" status on your commits. 

## Best practices {#best-practices}

To facilitate the reviewing process, please use [semantic line breaks](https://sembr.org/) (e.g., one line per sentence).
We recommend checking out this [markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/) 
to correctly format Markdown text in GitHub (e.g., hyperlink, bold, italic).
And when naming .md files, please use lowercase letters and hyphens instead of spaces to separate words and avoid parenthesis.

## Style guide

Read our [Style Guide](/style-guide/) to understand our guidelines for formatting and writing documents and make the contribution process more efficient. 

## Join the Reference Architectures community! {#join-the-reference-architectures-community}

If you want to contribute regularly, consider joining our monthly Glossary Working Group meetings. 
You can find the meeting details in the [CNCF calendar](https://www.cncf.io/calendar/). 
You can also connect with the maintainers and fellow contributors in our [#reference-architectures](https://cloud-native.slack.com/archives/C07JCV4CQD9) channel on the CNCF Slack 
— we'd love to meet you! 

## Work on an existing issue {#work-on-an-existing-issue}

Go to the [Reference Architecture GitHub repo issues](https://github.com/cncf/architecture/issues) to find a list of available issues. 
You can use labels (e.g., English language, help needed, good first issue) to filter out issues.

![Issue and labels](/images/how-to/issue-and-labels.png)

Be sure the term you select hasn't already been assigned to anybody. 
For example, here you can see that the first three terms are available while the fourth one has already been assigned.

![assigning a term](/images/how-to/howto-04.png)

Once you select a term to work on, comment on the issue. 

![Claiming an issue](/images/how-to/claiming-an-issue.png)

Additionally, notify the maintainers on the [#glossary](https://cloud-native.slack.com/archives/C07JCV4CQD9) channel of the CNCF Slack workspace.

For the next steps, please refer to the [Submitting a new term (creating a PR)](#submitting-a-new-term) section.

**Note**: you can start working on an issue after the maintainers assigned it to you. 

### Creating an issue {#creating-an-issue}

Go to the [Reference Architecture GitHub repo](https://github.com/cncf/architecture/issues) issues and click on "New issue".

![issues](/images/how-to/howto-01.png)

### Triaging your issue {#triaging-your-issue}

Next, the maintainers will triage the issue. 

### Submitting a new architecture (creating a PR) {#submitting-a-new-architecture}

There is an [example markdown file](https://github.com/cncf/architecture/content/en/architectures/example.md), which you can follow to see how you might build your story. Diagrams are available using [mermaid.js](https://mermaid.js.org/).

Once the architecture is ready to submit, go to content (under <>code)…

![content](/images/how-to/howto-05.png)

…then "en" (for English, other languages are not yet supported)

![language folder](/images/how-to/howto-06.png)

…and select `_TEMPLATE.md`

![template](/images/how-to/howto-07.png)

Copy the content…

![copy content](/images/how-to/howto-08.png)

…and go back to the "en" folder. Click "Add file" and select "Create new file".

![create new file](/images/how-to/howto-09.png)

Add the name of the architecture in the URL as described in the [Best practices](#best-practices) section. 
Add the .md extension at the end of the name (without this extension you won't be able to preview your file).
Now paste the template content in the section below. Copy and paste the text of your definition into the file.
To verify you've used Markdown as described in the [Best practices](#best-practices) section, click on "Preview".

![finalize term](/images/how-to/howto-10.png)

Scroll down and name the new commit file. Hit "Commit new file" when you are ready to submit 
and…

![commit new file](/images/how-to/howto-11.png)

… you're now ready to create a new PR:

![create a pr](/images/how-to/howto-12.png)

Once you hit the "Create pull request" button your PR should be visible in the "Pull requests" tab.

![prs](/images/how-to/howto-13.png)

## Update an existing architecture {#update-an-existing-architecture}

To update an existing architecture, you can request changes by creating an issue or, if you are from the organization that submitted the architecture, work on the changes yourself and submit a PR.

### Request a change via an issue {#request-a-change-via-an-issue}

If you want to flag a problem with an architecture, you can use the "Report issue" option of the CNCF Reference Architecture webpage. 
Locate yourself in the CNCF page of the architecture you'd like to flag and click on "Report issue". 
This will automatically open an issue for you

![report issue](/images/how-to/howto-14.png)

Please describe your suggestions and why they are needed. Hit submit, and that's it. 

![submit issue](/images/how-to/howto-15.png)

## Spell check {#spell-check}

There are two main reasons why the spell check can fail:

- The PR contains misspellings. 
- The PR contains words that are not registered in the word list. 

To add new words to the list, follow these steps:

1. In your PR, locate the file "wordlist.txt". 
2. Click "Edit this file" and add the missing words in alphabetic order. 
3. Add a commit message and select "Sign off and propose changes".

**Note**: the spell check is case-insensitive. 


**We updated this guide based on templates from [The Good Docs Project](https://thegooddocsproject.dev/).**
