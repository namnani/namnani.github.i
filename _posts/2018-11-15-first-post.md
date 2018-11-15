---
title: "Welcome to Jekyll!"
date: 2018-11-15 18:57:28 -0400
categories: jekyll update
---
<h1>
   CPU 스케쥴링에 대해 알아보기 전에...
  </h1>

![process](https://user-images.githubusercontent.com/21725428/48548121-892cdc80-e90f-11e8-8eda-1fab0b849adf.PNG)

![thread](https://user-images.githubusercontent.com/21725428/48548459-56371880-e910-11e8-80a8-79ca1c79db9f.PNG)
<hr>
<hr>


![process thread](https://user-images.githubusercontent.com/21725428/48548651-d6f61480-e910-11e8-9687-a2868a4ae660.PNG)
<br>
<h3>
<b>
이러한 Thread는 어디에 활용되고 있을까?
  </b>
  </h3>
<br>
1. 게임 프로그래밍
<br>
2. 네트워크 프로그래밍
<hr>


다중프로그래밍(Multi-programming)을 위해 CPU 스케쥴링이 중요하다!

![cpu-io burst cycle](https://user-images.githubusercontent.com/21725428/48549513-5684e300-e913-11e8-9b76-d4ef458be3b0.PNG)

<br>
<b>
  CPU burst time?
</b>

=> CPU가 일을 수행하는 시간

<b>
  I/O burst time
</b>

=> I/O 요청에 대한 응답을 기다리는 시간 

<br>
<br>

<b>
  CPU가 유휴 상태(idle state)가 될 때마다 운영체제는 준비 큐에 있는 프로세스들(프로세스 제어 블록 : PCB) 중에서 하나를 선택하여 실행
  </b>
  
  <p align="center">
  여기서 잠깐 PCB(Process Control Block)란?
  <br>=>특정한 프로세스를 관리할 필요가 있는 정보를 포함하는 운영 체제 커널의 자료 구조이다.  
  
  ![pcb](https://user-images.githubusercontent.com/21725428/48549872-5d602580-e914-11e8-8fc3-4f6147f0c22e.PNG)
  </p>


<h1>
   CPU 스케쥴링의 2가지 형태
   </h1>
   <b><li> 선점 스케쥴링(Preemptive Scheduling) : 선점은 한 프로세스가 CPU를 점유하고 있을 때 다른 프로세스가 현재 프로세스를 중지시키고 자신이 CPU를 차지 할 수 있는 방식이다. 우선순위가 높은 프로세스가 먼저 수행 될 때 유리하고, 빠른 응답시간을 요구하는 시분할 시스템에 유용하다. 하지만 선점 때문에 많은 오버헤드를 초래한다.
   
   ![process state_preemptive](https://user-images.githubusercontent.com/21725428/48551273-6a7f1380-e918-11e8-81d9-2a260457fd57.PNG)

   </li>
   <br>
   <li>
      비선점 스케쥴링(Non-preemptive Scheduling) : 한 프로세스가 CPU를 할당받으면 다른 프로세스는 할당 받은 프로세스가 작업을 종료할때 까지 CPU를 사용 불가능한 방식이다. 모든 프로세스의 요구를 공정히 처리할 수 있다. 응답시간이 예측 가능하다. 단 짧은 작업이 긴 작업을 기다리는 경우가 발생 할 수 있다.
   </li>
   
![process scheduling](https://user-images.githubusercontent.com/21725428/48551081-cdbc7600-e917-11e8-86f7-f4beecb15aad.PNG)

▶ 선점 알고리즘의 특징

   - 선점 스케쥴링을 위해 타이머와 같은 특정 하드웨어를 요구할 수 있음

   - 동기화를 위한 비용 증가 : 공유 자료에 대한 접근 조정 필요

    ex) 선점을 한 프로세스가 이전 프로세스가 조작 중이었던 자료에 접근해선 안됨

   - 커널 자료구조의 불일치를 방지하기 위해, 문맥교환을 수행하기 전에 시스템 호출이 완료되거나 I/O 요청이 완료되기를 기다려야 함

   - 그러나 이 방법은 멀티프로세싱과 실시간 컴퓨팅을 지원하기에는 부적합함



 ▶ 디스패처(Dispatcher) : CPU의 제어를 단기 스케쥴러가 선택한 프로세스에게 부여하는 모듈

   - 문맥을 교환하는 일

   - 사용자 모드로 전환하는 일

   - 프로그램을 다시 시작하기 위해 사용자 프로그램의 적절한 위치로 이동(jump)하는 일

   - 디스패치 지연(Dispatch latency) : 디스패처가 한 프로세스를 중단시키고 다른 프로세스의 수행을 시작하도록 하는 시간

    -> 가능한 짧아야 함



 스케쥴링 기준(Scheduling Criteria)

 ▶ 기준

<시스템 입장에서의 효율성 판단 척도>

   1) CPU 이용률(Utilization) : CPU 수행 시간 / 시스템 구동 시간 (%) (↑)

   2) 처리율(throughput) : 단위 시간당 완료되는 프로세스 수 (↑)
   
   <사용자 입장에서의 효율성 판단 척도>

   3) 반환 시간(turnaround time) : 프로세스가 시스템에 진입하여 완료되기까지의 시간(↓)

    - 기억장치에 들어가는 시간

    - 준비 큐에서 대기하는 시간 -> 4)에 해당

    - CPU에서의 실행 시간

    - 입출력 시간

   4) 대기 시간(waiting time) : 준비 큐에서 대기하는 시간 (↓)

    -> CPU 스케쥴링 알고리즘에 따라 실질적으로 영향받는 요소

   5) 반응 시간(response time) : 작업을 제출한 후 첫 응답이 나올 때까지의 시간 (↓)

    -> 대화식 시스템의 경우 반환 시간보다 적합

<h1>
   각종 스케쥴링 알고리즘(Scheduling Algorithm)
   </h1>
   
▶ 선입 선처리 스케쥴링(First-Come First-Served; FCFS Scheduling) : CPU를 요구하는 순으로 할당

   - 선입선출(FIFO) 큐로 구현, 제일 간단함



   ex) 프로세스 , CPU 버스트 시간(msec)

          P1                 24

          P2                  3

          P3                  3   
   
![FCFS](https://user-images.githubusercontent.com/21725428/48552778-0448bf80-e91d-11e8-8476-4b1eba44e405.PNG)

ex) 하나의 CPU 중심 작업과 다수의 입출력 중심 작업이 존재하는 경우

-> Convoy effect : 소요시간이 긴 프로세스가 먼저 도달하여 시간을 잡아먹고 있는 부정적인 현상.
해결책은? 짧은 것부터 먼저 처리하는 식의 알고리즘으로 가능!


▶ 최단 작업 우선 스케쥴링(Shortest-Job-First Scheduling) : CPU 버스트 시간이 가장 작은 프로세스를 선택. 단, 동일할 경우는 선입선출 스케쥴링을 적용

    -> 최적 알고리즘 : 평균 대기 시간을 최소로 함



   ex) 프로세스 , CPU 버스트 시간

           P1                 6

           P2                 8

           P3                 7

           P4                 3
           
           ![SJF](https://user-images.githubusercontent.com/21725428/48553068-d9ab3680-e91d-11e8-87fe-d29f2ab02418.PNG)
           
 ▶ 선점 SJF 스케쥴링 : 최소 잔여 시간 우선(Shortest Remaining Time First) 스케쥴링

   - ex) 프로세스 , 도착 시간 , 버스트 시간

             P1             0               8

             P2             1               4

             P3             2               9

             P4             3               5
             
             ![SRJF](https://user-images.githubusercontent.com/21725428/48553166-2e4eb180-e91e-11e8-9d97-2c52e454b2ec.PNG)
