# 1단계: Gradle로 Spring Boot JAR 빌드
FROM gradle:8.7-jdk17-alpine AS builder

# 컨테이너 안 작업 디렉터리
WORKDIR /app

# Gradle 설정 및 소스 전체 복사
COPY . .

# bootJar 실행 (스프링 부트 실행용 JAR 빌드)
RUN ./gradlew bootJar --no-daemon

# 2단계: JRE만 있는 가벼운 이미지로 실제 실행
FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

# 빌더 단계에서 만든 JAR만 가져오기
COPY --from=builder /app/build/libs/*.jar app.jar

# 외부로 노출할 포트
EXPOSE 8080

# 스프링 부트 애플리케이션 실행
ENTRYPOINT ["java", "-jar", "app.jar"]