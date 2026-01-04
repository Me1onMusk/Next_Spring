# 1단계: Next.js 앱 빌드
FROM node:20-alpine AS builder

WORKDIR /app

# 패키지 정보 복사 후 의존성 설치
COPY package*.json ./
RUN npm install

# 나머지 소스 복사
COPY . .

# 프로덕션 빌드
RUN npm run build

# 2단계: 실행용 이미지
FROM node:20-alpine

WORKDIR /app

# 빌드 결과와 필요한 파일들 복사
COPY --from=builder /app ./

# Next.js 프로덕션 서버 실행
EXPOSE 3000

CMD ["npm", "start"]