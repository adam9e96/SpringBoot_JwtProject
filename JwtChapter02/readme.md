# 챕터 2

이 프로젝트는 Spring Boot를 사용하여 기본적인 시큐리티 설정과 데이터 설정을 포함하고 있습니다. 주된 목적은 JWT를 이용한 인증 및 권한 부여를 구현하는 것입니다.

## 목적

- **JWT 인증**: JSON Web Token을 사용하여 사용자 인증을 처리합니다.
- **권한 부여**: 사용자에게 역할(Role)을 부여하고, 역할에 따라 접근 권한을 제어합니다.
- **보안 설정**: Spring Security를 사용하여 애플리케이션의 보안을 강화합니다.
- **데이터 관리**: H2 데이터베이스를 사용하여 사용자 및 권한 데이터를 관리합니다.

## 주요 기능

### 시큐리티 설정

- **CSRF 비활성화**: 토큰 기반 인증을 사용하기 때문에 CSRF 보호를 비활성화합니다.
- **HTTP 요청 권한 설정**:
  - `/api/hello`, `/api/authenticate`, `/api/signup` 경로는 모든 사용자에게 허용됩니다.
  - H2 콘솔 경로는 모든 사용자에게 허용됩니다.
  - 그 외의 모든 요청은 인증이 필요합니다.
- **세션 관리**: 세션을 사용하지 않기 때문에 세션 정책을 `STATELESS`로 설정합니다.
- **H2 콘솔 활성화**: H2 콘솔을 사용하기 위해 `frameOptions`를 `sameOrigin`으로 설정합니다.
- **JWT 설정**: `JwtSecurityConfig`를 사용하여 JWT 필터를 추가합니다.

### 데이터 설정

- **H2 데이터베이스**: 메모리 내 데이터베이스를 사용하여 데이터를 관리합니다.
- **초기 데이터 설정**: `data.sql` 파일을 통해 초기 사용자 및 권한 데이터를 설정합니다.

## 프로젝트 구조

- `src/main/java/com/adam9e96/JwtStudy/config/SecurityConfig.java`: 스프링 시큐리티 설정 파일
- `src/main/java/com/adam9e96/JwtStudy/controller/HelloController.java`: 간단한 REST 컨트롤러
- `src/main/java/com/adam9e96/JwtStudy/entity/User.java`: 사용자 엔티티
- `src/main/java/com/adam9e96/JwtStudy/entity/Authority.java`: 권한 엔티티
- `src/main/resources/application.properties`: 애플리케이션 설정 파일
- `src/main/resources/data.sql`: 초기 데이터 설정 파일