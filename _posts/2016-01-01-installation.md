---
title: Installation
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: installation
---

## Manual

Select a location where ERS will be installed and then change directory to that folder. Install ERS through the following command:

    npm install http://tarballs.evostream.com/ers/ers-<version>.tgz

For example:

    npm install http://tarballs.evostream.com/ers/ers-1.0.0.tgz

## Automatic

For Linux/Unix platforms, an easy to use script is provided to install Node.JS, PM2 and ERS automatically, and then start ERS using the PM2 node.js application manager.

This script can be download from

    http://tarballs.evostream.com/ers/ers-<version>-<OS>-<arch>.sh

For example:

    http://tarballs.evostream.com/ers/ers-1.0.0-linux-x64.sh

Once downloaded, select the target installation directory, change to that folder, and run the script:

    sudo ./ers-<version>-<OS>-<arch>.sh

