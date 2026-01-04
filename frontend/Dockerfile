FROM node:20-alpine

WORKDIR /app

# 빌드 결과물과 실행에 필요한 것만 복사
COPY .next ./.next
COPY public ./public
COPY package*.json ./

# 프로덕션 의존성만 설치
RUN npm install --omit=dev

EXPOSE 3000

CMD ["npm", "start"]