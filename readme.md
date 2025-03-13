![Mend Renovate CLI banner](https://docs.renovatebot.com/assets/images/mend-renovate-cli-banner.jpg)

[![License: AGPL-3.0-only](https://img.shields.io/badge/license-%20%09AGPL--3.0--only-blue.svg)](https://raw.githubusercontent.com/renovatebot/renovate/main/license)
[![codecov](https://codecov.io/gh/renovatebot/renovate/branch/main/graph/badge.svg)](https://codecov.io/gh/renovatebot/renovate)
[![Renovate enabled](https://img.shields.io/badge/renovate-enabled-brightgreen.svg)](https://renovatebot.com/)
[![Build status](https://github.com/renovatebot/renovate/actions/workflows/build.yml/badge.svg)](https://github.com/renovatebot/renovate/actions/workflows/build.yml)
![Docker Pulls](https://img.shields.io/docker/pulls/renovate/renovate?color=turquoise)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/renovatebot/renovate/badge)](https://securityscorecards.dev/viewer/?uri=github.com/renovatebot/renovate)

# What is the Mend Renovate CLI?

* 💡== automated dependency update tool 💡 /
  * allows
    * updating AUTOMATICALLY dependencies | your code
      * == create PRs
* requirements
  * Renovate runs | your repo
* how does it work? 
  * looks for references to dependencies (👀public & private👀)

## Features

- create AUTOMATICALLY PRs | your repo
  - -> package files -- are AUTOMATICALLY -- discovered
  - support
    - LARGE collection of languages and platforms
    - -- connection with -- private repositories & package registries 
- provides information about the suggested updates (age, adoption, pass rates, merge confidence)
- HIGHLY configurable

### Languages

* npm, Java, Python, .NET, Scala, Ruby, Go, Docker, ...
* [> 90 different package managers](docs/usage/modules/manager)

### Platforms

* GitHub, GitLab, Bitbucket, Azure DevOps, AWS Code Commit, Gitea, Forgejo, Gerrit (experimental)

## Ways to run Renovate

* recommendation
  * automated job scheduling system / run Renovate

### Mend Renovate Community (Cloud-Hosted)

* TODO:
**Supports: GitHub.com, Bitbucket Cloud**

Hosted by Mend.io.
No setup is needed.
Community plan available (Free)

- GitHub Cloud: Install the [Renovate Cloud-Hosted App](https://github.com/apps/renovate) on your GitHub org, then select the repos to enable
- Bitbucket Cloud: Add the [Mend App](https://marketplace.atlassian.com/apps/1232072/mend) to your Workspace, then add the Mend Renovate user to the projects you want to enable

### Mend Renovate Community (Self-hosted)

* supports
  * GitHub,
  * GitLab,
  * Bitbucket Data Center
* steps
  * install and run your OWN Renovate server
  * access internal packages
* options
  * [Mend Renovate Community Self-Hosted](https://github.com/mend/renovate-ce-ee/tree/main/docs)
    * == FREE
  * [Mend Renovate Enterprise](https://www.mend.io/mend-renovate/)
    * == Paid

### Others

* == 
  * NOT use a pre-built job scheduling system
  * build your own

#### Run Renovate | your Pipeline

* -- depending on the -- platform
  * GitHub Action: [renovatebot/github-action](https://github.com/renovatebot/github-action)
  * GitLab Runner: [Renovate Runner project](https://gitlab.com/renovate-bot/renovate-runner/)
  * AzureDevOps action: [Renovate Me extension](https://marketplace.visualstudio.com/items?itemName=jyc.vsts-extensions-renovate-me)
    * created & maintained personally -- by a -- Renovate developer/user
  * Custom pipeline
    * create a custom pipeline (== ".yml") / triggers `npx renovate`
    * see [here](lib/modules/platform/azure).

#### Run Renovate CLI

* supports
  * ALL platforms
* see [here](docs/usage/getting-started/running.md)
