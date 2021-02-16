# awesome-runners :runner:

[![Awesome Badges](https://img.shields.io/badge/badges-awesome-green.svg)](https://github.com/Naereen/badges) [![GitHub license](https://img.shields.io/github/license/jonico/awesome-runners.svg)](https://github.com/jonico/awesome-runners/blob/main/LICENSE)
[![made-with-Markdown](https://img.shields.io/badge/Made%20with-Markdown-1f425f.svg)](http://commonmark.org)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/jonico/awesome-runners/graphs/commit-activity)
[![Open Source? Yes!](https://badgen.net/badge/Open%20Source%20%3F/Yes%21/blue?icon=github)](https://github.com/jonico/awesome-runners/)

A curated list of awesome self-hosted GitHub Action runner solutions in a large comparison matrix

## Purpose

The purpose of this repository is to provide an overview on self-hosted runner solutions for GitHub Actions compared by various criteria. There is no rating implied as the importance of the various categories differ from use case to use case.
Data can be out of date, so if a certain feature is told to be missing, please double check whether this is still the case.

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

### General collection of self-hosted runner best practices

During my research, I stumbled over [dduzgun-security/github-self-hosted-runners](https://github.com/dduzgun-security/github-self-hosted-runners) with :sparkles: tips on what to consider when using self-hosted runners by yourself.

## The matrix (might be better readable on [GitHub pages](https://jonico.github.io/awesome-runners/))

| Solution name                                                                       | Runtime                       | GHES | RegScope                                    | Scaling                              | AutoScaling                                                    | Architecture           | AutoDereg                | PATInRunner | CleanUp         | Privileged                        | Exposed                            | AllInOne                          | SelfService                      | IdleCosts                                                                 |
|-------------------------------------------------------------------------------------|-------------------------------|------|---------------------------------------------|--------------------------------------|----------------------------------------------------------------|------------------------|--------------------------|-------------|-----------------|-----------------------------------|------------------------------------|-----------------------------------|----------------------------------|---------------------------------------------------------------------------|
| [summerwind/actions-runner-controller](https://github.com/summerwind/actions-runner-controller)  [![GitHub license](https://img.shields.io/github/license/summerwind/actions-runner-controller.svg)](https://github.com/summerwind/actions-runner-controller/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/summerwind/actions-runner-controller.svg)](https://github.com/summerwind/actions-runner-controller/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/summerwind/actions-runner-controller.svg)](https://github.com/summerwind/actions-runner-controller/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/summerwind/actions-runner-controller.svg)](https://GitHub.com/summerwind/actions-runner-controller/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/summerwind/actions-runner-controller.svg)](https://GitHub.com/summerwind/actions-runner-controller/issues?q=is%3Aissue+is%3Aclosed)                            | k8s                           | ✅    | Enterprise, Org, Repo, Labels, RunnerGroups | k8s manifests & dynamic scaling      | ✅ (pending + running jobs or percentage runners already, scale up/down and flapping prevention parameters)       | x86, AMD64, ARM, ARM64 | ✅                        | no          | yes (ephemeral) | yes (install time, optional DInD) | no                                 | no                                | yes (IssueOps project available) | actions-runner controller + at least one pod per org runner               |
| [philips-labs/terraform-aws-github-runner](https://github.com/philips-labs/terraform-aws-github-runner)  [![GitHub license](https://img.shields.io/github/license/philips-labs/terraform-aws-github-runner.svg)](https://github.com/philips-labs/terraform-aws-github-runner/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/philips-labs/terraform-aws-github-runner.svg)](https://github.com/philips-labs/terraform-aws-github-runner/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/philips-labs/terraform-aws-github-runner.svg)](https://github.com/philips-labs/terraform-aws-github-runner/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/philips-labs/terraform-aws-github-runner.svg)](https://GitHub.com/philips-labs/terraform-aws-github-runner/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/philips-labs/terraform-aws-github-runner.svg)](https://GitHub.com/philips-labs/terraform-aws-github-runner/issues?q=is%3Aissue+is%3Aclosed)                        | AWS EC2/Lambda                | ✅    | Org, Repo, Labels, RunnerGroups             | Terraform config & dynamic scaling   | ✅ (pending jobs in org/repo, scale up/down and flapping prevention parameters)                                   | x86, AMD64, ARM, ARM64 | ✅                        | no          | no              | no                                | yes (GitHub check_run events)      | yes (at least intended this way)  | yes (IssueOps project available) | no (only Lambdas, KMS, queue service, API gateway)                        |
| [myoung34/docker-github-actions-runner](https://github.com/myoung34/docker-github-actions-runner)  [![GitHub license](https://img.shields.io/github/license/myoung34/docker-github-actions-runner.svg)](https://github.com/myoung34/docker-github-actions-runner/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/myoung34/docker-github-actions-runner.svg)](https://github.com/myoung34/docker-github-actions-runner/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/myoung34/docker-github-actions-runner.svg)](https://github.com/myoung34/docker-github-actions-runner/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/myoung34/docker-github-actions-runner.svg)](https://GitHub.com/myoung34/docker-github-actions-runner/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/myoung34/docker-github-actions-runner.svg)](https://GitHub.com/myoung34/docker-github-actions-runner/issues?q=is%3Aissue+is%3Aclosed)                           | Docker                        | ✅    | Org, Repo, Labels, RunnerGroups             | docker-compose, Nomad & k8s examples | ❌                                                              | x86, ARM64, ARM        | ✅                        | yes         | no              | yes (DInD)                        | no                                 | no                                | no                               | no                                                                        |
| [evryfs/github-actions-runner-operator](https://github.com/evryfs/github-actions-runner-operator)  [![GitHub license](https://img.shields.io/github/license/evryfs/github-actions-runner-operator.svg)](https://github.com/evryfs/github-actions-runner-operator/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/evryfs/github-actions-runner-operator.svg)](https://github.com/evryfs/github-actions-runner-operator/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/evryfs/github-actions-runner-operator.svg)](https://github.com/evryfs/github-actions-runner-operator/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/evryfs/github-actions-runner-operator.svg)](https://GitHub.com/evryfs/github-actions-runner-operator/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/evryfs/github-actions-runner-operator.svg)](https://GitHub.com/evryfs/github-actions-runner-operator/issues?q=is%3Aissue+is%3Aclosed)                           | k8s                           | ✅    | Organization, Repo                          | yes (k8s manifests define max and min)                  |✅ scales up to min runners ASAP, then adds one runner at a time up to max if all current runners are busy, scales down idle runners up to min| x86                    | ✅                        | no          | no              | yes (install time, optional DInD) | no                                 | no                                | no                               | actions-runner controller                                                 |
| [MonolithProjects/ansible-github_actions_runner](https://github.com/MonolithProjects/ansible-github_actions_runner)  [![GitHub license](https://img.shields.io/github/license/MonolithProjects/ansible-github_actions_runner.svg)](https://github.com/MonolithProjects/ansible-github_actions_runner/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/MonolithProjects/ansible-github_actions_runner.svg)](https://github.com/MonolithProjects/ansible-github_actions_runner/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/MonolithProjects/ansible-github_actions_runner.svg)](https://github.com/MonolithProjects/ansible-github_actions_runner/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/MonolithProjects/ansible-github_actions_runner.svg)](https://GitHub.com/MonolithProjects/ansible-github_actions_runner/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/MonolithProjects/ansible-github_actions_runner.svg)](https://GitHub.com/MonolithProjects/ansible-github_actions_runner/issues?q=is%3Aissue+is%3Aclosed)                  | bare metal/VM                 | ✅    | Organization, Repo                          | based on Ansible playbook            | ❌                                                              | x86, AMD64, ARM, ARM64 | explicitly in playbook   | no          | no              | install Ansible agents            | Ansible agents                     | possible                          | no                               | Ansible agents                                                            |
| [SanderKnape/github-runner](https://github.com/SanderKnape/github-runner)  [![GitHub license](https://img.shields.io/github/license/SanderKnape/github-runner.svg)](https://github.com/SanderKnape/github-runner/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/SanderKnape/github-runner.svg)](https://github.com/SanderKnape/github-runner/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/SanderKnape/github-runner.svg)](https://github.com/SanderKnape/github-runner/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/SanderKnape/github-runner.svg)](https://GitHub.com/SanderKnape/github-runner/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/SanderKnape/github-runner.svg)](https://GitHub.com/SanderKnape/github-runner/issues?q=is%3Aissue+is%3Aclosed)                                       | Docker                        | ❌    | Org, Repo, Labels                           | k8s manifest example                 | ❌                                                              | x86                    | ✅                        | yes         | no              | no                                | no                                 | no                                | no                               | no                                                                        |
| [machulav/ec2-github-runner](https://github.com/machulav/ec2-github-runner)  [![GitHub license](https://img.shields.io/github/license/machulav/ec2-github-runner.svg)](https://github.com/machulav/ec2-github-runner/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/machulav/ec2-github-runner.svg)](https://github.com/machulav/ec2-github-runner/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/machulav/ec2-github-runner.svg)](https://github.com/machulav/ec2-github-runner/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/machulav/ec2-github-runner.svg)](https://GitHub.com/machulav/ec2-github-runner/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/machulav/ec2-github-runner.svg)](https://GitHub.com/machulav/ec2-github-runner/issues?q=is%3Aissue+is%3Aclosed)                                      | AWS EC2                       | ❌    | Repo                                        | GitHub Actions workflow params       | ✅ (1 runner per workflow run that requests it)                 | x86                    | part of Actions workflow | no          | yes (ephemeral) | no                                | embedded in GitHub Action workflow | possible                          | yes (Actions Workflow)           | no                                                                        |
| [terraform-google-modules/terraform-google-github-actions-runners](https://github.com/terraform-google-modules/terraform-google-github-actions-runners)  [![GitHub license](https://img.shields.io/github/license/terraform-google-modules/terraform-google-github-actions-runners.svg)](https://github.com/terraform-google-modules/terraform-google-github-actions-runners/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/terraform-google-modules/terraform-google-github-actions-runners.svg)](https://github.com/terraform-google-modules/terraform-google-github-actions-runners/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/terraform-google-modules/terraform-google-github-actions-runners.svg)](https://github.com/terraform-google-modules/terraform-google-github-actions-runners/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/terraform-google-modules/terraform-google-github-actions-runners.svg)](https://GitHub.com/terraform-google-modules/terraform-google-github-actions-runners/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/terraform-google-modules/terraform-google-github-actions-runners.svg)](https://GitHub.com/terraform-google-modules/terraform-google-github-actions-runners/issues?q=is%3Aissue+is%3Aclosed)| k8s (GKE), Docker, VMs (GCE)  | ❌    | Repo                                        | Terraform config/k8s manifests       | only on k8s, based on generic pod CPU consumption (HPA metric) | x86                    | only worked for Docker   | yes         | no              | no                                | no                                 | VMs could be configured like this | no                               | at least one idle runner to allow HPA to kick in based on CPU consumption |
| [cosmoconsult/github-runner-windows](https://github.com/cosmoconsult/github-runner-windows)  [![GitHub license](https://img.shields.io/github/license/cosmoconsult/github-runner-windows.svg)](https://github.com/cosmoconsult/github-runner-windows/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/cosmoconsult/github-runner-windows.svg)](https://github.com/cosmoconsult/github-runner-windows/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/cosmoconsult/github-runner-windows.svg)](https://github.com/cosmoconsult/github-runner-windows/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/cosmoconsult/github-runner-windows.svg)](https://GitHub.com/cosmoconsult/github-runner-windows/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/cosmoconsult/github-runner-windows.svg)](https://GitHub.com/cosmoconsult/github-runner-windows/issues?q=is%3Aissue+is%3Aclosed)                              | Windows Docker container      | ❌    | Org, Repo                                   | docker compose example in [blog post](https://tobiasfenster.io/building-docker-images-for-multiple-windows-server-versions-using-self-hosted-github-runners)      | ❌                                                              | win-x86                | replace but not remove   | yes         | no              | no                                | no                                 | no                                | no                               | no                                                                        |
| [aslafy-z/github-runner](https://github.com/aslafy-z/github-runner)  [![GitHub license](https://img.shields.io/github/license/aslafy-z/github-runner.svg)](https://github.com/aslafy-z/github-runner/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/aslafy-z/github-runner.svg)](https://github.com/aslafy-z/github-runner/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/aslafy-z/github-runner.svg)](https://github.com/aslafy-z/github-runner/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/aslafy-z/github-runner.svg)](https://GitHub.com/aslafy-z/github-runner/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/aslafy-z/github-runner.svg)](https://GitHub.com/aslafy-z/github-runner/issues?q=is%3Aissue+is%3Aclosed)                                          | (fat) Docker, AWS EC2         | ❌    | Repo, Labels                                | k8s & Nomad examples                 | ❌                                                              | x86                    | ❌                        | yes         | no              | optional to run DInD              | no                                 | yes (50G+ image with all tools)   | no                               | no                                                                        |
| [redhat-actions/self-hosted-runner-installer](https://github.com/redhat-actions/self-hosted-runner-installer)  [![GitHub license](https://img.shields.io/github/license/redhat-actions/self-hosted-runner-installer.svg)](https://github.com/redhat-actions/self-hosted-runner-installer/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/redhat-actions/self-hosted-runner-installer.svg)](https://github.com/redhat-actions/self-hosted-runner-installer/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/redhat-actions/self-hosted-runner-installer.svg)](https://github.com/redhat-actions/self-hosted-runner-installer/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/redhat-actions/self-hosted-runner-installer.svg)](https://GitHub.com/redhat-actions/self-hosted-runner-installer/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/redhat-actions/self-hosted-runner-installer.svg)](https://GitHub.com/redhat-actions/self-hosted-runner-installer/issues?q=is%3Aissue+is%3Aclosed)                     | Kubernetes (OpenShift)        | ❌    | Org, Repo, Labels                           | HELM chart parameters                | ❌                                                              | x86                    | ✅                        | yes         | no              | no                                | no                                 | no                                | no                               | no                                                                        |
| [peter-murray/github-actions-runner-container](https://github.com/peter-murray/github-actions-runner-container)  [![GitHub license](https://img.shields.io/github/license/peter-murray/github-actions-runner-container.svg)](https://github.com/peter-murray/github-actions-runner-container/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/peter-murray/github-actions-runner-container.svg)](https://github.com/peter-murray/github-actions-runner-container/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/peter-murray/github-actions-runner-container.svg)](https://github.com/peter-murray/github-actions-runner-container/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/peter-murray/github-actions-runner-container.svg)](https://GitHub.com/peter-murray/github-actions-runner-container/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/peter-murray/github-actions-runner-container.svg)](https://GitHub.com/peter-murray/github-actions-runner-container/issues?q=is%3Aissue+is%3Aclosed)                    | Docker                        | ❌    | Enterprise, Org, Repo, Labels, RunnerGroups | ❌                                    | ❌                                                              | x86                    | ✅                        | yes         | yes             | no                                | no                                 | no                                | no                               | no                                                                        |
| [lts-beratung/ansible-github-action-runner](https://github.com/lts-beratung/ansible-github-action-runner)  [![GitHub license](https://img.shields.io/github/license/lts-beratung/ansible-github-action-runner.svg)](https://github.com/lts-beratung/ansible-github-action-runner/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/lts-beratung/ansible-github-action-runner.svg)](https://github.com/lts-beratung/ansible-github-action-runner/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/lts-beratung/ansible-github-action-runner.svg)](https://github.com/lts-beratung/ansible-github-action-runner/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/lts-beratung/ansible-github-action-runner.svg)](https://GitHub.com/lts-beratung/ansible-github-action-runner/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/lts-beratung/ansible-github-action-runner.svg)](https://GitHub.com/lts-beratung/ansible-github-action-runner/issues?q=is%3Aissue+is%3Aclosed)                       | bare metal or VM              | ❌    | Org, Repo                                   | Ansible playbook                     | ❌                                                              | x86                    | ✅                        | yes         | no              | install Ansible agents            | Ansible agents                     | possible                          | no                               | Ansible agents                                                            |
| [rakheshster/github-runner-on-ubuntu](https://github.com/rakheshster/github-runner-on-ubuntu)  [![GitHub license](https://img.shields.io/github/license/rakheshster/github-runner-on-ubuntu.svg)](https://github.com/rakheshster/github-runner-on-ubuntu/blob/master/LICENSE) [![GitHub contributors](https://img.shields.io/github/contributors/rakheshster/github-runner-on-ubuntu.svg)](https://github.com/rakheshster/github-runner-on-ubuntu/graphs/contributors/) [![GitHub Stars](https://img.shields.io/github/stars/rakheshster/github-runner-on-ubuntu.svg)](https://github.com/rakheshster/github-runner-on-ubuntu/stargazers/) [![GitHub issues](https://img.shields.io/github/issues/rakheshster/github-runner-on-ubuntu.svg)](https://GitHub.com/rakheshster/github-runner-on-ubuntu/issues/) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/rakheshster/github-runner-on-ubuntu.svg)](https://GitHub.com/rakheshster/github-runner-on-ubuntu/issues?q=is%3Aissue+is%3Aclosed)                             | Azure VM (ARM template)       | ❌    | Repo                                        | ❌                                    | ❌                                                              | x86                    | ❌                        | yes         | no              | no                                | no                                 | possible                          | no                               | no                                                                        |

## Comparison categories

#### Runtime - Container, Kubernetes, virtual machines

Specifies whether the self-hosted runners are running on a container, Kubernetes cluster or virtual machine. Virtual machine based runners typically have some cloud specific dependencies.

#### GHES - GitHub Enterprise Server support

While GitHub.com is supported by all self-hosted runner solutions evaluated, not all of them support GitHub Enterprise Server yet (although supporting GitHub Enterprise Server is often just a matter on changing the API endpoint).

#### RegScope - Registration Scope

Self-hosted runners can be registered on the repo, org and enterprise level and may register with custom labels inside runner groups - but not all runner solutions provide support for all those options.

#### Scaling - Ability to specify multiple runner instances

Some self-hosted runner solutions have the ability to specify how many runners of a certain kind should be launched and whether crashed runners should be restarted.

#### Scaling

Some self-hosted runner solutions have the ability to scale automatically with the amount of pending jobs, busy runners, CPU utilization, ...

#### Architecture - Operating systems supported

While self-hosted action runners can support Linux (x86, ARM, ARM64), Mac and Windows - most self-hosted runner solutions are restricted to a subset of those architectures

#### Dereg - Automatic Runner Deregistration

Not all runner solutions remove themselves after they have been deleted, which can be problematic, especially, if combined aith auto-scaling capabilities.

#### PATInRunner - Personal access or OAuth token needed in runner

Some runner solutions provide a personal access token (PAT) or OAuth token directly to the runner so that it can register itself. This imposes the risk of a malicious job trying to steal the token and use it to elevate its permissions. Solutions that only pass a runner token to the actual runners are preferred from a security perspective.

#### CleanUp - Automated clean up after a build

While self-hosted runner provide some isolation between jobs, it is the responsibility of the job to clean up in most cases. Some self-runner solutions automatically de-register and clean-up runners after every build to avoid any interference between jobs.


#### Privileged - Any special privileges needed to run or install the solution

Calls out any special privileges (like Kubernetes cluster admin, Docker privileged mode) needed to run or install the solution.

#### Exposed - Need for GitHub to reach parts of the runner solution via web hooks

Some centralized runner solutions rely on the ability to receive web hook events from GitHub about new jobs. This approach might not be feasible for some installations, although a reverse proxy may help.

#### AllInOne - Software installed in the self-hosted runners

GitHub's own, hosted runners have a lot of software already pre-installed. Most container based solutions follow a different philosophy where only a minimum amount of software is pre-installed.

#### Contributors - Number of contributors to the solution

While the number of contributors is not the only criteria, it is typically a good indicator for the maturity of a solution.

#### SelfService - Ability for end users to setup new runner scale sets

Some runner solutions have add-ons that allow end users to stand up new runner groups in a self-service fashion, e.g. via IssueOps.

#### IdleCosts - Costs that incur even if no jobs are running

Some solutions require certain central components to be up and running all the time or at least one idle runner to allow scaling up properly - this category provides an idea of what is needed in terms of components, not concrete $$$ costs.
