---
layout: post
title: "Anyone Who Uses Terminal on MacOS, Should Edit Their .bash_profile"
categories:
  - Terminal
  - Mac
tags:
  - Shell
  - Terminal
---
Everyone who uses terminal for anything, should know about `.bash_profile`. If you happen to be someone who didn’t even know a `.bash_profile` existed, you’ve come to the right place. Your `.bash_profile` is a file that basically allows you to customize your terminal.

Your hidden `.bash_profile` is usually found in the default home directory:
```shell
cd ~/.bash_profile
```
I have atom text editor installed, so I can open .bash_profile with:
```shell
$ atom ~/.bash_profile
```
Although I’m not a huge fan, you can edit directly from terminal instead of installing atom with:
```shell
$ nano ~/.bash_profile
```
## Change Terminal Prompt Display

If you’d no longer want to display you username as your terminal prompt and want it to now say “Hacker” instead, add this to your `.bash_profile`:
```
PS1 = "Hacker "
```
Similarly you can even drag and drop an emoji in-between the quotation and your terminal prompt will display it:
```
PS1 = "Hacker 💀 "
```
You can add “\W” or “\w” to your PS1. Where typing uppercase “\w” shows the whole working directory and lowercase “\W” adds only the current working directory to your terminal prompt, if you’d still like those displayed:
```
PS1 = "Hacker 💀 \w"
```
You can save and refresh these changes from terminal with following command:
```shell
$ source ~/.bash_profile
```
## Adding an Alias Shortcut

Adding an alias is awesome. You can use an alias from any place by simply typing the alias and it’ll do the requested command. For example if you had a directory that you use often:
```
~/some_path/folder
```
You can then just add the following to the `.bash_profile`:
```
alias hack="cd ~/some_path/folder"
```
Save and refresh:
```shell
$ source ~/.bash_profile
```
And now every time you type the alias in terminal, you’ll cd into that directory:
```shell
$ hack
```
