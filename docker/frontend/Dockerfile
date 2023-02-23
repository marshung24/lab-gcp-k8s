# Vue App編譯+包暈像檔 範本
# Mars.Hung 2022-10-05
# @todo 結合自定最佳化nginx.conf

# Build App Stage: Build Vue App by nodejs image.
FROM node:16-alpine as Build-App
RUN mkdir -p /app
WORKDIR /app
COPY . .
RUN npm ci && npm run build

# Production Inage Stage: Build Container Image, Data from pre-stage.
FROM nginx:stable-alpine as Production-image
RUN rm -rf /usr/share/nginx/html/*
COPY --from=Build-App /app/dist/* /usr/share/nginx/html/