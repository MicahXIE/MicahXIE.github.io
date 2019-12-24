---
layout:     post
title:      Setup Local GitLab Server
subtitle:   DevOps
date:       2019-12-24
author:     Micah
header-img: img/little_snow.jpg
catalog: true
tags:
    - code management
---

## Background

Recently I need to help to setup local gitlab server, this blog will introduce the flow and issues.


## System Environment
* Distributor ID:   Ubuntu
* Description:      Ubuntu 16.04.6 LTS
* Release:    16.04
* Codename:   xenial
* x86_x64


## Steps

### Install The Dependency Packages
* sudo apt-get install curl openssh-server ca-certificates postfix
* choose `Internet` option without `Smarthost`
* set your email domain name (e.g test@example.org) to example.org 


### Add GPG Pulic Key, update source list and install
* curl https://packages.gitlab.com/gpg.key 2> /dev/null | sudo apt-key add - &>/dev/null
* update source list, (use root not sudo) vi `/etc/apt/sources.list.d/gitlab-ce.list`
* add `deb https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/ubuntu xenial main` to `/etc/apt/sources.list.d/gitlab-ce.list`
* sudo apt-get update
* sudo apt-get install gitlab-ce


### Configuration
* sudo gitlab-ctl reconfigure


### Start services and open port
* service sshd start
* service postfix start
* sudo iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT (default open 80 port)


### Verify gitlab status
* sudo gitlab-ctl status

```
run: gitlab-workhorse: (pid 1148) 884s; run: log: (pid 1132) 884s
run: logrotate: (pid 1150) 884s; run: log: (pid 1131) 884s
run: nginx: (pid 1144) 884s; run: log: (pid 1129) 884s
run: postgresql: (pid 1147) 884s; run: log: (pid 1130) 884s
run: redis: (pid 1146) 884s; run: log: (pid 1133) 884s
run: sidekiq: (pid 1145) 884s; run: log: (pid 1128) 884s
run: unicorn: (pid 1149) 885s; run: log: (pid 1134) 885s
```

### Login the website
* then you can use `http://127.0.0.1` or `http://192.168.x.x` to register and login
* result as below: 


![gitlab login page](https://github.com/MicahXIE/MicahXIE.github.io/tree/master/img/gitlab_login.png)