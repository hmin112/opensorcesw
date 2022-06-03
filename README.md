# top, ps, job, kill 명령어
###### 컴퓨터공학과 20223203 김형민 - 오픈소스SW개론
---
### **1) top**

+ 시스템의 상태를 전반적으로 가장 빠르게 파악 가능
+ 옶션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여줌
+ q를 눌러 작동 정지 가능
+ 실행 상태에서 다양한 명릉을 입력하여 프로세스 상태를 출력하거나 제어가 가능

### 주요 옵션 
---
|옵션|내용|
|---|---|
|d[second]|지정한 초(second)마다 갱신|
|p[process id]|지정한 프로세스 ID의 정보만 출력|
|c|커맨드를 실행 옵션을 포함해서 출력|

### 사용예제
---
```c 
$ top
top - 01:57:34 up 882 days, 20:54,  2 users,  load average: 0.02, 0.05, 0.05
Tasks:  93 total,   2 running,  90 sleeping,   1 stopped,   0 zombie
Cpu(s):  0.8%us,  0.1%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.1%st
Mem:   3921016k total,  1928212k used,  1992804k free,   159100k buffers
Swap:        0k total,        0k used,        0k free,  1000296k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                                                         
    1 root      20   0 19232  928  644 S  0.0  0.0   0:02.73 init                                                                                                                                                                                                             
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                                                                                                                                         
    3 root      RT   0     0    0    0 S  0.0  0.0   0:47.44 migration/0   

# 10초마다 갱신 
$ top -d 10

# pid 지정하여 1024 프로세스의 정보만 출력 
$ top -p 1024 
```
---
### **2) ps**
---
ps와 top의 차이점
###### - ps와 달리 top은 지속적인 모니터링이 가능함 (작업관리자와 유사함)
---
사용법 : ps
###### (process status)
---
### 주요 옵션
---
|옵션|내용|
|---|---|
|e|옵션은 모든 프로세스에 대한 내용을 보여줌|
|f|옵션은 프로세스에 대한 자세한 정보를 출력함(PPID, UID 확인 가능)|
|u[username|옵션은 특정 사용자에 대한 프로세스의 정보를 출력함|
|USER|프로세스 사용자명|
|UID|사용자ID|
|PID|프로세스ID|
|PPID|부모 프로세스ID|
|RSS|프로세스에 의해 사용되는 실제되는 실제 메모리 용량(Kbyte)|
|VSZ|프로세스에 의해 사용되는 사용되는 가상 메모리 용량(Kbyte)|
|TIME|총 CPU 사용 시간(분,초)|
|TTY|해당 프로세스의 제어 터미널(t3=/dev/tty3)|
|%CPU|마지막 분 동안 프로세스가 사용한 CPU 이용률|
|%MEM|마지막 분 동안 프로세스가 사용한 메모리 이용률|
|START|프로세스 시작 시간|
|COMMAND, CMD|실행된 명령 라인|
|STAT|프로세스의 상태(R: 실행 가능, S: 슬립, D: 디스크 내부, T: 정지, Z: 좀비)|
---
### **3) job**
---
+ 백그라운드로 실행되는 작업목록(작업번호, 상태, 명령어)을 보여주는 리눅스 명령어
+ 작업번호는 PID와는 달리, 별도로 부여되는 백그라운드 작업목록 사의 번호임
+ 현재 쉘 프로세스(bash)의 자식 백그라운드 프로세스들을 보여줌
---
### 주요 옵션
|옵션|내용|
|---|---|
|-l|프로세스 ID를 표시|
|Running|실행 중|
|Stoped|일시 중단(Ctrl + Z)|
|Teminated|강제 종료(kill 명령 종료)|
|Done|정상 종료||
---

### **4) kill**


https://www.wikidocs.net/36783
https://wikidocs.net/36674
https://wikidocs.net/44362
