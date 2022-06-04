#  top, ps, job, kill 명령어 / 매크로 사용법

###### 컴퓨터공학과 20223203 김형민 - 오픈소스SW개론
---
## **1) top**

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
[top](https://www.wikidocs.net/36783)
---
## **2) ps (process status)**
---
ps와 top의 차이점
###### - ps와 달리 top은 지속적인 모니터링이 가능함 (작업관리자와 유사함)
---
사용법 : ps
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

[ps](https://wikidocs.net/36674)
---
## **3) job**
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
|Done|정상 종료|
---
### 사용예제
###### [] 표시는 순서, - 는 이전 프로세스, + 는 현제 프로세스
```c
# 실행중인 프로세스를 표시 
$ jobs 
[1]   Stopped                 watch date
[2]   Stopped                 watch date
[3]   Stopped                 watch date
[4]-  Stopped                 watch date
[5]+  Stopped                 watch date

# 실행 중인 프로세스의 PID 확인 
$ jobs -l
[1]  18129 Stopped                 watch date
[2]  18188 Stopped                 watch date
[3]  19726 Stopped                 watch date
[4]- 19741 Stopped                 watch date
[5]+ 19751 Stopped                 watch date
```
[job](https://wikidocs.net/44362)
---
## **4) kill**
---
+ 프로세스를 종료함
+ 프로세스에 시그널 전송함
+ 아래 표의 9 옵션 이용시 프로세스 강제 종료
---
|시그널|번호|설명|
|:---:|:---:|---|
|HUP|1|프로세스에 재기동을 통지함|
|INT|2|프로세스에 인터럽트를 통지함|
|QUIT|3|프로세스에 종료를 통지함|
|KILL|9|프로세스에 강제종료를 통지함|
|TERM|15|프로세스에 종료를 통지함|
|STOP|17|프로세스에 중단을 통지함|
|CONT|19|프로세스에 재개를 통지함|
---
### 사용예제
---
```c
# 잡아이디를 이용한 종료 
$ jobs
[1]+  Stopped                 hive

$ kill -9 %1

# 프로세스 아이디를 이용한 종료 
$ ps
  PID TTY          TIME CMD
15302 pts/0    00:00:00 bash
16357 pts/0    00:00:00 ps

$ kill -9 15302
```
[kill](https://wikidocs.net/47975)
---
## **5) 매크로 사용법**
---
##### - 매크로 기록하는 법
###### 1.vim 중립 모드에서 q와 매크로 이름으로 사용할 알파벳 누르기
###### 2.하단에 recording이 뜨며 매크로 기록
###### 3.중립모드에서 q누르면 기록 끝

##### - 매크로 재생 방법
###### 1.중립 모드에서 @와 기록할 때 사용했던 매크로 이름을 누르면 매크로가 실행
###### (@@를 누르면 가장 최근에 재생했던 매크로 실행)

##### - 매크로를 파일로 저장하는 법
###### ~/.vimc 파일을 열고 아래와 같이 작성
```
let @새로 지을 매크로이름='
```
###### 후에 insert 모드에서 ```Ctrl + R``` ```Ctrl + R b```를 눌러 내용물 저장 후 종료
###### 매크로에 저장된 내용 예시
```
let @w='wyw$a = #(^M    [^[pbg~w$a, "^[pa"],^M#^[pa^M);^[0xx$'
let @e='0yypi#^[@wa^M}^[kkkkk$a^M{^[j4>>k6>>6>>'
let @r='dwdwyypki   case ^[wg~w$a :^[j>>>>$a( c, ind );^Mbreak;^[jdd.....0'
```
[매크로](https://forcecore.tistory.com/1255)
---
<img src="https://user-images.githubusercontent.com/106798142/171936044-6afeb18d-f8b6-4630-8ceb-a87e7d0e6823.jpeg" width="480" height="360">
