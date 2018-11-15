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



