
# 🙆‍♂️ import 🙇‍♂️

[Linux ps (프로세스 확인하기)[IT 지식창고 - 창공]](https://m.blog.naver.com/PostView.nhn?blogId=diceworld&logNo=220201131993&proxyReferer=https:%2F%2Fwww.google.com%2F)

[[리눅스, 유닉스] ps 프로세스 명령어 완벽정리, 프로세스 관리, 계열에 따른 옵션 차이, 조건에 맞게 프로세스 정보 추출하기[양햄찌가 만드는 세상]](https://jhnyang.tistory.com/268)

[]()


<br>

# ps

`ps` 는 **프로세스의 상태를 확인하는 명령어**이다.

**현재 특정 프로세스가 실행되고 있는지** 실행되는 **프로세스가 어떤 pid를 갖고 있는지 등**을 

**확인하는데 많이 쓰이며**, 옵션을 통해 **CPU와 메모리 점유율등의 상세 정보도 확인**할 수 있다.

```
ps [옵션]

[gillog@localhost ~]# ps
PID  TTY    TIME   CMD
1380 tty1 00:00:01 bash
1525 tty1 00:00:00 ps
```

|항목|설명|
|:--:|:--:|
| PID|프로세스의 아이디, 식별변호|
|PPID	|부모 프로세스 ID|
|UID	|SYSTEM V계열에서 나타나는 항목으로 프로세스 소유자의 이름|
|TTY|프로세스를 제어하는 수단, 프로세스와 연결된 터미널로 <br> 콘솔접속시 "tty숫자" 행태로 표시되며, <br>원격이나 에뮬레이터 접속시 "pts/숫자" 형태로 표시|
|TIME|프로세스에 사용된 CPU 시간|
|CMD|프로세스 실행 명령어|
|COMMAND|	프로세스의 실행 명령행|
|USER	|BSD계열에서 나타나는 항목으로 프로세스 소유자의 이름|
|%CPU	|CPU 사용 비율의 추정치(BSD)|
|%MEM	|메모리의 사용 비율의 추정치 (BSD)|
|VSZ	|K단위 또는 페이지 단위의 가상메모리 사용량|
|RSS	|실제 메모리 사용량 (Resident Set Size)|
|S, STAT	|현재 프로세스의 상태 코드 (S: Sys V, STAT: BSD)|
|STIME	|프로세스가 시작된 시간 혹은 날짜|
|C, CP	|짧은 기간 동안의 CPU 사용률 (C: Sys V, CP: BSD)|
|F	|프로세스의 플래그 |
|PRI	|실제 실행 우선순위|
|NI	|nice 우선순위 번호 |

<br>

## ps -ef

**`ps -ef`는 `ps`명령어에 두가지 옵션 `e`,`f`를 추가한 것**이다.

**`e`는 모든 프로세스를 표시**하는 것이고, **`f`는 프로세스의 정보를 더 많이 보여주도록 하는 옵션**이다.

<br>

일반적으로 **`ps`명령어 사용시 자주 사용하는 옵션 조합**이다.

하지만 **`ps -ef` 만을 사용하면 많은 프로세스가 한번에 표시**되기 때문에 **`grep` 명령어로 원하는 키워드를 가려서 사용**한다.

```
[gillog@localhost ~]# ps -ef

UID   PID PPID C STIME TTY      TIME CMD

root    1    0 0 21:20 ?    00:00:05 /sbin/init

root    2    0 0 21:20 ?    00:00:00 [kthreadd]

                     ㆍ
                     ㆍ
                     ㆍ

root 1380    0 0 21:25 tty1 00:00:01 -bash

root 1594 1380 0 21:38 tty1 00:00:00 ps -ef
```
