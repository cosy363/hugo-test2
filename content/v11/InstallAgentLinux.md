---
title: 에이전트 설치 (Linux, UNIX)
menu:
  v11:
    parent: v11-about
weight: 2
hideNav: true

---
---
## 파일 준비

최신 버전의 설치 파일을 준비합니다.(e.g. opma-inst-1.1.005-20230327.tar.gz)

```bash
$ ls
opma-inst-1.1.005-20230327.tar.gz
```

## root 로 로그인

```bash
$ su -
```

## 압축 해제 및 인스톨러 실행

```bash
$ gunzip opma-inst-1.1.005-20230327.tar.gz
$ tar -xvf opma-inst-1.1.005-20230327.tar
$ cd opma-inst-1.1.005-20230327
$ ./install.sh
```

## 입력

설치할 경로를 입력하고, 출력되는 내용을 확인 후 설치를 진행합니다.

```bash
Input installation directory (ex. /infsw/opma) : /infsw/opma
...
Input 'yes' to proceed installation : yes
```

## 설정 파일 수정

설치된 디렉토리의 설정 파일(e.g. /infsw/opma/cfg/agent.conf)을 열고,

다음 예와 같이 올바른 마스터서버의 접속 정보로 수정합니다.

```bash
$ vi /infsw/opma/cfg/agent.conf
master_ip = 127.0.0.1
master_port = 34813
```

## 구동

인스톨러의 안내에 따라, OS별로 다음과 같이 입력하여 구동합니다.

구동 후 로그 파일 (e.g. /infsw/opma/log/opm-agent.log) 을 확인하여 에러없이 정상적으로 시작되었는지 확인합니다.

- CentOS 7.x 기준
  ```bash
  $ systemctl start opmagent
  ```

- CentOS 6.x/5.x 기준
  ```bash
  $ service opmagent start
  ```

- AIX/SunOS/HP-UX 기준
  ```bash
  $ /infsw/opma/bin/start.sh
  ```

## 주의사항

에이전트는 각각 고유의 GUID를 가지고 있습니다. 이미 에이전트가 설치되어 있는 VM을 복제하여 생성하거나 또는 설치된 에이전트를 복사하여 설치할 경우 에이전트의 GUID도 복제되어 오동작이 발생하게 됩니다. 복제된 에이전트는 삭제(디렉토리 전체 삭제)하시고 재설치하시기 바랍니다. 삭제하지 않고 재설치할 경우에는 업데이트로 인식하기 때문에 GUID를 새로 받을수 없습니다.
