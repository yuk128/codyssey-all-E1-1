# 베이스: 가벼운 nginx 웹 서버 이미지에서 시작
FROM nginx:alpine
# 이미지에 이름표(메타데이터)를 붙임
LABEL org.opencontainers.image.title="my-custom-nginx"
# 환경변수 설정 (설정값을 코드와 분리)
ENV APP_ENV=dev
# nginx 기본 페이지를 내 site 폴더의 페이지로 교체
COPY site/ /usr/share/nginx/html/