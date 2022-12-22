---
layout: post
title: Multiple Git configs on MacOS
categories: General
ready : true
---

If you have multiple git accounts and would like to config them in one computer, this post is for you. `.gitconfig` 
file is starter point for Git to identify what configurations need to be used. 

## Generating a new SSH key

You can generate a new SSH key on your local machine for both personal and work github account. After you generate the key, you can add the key to your account on GitHub.com to enable authentication for Git operations over SSH.

Open terminal and paste the text below, substituting in your GitHub email address
```shell
> ssh-keygen -t ed25519 -C "your_email@example.com"`
> Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM: [Press enter]
```

At the prompt, type a secure passphrase.
```shell
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```
Make sure your ssh-key has passphrase when you create it because it is required for Apple keychain. If you don't have, you still can modify your no-passphrase-privatekey to have one by runnint this command: 
```shell
ssh-keygen -p -f ~/.ssh/<.your-privatekey-filename.>
```

### Create separate directories for repos

Organize the projects that you are working on into separate folders by the profiles you want to work with. For example 
let's say there are two Git profiles you are working with. This is a common use case for most of us:

* WORK: for work related projects
* PERSONAL: for open source and side projects

### Create a global Git configuration

Create the global `.gitconfig` file in your home directory if it doesn't already exist. Then add all the profile 
directories as an entry like in the example below.

The way this works is very intuitive – if the directory path where you created the Git directory matches one of the 
paths in `inclideIF`, then Git uses that particular profile configuration file. Otherwise, it uses the default 
configuration.

```
[includeIf "gitdir:~/personal/"]
  path = ~/.gitconfig-personal
[includeIf "gitdir:~/work/"]
  path = ~/.gitconfig-work
```

### Create individual Git configurations for profiles

If you haven't noticed by now, we just mentioned the `.gitconfig-personal` and  `.gitconfig-work` files in the global 
`.gitconfig` file, but we didn't create them yet. These individual files can contain all the customization that you 
need, from username and email to commit hooks.

`~/.gitconfig-work` will contain:

```
[user]
 name = work_user
 email = work_email
```

`~/.gitconfig-personal` will contain:

```
[user]
 name = personal_user
 email = personal_email
```

We can configure git to use a custom SSH command like above by setting `core.sshCommand` with corresponding public 
key `personal_user_key` connected with the git account. 

```
[user]
 name = personal_user
 email = personal_email
[core]
 sshCommand = "ssh -i ~/.ssh/personal_user_key"
```

Now all repo in `~/personal/` will be associated with `.gitconfig-personal` git account and repos in `~/work/` will 
be associated with `.gitconfig-work` git account.

### Add ssh key to Apple keychain

Make sure your ssh-key has passphrase when you create it because it is required for keychain. If you don't 
have, you still can modify your no-passphrase-privatekey to have one by runnint this command: 
```shell
ssh-keygen -p -f ~/.ssh/<.your-privatekey-filename.>
```

Add your ssh private key to keychain by run this command: 
```shell
ssh-add --apple-use-keychain ~/.ssh/<.your-privatekey-filename.>
```

Add all your SSH related private keys in keychain to your ssh-agent by running this command: 
```shell
ssh-add --apple-load-keychain
```

Verify by running `ssh-add -l`. You should see a list of results if everything works well. You would notice, 
after you reboot your computer you lost your ssh identity (`ssh-add-l result no identity found`).

You can fix it by adding `ssh-add --apple-load-keychain` to your terminal profile `.zprofile`.

Source: [github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent), [stackexchange](https://unix.stackexchange.com/a/560404)

