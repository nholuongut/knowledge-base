# direnv - `.envrc`

[direnv](https://direnv.net/) reads `.envrc` files and auto-loads useful environment variables upon switching directories
that allow you to quickly switch between AWS profiles, EKS clusters, Terraform & Terragrunt versions or any number of
other software versions or profiles.

<!-- INDEX_START -->

- [Install direnv](#install-direnv)
- [Commands](#commands)
  - [Enable direnv in your shell](#enable-direnv-in-your-shell)
  - [Approve `.envrc` files](#approve-envrc-files)
- [Advanced Examples](#advanced-examples)
  - [General - Ansible, Cloudflare, Docker, GitHub, Pre-Commit](#general---ansible-cloudflare-docker-github-pre-commit)
  - [Python](#python)
  - [AWS](#aws)
  - [GCP](#gcp)
  - [Kubernetes](#kubernetes)
  - [Terraform](#terraform)

<!-- INDEX_END -->

## Install direnv

On Mac just:

```shell
brew install direnv
```

This is automatically installed as part of core software by `make` in [DevOps-Bash-tools](devops-bash-tools.md) repo.

For other platforms and more install details read:

<https://direnv.net/docs/installation.html>

## Commands

### Enable direnv in your shell

Add the direnv hook to your shell `$HOME/.bashrc` or similar:

```shell
eval "$(direnv hook bash)"
```

### Approve `.envrc` files

When you switch to a directory containing an `.envrc` file for the first time it will print a warning
that you need to approve the `.envrc` file.

`cd` to a dir with a `.envrc` and then run this allow it to automatically load this `.envrc` each time in future:

```shell
direnv allow
```

To edit, will auto-approve when you save and exit:

```shell
direnv edit
```

## Advanced Examples

### General - Ansible, Cloudflare, Docker, GitHub, Pre-Commit

[.envrc](https://github.com/nholuongut/devops-bash-tools/blob/master/.envrc)

### Python

Since recent versions of pip on Macs don't like to let you install packages to the system python any more,
you really need to keep a virtualenv activated all the times for your personal tools and scripts.

Create your Python virtual:

```shell
virtualenv ~/venv
```

Then use this `.envrc` to keep it automatically activated:

[.envrc-python](https://github.com/nholuongut/devops-bash-tools/blob/master/.envrc-python)

### AWS

[.envrc-aws](https://github.com/nholuongut/devops-bash-tools/blob/master/.envrc-aws)

### GCP

[.envrc-gcp](https://github.com/nholuongut/devops-bash-tools/blob/master/.envrc-gcp)

### Kubernetes

[.envrc-kubernetes](https://github.com/nholuongut/kubernetes-configs/blob/master/.envrc-kubernetes) -
[Kubernetes-configs](https://github.com/nholuongut/kubernetes-configs) repo

or

[.envrc-kubernetes](https://github.com/nholuongut/devops-bash-tools/blob/master/.envrc-kubernetes) -
[DevOps-Bash-tools](https://github.com/nholuongut/devops-bash-tools) repo

### Terraform

[.envrc-terraform](https://github.com/nholuongut/devops-bash-tools/blob/master/.envrc-terraform)

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=DevOps-Bash-tools&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/devops-bash-tools)

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=Terraform&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/Terraform)
