---
title: 2. 계정 생성 및 로그인
description: 계정 생성 및 로그인
weight: 2
menu:
  v11:
    parent: v11-tutorial
---

다음과 같이 나의 사용자 계정을 만듭니다. 사용자ID는 bumbee이고, 이름, 전화번호, 이메일 등을 입력합니다.

```bash
$ opmate user create -id bumbee -nm 'cutefly' -pn '010-2222-2222' -ea 'bumbee@email.com'
Requesting https://127.0.0.1:8443/opmate
Enter password: 
Confirm password: 
bumbee has been created successfully.
```

정상적으로 생성이 되었지만, 아직은 사용이 불가능합니다.
시스템관리자 권한을 가지고 있는 사용자에게 활성화를 요청합니다.


시스템관리자(admin)는 당신의 요청을 듣고, 다음과 같이 사용자 목록을 조회해 봅니다.

```bash
$ opmate user list
Requesting https://127.0.0.1:8443/opmate;user=admin
+--------+---------------+------+---------+------------------+
| ID     | NAME          | ROLE | STATUS  | LAST LOGIN       |
+--------+---------------+------+---------+------------------+
| admin  | lovelyhana    | 0    | enable  | 2020/03/13 14:07 |
| oprim  | smartsteel    | 1    | enable  | 2020/03/13 09:35 |
| bumbee | cutefly       | 3    | disable | 2020/03/11 15:12 |
+--------+---------------+------+---------+------------------+

ROWS COUNT : 3/3
```

bumbee라는 사용자가 추가된 것을 확인하고, 다음과 같은 명령으로 활성화 및 ROLE 2를 부여합니다.
ROLE은 권한 레벨을 의미하며, 최소 2레벨이 되어야 각종 작업을 수행할 수 있습니다.

```bash
$ opmate user edit -id bumbee -ro 2 -st E
Requesting https://127.0.0.1:8443/opmate;user=admin
bumbee has been modified successfully.
```

자, 이제 bumbee로 로그인해볼까요?

```bash
$ opmate user login -id bumbee
Requesting https://127.0.0.1:8443/opmate
Enter password: 
bumbee has been logged in successfully.
```
