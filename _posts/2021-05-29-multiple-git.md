---
layout: post
title: Multiple Git configs on linux system
categories: General
ready : true
---

If you have multiple git accounts and would like to config them in your linux machine, this post is for you. `.gitconfig` 
file is starter point for Git to identify what configurations need to be used. 

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

