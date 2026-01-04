# 1단계: 빌드 단계
FROM node:20-alpine AS builder

WORKDIR /app

# 패키지 정보 복사
COPY package*.json ./

# 의존성 설치
RUN npm install

# 나머지 소스 복사
COPY . .

# Next.js 빌드
RUN npm run build

# 2단계: 실행 단계
FROM node:20-alpine

WORKDIR /app

# builder 단계 결과 복사
COPY --from=builder /app ./

EXPOSE 3000

# Next.js 프로덕션 서버 실행
CMD ["npm", "start"]