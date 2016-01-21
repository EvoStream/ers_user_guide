---
title: EvoStream Rendezvous Server (ERS)
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: evostream_rendezvous_server
---

## What is ERS?

EvoStream Rendezvous Server (ERS) allows EMS and client browser to be able to meet and communicate with each other without knowing each other’s IP addresses. It acts as the signaling server needed to establish connection between these endpoints.

------



## Key Features

- Acts as signaling server
- Capable of serving static html pages
- Protect streams through tokens

------



## Pre-requisites

### A. STUN Server

STUN is a set of methods and network protocols to allow an end host to discover its public IP address even if it's located behind a NAT. This server is used by ERS to allow both EMS and the client end-point (browser) to discover their respective IP addresses. Restund is the recommended open-source STUN/TURN server to be used with ERS.

The default configuration of ERS already points to a public EvoStream STUN server. However, hosting your own STUN/TURN server is also possible as described below.

To install and host restund on Linux, execute the following instructions:

1. Make sure that build-essential and unzip packages are already installed. On a debian-based Linux, these can be done through the following:
   
        apt-get install build-essential
        apt-get install unzip

2. Download and install the toolkit library to be used by restund:
   
        wget http://www.creytiv.com/pub/re-0.4.12.tar.gz
        tar -xzf re-0.4.12.tar.gz
        cd re-0.4.12/
        make
        sudo make install

3. Download and install restund itself:
   
        wget https://github.com/otalk/restund/archive/master.zip
        unzip master.zip
        cd restund-master
        make
        sudo make install
        sudo ldconfig

4. Configure restund (following is a basic sample config file):
   
        #
        # restund.conf
        #
        # core
        #
        daemon no
        debug yes
        realm TestRealmThatCanBeChanged
        syncinterval 600
        udp_listen <ip>:<port>
        udp_sockbuf_size 524288
        tcp_listen <ip>:<port>
        #
        # modules (STUN messages are processed in module loading order)
        #
        module_path /usr/local/lib/restund/modules
        module stat.so
        module binding.so
        module syslog.so
        module status.so
        #
        # syslog
        #
        syslog_facility 24

5. Copy the updated configuration file:
   
        sudo cp restund.conf /etc/

6. Run restund:

        sudo restund /etc/restund.conf # add -d option for daemon

### B. Node.JS

Node.js is a server side JavaScript runtime utilized to run ERS.

For Linux/Unix variants, a helper script is available to automate the installation process. See Automatic section.

For windows platforms and/or manual installation:

Download and install or extract node.js from their website: [*https://nodejs.org/en/download/*](https://nodejs.org/en/download/)

If extracted, add the Node.JS location to the environment path so that the corresponding binaries can be found even if packages are installed on different folder location.

### C. NPM

The Node Package Manager allows easy installation of a Node.JS package and its dependencies. NPM will be used to install ERS. NPM is already part of the Node.JS application.

### D. PM2

Although not necessarily a prerequisite, a Node.JS application/process manager can be installed, as well. This will manage the ERS process and restart it in case of failures and/or machine restart if configured. Currently PM2 is the recommended package for this task.

This package is already automatically installed through the Linux/Unix helper script as described on Automatic section.

To manually install pm2 package:

    npm install -g pm2

