# Robot_engineering_design
로봇종합설계

# 설계 목표

## 1차
- 지정된 경로를 따라 로봇을 직접 조종하여 이동하고, 경로내에 위치한 장애물을 최종 장소에 운반하여 지정된 위치에 이송.

## 2차
- 로봇을 직접 조종하지 않으며 정해진 경로를 이탈하지 않고 주행하되 무작위로 주어진 장애물을 회피하여 목표지점에 도달.

# Hardware
## 1차 목표시 하드웨어 형상
![image](https://user-images.githubusercontent.com/102535447/187156224-35c754e6-7aec-4937-9729-cd7a9f8b57ce.png)
![image](https://user-images.githubusercontent.com/102535447/187156311-fc443af5-f02e-4877-9aa6-346ba7a00d2b.png)

## 2차 목표시 하드웨어 형상
![image](https://user-images.githubusercontent.com/102535447/187156440-2b9e97f4-912e-4ea4-a627-5c002776cb66.png)

# Software
## Arduino
- 카메라, 초음파 센서 를 통하여 판단한 로봇의 제어 정보를 Myrio에 전달.
## Myrio
- 전달 받은 제어 정보에 따라 제어하며, 로봇 모터의 엔코더 정보를 받아와, PID제어 구현 및 모터제어.
- FPGA 프로그램으로 PWM, 4체배 형식의 ENCODER Counter 구성.
  
## 작동 알고리즘
- 카메라를 통하여 얻은 이미지 정보를 이용하여 라인 트레킹하여 움직임.
- 초음파 센서를 통하여 장애물 탐지시 장애물 회피 동작 수행.
