# Shorten URL Service

Spring Boot 기반의 **단축 URL 생성 및 관리 서비스**입니다.

긴 URL을 짧은 주소로 변환하고, 링크별 클릭 통계와 사용 상태를 관리할 수 있습니다.

## 1. 프로젝트 개요

### 개발 목적
- 긴 URL을 단축하여 공유 편의성 향상
- 링크별 클릭 통계를 통한 접속 현황 파악
- 링크 사용 중지 및 재개를 통한 효율적인 관리

### 주요 사용자
- 고객센터 상담사
- 고객 안내 링크를 관리하는 업무 담당자

## 2. 주요 기능

- **단축 URL 생성:** 원본 URL을 8자리 단축 코드로 변환
- **URL 리다이렉트:** 단축 URL 접속 시 원본 페이지로 이동
- **클릭 통계:** 링크별 클릭 횟수 조회 및 TOP 3 순위 시각화
- **URL 관리:** 등록된 URL 검색 및 사용 중지·재개
- **페이지네이션:** URL 목록을 5개씩 조회
- **통계 대시보드:** 전체 URL 수, 활성 URL 수, 총 클릭 수 및 TOP 5 그래프 제공

## 3. 기술 스택

| 구분 | 기술 |
|---|---|
| Backend | Java, Spring Boot |
| Frontend | HTML, CSS, JavaScript |
| Database | MySQL |
| Infrastructure | Docker |
| Build Tool | Gradle |
| Architecture | Layered Architecture |
| Data Access | Spring JDBC |

## 4. 프로젝트 구조

```text
src/main
├── java/kr/co/shortenurlservice
│   ├── application
│   │   └── SimpleShortenUrlService.java
│   ├── domain
│   │   ├── ShortenUrl.java
│   │   └── ShortenUrlRepository.java
│   ├── infrastructure
│   │   └── JdbcShortenUrlRepository.java
│   ├── presentation
│   │   ├── DTO 클래스
│   │   └── ShortenUrlRestController.java
│   └── ShortenurlserviceApplication.java
└── resources
    ├── static
    │   └── index.html
    └── application.properties
```

## 5. 서비스 동작 흐름

1. 사용자가 원본 URL을 입력합니다.
2. 서버에서 8자리 단축 코드를 생성하고 MySQL에 저장합니다.
3. 단축 URL 접속 시 활성 상태를 확인하고 원본 페이지로 이동합니다.
4. 접속 횟수를 DB에 기록하고 대시보드에 통계를 표시합니다.
5. 관리자는 URL을 검색하고 사용 중지·재개할 수 있습니다.