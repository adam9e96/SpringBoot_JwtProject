# 챕터 1

이 프로젝트는 Spring Boot를 사용하여 기본적인 시큐리티 설정과 데이터 설정을 포함하고 있습니다.

## 프로젝트 구조

- `src/main/java/com/adam9e96/JwtStudy/config/SecurityConfig.java`: 스프링 시큐리티 설정 파일
- `src/main/java/com/adam9e96/JwtStudy/controller/HelloController.java`: 간단한 REST 컨트롤러
- `src/main/java/com/adam9e96/JwtStudy/entity/User.java`: 사용자 엔티티
- `src/main/java/com/adam9e96/JwtStudy/entity/Authority.java`: 권한 엔티티
- `src/main/resources/application.properties`: 애플리케이션 설정 파일
- `src/main/resources/data.sql`: 초기 데이터 설정 파일

## 주요 기능

### 시큐리티 설정

- `/api/hello` 엔드포인트는 모든 사용자에게 허용됩니다.
- 그 외의 모든 요청은 인증이 필요합니다.
- HTTP Basic 인증을 사용합니다.

### 데이터 설정

- H2 데이터베이스를 사용하여 메모리 내 데이터베이스를 설정합니다.
- `data.sql` 파일을 통해 초기 데이터를 설정합니다.

## 설정 파일

### `application.properties`

```ini
spring.application.name=JwtStudy
# H2 콘솔 설정
spring.h2.console.enabled=true
# 데이터소스 설정
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driver-class-name=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
# JPA 설정
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=create-drop
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.properties.hibernate.show_sql=true
spring.jpa.defer-datasource-initialization=true
# JWT 설정
# 로깅 설정
logging.level.com.adam9e96=DEBUG