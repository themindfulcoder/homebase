---
title: "Github Using Ssh on Linux"
date: 2018-01-29T22:46:50+02:00
draft: true
---

logon to github.com

go to profile, select settings
on the pane on the left select ssh and gpg keys
run from terminal to create a ssh key on your machine
``` bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

run from terminal to start ssh agent
``` bash
eval "$(ssh-agent -s)"
```
run from terminal to add your ssh key to the ssh agent
``` bash
ssh-add ~/.ssh/id_rsa
```

install xclip to copy the rsa key to a clipboard manager called xclip
``` bash
sudo apt install xclip
```
copy your rsa key into xclip
``` bash
xclip -sel clip < ~/.ssh/id_rsa.pub
```

click new ssh
give it a friendly name (laptop)
ctrl+v to paste key
click add ssh key
type in password if required