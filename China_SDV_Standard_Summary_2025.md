# 중국 SDV 표준 종합 요약 (2025년 1월)

## 📊 핵심 요약

### SDV/T 001-2022 Version 4 Beta 1
- **총 API 수**: 520개+ (Part 1: 290개+, Part 2: 230개+)
- **최신 버전**: Version 4 Beta 1 (2022년 12월 발표)
- **주관**: 중국자동차공업협회(CAAM) 소프트웨어 분과
- **참여 기업**: 60개+ (BYD, NIO, Geely, Huawei, Bosch 등)

## 🏗️ 4계층 아키텍처

### Layer 1: 애플리케이션 계층
- OEM 특화 애플리케이션
- 3rd Party 앱
- 사용자 서비스

### Layer 2: 아토믹 서비스 API (Part 1)
**6대 도메인 / 290+ APIs**
- **BCM** (Body Control Module): 31개 서비스
- **TMS** (Thermal Management System): 8개 서비스  
- **VCS** (Vehicle Control System): 12개 서비스
- **EMS** (Energy Management System): 15개 서비스
- **ADAS** (Advanced Driver-Assistance Systems): 18개 서비스
- **HMI** (Human Machine Interface): 10개 서비스

### Layer 3: 디바이스 추상화 API (Part 2)
**5대 도메인 / 230+ APIs**
- **BCM**: 액추에이터 25개, 센서 18개
- **TMS**: 액추에이터 12개, 센서 8개
- **PWT** (Powertrain): 액추에이터 15개, 센서 12개
- **CHS** (Chassis): 액추에이터 8개, 센서 15개
- **ADAS**: 액추에이터 3개, 센서 8개

### Layer 4: 기초 플랫폼 계층
- Linux, QNX, Android Automotive
- RTOS
- 하드웨어 드라이버

## 🔄 Version 3 → Version 4 주요 변경사항

### 신규 서비스 추가
1. **BCM_SafetyBelt**: 안전벨트 버클 상태 관리
2. **BCM_ScreenAdjust**: 스크린 위치 조절
3. **6개 모터 서비스**:
   - Actr_SingleFbMot (단일 피드백)
   - Actr_DoubleFbMot (2중 피드백)
   - Actr_TripleFbMot (3중 피드백)
   - Actr_SlideRMot (가변 저항)
   - Actr_GradedMot (다단 등급)
   - Actr_Heatr (히터)

### API 개선사항
- **TMS_Battery**: WorkMode 관련 API 3개 추가
- **EMS_ChargePort**: AC/DC 온도 모니터링 추가
- **오류 등급**: 4단계 → 8단계로 세분화
- **모터 제어**: dutyRat, speed 매개변수 추가

## 🚗 중국 OEM 구현 현황

### BYD (比亞迪)
- **DiLink 시스템**: 520개 API 중 450개 구현
- **Xuanji 아키텍처**: 전동화와 지능화 통합 (2024년 1월 발표)
- **월간 OTA 업데이트**: 전 차종 무료 제공
- **God's Eye ADAS**: 100만대+ 장착 (2025년 2월)
- **투자**: 1,000억 위안 SDV 개발 투자

### NIO (蔚來)
- **구현 수준**: 자체 개발 80%+
- **중앙집중식 E/E 아키텍처**
- **NOMI AI**: 음성 어시스턴트 통합
- **배터리 교체 시스템과 SDV 연계**

### Xiaopeng (小鵬)
- **XPILOT 4.0**: 도심 자율주행
- **완전 SDV 구현**
- **분기별 주요 기능 업데이트**
- **차량-집-사무실 연결 생태계**

### Li Auto (理想)
- **Li OS**: 부분 구현 중
- **2025년 완전 구현 목표**

### Geely (吉利)
- **GEEA 2.0 아키텍처**
- **70% API 구현**
- **글로벌 확대 전략**

## 🏢 화웨이 IDVP 플랫폼

### 2024년 성과
- **순이익**: 22.3억 위안 (상반기)
- **기업 가치**: 1,150억 위안 (160억 달러)
- **독립 자회사**: Shenzhen Yinwang Intelligent Technology Ltd.

### 2030 전망
- NEV 점유율: 82%
- 차량 컴퓨팅 파워: 5,000+ TOPS
- L3 자율주행: 30% 보급
- 네트워크 속도: 100+ Gbps

## 📈 시장 전망

### 글로벌 SDV 시장
- **2024년**: 2,135억 달러
- **2030년**: 1조 2,370억 달러
- **CAGR**: 34.0%

### 중국 시장 특징
- 아시아태평양 시장 주도
- 글로벌 SDV 시장의 40% 차지 예상
- NEV 판매: 2025년 1,600만대 예상

## 💡 핵심 API 예시

### BCM_Door (도어 제어)
```cpp
Result lock(DoorPosition pos);
Result unlock(DoorPosition pos);
Result open(DoorPosition pos, uint8_t angle);
DoorStatus getStatus(DoorPosition pos);
```

### TMS_AC (공조 제어)
```cpp
Result setTargetTemp(float temp);
Result setFanSpeed(uint8_t speed);
Result setWorkMode(TMS_Mode mode); // V4 신규
```

### ADAS_Perception (인지)
```cpp
vector<Object> getTrackObjects();
LaneInfo getLaneline();
TrafficLight getTrafficLight();
ParkingSpace getParkingSpace();
```

### EMS_Charging (충전)
```cpp
Result start(ChargeType type);
Result stop();
Result setChargingPower(uint32_t power);
ChargeStatus getChargingStatus();
Result notifyACTemp(); // V4 신규
Result notifyDCTemp(); // V4 신규
```

## 🌏 국제 협력

### 글로벌 Tier-1
- **Bosch**: AUTOSAR-중국 표준 매핑
- **Continental**: 듀얼 스택 지원
- **Aptiv**: 중국향 SDV 플랫폼
- **ZF**: 중국 OEM 공동 개발

### IT 기업
- **Baidu Apollo**: SDV 표준 통합
- **Alibaba**: AliOS Auto 연계
- **Tencent**: TAI 3.0 호환
- **Xiaomi**: SU7 SDV 구현

## 🇰🇷 한국 대응 전략 제안

### 단기 (2025년)
1. K-SDV 표준화 협의체 구성
2. 중국 표준 상세 분석
3. AUTOSAR 갭 분석
4. 파일럿 프로젝트 착수

### 중기 (2026-2027년)
1. K-SDV Version 1.0 발표
2. Core API + Extension 구조
3. 국제 호환성 확보
4. 개발자 생태계 구축

### 장기 (2028년+)
1. 글로벌 시장 진출
2. MaaS/C-ITS 연계
3. 동남아 시장 표준 주도

## 📌 결론

중국 SDV 표준(SDV/T 001-2022)은:
- **세계 최대 규모**: 520개+ API
- **빠른 반복**: 6개월 주기 업데이트
- **강력한 실행력**: 60개+ 기업 참여
- **시장 주도**: 2030년 글로벌 40% 예상

한국은 신속한 대응으로 글로벌 SDV 경쟁에서 차별화된 포지션을 확보해야 함.

---
*최종 업데이트: 2025년 1월*
*작성: 한국전자기술연구원 (KETI)*