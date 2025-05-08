# 지니어스, 소원을 이뤄주는 최저가 쇼핑

![image](https://github.com/user-attachments/assets/967fd02f-2e07-4224-a194-1b0ace303b28)

## 서비스/프로젝트 소개
**지니어스(Genie-Us)는 우리 곁의 천재(Genius)가 소원을 이뤄주듯, 최저가 상품과 선착순 쿠폰으로 최고의 쇼핑 경험을 제공합니다.** </br>
Genie(🧞‍♂️)와 Us(우리)가 만나, 가장 합리적인 소비를 완성합니다.

> "🪔 최저가를 소환하세요, 지니어스와 함께!”
</br>
</aside>

## 서비스/프로젝트 목표

**1️⃣ MSA 멀티 프로젝트 구조를 통한 확장성 확보**

- 각 기능을 독립된 서비스로 분리하여 대규모 트래픽 상황에서도 안정적이고 유연한 서비스를 운영합니다.

**2️⃣ Feign과 Kafka를 조합한 안정적인 통신 방식**

- 핵심 트랜잭션은 Feign 동기 통신으로 처리하고, 실패 복구와 후속 처리는 Kafka 비동기 이벤트로 안정성을 강화했습니다.

**3️⃣ Batch 처리를 통한 안정적인 대량 데이터 저장**

- 임시 저장된 **선착순 쿠폰 발급 데이터**와 **재고 히스토리 데이터**를 **Spring Batch**로 주기적 수집 및 **Bulk Insert**하여 대량 데이터 입력 시 안정성과 일관성을 확보하였습니다.

**4️⃣ Redis를 활용한 실시간 프로모션 최저가 보장**

- 프로모션은 상품 별 할인율을 관리하고, Redis에 구간별 상품의 최대 할인율을 사전에 저장해 실시간으로 정확한 최저가 제공이 가능합니다.
- 프로모션 관리 및 할인율 조회 성능을 최적화하여 사용자가 언제나 최적의 가격 혜택을 누릴 수 있도록 보장합니다.

 **5️⃣ Redis를 활용한 안정적 재고 관리**

- **Lua 스크립트를 활용한 원자적 재고 처리**로 주문 발생 시 **상품 재고**와 선착순 **쿠폰 재고**를 정확하고 안전하게 관리합니다.
- **Redis 기반의 빠른 동기식 검증**으로 대규모 트래픽 상황에서도 실시간으로 안정적인 재고 관리가 가능합니다.

 **6️⃣ Prometheus, Grafana, Loki, k6를 활용한 통합 모니터링 및 성능 테스트**

- 시스템 지표와 로그를 통합 관리하여 장애를 조기에 감지하고 실시간 대응할 수 있는 모니터링 체계를 구축했습니다.
- 실제 사용자 흐름을 기반으로 부하 테스트를 수행하고, 시스템의 병목 지점을 사전에 개선했습니다.

</br>

## 인프라 설계

<aside>

### 시스템 아키텍처 설계도

![인프라_아키텍처 drawio](https://github.com/user-attachments/assets/7d6074dd-b73d-436c-9f2e-9845e2373b56)

### 카프카 이벤트 흐름
![image 2](https://github.com/user-attachments/assets/c74ba7d2-7dd8-4c10-b61d-a07249715572)

</aside>

## 주요 기능

### [🌐 게이트웨이 & 인증](https://github.com/Genie-Uss/genieus/wiki/게이트웨이&인증)

### [🪄 주문](https://github.com/Genie-Uss/genieus/wiki/주문)

### [💸 결제](https://github.com/Genie-Uss/genieus/wiki/결제)

### [🔥 프로모션](https://github.com/Genie-Uss/genieus/wiki/프로모션)

### [🎁 상품](https://github.com/Genie-Uss/genieus/wiki/상품)

### [🎟️ 쿠폰](https://github.com/Genie-Uss/genieus/wiki/쿠폰)

</br>

## 적용 기술
![스크린샷 2025-05-08 오후 12 51 42](https://github.com/user-attachments/assets/2fe42ad2-fa10-4519-a489-1b39421d4ec1)


</br>

## 기술적 의사결정

### [📖 공통 라이브러리 설계 및 의존성 관리 전략](https://github.com/Genie-Uss/genieus/wiki/공통-라이브러리-설계-및-의존성-관리-전략)
### [📨 서비스 간 통신 방식 결정 (동기 vs 비동기)](https://github.com/Genie-Uss/genieus/wiki/서비스-간-통신-방식-결정-(동기-vs-비동기))
### [📈 성능 최적화를 위한 배치 및 캐시 전략](https://github.com/Genie-Uss/genieus/wiki/성능-최적화를-위한-배치-및-캐시-전략)
### [👨‍🔬 통합 모니터링 및 트레이싱 환경 구축](https://github.com/Genie-Uss/genieus/wiki/통합-모니터링-및-트레이싱-환경-구축)
### [❤️‍🩹 서비스 장애 대응 및 복구 전략 수립](https://github.com/Genie-Uss/genieus/wiki/서비스-장애-대응-및-복구-전략-수립)
### [🐳 배포 전략 결정 및 클라우드 인프라 설계](https://github.com/Genie-Uss/genieus/wiki/배포-전략-결정-및-클라우드-인프라-설계)

## 트러블슈팅

### [♻️ MSA 환경에서 API Gateway 연결](https://github.com/Genie-Uss/genieus/wiki/MSA-환경에서-API-Gateway-연결-트러블슈팅)
### [♾️ RDS 커넥션 제한과 Hikari CP 충돌 문제](https://github.com/Genie-Uss/genieus/wiki/RDS-커넥션-제한과-Hikari-CP-충돌-문제)
### [💸 실시간 최저가 상품 반영을 위한 엔티티 구조 설계](https://github.com/Genie-Uss/genieus/wiki/실시간-최저가-상품-반영을-위한-엔티티-구조-설계)
### [🎟️ 배포 서버 배치 실행 시 직렬화 문제](https://github.com/Genie-Uss/genieus/wiki/배포-서버-배치-실행-시-직렬화-문제)
### [⚡️ 서킷브레이커 사용시 예외 문제](https://github.com/Genie-Uss/genieus/wiki/서킷브레이커-사용시-예외-문제)

## 👥 개발 인원 및 역할

| [<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="20">](https://github.com/orkrj) 정우준 | [<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="20">](https://github.com/seongmin1117) 최성민 | [<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="20">](https://github.com/Soobinnni) 김수빈 | [<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="20">](https://github.com/Ryujy) 류지윤 | [<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="20">](https://github.com/sosa7753) 박상욱 |
|:--:|:--:|:--:|:--:|:--:|
| ![정우준](https://github.com/orkrj.png) | ![최성민](https://github.com/seongmin1117.png) | ![김수빈](https://github.com/Soobinnni.png) | ![류지윤](https://github.com/Ryujy.png) | ![박상욱](https://github.com/sosa7753.png) |
| [📝 Wiki](https://github.com/Genie-Uss/genieus/wiki/정우준)<br/>• 배포 전략 수립<br/>• 클라우드 인프라 담당<br/>• 결제 서비스 개발 | [📝 Wiki](https://github.com/Genie-Uss/genieus/wiki/최성민)<br/>• 공통 라이브러리 설계<br/>• 주문 서비스 구현<br/>• 성능 개선<br/>• CI 구축 | [📝 Wiki](https://github.com/Genie-Uss/genieus/wiki/김수빈)<br/>• 인증 서버 / 게이트웨이<br/>• 유저 / 상품 도메인<br/>• 공통 인증 모듈<br/><br/> | [📝 Wiki](https://github.com/Genie-Uss/genieus/wiki/류지윤)<br/>• 쿠폰 서비스 설계 및 개발<br/><br/><br/> | [📝 Wiki](https://github.com/Genie-Uss/genieus/wiki/박상욱)<br/>• 프로모션 도메인 개발<br/>• 상품 도메인 개발<br/><br/> |


