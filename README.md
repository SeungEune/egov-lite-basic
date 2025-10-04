## 📋 프로젝트 개요

해당 프로젝트는 전자정부 프레임워크 기반으로 작성되었고, 이후로 egov-full-basic으로부터 경량화하여 최소 기능만 남겨둔 버전입니다.

## 🏗️ 기술 스택

- **Java**: 17
- **Spring Framework**: 5.3.37
- **전자정부 프레임워크**: 4.3.0
- **데이터베이스**: PostgreSQL
- **빌드 도구**: Maven
- **웹 서버**: Tomcat 8.x (기본)
- **보안**: Spring Security, 암호화 서비스
- **기타**: MyBatis, Quartz Scheduler, JSTL, Jackson

## 🎯 주요 기능

### 1. 공통 컴포넌트 (CMM)
- **파일 관리**: 파일 업로드/다운로드, 파일 시스템 유틸리티
- **보안**: XSS 방지, 암호화/복호화, 세션 관리
- **유틸리티**: 브라우저 감지, 웹 유틸리티, 예외 처리
- **인터셉터**: 인증 인터셉터, IP 획득 인터셉터

### 2. 보안 관리 (SEC)
- **권한 관리**: 사용자 권한, 권한 그룹, 부서 권한 관리
- **그룹 관리**: 사용자 그룹 생성 및 관리
- **역할 관리**: 권한별 역할 관리
- **암호화**: PKI 기반 암호화 서비스

### 3. 시스템 관리 (SYM)
- **코드 관리**: 공통코드, 상세코드 관리
- **메뉴 관리**: 메뉴 생성 및 관리
- **로그 관리**: 접속로그, 시스템로그, 사용자로그, 웹로그 관리

### 4. 사용자 인증/디렉토리 서비스 (UAT)
- **사용자 인증**: 로그인 정책 관리
- **사용자 정보**: 사용자 정보 관리

### 5. 사용자 지원 (USS)
- **사용자 관리**: 사용자 등록, 수정, 삭제
- **사용자 통계**: 사용자 현황 및 통계

### 6. 유틸리티 기술 (UTL)
- **파일 동기화**: 파일 동기화 컴포넌트
- **시스템 통합**: 시스템 간 연동
- **웹 에디터**: CKEditor 기반 웹 에디터

### 1. 데이터베이스 설정
```properties
# src/main/resources/egovframework/egovProps/globals.properties
Globals.DbType = postgres
Globals.postgres.DriverClassName=org.postgresql.Driver
Globals.postgres.Url=jdbc:postgresql://localhost:5432/egovdb
Globals.postgres.UserName=egov_user
Globals.postgres.Password=your_password
```

## 📁 프로젝트 구조

```
src/main/java/egovframework/com/
├── cmm/          # 공통 컴포넌트
├── sec/          # 보안 관리
├── sym/          # 시스템 관리
├── uat/          # 사용자 인증/디렉토리 서비스
├── uss/          # 사용자 지원
└── utl/          # 유틸리티 기술

src/main/resources/egovframework/
├── egovProps/    # 설정 파일
├── mapper/       # MyBatis 매퍼
├── message/      # 다국어 메시지
├── spring/       # Spring 설정
└── validator/    # 유효성 검사 규칙

src/main/webapp/
├── WEB-INF/
│   ├── config/   # 웹 설정
│   ├── jsp/      # JSP 페이지
│   └── lib/      # 라이브러리
├── css/          # 스타일시트
├── js/           # JavaScript
└── images/       # 이미지 리소스
```

## ⚙️ 주요 설정

### 인증 방식 설정
```properties
# globals.properties
Globals.Auth = dummy    # dummy, session, security 중 선택
```

### 파일 업로드 설정
```properties
Globals.fileStorePath = C:/egovframework/upload/
Globals.fileUpload.Extensions = .gif.jpg.jpeg.png.xls.xlsx
Globals.fileUpload.maxSize = 1048576
```

### 로그인 제한 설정
```properties
Globals.login.Lock = true
Globals.login.LockCount = 5
```