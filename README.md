# 리눅스 명령어 조사

## top 명령어
top 명령어는 리눅스 시스템에서 현재 실행 중인 프로세스들의 정보를 실시간으로 보여주는 도구<br>
시스템의 가장 많은 CPU를 사용하는 프로세스부터 순서대로 보여주며, CPU 사용량, 메모리 사용량, 실행 시간 등 다양한 정보를 제공

### top 명령어 실행 시 표시되는 정보
- **PID**: 프로세스 ID. 각 프로세스를 구별하는 고유한 번호
- **USER**: 프로세스를 실행하는 사용자의 이름
- **PR**: 프로세스의 우선순위
- **NI**: nice 값으로, 프로세스의 우선순위를 조절하는 데 사용
- **VIRT**: 가상 메모리의 총량
- **RES**: RAM에 실제로 사용되고 있는 메모리의 양
- **SHR**: 다른 프로세스와 공유되는 메모리의 양
- **S**: 프로세스의 상태. 예를 들어, S(sleeping), R(running) 등이 있음
- **%CPU**: 프로세스가 사용하는 CPU의 비율
- **%MEM**: 프로세스가 사용하는 메모리의 비율
- **TIME+**: 프로세스가 시작된 후 총 CPU 시간
- **COMMAND**: 프로세스를 시작한 명령어


### top 명령어의 주요 옵션
- **n** : 업데이트 횟수를 지정. 예를 들어, top -n 1은 정보를 한 번만 표시하고 종료
- **d** : 화면을 갱신하는 시간 간격을 지정. 예를 들어, top -d 5는 5초마다 화면을 갱신
- **p** : 특정 PID의 프로세스 정보만을 모니터링하고 싶을 때 사용. 예를 들어, top -p 1234는 PID가 1234인 프로세스의 정보만을 표시


## ps 명령어
ps 명령어(Process Status)는 현재 실행 중인 프로세스의 스냅샷을 보여줌.<br>
사용자는 이 명령어를 통해 프로세스 ID(PID), 실행 중인 시간, 사용 중인 메모리 등의 정보를 확인할 수 있음.<br> 
ps 명령어는 다양한 옵션과 함께 사용되어 보다 상세한 정보를 제공받을 수 있음

### 기본 사용법
```ruby
ps [options]
```

### ps 명령어의 주요 옵션 
- **e** : 시스템상의 모든 프로세스를 보여줌
- **f** : Full format으로 보다 상세한 정보를 보여줌
- **u [사용자명]** : 지정된 사용자의 프로세스를 보여줌
- **p [PID]**: 특정 PID(Process ID)를 가진 프로세스의 정보를 보여줌
- **aux**: 사용자별, 메모리 사용량, CPU 사용량 등을 포함한 모든 프로세스의 정보를 상세히 보여줌<br>
  a는 다른 사용자의 프로세스도 보여주며, u는 사용자 친화적 형식으로 보여주고, x는 터미널이 없는 프로세스도 포함


## jobs 명령어
jobs 명령어는 현재 쉘 세션에서 실행 중이거나 중지된 작업의 목록을 보여준다<br> 
이 명령어는 사용자가 백그라운드로 실행시킨 프로세스들의 상태를 확인할 때 유용하게 사용<br> 
일반적으로, 리눅스나 유닉스 기반 시스템에서 백그라운드 프로세스를 관리할 때 jobs, bg, fg 명령어를 함께 사용함<br>

### 기본 사용법
```ruby
jobs [옵션] [작업번호...]
```

### ps 명령어의 주요 옵션 
- **l** : 프로세스 그룹 ID(PGID)를 포함하여 작업을 나열
- **n** : 프로세스 그룹 중 대표 프로세스의 상태가 마지막으로 보고된 이후에 변경된 작업만을 나열
- **p** : 각 작업에 대해 대표 프로세스의 ID만을 나열
- **r** : 현재 실행 중인 작업만을 나열
- **s** : 현재 중지된 작업만을 나열


### 출력되는 작업 상태
- **Running** : 작업이 현재 실행 중임을 나타냄
- **Stopped** : 작업이 중지되었음을 나타냄 일반적으로 Ctrl+Z를 통해 작업을 중지시킬 수 있음
- **Done**: 작업이 완료되었음을 나타냄


##  kill 명령어
kill 명령어는 특정 프로세스에 시그널(signal)을 보내어 그 프로세스를 종료시키는 명령어다. <br>
주로 프로세스 ID(PID)를 사용하여 특정 프로세스를 종료시키지만, 작업 번호를 사용하여 jobs 명령어로 확인된 작업을 종료시킬 수도 있음. <br> 
kill 명령어는 다양한 종류의 시그널을 지원하며, 그 중 SIGKILL (9) 시그널은 프로세스를 바로 종료시키는 데 사용됨 

### 기본 사용법
```ruby
kill [옵션] <PID>
```

### kill 명령어의 주요 시그널
- **SIGTERM (15)** : 기본 시그널로 프로세스에게 종료할 것을 요청. 
- **SIGKILL (9)** : 프로세스 즉시 종료. 프로세스가 반응하지 않을 때 사용.
- **SIGSTOP (19)** : 프로세스 일시 중지.

### 옵션
- **l** : 사용 가능한 모든 시그널의 목록을 보여줌.
- **s <시그널> 또는 -<시그널>** : 특정 시그널을 보냄. 시그널은 이름이나 숫자로 지정할 수 있음.
