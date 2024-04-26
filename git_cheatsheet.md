
## How to manage multiple SSH keys

The process is very simple, open a git-bash terminal and run the following commands to generate a new SSH key pair:

```bash
cd ~/.ssh
ssh-keygen -t ed25519 -C "your_email@example.com"
```

use a meaningful name like `id_ed25519_github` and then enter a secure passphrase. Now you should have a SSH key-pair inside the `~/.ssh` directory, something like `id_ed25519_github` and `id_ed25519_github.pub`, your private and public keys.

Then create a `~./.ssh/config` file

```bash
touch config
```

and write a configuration similar to the following example:

```bash
# GitHub account
Host github.com
  Hostname github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_ed25519_github

# GitLab account
Host gitlab.com
  Hostname gitlab.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_ed25519_gitlab

# CERN GitLab account
Host gitlab.cern.ch
  Hostname gitlab.cern.ch
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_ed25519_gitlab_cern
```

Now, you can verify if everything is functioning correctly by executing the following command:

```bash
ssh -T git@github.com
git clone git@github.com:username/dummy_repository_github.git
```

> [!warning]
> `Host` is only an alias and `Hostname` is the domain.

In some Linux machines if you get the error `Bad owner or permissions on...` you have to change the permission of the `config` file with:

```bash
chmod 600 config
```

If you have multiple GitHub accounts, you can do the following:

```bash
# GitHub account
Host personal-github.com
  Hostname github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_ed25519_github_personal

# GitLab account
Host github.com
  Hostname github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_ed25519_github_work
```

The GitHub work account is functioning normally. However, when cloning your personal projects, you now need to adjust the command to:

```bash
git clone git@personal-github.com:username/dummy_repository_github.git
```

if you already have a repository and you make changes to the `~/.ssh/config` file, you also need to update the `.git/config` file to ensure proper functionality.

```bash
# Before
[remote "origin"]
	url = git@github.com:username/dummy_repository_github.git
	fetch = +refs/heads/*:refs/remotes/origin/*
# After
[remote "origin"]
	url = git@personal-github.com:username/dummy_repository_github.git
	fetch = +refs/heads/*:refs/remotes/origin/*
```

You can do this process manually or with the following command:

```bash
git remote set-url origin git@personal-github.com::username/dummy_repository_github.git
```

When cloning the repository for the first time, the `url` is automatically populated with the correct information.

> [!note] Note
> If `Could not open a connection to your authentication agent.` run before `eval $(ssh-agent)`

# References

[GitHub - About SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh)

[GitHub - Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

[GitHub - Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

[GitLab - Use SSH keys to communicate with GitLab](https://docs.gitlab.com/ee/user/ssh.html)

[GitLab - Generate an SSH key pair](https://docs.gitlab.com/ee/user/ssh.html#generate-an-ssh-key-pair)

[GitLab - Add an SSH key to your GitLab account](https://docs.gitlab.com/ee/user/ssh.html#add-an-ssh-key-to-your-gitlab-account)

[GitLab - Use different accounts on a single GitLab instance](https://docs.gitlab.com/ee/user/ssh.html#use-different-accounts-on-a-single-gitlab-instance)
