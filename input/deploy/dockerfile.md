## Dockerfile
```
FROM node:10.17.0-alpine3.10 as builder

ARG BASIC_USER
ARG BASIC_PASS
ARG APP_ENV

WORKDIR /app

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
    echo "151.101.0.133 raw.githubusercontent.com" >> /etc/hosts

RUN apk add --no-cache wget git

COPY package*.json /app/

RUN npm install

COPY ./ /app/

RUN wget --auth-no-challenge --http-user=${BASIC_USER} --http-passwd=${BASIC_PASS} --header="host: sign.baie.com.cn" http://47.112.222.92/${APP_ENV}.tar.gz -O - | tar -zx

RUN RELEASE_MODE=remote GENERATE_SOURCEMAP=false APP_ENV=${APP_ENV} npm run build

FROM registry.gitlab.meiguipai.com/gaogao1030/nginx:master

COPY --from=builder /app/build/ /usr/local/openresty/nginx/html
```
