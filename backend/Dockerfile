# 실행 전제:
# 컨테이너 밖(EC2 또는 로컬)에서 먼저 ./gradlew bootJar 로 JAR를 빌드해 둔다.

FROM eclipse-temurin:17-jre-alpine

# 애플리케이션이 실행될 작업 디렉터리
WORKDIR /app

# 미리 빌드된 Spring Boot JAR 파일을 컨테이너 안으로 복사
# build/libs 안에 *.jar (예: backend-0.0.1-SNAPSHOT.jar) 가 있어야 한다.
COPY build/libs/*.jar app.jar

# 외부에서 접근할 포트
EXPOSE 8080

# 스프링 부트 애플리케이션 실행
ENTRYPOINT ["java", "-jar", "app.jar"]