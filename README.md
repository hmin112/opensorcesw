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
|-d[second]|지정한 초(second)마다 갱신|
|-p[process id]|지정한 프로세스 ID의 정보만 출력|
|-c|커맨드를 실행 옵션을 포함해서 출력|

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
### **3) job**

### **4) kill**
