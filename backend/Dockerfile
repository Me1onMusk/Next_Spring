# 1단계: Gradle로 Spring Boot JAR 빌드
FROM gradle:8.7-jdk17-alpine AS builder

WORKDIR /app

# Gradle 관련 파일 복사
COPY build.gradle settings.gradle gradlew ./
COPY gradle ./gradle

# 소스 복사
COPY src ./src

# Spring Boot JAR 빌드 (bootJar)
RUN ./gradlew bootJar --no-daemon

# 2단계: 실행용 JRE 이미지
FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

# 빌드된 JAR만 가져오기
COPY --from=builder /app/build/libs/*.jar app.jar

EXPOSE 8080

# 스프링 부트 실행
ENTRYPOINT ["java", "-jar", "/app/app.jar"]