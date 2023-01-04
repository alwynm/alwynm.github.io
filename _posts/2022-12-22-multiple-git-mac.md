---
layout: post
title: Multiple Git configs on MacOS
categories: General
ready : true
---

If you have multiple git accounts and would like to config them on your mac, this post is for you.

## Generating a new SSH key

You can generate a new SSH key on your local machine for both personal and work github account. After you generate the key, you can add the key to your account on GitHub.com to enable authentication for Git operations over SSH.

Open terminal and paste the text below, substituting in your GitHub email address
```shell
> ssh-keygen -t ed25519 -C "your_email@personal.com"`
> Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM: ~/.ssh/personal
```
```shell
> ssh-keygen -t ed25519 -C "your_email@work.com"`
> Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM: ~/.ssh/work
```

Add SSH keys to git accounts.

### SSH config

In order to be able to determine what SSH key will be used for each repository, we will need to add configuration to our SSH config to associate each key to certain repositories.
Open `~/.ssh/config`. Once in your editor, you will need two different sections for `github.com` hosts. Your configuration will look like this:

```shell
Host github.com-perosnal
  Hostname github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/personal
Host github.com-work
  Hostname github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/work
```

### Associate Repository to New Key

Once we have that configuration in place, the next step is not very intuitive, but we’ll try to make it clear.

We have to either clone our repository in a different way or modify the remote origin url for our existing repositories.

Let’s see how to do it in both cases:

#### Clone New Repository

If we are going to clone a new repository, instead of using the original `github.com` url, we will clone it in a slightly different way:

```shell
git clone git@github.com-work:alwyn/my-work-repo.git
```

Notice that the hostname has changed to use the host we previously configured in our `~/.ssh/config` file!

#### Modify Remote Url For Existing Repository

If instead we already have a local repository we would like to configure to be able to push using the new SSH key, we’d have to do the following:

```shell
git remote set-url origin git@github.com-work:alwyn/my-work-repo.git
```

### Set User For Current Repository

One more thing to do, if we have a global username and email already defined in Git, is to override the username and email for our current repository. This step will only be needed if you need to use a different user from the one you normally use.

In order to do so, you’d just have to do something similar to this inside your git repository:

```shell
git config user.name  "work"
git config user.email "your_email@work.com"
```

Source: [theboreddev](https://theboreddev.com/use-multiple-ssh-keys-different-git-accounts/)

