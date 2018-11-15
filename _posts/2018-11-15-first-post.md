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




