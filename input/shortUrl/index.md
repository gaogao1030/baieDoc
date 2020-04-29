# nodeShortUrl

短链接服务

## Framework

[Fastify](https://www.fastify.io)

## Requirements

* mysql

## Getting Started

1. npm install

2. npx sequelize db:create

3. npx sequelize db:migrate

4. node start.js

## 生成短链接接口

### 环境

测试环境: http://t.yunchuangfu.com

正式环境: http://t.moku.net

#### URL

> [http://t.yunchuangfu.com/api/v1/short_urls](http://t.yunchuangfu.com/api/v1/short_urls)

#### 请求方式

> post

#### 是否签名

> 否

#### 请求参数

| 字段名称   | 字段类型 | 说明                    |
| ---------- | -------- | ------------------------|
| url        | string   | 需要转换的长链接        |

#### 响应字段

```
{
  shortUrl: 'http://t.yunchuangfu.com/r4b43' // 短链接
  longUrl: 'http://www.bilibili.tv' // 原链接
}
```

## 部署部分

```
env = ['beta', 'production']
```

pm2 deploy ecosystem.config.js [env] deploy

* [pm2 deploy](http://pm2.keymetrics.io/docs/usage/deployment/)
