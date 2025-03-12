# test-for-mirroring

This is a test for how to develop in gitlab for a project where the main fork is hosted on github.

## Setup

- create a fork of the repository on github: https://github.com/colmtalbot-test/test-for-mirroring/fork in your personal namespace

- clone the upstream repository

```console
git clone git@github.com:colmtalbot-test/test-for-mirroring.git
cd test-for-mirroring
```

- add a new remote pointing to gitlab

```console
git remote add gitlab git@gitlab.com/ColmTalbot/test-for-mirroring.git
```

- set up [repository mirroring](https://docs.gitlab.com/17.9/user/project/repository/mirror/)
  - set the repository URL using ssh pointing to your fork `ssh://git@github.com/colmtalbot/test-for-mirroring.git`
  - mirror direction: Push
  - authentication method: SSH public key
  - username: git **Note: this is not your username**
- after creating the mirror, copy the SSH public key and add it to your [github SSH keys](https://github.com/settings/keys)
- from the gitlab repository settings, trigger a test of the mirror

## Contributing changes upstream

- create a feature branch and push to the gitlab remote

```console
git checkout -b feature-branch
git push --set-upstream gitlab feature-branch
```

- the feature branch should automatically mirror to your fork on github
- open a pull request with the upstream through the web interface
