# 📚 LIBO: ROS2와 AI를 활용한 자율주행 서점 도우미 로봇

<div align="center">
  <img src="data/readme_src/main_theme.JPG" alt="대표 이미지" width="600px">
</div>
<p align="center">
  <strong>서점고객에게는 편리함을, 직원에게는 효율성을 제공하는 <br>똑똑한 자율주행 로봇 솔루션</strong>
</p>



---

# 📖 목차

- [1. 프로젝트 개요](#1-프로젝트-개요)
- [2. 주요 기능](#2-주요-기능)
- [3. 핵심 기술](#3-핵심-기술)
- [4. 기술적 문제 및 해결](#4-기술적-문제-및-해결)
- [5. 시스템 설계](#5-시스템-설계)
- [6. 프로젝트 구조](#6-프로젝트-구조)
- [7. 기술 스택](#7-기술-스택)
- [8. 프로젝트 관리](#8-프로젝트-관리)
- [9. 팀 구성](#9-팀-구성)

---

# 1. 프로젝트 개요

### 프로젝트 소개
'LIBO'는 스페인어로 책을 의미하는 ***Libro***와 ***Robot***의 합성어로, 서점에서 발생하는 반복적인 안내 및 운반 업무를 서포트하여 **고객 만족도**와 **운영 효율성**을 동시에 높이는 것이 목적인 서점 업무지원 자율주행 로봇 프로젝트 입니다.

- **고객:** 책의 위치를 쉽고 빠르게 찾아 드립니다.
- **직원:** 단순 반복 업무에서 벗어나 핵심 업무에 집중하도록 지원합니다.
- **서점:** 차별화된 고객 경험과 효율적인 매장 관리를 제공합니다.

### 프로젝트 기간
- 2025년 7월 14일 ~ 2025년 8월 13일
---

# 2. 주요 기능

## 🧭 Escort (고객 도서 위치 안내)

고객이 키오스크에서 찾고 싶은 책을 검색하면, LIBO가 해당 책이 있는 위치까지 안전하게 안내합니다.

<table>
  <tr>
    <th style="width:15%">주요 단계</th>
    <th style="width:50%">설명</th>
    <th style="width:35%">이미지/GIF</th>
  </tr>
  <tr>
    <td><b>에스코트 요청 </b></td>
    <td>
      ▪ 키오스크에서 검색된 책의 위치 확인 후 에스코트 요청 <br>
      ▪ 서점지도상의 서적코너 선택하여 에스코트 요청 <br>
      ▪ 요청된 키오스크로 로봇이동
    </td>
    <td align="center">
      <img src="data/readme_src/escort_GUI1.png" width="48%"/>
      <img src="data/readme_src/escort_GUI2.png" width="48%"/><br>
      <img src="data/readme_src/escort_gui_arrived.png" width="48%"/>
      <img src="data/readme_src/escort_arrived.gif" width="48%"/>
    </td>
  </tr>
  <tr>
    <td><b>안내 주행</b></td>
    <td>
      ▪ 키오스크에서 서적코너로 안내 시작<br>
      ▪ Nav2 기반 자율주행으로 목적지까지 이동
    </td>
    <td align="center">
      <img src="data/readme_src/escort_gui_guide.png" width="48%"/>
      <img src="data/readme_src/escort_guide.gif" width="48%"/>
    </td>
  </tr>
  <tr>
    <td><b>동행 확인</b></td>
    <td>
      ▪ 주행 중 후방 카메라로 고객이 잘 따라오는지 지속적으로 확인<br>
      ▪ 고객이 일정 시간 이상 보이지 않으면 안내음과 함께 잠시 대기<br>
      ▪ 고객의 장시간 이탈시 에스코트 자동종료
    </td>
    <td align="center">
      <img src="data/readme_src/escort_back_check1.gif" width="48%"/>
      <img src="data/readme_src/escort_back_check2.gif" width="48%"/>
    </td>
  </tr>
  <tr>
    <!-- <td><b>4) 도착 및 복귀</b></td>
    <td>
      ▪ 목적지 도착 후 음성으로 안내 종료 알림<br>
      ▪ 초기 대기 장소로 복귀
    </td>
    <td align="center">*(이미지 삽입 위치)*</td> -->
  </tr>
</table>


## 🚚 Delivery (직원 도서 운반)

직원이 관리자용 GUI를 통해 새로 입고되거나 정리할 도서를 지정한 위치까지 운반시킵니다.

| 주요 단계 | 설명 | 이미지/GIF |
| :--- | :--- | :--- |
| **원격 호출** | ▪ 직원데스크에서 로봇호출 |  <p align="center"><img src="https://github.com/user-attachments/assets/1223eeef-de9c-468e-a395-368a4b554f54" width="45%"/> <img src="https://github.com/user-attachments/assets/9aecc2e6-70bb-41f6-bebe-2ce62aaec61b" width="30%"/></p> |
| **도서 적재** | ▪ 적재함에 운반할 도서 적재<br>▪ 무게 센서가 실시간으로 책 무게 GUI 표시 및 과적시 알림<br>▪ 직원 GUI에서 운반할 목적지 선택 후 출발 명령 | <div align="center"><img src="data/readme_src/scale_GUI.gif" width="65%"/> <br><img src="data/readme_src/scale_exercise.gif" width="70%"/></p> |
| **운반 주행** | ▪ 지정된 목적지까지 자율주행하여 이동<br>▪ 직원 GUI에서 로봇의 현재 위치와 상태를 실시간 모니터링 |  <p align="center"> <img src="https://github.com/user-attachments/assets/2728812e-7e07-4137-8405-907031c88501" width="60%"/> <br><img src="https://github.com/user-attachments/assets/352e0b66-fb7a-4a04-a6e4-ffad180dce08" width="60%"/> </p> |
<!-- | **4) 작업 완료 및 대기** | ▪ 목적지 도착 후 다음 명령을 대기하거나, 작업 종료 명령 시 대기 장소로 복귀 | *(이미지 삽입 위치)* | -->

## 🤝 Assist (직원 추종 및 보조)

직원이 서가 정리 등의 작업을 할 때, LIBO가 직원을 따라다니며 무거운 책을 대신 운반해주는 기능입니다.

| 주요 단계 | 설명 | 이미지/GIF |
| :--- | :--- | :--- |
| **직원인증 및 호출** | ▪ 키오스크에서 직원용 QR코드를 스캔하여 '직원용 호출' 기능 활성화<br>▪ 로봇 호출 후, 도착한 로봇의 카메라에 QR코드를 2차인증 | <div align="center"><img src="data/readme_src/assist_QR1.png" width="300px"/> <img src="data/readme_src/assist_QR2.png" width="300px"/></div> |
| **팔로우 모드** | ▪ 인증 완료 시 전방의 직원을 타겟으로 지정<br>▪ 사람 추적(Person Tracking) 알고리즘을 통해 팔로우 모드 시작 | <div align="center"><img src="data/readme_src/assist_QR1.gif" width="300px"/> <img src="data/readme_src/assist_QR2.gif" width="300px"/></div> |
| **음성 및 제스처 제어** | ▪ "따라와", "잠깐만" 등 음성 명령으로 로봇 제어<br>▪ 음성으로 '핸드 제스처 모드'로 전환 가능<br>▪ MediaPipe 기반 손동작 인식(전진, 후진, 정지, 회전)으로 정밀 제어 | <div align="center"><img src="data/readme_src/assist_follow.gif" width="300px"/> <img src="data/readme_src/assist_voice_control.gif" width="300px"/> <img src="data/readme_src/assist_gesture_control1.gif" width="300px"/> <img src="data/readme_src/assist_gesture_control2.gif" width="300px"/></div> |
<!-- | **4) 작업 종료 및 복귀** | ▪ 직원이 음성으로 작업 종료를 명령하면 팔로우 모드를 해제 및 대기 장소로 복귀 | *(이미지 삽입 위치)* | -->

## 🔔 로봇 상태 시각화 알림

| 항목 | 예시 이미지 |
| :--- | :---: |
| **표정 변화**<br>• 임무 상태(대기/작업/완료) 및 배터리 상태에 따라 표정 전환<br>• GUI와 동기화해 현재 표정을 표시 | <div align="center"><img src="data/readme_src/liboFace_charge.gif" width="300px"/><br/><img src="data/readme_src/liboFace_listening.gif" width="300px"/></div> |
| **LED 상태등**<br>• 로봇상태에 따른 LED 상태표시 | <div align="center"> <img src="data/readme_src/Libo_statusLED.PNG" width="100%" alt="LED 예시"/></div> |


  # 3. 핵심 기술  

## 🚗 경로 탐색 및 자율 주행  
| 주요 요소 | 설명 | 이미지/도식 |
| :--- | :--- | :--- |
| **웨이포인트 기반<br>자율주행** | ▪ Nav2 기본 플래너를 활용하여 맵 주요 지점을 웨이포인트 그래프 구성<br>▪ A* 알고리즘을 사용해 가장 안정적이고 예측 가능한 경로 생성 | <div align="center"><img src="data/readme_src/core_technologies_waypoint2.gif" width="300px"/> <img src="data/readme_src/core_technologies_custom_navigator2.png" width="300px"/></div> |
| **장애물 회피 및 <br> 경로 재계획** | ▪ 주행 중 장애물 탐지 및 회피<br>▪ 경로가 차단될 경우 현재 위치 기반으로 새로운 최적 경로를 재계산 및 주행 재개 | <div align="center"><img src="data/readme_src/core_technologies_rerouting1.gif" width="300px"/> <img src="data/readme_src/core_technologies_rerouting2.gif" width="300px"/></div> |

---

## 👤 사람 추적 및 Re-ID  
| 주요 요소 | 설명 | 이미지/도식 |
| :--- | :--- | :--- |
| **YOLOv5 + StrongSORT** | ▪ YOLOv5로 영상 내 사람을 실시간 탐지<br>▪ StrongSORT가 각 사람에 ID 부여 및 연속 추적 수행 | <img src="data/readme_src/deepsort_target_maintain.gif" width="300px"/> |
| **재식별(Re-ID)** | ▪ 대상이 잠시 가려져도 외형 특징 벡터 기반 유사도 비교<br>▪ 동일 인물로 재식별하여 추적 안정성 확보 | <img src="data/readme_src/deepsort_target_reacquire.gif" width="300px"/>|

---

## 🗣️ 음성인식 및 LLM 기반 상호작용  
| 주요 요소 | 설명 | 이미지/도식 |
| :--- | :--- | :--- |
| **Wake Word 감지** | ▪ Pico voice의 Porcupine 엔진 기반 실시간 온디바이스 동작| <img src="data/readme_src/porcupine_wakeword.png" width="300px"/> |
| **STT → LLM → TTS 파이프라인** | ▪ Google STT: 음성 → 텍스트 변환<br>▪ OpenAI LLM: 맥락 분석 및 답변 생성<br>▪ Google TTS: 텍스트 → 음성 변환 | <div align="center"><img src="data/readme_src/core_technologies_voice.png" width="300px"/> <img src="data/readme_src/core_technologies_voice.gif" width="300px"/></div> |

---

## ✋ MediaPipe 기반 핸드 제스처 제어  
| 주요 요소 | 설명 | 이미지/도식 |
| :--- | :--- | :--- |
| **손 랜드마크 인식** | ▪ MediaPipe로 손의 21개 주요 랜드마크 좌표 추출 | <div align="center"><img src="data/readme_src/core_technologies_handgesture.png" width="300px"/></div> |
| **제스처 분류 및 제어** | ▪ 손가락의 펴짐/굽힘, 방향 등을 분석<br>▪ 전진, 후진, 정지, 회전 등 로봇 제어 명령으로 변환 | <div align="center"><img src="data/readme_src/core_technologies_handgesture.gif" width="300px"/></div> |

---

# 4. 기술적 문제 및 해결

### 🤖 경로 계획의 안정성 문제
- **문제**: Nav2의 기본 경로 플래너 사용 시, 장애물이나 벽에 너무 가깝게 경로가 생성되어 주행 중 불안정성을 유발하고 충돌 위험이 있었습니다.
- **해결**: Nav2 파라미터들을 조율하고 주요 길목에 **웨이포인트를 설정**하고 이를 노드로 하는 그래프를 직접 구성했습니다. **A\* 알고리즘**으로 이 웨이포인트들을 경유하는 경로를 생성하도록 하여, 항상 안전하고 예측 가능한 중앙 경로로 주행하도록 개선했습니다.

### 👥 추종 대상 유실 문제
- **문제**: Assist 모드에서 직원이 다른 사람이나 서가에 의해 잠시 가려졌을 때, 추적 ID가 변경되거나 다른 사람을 타겟으로 오인하는 경우가 발생했습니다.
- **해결**: 단순 객체 추적을 넘어 **StrongSORT 알고리즘을 도입**했습니다. 이 알고리즘은 외형적 특징을 임베딩 벡터로 저장하여, 대상이 다시 나타났을 때 외형 유사도를 비교해 **재식별(Re-ID)**함으로써 추적의 연속성과 정확도를 크게 향상시켰습니다.

### ⚙️ 분산 시스템 간의 비동기 통신 문제
- **문제**: 로봇(ROS2), 중앙 서버, AI 서버, GUI 등 여러 컴포넌트가 독립적으로 동작하여 상태 동기화가 어렵고, 특정 기능 호출 시 응답 지연이 발생했습니다.
- **해결**: **중앙 서버(Libo Server)를 아키텍처의 중심으로** 설계하여 모든 작업 요청과 상태 관리를 총괄하도록 했습니다. ROS2 토픽은 로봇의 실시간 데이터(위치, 센서 값) 전송에, TCP 소켓 통신은 GUI와 서버 간의 작업 명령 및 상태 업데이트에 사용하는 등 프로토콜을 명확히 분리하여 안정적인 시스템 통합을 구현했습니다.

---

# 5. 시스템 설계

<details>
<summary><b>시스템 아키텍처</b></summary>

<br>
LIBO 시스템은 역할에 따라 명확하게 분리된 5개의 핵심 컴포넌트로 구성

- **🤖 Libo Package:** 로봇의 구동과 하드웨어(카메라, 라이다, 마이크 등)를 직접 제어하는 ROS2 기반 패키지.
- **🧠 AI Server:** 음성 인식(STT), LLM 분석, 영상 분석(YOLO, MediaPipe) 등 높은 컴퓨팅 자원을 요구하는 AI 연산을 전담하는 서버.
- **🖥️ Libo Server:** 모든 컴포넌트의 통신을 중재하고, 작업 할당 및 로봇 상태를 관리하는 중앙 제어 서버.
- **👨‍💼 User Interfaces:** 고객이 사용하는 Kiosk GUI와 직원이 사용하는 Admin GUI로 구성된 사용자 인터페이스.
- **☁️ Database (GCP):** 도서 정보, 로봇 상태 로그, 작업 이력 등 모든 영구 데이터를 저장하는 클라우드 기반 데이터베이스.
<div style="text-align: center;">
  <img src="data/readme_src/libo_system_architecture.png" width="300px"/>
</div>
</details>


# 6. 기술 스택

| 분류 | 사용 기술 |
| :--- | :--- |
| **Robotics & Simulation** | ![ROS 2](https://img.shields.io/badge/ROS%202-Humble-22314E?style=for-the-badge&logo=ros&logoColor=white) ![Nav2](https://img.shields.io/badge/Nav2-D33825?style=for-the-badge) |
| **AI / Deep Learning** | ![YOLOv5](https://img.shields.io/badge/YOLOv5-00FFFF?style=for-the-badge) ![StrongSORT](https://img.shields.io/badge/StrongSORT-8A2BE2?style=for-the-badge) ![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white) ![MediaPipe](https://img.shields.io/badge/MediaPipe-007F7F?style=for-the-badge) |
| **Development** | ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) ![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white) ![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white) |
| **GUI & Database** | ![PyQt5](https://img.shields.io/badge/PyQt5-41CD52?style=for-the-badge&logo=qt&logoColor=white) ![SQL](https://img.shields.io/badge/SQL-005C84?style=for-the-badge) ![GCP](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white) |
| **Collaboration** | ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white) ![Jira](https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white) ![Confluence](https://img.shields.io/badge/Confluence-172B4D?style=for-the-badge&logo=confluence&logoColor=white) ![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white) |

---

# 7. 프로젝트 관리

- **Jira:** 스프린트 기반의 애자일 방법론을 적용하여 태스크를 관리하고 진행 상황을 추적했습니다.
- **Confluence:** 요구사항 정의서, 설계 문서, 회의록 등 모든 산출물을 체계적으로 문서화하고 공유했습니다.
- **GitHub:** Git-flow 전략을 사용하여 소스 코드를 효율적으로 버전 관리하고 협업했습니다.

<div style="text-align: center;">
  <img src="data/readme_src/co-op_tools.PNG" width="300px"/>
</div>

---

# 8. 팀 구성

| 이름 | 역할 | 담당 업무 |
| :--- | :--- | :--- |
| **이승훈** | 팀장 | 팀 총괄, KIOSK GUI 개발, 임베디드 설계, 시뮬레이션 환경 구축 |
| **김대인** | 팀원 | 시스템 메인 서버 설계 및 개발, ADMIN GUI 개발, 연동 테스트 기획/진행 |
| **박태환** | 팀원 | AI 비전 서버 시스템 개발, YOLO & StrongSort 모델 구현, 로봇 팔로잉 제어 개발 |
| **김민수** | 팀원 | LLM 음성인식 제어 설계, 핸드 제스처 로봇 제어 개발, DataBase 설계 및 구성 |
| **이건우** | 팀원 | 프로젝트 관리(Jira, Confluence), 시스템 시나리오 제작, SLAM & Navigation 알고리즘 |



