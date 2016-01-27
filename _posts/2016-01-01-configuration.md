---
title: Configuration
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: configuration
---

## Default

A default configuration file, `default.json` is included in the `config` folder where ERS was installed (e.g. `INSTALL_DIRECTORY/node_modules/ers/config/default.json`). This file can be modified to customize the settings of ERS.

Following is the content of the `default.json` config file:

    {
      "server": {
        "port": 3535,
        "secure": false,
        "key": null,
        "cert": null,
        "password": null,
        "tokensEnabled": false,
        "webServerEnabled": true,
        "adminAccessEnabled": true,
        "adminIP": "127.0.0.1",
        "adminPort": 3030
      },
      "allowedrooms": [
      ],
      "stunservers": [
        {
        "url": "stun:162.209.96.37:55555"
        }
      ],
      "turnservers": [
      ]
    }



## Field Description

|      **Name**      | **Default Value** | **Description**                          |
| :----------------: | :---------------: | ---------------------------------------- |
|       server       |                   | Top level field containing all server related settings |
|        port        |       3535        | Port number where ERS will listen to     |
|       secure       |       false       | Indicates if ERS will use HTTPS instead of regular HTTP |
|        key         |       null        | Private Key file to be used for HTTPS    |
|        cert        |       null        | Certificate file to be used for HTTPS    |
|      password      |       null        | Password of the certificate file         |
|   tokensEnabled    |       false       | Indicates if tokens (a security mechanism) is enabled. This limits viewers who can access available streams of EMS |
|  webServerEnabled  |       true        | Indicates if a web server will be instantiated that enables ERS to serve static files such as html pages containing the video player |
| adminAccessEnabled |       true        | Indicates if admin access used to manage ERS is enabled |
|      adminIP       |     127.0.0.1     | Allowed IP address that can connect to ERS as an admin. This needs to be adjusted to match the actual IP address of the machine used to access the admin APIs of ERS |
|     adminPort      |       3030        | Port number where ERS admin access listens to |
|    allowedrooms    |                   | List of room names as strings that will only allowed to be created by ERS. Leave this empty to allow any rooms to be created. Or create one room for each running ems instance so that only intended rooms get created which also serves as an additional layer of security |
|    stunservers     |                   | List of STUN servers that ERS can use    |
|    turnservers     |                   | List of TURN servers that ERS can use    |

