# Devpod Example

A simple example of how to use my dotfiles repository with a Devpod devcontainer.
It works completely independent of your operating system — all you need is Devpod and a provider of your choice.
In this example, we’ll use Docker as the provider.

We also use [mise](https://mise.jdx.dev) as our all-in-one, cross-OS package manager. It provides a great developer experience, allowing us to easily switch between versions of programming languages without restarting the container.

## How does it work?

After installing Devpod, make sure to add the Docker provider:

```bash
devpod provider add docker
```

From the project root, run the following command to start your workspace:

```bash
devpod up --dotfiles https://github.com/dankaiser1808/dotfiles.git .
```

It will perform the following actions:
1. Create a container based on the devcontainer.json file located in .devcontainer/.
2. Run scripts/setup to trust the mise.toml tool specification which is required before mise will install the defined tools.

## Devpod Dotfiles Support

Devpod has built-in dotfiles support.
When you pass --dotfiles https://github.com/dankaiser1808/dotfiles.git, Devpod will clone the repository and look for a setup script in the following locations:

- install.sh
- install
- bootstrap.sh
- bootstrap
- script/bootstrap
- setup.sh
- setup
- script/setup

Once a matching script is found, it will be executed.

From there, chezmoi takes over to apply and initialize the dotfiles.

You can check my [dotfiles repository](https://github.com/dankaiser1808/dotfiles) to see the full workflow.