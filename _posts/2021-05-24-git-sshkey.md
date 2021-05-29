---
layout: post
title: Setup SSH key for git
categories: General
ready : true
---

You may already know that GitHub will [no longer accept account passwords](https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/) when authenticating Git operations 

> Beginning August 13, 2021, we will no longer accept account passwords when authenticating Git operations and will require the use of token-based authentication, such as a personal access token (for developers) or an OAuth or GitHub App installation token (for integrators) for all authenticated Git operations on GitHub.com. You may also continue using SSH keys where you prefer.

If you are still using password for GitHub authentication, this post will help you setup ssh key for your git account.

### Creating a new SSH key

You should create a SSH key in your local machine. Type the following in terminal to generate a SSH key.

```
cd ~/.ssh 
ssh-keygen -t rsa -C "your_email@example.com"
```

If you want to force rename the ssh key, you should the command below:

```
ssh-keygen -t rsa -C "your_email@example.com" -f "id_rsa_user1"
```

here `id_rsa_user1` will be the name of the key.

Once you entered that command, you will get a few more questions:

```
Enter file in which to save the key (/home/demo/.ssh/id_rsa):
```
You can press enter here, saving the file to the user home (in this case, my example user is called `demo`). 
Then this will be shown: 

```
Enter passphrase (empty for no passphrase):
```

The only downside, of course, to having a passphrase, is then having to type it in each time you use the key pair. 
I suggest you to use a passphrase though, due to security concerns. In the end, the entire process looks like this:

```
Enter file in which to save the key (/home/demo/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/demo/.ssh/id_rsa.
Your public key has been saved in /home/demo/.ssh/id_rsa.pub.
The key fingerprint is:
4a:dd:0a:c6:35:4e:3f:ed:27:38:8c:74:44:4d:93:67 demo@a
The key's randomart image is:
+--[ RSA 2048]----+
|          .oo.   |
|         .  o.E  |
|        + .  o   |
|     . = = .     |
|      = S = .    |
|     o + = +     |
|      . o + o .  |
|           . o   |
|                 |
+-----------------+
```

The public key is now located in `/home/demo/.ssh/id_rsa.pub`. 
The private key (identification) is now located in `/home/demo/.ssh/id_rsa.`

### Deploy your key to Github/Gitlab

Open `id_rsa.pub` file (you can use any text editor you want) at location `~/.ssh/`.
Copy the entire content of that file.

Github: Setting >> SSH and GPG keys >> new SSH keys >> paste key >> Add SSH key <br />
Gitlab: Preference >> SSH keys >> paste key >> Add key <br />

Enter title and copy paste the content of the public key generated at `~/.ssh/` to key field. <br />

### Configure Git

If git is not configured in your local machine, do the following. In your terminal, add your username: 

```git config --global user.name "your_username"```

And your email address: 

```git config --global user.email "your_email_address@example.com"```

Now you can clone your git repo with ssh key.

