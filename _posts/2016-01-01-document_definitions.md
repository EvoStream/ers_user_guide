---
title: Document Definitions
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: document_definitions
---

| **TERM** | **DEFINITION**                           |
| :------: | ---------------------------------------- |
|   EMS    | EvoStream Media Server                   |
|   JSON   | JavaScript Object Notation               |
|   NAT    | Network Address Translators              |
|   Room   | A logical place where a single EMS joins and waits for incoming clients (web browsers) to connect/join. If there are 10 IP cameras that has a running EMS on each of those cameras, 10 unique rooms will be created by these EMS as they connect to ERS. If an EMS attempts to connect to a room already joined by another EMS instance, the last EMS will not be allowed to join this room.  Rooms can be limited by having entries on *allowedrooms* field of the configuration file (config/default.json) upon ERS start-up. Or they can be added upon run-time through the ***addRoom*** admin command. |
|   STUN   | Session Traversal Utilities for NAT      |
|  Token   | A valid identifier passed by a connecting client (browser) to ERS to indicate that it has the appropriate permission to access the streams available on EMS of a specified room. This token will be available within 10 minutes after it is used by a client and will be removed once the 10 minute mark has expired. Once used, other clients using the same token will not be able to join a room. This prevents unwanted access to the available streams of a running EMS instance. Tokens can be added using the ***addToken*** admin command. |
|   TURN   | Traversal Using Relays around NAT        |
|  webRTC  | Web Real-Time Communication              |
