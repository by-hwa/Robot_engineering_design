# 🤖 AMR Robot Design
### 센서 기반 자율주행 및 장애물 회피 기능을 갖춘 AMR 설계 및 구현

## 1. Project Overview

본 프로젝트는 **주어진 경로를 따라 자율주행하고 주행 중 장애물을 감지하여 회피할 수 있는 AMR(Autonomous Mobile Robot)을 설계·제작한 프로젝트**입니다.

로봇의 기구 설계부터 구동부 제작, 센서 구성, 주행 알고리즘 및 모터 제어까지 수행하여 하나의 모바일 로봇 시스템으로 통합했습니다.

SolidWorks를 활용하여 로봇의 프레임과 구동부를 설계하고, 3D 프린팅을 통해 기어박스 등 필요한 부품을 제작했습니다.

소프트웨어는 **Arduino와 NI myRIO를 활용하여 센서 기반 주행 판단과 모터 제어 기능을 구성**했습니다. 카메라와 초음파 센서로 주변 환경을 인식하고 주행 판단 결과에 따라 모터를 제어하도록 구현했습니다.

또한 엔코더 피드백과 PID 제어를 활용하여 모터의 동작을 제어하고 실제 주행 실험을 통해 제어 파라미터를 조정했습니다.

### Project Information

| 항목 | 내용 |
|---|---|
| Project | AMR Robot Design (로봇종합설계) |
| Robot Type | Autonomous Mobile Robot |
| Mechanical Design | SolidWorks, 3D Printing |
| Controller | Arduino, NI myRIO |
| Programming | LabVIEW, Arduino |
| Motor Control | PWM, Encoder, PID Control |
| Sensors | Camera, Ultrasonic Sensor, Encoder |
| Key Functions | Line Tracking, Obstacle Detection & Avoidance |

### Final Result

<!-- 실제 AMR 사진 또는 주행 영상 추가 -->

<div align="center">
  <video
    src="https://github.com/user-attachments/assets/b7212e41-315a-4d19-b06e-dc2aa5fd1a68"
    width="480"
    controls>
  </video>
</div>


---

## 2. Hardware Design

### 2.1 Mechanical Design

SolidWorks를 활용하여 로봇의 프레임과 구동부를 설계했습니다.

로봇의 무게와 구동에 필요한 힘을 고려하여 모터를 선정하고, 모터 출력에 맞는 기어박스를 구성했습니다.

또한 배터리와 제어기, 각종 센서의 배치 공간 및 배선 경로를 고려하여 로봇의 전체 구조를 설계했습니다.

**주요 설계 내용**

- **Motor Selection:** 로봇의 무게와 구동에 필요한 힘을 고려한 모터 선정
- **Gearbox Design:** 모터의 출력과 필요한 구동 특성을 고려한 기어박스 설계
- **Chassis Design:** 구동부, 배터리 및 제어기 배치를 고려한 프레임 설계
- **3D Modeling:** SolidWorks 기반 로봇 부품 모델링 및 조립 구조 검토

설계한 기구 구조는 3D 모델링을 통해 조립 상태와 동작을 확인한 후 실제 제작에 활용했습니다.

#### SolidWorks Modeling

<p align="center">
  <img src="https://github.com/user-attachments/assets/6bb17306-d617-43ce-944c-0795405e425b" width="520" alt="AMR CAD Model"/>
</p>

#### Gearbox Design

<p align="center">
  <img src="https://github.com/user-attachments/assets/f288c667-0b25-41f2-9d2b-322d3c52d918" width="450" alt="Gearbox Design"/>
</p>



---

### 2.2 Power System & Wiring

로봇의 모터, 모터 드라이버, 센서 및 제어기에 필요한 전원을 공급하기 위해 배터리와 배선 시스템을 구성했습니다.

각 장치의 소비전력과 로봇의 작동 시간을 고려하여 배터리 용량 및 출력을 선정하고, 장치별 요구 전압에 맞게 전원 공급 구조를 설계했습니다.

또한 로봇의 무게중심과 내부 공간을 고려하여 배터리 및 제어기의 배치 위치를 결정했습니다.

**주요 설계 내용**

- 모터 및 제어 장치의 소비전력을 고려한 배터리 선정
- 배터리와 제어기의 배치 및 무게중심 고려
- 장치별 요구 전압을 고려한 전원 공급 및 배선
- 센서, 모터 드라이버 및 제어기 연결

#### Power System & Wiring

<p align="center">
  <img src="https://github.com/user-attachments/assets/b4426da9-77c0-4799-b4bf-b460e53d133b" width="500" alt="Power System"/>
</p>

---

### 2.3 Hardware Implementation

설계한 로봇의 기구 부품을 제작하고, 모터와 구동부, 제어기 및 센서를 조립하여 실제 AMR을 구현했습니다.

프레임과 기어박스를 조립한 후 배터리, 모터 드라이버 및 제어기를 배치하고 각 장치의 전원 및 신호선을 연결했습니다.

이후 실제 구동을 통해 하드웨어의 동작 상태를 확인했습니다.

#### Hardware Assembly

<p align="center">
  <img src="https://github.com/user-attachments/assets/baaf4098-458f-4b67-8127-519531a093e5" width="360" alt="Hardware Assembly1"/>
  &nbsp;
  <img src="https://github.com/user-attachments/assets/7b46e359-fe5f-4dfe-9a09-49d1b0dea4d5" width="360" alt="Hardware Assembly2"/>
</p>

---

## 3. Software Design

본 프로젝트에서는 **Arduino와 NI myRIO를 활용하여 센서 기반 주행 판단과 모터 제어 기능을 분리하여 구성**했습니다.

Arduino에서는 카메라와 초음파 센서로부터 얻은 정보를 바탕으로 주행 알고리즘을 수행하고, NI myRIO에서는 전달받은 제어 정보에 따라 모터를 구동하도록 구성했습니다.

### 3.1 System Architecture

**시스템 동작 구조**

```text
     Camera       Ultrasonic Sensor
        |                 |
        +--------+--------+
                 |
                 v
              Arduino
       (주행 판단 알고리즘)
                 |
                 v
              NI myRIO
          (LabVIEW / FPGA)
                 |
                 v
            Motor Driver
                 |
                 v
               Motor
                 |
                 v
              Encoder
                 |
                 +----> PID Feedback Control
```

각 장치의 역할은 다음과 같습니다.

| Component | Function |
|---|---|
| Camera | 주행 경로 인식을 위한 영상 정보 획득 |
| Ultrasonic Sensor | 주변 장애물 감지 |
| Arduino | 센서 정보 기반 주행 방향 및 회피 판단 |
| NI myRIO | Arduino의 제어 정보에 따른 모터 제어 |
| FPGA | Encoder Counter 및 PWM 신호 처리 |
| Encoder | 모터 회전 정보 측정 |
| PID Controller | 엔코더 피드백 기반 모터 제어 |

---

### 3.2 Sensor-based Navigation (Arduino)

Arduino에서는 카메라와 초음파 센서를 통해 얻은 정보를 활용하여 로봇의 주행 방향과 장애물 회피 동작을 판단하도록 구성했습니다.

**주요 기능**

**① Line Tracking**
- 카메라 기반 주행 경로 정보 활용
- 로봇이 주어진 경로를 따라 이동하기 위한 주행 방향 판단
- 주행 판단 결과를 NI myRIO에 전달

**② Obstacle Detection & Avoidance**
- 초음파 센서를 활용한 주변 장애물 감지
- 장애물 감지 정보를 바탕으로 회피 동작 판단
- 장애물 회피를 위한 제어 정보 전달

이를 통해 로봇이 주어진 경로를 따라 이동하면서 장애물에 대응할 수 있도록 주행 알고리즘을 구성했습니다.

---

### 3.3 Motor Control (NI myRIO)

NI myRIO와 LabVIEW를 활용하여 로봇의 모터 제어 시스템을 구현했습니다.

Arduino에서 전달받은 제어 정보를 기반으로 모터를 구동하고, 엔코더를 통해 측정한 회전 정보를 활용하여 PID 제어를 수행했습니다.

**주요 구현 내용**

- **PWM Control:** 모터 구동을 위한 PWM 신호 생성
- **Encoder Counter:** FPGA를 활용한 4체배(Quadrature) 엔코더 카운터 구성
- **PID Control:** 엔코더 피드백을 활용한 모터 제어
- **Parameter Tuning:** 실제 로봇 구동 실험을 통한 PID 제어 계수 조정

#### Encoder Feedback & PID Control

모터의 실제 동작 상태를 확인하기 위해 엔코더 정보를 활용했습니다.

FPGA에서 PWM 신호 생성과 엔코더 카운팅 기능을 구성하고, 엔코더 피드백을 이용하여 PID 제어를 구현했습니다.

또한 실제 로봇을 주행시키면서 제어 계수를 조정하여 모터의 동작을 확인했습니다.

#### LabVIEW Motor Control

<p align="center">
  <img src="https://github.com/user-attachments/assets/0267be16-1603-461a-88ff-4147d646a581" width="320" alt="LabVIEW Motor Control1"/>
  &nbsp;
  <img src="https://github.com/user-attachments/assets/e4551d1f-7f50-45d7-b79f-148945494003" width="320" alt="LabVIEW Motor Control2"/>
</p>

---

## 4. System Integration & Testing

### 4.1 System Integration

개별적으로 구성한 센서, 주행 판단 알고리즘 및 모터 제어 기능을 하나의 AMR 시스템으로 통합했습니다.

카메라와 초음파 센서에서 획득한 정보를 기반으로 Arduino가 주행 방향을 판단하고, 해당 정보를 NI myRIO에 전달하여 모터를 제어하도록 구성했습니다.

또한 모터의 엔코더 피드백을 활용한 PID 제어를 적용하여 실제 로봇에서 주행 동작을 수행했습니다.

**통합 시스템 동작 과정**

1. **Perception:** 카메라 및 초음파 센서로 주변 환경 인식
2. **Decision:** 센서 정보를 기반으로 주행 방향 및 회피 동작 판단
3. **Control:** NI myRIO에서 모터 구동 및 PID 제어 수행
4. **Feedback:** 엔코더 정보를 활용한 모터 상태 확인

### 4.2 Robot Testing

제작한 AMR을 실제 주행 환경에서 테스트하며 주행 알고리즘과 모터 제어 기능을 확인했습니다.

**주요 검증 항목**

- 로봇의 기본 주행 및 조향 동작
- 카메라 정보를 활용한 Line Tracking
- 초음파 센서 기반 장애물 감지 및 회피
- 엔코더 피드백 및 PID 모터 제어
- 센서, 제어기 및 구동부의 통합 동작

#### Robot Testing

<div align="center">
  <video
    src="https://github.com/user-attachments/assets/10a7d983-8ddf-4600-81b7-9053bf339614"
    width="480"
    controls>
  </video>
</div>

---

## 5. Results

SolidWorks 기반 기구 설계부터 하드웨어 제작, 센서 기반 주행 판단 및 PID 모터 제어까지 통합하여 AMR 시스템을 구현했습니다.

### 주요 결과

- **Mechanical Design:** 로봇 프레임 및 기어박스 설계·제작
- **Hardware Implementation:** 모터, 배터리, 센서 및 제어기를 포함한 AMR 제작
- **Autonomous Navigation:** 카메라 기반 Line Tracking 구현
- **Obstacle Avoidance:** 초음파 센서를 활용한 장애물 감지 및 회피 기능 구현
- **Motor Control:** NI myRIO와 FPGA를 활용한 PWM 및 Encoder Counter 구성
- **PID Control:** 엔코더 피드백 기반 모터 제어 및 실제 실험을 통한 계수 조정
- **System Integration:** 센서 인지부터 주행 판단 및 모터 제어까지 기능 통합

최종적으로 **로봇이 주변 환경을 인식하고, 주어진 경로를 따라 주행하면서 장애물을 회피하는 동작을 구현**했습니다.

또한 로봇종합설계 프로젝트 수행 팀 중 가장 우수한 결과를 달성했습니다.

#### Final Result

<p align="center">
  <img src="https://github.com/user-attachments/assets/e0004afc-a74e-435c-84ff-74ac52a206a4" width="520" alt="Final Result"/>
</p>



