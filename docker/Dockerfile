FROM floryn90/hugo:latest AS builder

COPY . /src

RUN hugo

FROM nginx:alpine

COPY --from=builder /src/public /usr/share/nginx/html

EXPOSE 80
