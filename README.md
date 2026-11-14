# Shorten URL Service

Spring Boot 기반의 단축 URL 생성 및 관리 서비스입니다.

긴 URL을 짧은 주소로 변환하고, 생성된 단축 URL을 통해 원본 페이지로 이동할 수 있도록 구현합니다.

향후 고객센터 상담사가 고객에게 안내 자료를 전달하고, 링크 접속 현황과 유효기간을 관리할 수 있는 **CRM 고객 안내 링크 관리 서비스**로 확장하는 것을 목표로 합니다.

## 1. 프로젝트 개요

### 개발 목적
- 긴 URL을 짧은 URL로 변환하여 공유 편의성 향상
- 단축 URL을 통한 원본 페이지 리다이렉트
- 고객 안내 링크의 접속 현황 및 유효기간 관리 기능 확장

### 주요 사용자
- 고객센터 상담사
- 고객 안내 자료를 공유하는 업무 담당자

## 2. 주요 기능

### 기본 기능
- 원본 URL 등록
- 단축 URL 생성
- 단축 URL을 통한 원본 페이지 이동
- 단축 URL 정보 조회

### 확장 예정 기능
- **클릭 통계:** 링크별 접속 횟수 및 접속 여부 확인
- **링크 만료:** 설정된 만료일 이후 접근 제한

## 3. 기술 스택

| 구분 | 기술 |
|---|---|
| Language | Java |
| Framework | Spring Boot |
| Build Tool | Gradle |
| Architecture | Layered Architecture |
| Data Storage | In-Memory (Map 기반 Repository) |

## 4. 프로젝트 구조

```text
src/main/java/kr/co/shortenurlservice
├── application
│   └── SimpleShortenUrlService.java
├── domain
│   ├── ShortenUrl.java
│   └── ShortenUrlRepository.java
├── infrastructure
│   └── MapShortenUrlRepository.java
├── presentation
│   ├── ShortenUrlCreateRequestDto.java
│   ├── ShortenUrlCreateResponseDto.java
│   ├── ShortenUrlInformationDto.java
│   └── ShortenUrlRestController.java
└── ShortenurlserviceApplication.java
```

### 계층별 역할

| 계층 | 역할 |
|---|---|
| Presentation | HTTP 요청 및 응답 처리 |
| Application | URL 단축 관련 비즈니스 로직 |
| Domain | 단축 URL 도메인 객체 및 Repository 인터페이스 |
| Infrastructure | Map 기반 데이터 저장소 구현 |

## 5. 서비스 동작 흐름

1. 사용자가 원본 URL을 입력합니다.
2. 서버에서 단축 URL을 생성합니다.
3. 생성된 단축 URL 정보를 저장합니다.
4. 사용자가 단축 URL에 접속합니다.
5. 서버에서 원본 URL을 조회하고 해당 페이지로 이동시킵니다.
