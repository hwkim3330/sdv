# 중국 SDV 표준 분석 리포지토리

## 개요
이 리포지토리는 중국 지능형 커넥티드카 서비스 인터페이스 사양(SDV/T 001-2022) Version 4 Beta 1에 대한 분석 자료를 포함하고 있습니다.

## 내용

### 원본 문서 (중국어)
- `SDV Intelligent Connected Vehicle Service Interface Specification Part 1 Atomic Service API Interface Version 4 Beta 1(중국어).pdf`
- `SDV Intelligent Connected Vehicle Service Interface Specification Part 2 Device Abstraction API Interface Version 4 Beta 1(중국어).pdf`

### 분석 문서
- `China_SDV_Standard_Analysis_v4_Professional.pptx` - 중국 SDV 표준을 분석한 전문 프레젠테이션
- 프레젠테이션 생성을 위한 Python 스크립트

### 보조 자료
- 전략적 분석 문서
- 중국의 표준화 전략 사례 연구
- SDV 생태계 분석

## SDV/T 001-2022 표준 소개

### Part 1: 아토믹 서비스 API 인터페이스
아토믹 서비스 API는 애플리케이션 개발자를 위한 표준화된 기능 인터페이스를 제공하며, 6개 핵심 도메인에 걸쳐 290개 이상의 API를 포함합니다:

- **BCM (Body Control Module)**: 차체 제어 기능
- **TMS (Thermal Management System)**: 온도 및 공조 제어
- **VCS (Vehicle Control System)**: 차량 운동 제어
- **EMS (Energy Management System)**: 전력 및 에너지 관리
- **ADAS (Advanced Driver-Assistance Systems)**: 지능형 주행 기능
- **HMI (Human Machine Interface)**: 사용자 상호작용 인터페이스

### Part 2: 디바이스 추상화 API 인터페이스
디바이스 추상화 API는 하드웨어 추상화 계층을 제공하며, 5개 도메인에 걸쳐 230개 이상의 API를 포함합니다:

- **BCM**: 차체 제어 하드웨어 장치
- **TMS**: 열 관리 장치
- **PWT (Powertrain)**: 파워트레인 구성요소
- **CHS (Chassis)**: 섀시 시스템
- **ADAS**: 센서 및 액추에이터 인터페이스

## 표준의 주요 특징

### 4계층 아키텍처
1. **애플리케이션 계층**: 사용자 경험 및 차량별 특화 기능
2. **아토믹 서비스 계층**: 표준화된 기능 단위 (Part 1)
3. **디바이스 추상화 계층**: 하드웨어 제어 인터페이스 (Part 2)
4. **기초 플랫폼 계층**: OS 및 기본 컴퓨팅 환경

### 전략적 의의
- 중국자동차공업협회(CAAM) 소프트웨어 분과 주도
- BYD, GWM, Geely, FAW, SAIC, Huawei, Bosch, Continental, Baidu 등 60개 이상 기업 참여
- 통일된 개발 표준 수립 및 중국 고유 SDV 생태계 구축 목표

## 핵심 통찰

### 기술적 성과
- 520개 이상 API를 통한 차량 기능의 포괄적 범위
- 하드웨어와 소프트웨어의 완전한 분리(HW-SW 디커플링)
- 개발 효율성의 획기적 개선
- 자동차 "앱 스토어" 모델 구현

### 전략적 시사점
- 글로벌 표준화 경쟁의 새로운 차원
- 소프트웨어 생태계 주도권 확보
- 자동차 산업 패러다임 전환 가속화
- 국가 간 기술 경쟁력 재편

## 한국형 SDV 표준 권고사항

### 제안 방향
1. **Core API + Extension Profiles**: 핵심 API만 표준화, 확장은 프로파일 방식으로 추가
2. **국제 표준 호환성**: AUTOSAR, ISO 20078, W3C VISS와의 매핑 테이블 제공
3. **내장 보안/OTA**: 인증, 권한, 암호화 필수; OTA 업데이트 API 포함
4. **차량-서비스 통합**: MaaS, C-ITS, 클라우드 연계, V2X 데이터 공유를 위한 API 정의

### 전략적 대응
- K-SDV 표준화 협의체 가속화
- 글로벌 표준(AUTOSAR, SOAFEE)과의 협력 강화
- OEM-IT-Tier1 협업 생태계 구축
- SDV 전문 인력 양성

## 버전 정보
- 표준 버전: SDV/T 001-2022 Version 4 Beta 1
- 분석 일자: 2025년 8월
- 리포지토리 관리: 한국전자기술연구원(KETI) 모빌리티플랫폼연구센터

## 라이선스
이 리포지토리는 공개적으로 이용 가능한 표준 문서에 대한 분석과 해설을 포함합니다. 모든 원본 표준은 해당 소유자의 재산입니다.

## 연락처
질문이나 협업 문의는 KETI 모빌리티플랫폼연구센터로 연락 주시기 바랍니다.