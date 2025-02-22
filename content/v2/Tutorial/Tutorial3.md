---
title: 3. 노드 조회
description: Tutorial 3 - View Node
# version: v1.00
menu:
  v2:
    parent: v2-tutorial
---

---


<b>노드(Node)</b>는 자동화 작업의 대상이 되는 호스트(Host)입니다.\
에이전트를 호스트에 설치하면, 해당 호스트가 마스터 서버에 노드로 등록됩니다.

그러면 사용 가능한 노드가 어떤 것들이 있는지 확인해 보겠습니다.\
<span>우선 <inline style="color:#ff4500">opmate node list</inline>로 전체 노드 목록을 조회합니다.</span>

```bash
$ opmate node list

> Requesting https://127.0.0.1:8443/opmate;user=gildong

+--------------------------------------+-----------------+---------------+------------+-----------+-------------------------+
| NODE-SESSION-ID                      | HOSTNAME        | REMOTE-ADDR   | OS-TYPE    | AGENT-VER | HEARTBEAT               |
+--------------------------------------+-----------------+---------------+------------+-----------+-------------------------+
| 01d5020e-dc5f-4744-ad9c-22f23727db76 | DB-DEV-LINUX    | 172.31.3.147  | Linux      | 2.0.020   | 2024-03-20 11:05:59 KST |
| 98a318fd-f51e-4222-a3c0-2f58e55b5822 | DB-DEV-WIN      | 172.31.9.20   | Windows_NT | 2.0.020   | 2024-03-20 11:05:39 KST |
| e8167cfe-a696-4733-b5a0-8de5823f5a95 | DB-PROD-LINUX   | 172.31.8.148  | Linux      | 2.0.020   | 2024-03-20 11:05:22 KST |
| 9510d4b6-4269-4b00-a2be-cb408c6e668d | APP-DEV-LINUX   | 172.31.8.75   | Linux      | 2.0.020   | 2024-03-20 11:05:51 KST |
+--------------------------------------+-----------------+---------------+------------+-----------+-------------------------+

> ROWS COUNT : 4/4

```

<span><u>OS-TYPE</u>을 기준으로 윈도우 노드가 1개, 리눅스 노드가 3개 - 총 4개의 노드가 조회됩니다.<br></span>

<span>이 중 <u>HOSTNAME</u>이 'DB-PROD-LINUX'인 노드를 좀 더 자세히 살펴볼까요?</span>\
<span><inline style="color:#ff4500">opmate node view</inline>로 노드의 상세 정보를 조회할 수 있습니다.</span>

```bash
$ opmate node view -id e8167cfe-a696-4733-b5a0-8de5823f5a95

> Requesting https://127.0.0.1:8443/opmate;user=gildong

+-----------------------+---------------------------------------------------------+
| FIELD                 | VALUE                                                   |
+-----------------------+---------------------------------------------------------+
| NODE-SESSION-ID       | e8167cfe-a696-4733-b5a0-8de5823f5a95                    |
| SESSION-ESTABLISHMENT | 2024-03-18 15:15:51 KST                                 |
| SESSION-STATUS        | normal                                                  |
| AGENT-VERSION         | 2.0.020.Linux.x86_64.20240216.1                         |
| REMOTE-ADDRESS        | 172.31.8.148                                            |
| HEARTBEAT             | 2024-03-20 11:15:22 KST                                 |
| HOSTNAME              | DB-PROD-LINUX                                           |
| OS-TYPE               | Linux                                                   |
| OS-NAME               | Red Hat Enterprise Linux 9.3 (Plow)                     |
| OS-VERSION            | 5.14.0-362.18.1.el9_3.x86_64                            |
+-----------------------+---------------------------------------------------------+
| CSP-RESOURCE-ID       | i-099ab766133afbf23                                     |
| CSP-TAG               | CT.Environment=Production                               |
|                       | CT.Name=DB-PROD-RHEL                                    |
|                       | CT.ResourceType=AWS                                     |
+-----------------------+---------------------------------------------------------
| EXT-TAG               |                                                         |
+-----------------------+---------------------------------------------------------+


```

<span>노드 목록에서 조회할 수 없었던 노드의 추가 정보(OS명, 세션 정보 등)를 확인할 수 있습니다.</span>

<span>또한 호스트가 클라우드에 있다면, CSP가 제공하는 메타데이터인 <u>Resource ID</u>와 <u>Tag</u>를 조회할 수 있습니다.</span>

<span>이러한 데이터를 기반으로 어떤 노드가 자동화 작업의 대상이 되는지 지정할 수 있습니다.</span>

<br>
