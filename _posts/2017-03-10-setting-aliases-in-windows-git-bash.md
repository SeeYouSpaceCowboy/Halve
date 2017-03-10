---
layout: post
title: "Setting Aliases In Windows Git Bash Profile"
categories:
  - Windows
  - Git Bash
tags:
  - Windows
  - Git Bash
---

# Setting Aliases In Windows Git Bash Profile

If you have a Windows computer and use a Git Bash to company you while you code,
there are some shortcuts you need to know about.

To set up your profile, you have to first go to your home directory with `cd`
then creating a file in that directory called `.bashrc`
.
```
 $ cd
 $ touch .bashrc
```
You can now edit it using vim

```
$ vim .bashrc
```

or just open it in your folder and then open it in your favorite editor if you
don't have a editor shortcut set up with your git bash.

```
$ start .bashrc
```

Now once it's open on your favorite editor, you can set aliases

```
alias workspace="cd ~/your-directory-path"
```

Now save this by typing

```
$ source .bashrc
```

for example I have a `Workspace` for where I write all my code and I have an alias
`$ workspace` which will immediately cd me into that directory.

```
alias workspace="cd ~/Documents/Workspace/"
```

And there you go. Hope you now have alias in your Windows Git Bash profile.
