---
title: "Colopl's FESTIBATTLE Infrastructure Architecture: Dedicated Game Servers with Agones on Kubernetes"
date: 2026-07-28

org_name: Colopl Inc.
org_team: 
org_url: https://colopl.co.jp/
org_logo_filename: images/logo.png
contact: 
email: 
org_description: 
org_size: 
user_size:
tags:
- agones
- gaming
- kubernetes

industries:
- gaming

categories:
  host-platform: [ "gke" ]

reference_architectures:
- gaming


---


## Relevant CNCF projects

{{< cardpane >}}
  {{< card header="Kubernetes" >}}
  [![kubernetes logo](https://raw.githubusercontent.com/cncf/artwork/main/projects/kubernetes/icon/color/kubernetes-icon-color.svg)](https://www.cncf.io/projects/kubernetes/)

  Kubernetes serves as the substrate for our platform.
  {{< /card >}}

  {{< card header="Agones" >}}
  [![Agones logo](images/agones.png)](https://www.cncf.io/projects/agones/) 

  Agones enables efficient scaling and management of our game servers on top of K8s.
  {{< /card >}}
{{< /cardpane >}}


## Architecture highlights


![](images/festibattle-architecture.png)

At COLOPL, our API servers run on Google Kubernetes Engine (GKE) with Cloud Spanner as the backend database. While that combination is somewhat distinctive, the overall structure is not far from a typical web service.


What makes this a game architecture is the orchestration of dedicated game servers with [Agones].
When allocating a dedicated game server through Agones, we place an in-house component called the Allocator Service in front of the allocation flow.
It decides which game server each request should be assigned to.
Reducing the maintenance cost of this in-house Allocator Service, and ultimately eliminating it, is one of our ongoing challenges.
We develop and operate multiple game titles concurrently, so custom components like this weigh on every title.


One of the reasons we built our own Allocator Service is that Agones originally had no way to re-allocate a dedicated game server that had already been allocated.
Many of COLOPL's titles are MO (multiplayer online) games where a small group of players plays together.
Our dedicated game servers implement a concept we call rooms: matched players are packed into the same room, which enables communication between them.


A single dedicated game server can host multiple rooms, so one process can handle the traffic of many player groups at once.
This lets us use server resources very efficiently.
The catch is that realizing the room concept requires re-allocating game servers that have already been allocated.


For [FESTIBATTLE], we implemented this re-allocation mechanism by adopting the [High Density GameServer pattern].
This brings our allocation flow much closer to the standard Agones Allocator Service and makes future migration easier.


## Current challenges and what's next


Agones now provides the [Counters and Lists] feature in Beta, which enables dedicated game server orchestration that fits our use case even better.
With Counters and Lists, user-defined values (something like a room ID, for example) can be stored on the GameServer resource and then used for allocation decisions or as autoscaling thresholds.


Going forward, we will explore using this feature to migrate from our in-house Allocator Service to the standard Agones one.


_NOTE: This article is an English translation adpation of [our original article] published in Japanese on Findy Tools._


[Agones]: https://agones.dev/site/
[FESTIBATTLE]: https://festibattle.jp/
[High Density GameServer pattern]: https://agones.dev/site/docs/integration-patterns/high-density-gameservers/
[Counters and Lists]: https://agones.dev/site/docs/guides/counters-and-lists/
[our original article]: https://findy-tools.io/companies/colopl/180/48
