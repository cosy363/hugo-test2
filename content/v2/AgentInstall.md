---
title: "에이전트 설치"
description: ""
date: 2023-08-21
menu:
  v2:
    parent: v2-intro
hideNav: true
toc: false

---
---

{{< tabs "AgentInstallation" >}}
{{< tab "Linux" >}} 

### 파일 준비

최신 버전의 설치 파일을 준비합니다.(e.g. opm-agent-2.0.018-linux-20231116.tar.gz)

```bash
$ ls
opm-agent-2.0.018-linux-20231116.tar.gz
```

### root 로 로그인

```bash
$ su -
```

### 압축 해제 및 인스톨러 실행

```bash
$ gunzip opm-agent-2.0.018-linux-20231116.tar.gz
$ tar -xvf opm-agent-2.0.018-linux-20231116.tar
$ cd opm-agent-2.0.018-linux-20231116
$ ./install.sh
```

### 입력

설치할 경로 등을 입력하고, 출력되는 내용을 확인 후 설치를 진행합니다.
아래 입력값은 예시입니다. 자신의 마스터 정보를 확인하고 올바른 IP와 PORT를 입력하시기 바랍니다.

```bash
Input installation directory (enter for /infsw/opmnsa) :
Input IP address of OPMATE MASTER : 10.0.0.1
Input PORT number of OPMATE MASTER (enter for 34813) :
...
Input 'yes' to proceed installation : yes
```

### 점검

구동 후 로그 파일 (e.g. `/infsw/opmnsa/log/opm-agent.log`) 을 확인하여 에러없이 정상적으로 시작되었는지 확인합니다.

  ```bash
  $ cat /infsw/opmnsa/log/opm-agent.log
  2021-11-19 16:12:42 INFO - Agent Starting...
  2021-11-19 16:12:42 INFO - Successfully registered to the master
  2021-11-19 16:12:42 INFO - Agent Started
  ```


{{< /tab >}}
{{< tab "Windows">}} 

### 파일 준비
최신 버전의 설치 파일(e.g. opm-agent-2.0.018-windows-20231116.exe)을 준비하여 `C:\` 에 복사합니다.

### 명령 프롬프트 실행

실행 메뉴에서 `cmd` 를 입력하여 명령프롬프트를 관리자 권한으로 실행한 후, 설치파일이 존재하는 디렉토리로 이동합니다.

```powershell
C:\Users\Administrator> cd /d C:\
C:\> dir *.exe
opm-agent-2.0.018-windows-20231116.exe
```

### 압축 해제 및 인스톨러 실행

```powershell
C:\> opm-agent-2.0.018-windows-20231116.exe
C:\> cd opm-agent-2.0.018-windows-20231116
C:\opm-agent-2.0.018-windows-20231116> install.bat
```

### 입력

설치할 경로 등을 입력하고, 출력되는 내용을 확인 후 설치를 진행합니다.

아래 입력값은 예시입니다. 자신의 마스터 정보를 확인하고 올바른 IP와 PORT를 입력하시기 바랍니다.

```powershell
Input installation directory (enter for C:\infsw\opmnsa) :
Input IP address of OPMATE MASTER : 10.0.0.1
Input PORT number of OPMATE MASTER (enter for 34813) : 
...
Input 'yes' to proceed installation : yes
```

### 점검

구동 후 로그 파일 (e.g. `C:\infsw\opmnsa\log\opm-agent.log`) 을 확인하여 에러없이 정상적으로 시작되었는지 확인합니다.

```powershell
C:\> type C:\infsw\opmnsa\log\opm-agent.log
2021-11-19 15:45:37 INFO - Agent Starting...
2021-11-19 15:45:37 INFO - Successfully registered to the master
2021-11-19 15:45:37 INFO - Agent Started
```
{{< /tab >}}
{{< /tabs >}}