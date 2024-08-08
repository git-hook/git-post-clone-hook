# Overview

As git does not provide a `post-clone` hook, some repositories come with manual instructions for post-clone configuration.
This project effectively provides a `post-clone` hook, allowing project maintainers to specify a project's post-clone behavior and install other various hooks.

# Usage

To clone a repository with post-clone hooks:

    curl -fsSL https://raw.githubusercontent.com/git-hook/post-clone/master/bin/clone | bash -s -- <normal-clone-args>

All arguments will be passed directly to `git clone`.

## Manual

1.  Clone this repository somewhere on disk:

        git clone https://github.com/git-hook/post-clone /tmp/post-clone

2.  Clone the desired repository:

        git clone --template=/tmp/post-clone git@github.com:username/repo-of-interest

In addition to cloning the repository, this method will: ensure

- if present in the cloned repo, `/hooks/` is symlinked to
  `/.git/hooks/`

- if present in the cloned repo, `/.git/hooks/post-clone` is invoked

> [!NOTE]
> This hook will not be automatically invoked again.

# Benefits

Using this `post-clone` template allows repo maintainers to

- automate installation of client-side git hooks
- version-control this automation inside the relevant repository

# Acknowledgements

This git hook was inspired by [this StackOverflow post].

[this stackoverflow post]: http://stackoverflow.com/questions/2141492/git-clone-and-post-checkout-hook/2141577#2141577
