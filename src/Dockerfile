FROM node:16-alpine as builder 
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
#1. build stage : From 부터 다음 From 까지는 빌더 단계임을 명시적으로 표시
#2. run stage : nginx 가동
# /app/build : build에서 생성된 파일들이 여기에 들어감
# /usr/share/nginx/html : 이장소로 build에서 생성한 파일을 옮기고 nginx가 이곳에 있는 파일들을 제공해줌