# 📡 nebula-proxy

The ultimate guide to establishing a VPN tunnel with Nebula Overlay Network

[![license: MIT](https://img.shields.io/badge/License-MIT-red.svg)](https://opensource.org/licenses/MIT)
[![lines](https://img.shields.io/tokei/lines/github/yqlbu/nebula-proxy)](https://img.shields.io/tokei/lines/github/yqlbu/nebula-proxy)
[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fyqlbu%2Fnebula-proxy&count_bg=%2329C4A5&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)
![](<https://img.shields.io/static/v1?label=architecture&message=x86,arm64&color=orange>)
![](https://img.shields.io/static/v1?label=software&message=Nebula&color=violet)
[![Last Commit](https://img.shields.io/github/last-commit/yqlbu/nebula-proxy)](https://img.shields.io/github/last-commit/yqlbu/nebula-proxy)

*** Copy Right 2020 Kevin Yu. All rights reserved.

*** Author: Kevin Yu

*** Update Time: 2021/05/12

This repo aims to give you clear instructions on how to install, config, and use Nebular in your local network. The Wiki below will guide you how to deploy Nebular Overlay Network on the Cloud.

## Introduction

## Diagram

## Auto-start

1. Login into the server with root access and copy the binary to `/usr/bin`

```
$ sudo -i
$ cp nebula /usr/bin/nebula
$ cp nebula-cert /usr/bin/nebula-cert
```

2. Create the following systemd unit file for the required service & change permissions per below:

```
$ touch /lib/systemd/system/nebula.service
$ chmod 0664 /lib/systemd/system/nebula.service
```
3. Add the following content into the `systemd` unit file to define the service

```
[Unit]
Description=nebula
Wants=basic.target
After=basic.target network.target
Before=sshd.service

[Service]
SyslogIdentifier=nebula
ExecReload=/bin/kill -HUP $MAINPID
ExecStart=/usr/bin/nebula -config /etc/nebula/config.yml
Restart=always

[Install]
WantedBy=multi-user.target
```

4. Enable `nebula.service` to run at background when the machine boots up

```bash
$ systemctl start nebula
$ systemctl enable nebula
$ systemctl status nebula
```

## Docs

## Supported Platforms

## References

- [Official Nebula Repo](https://github.com/slackhq/nebula)
