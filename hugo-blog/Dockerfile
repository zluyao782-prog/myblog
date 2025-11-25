# 第一阶段：构建 Hugo 站点
FROM floryn90/hugo:latest-ext AS builder
WORKDIR /src
COPY . .
# 生成静态文件到 /src/public
RUN hugo --minify
# 第二阶段：Nginx 运行环境
FROM nginx:alpine
# 复制 Hugo 生成的静态文件
COPY --from=builder /src/public /usr/share/nginx/html
# 暴露 80 端口
EXPOSE 80
# 使用默认的 Nginx 配置
CMD ["nginx", "-g", "daemon off;"]
