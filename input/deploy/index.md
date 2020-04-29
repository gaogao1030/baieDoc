# 部署文档(React on Kubernetes)

正式环境依旧维持原样部署方式

**本地推镜像发布操作指令**: ```bash update-image.sh [env]```

如果本地已经 build 过了，可以执行 NO_BUILD=true bash update-image.sh [env]

## 准备事项说明

### 需准备的项目文件模版

先执行 ```docker login registry.gitlab.meiguipai.com``` 输入 gitlab 的账号和密码登录

将以下的模版文件拷贝至项目内(文件名保持一致)

* [Dockerfile](./Dockerfile.html)

* [Local.DockerFile](./Local.Dockerfile.html)

* [.dockerignore](./dockerignore.html)

* [.gitlab-ci.yml](./gitlab-ci.yml.html)

* [update-image.sh](./update-image.sh.html) 需替换 image, project_id 和 token 变量

### 获取项目镜像地址

```进入项目所在的 gitlab 地址 -> Packages -> Container Registry ```将其镜像地址拷贝并填入 update-image.sh 中的 image 变量。

### 生成 Pipline trigger 以及获取 Pipline token (用于调用 Pipline trigger API 发布)

```进入项目所在的 gitlab 地址 -> settings -> CI/CD -> Pipelines triggers```, 填写描述说明后添加，将其生成的 token 记录下来，填入 update-image.sh 中的 token 变量。

### 获取 project_id

```进入项目所在的 gitlab 地址 -> Project overview ``` 项目 title 下就有 Project ID。

### 配置 CI/CD 变量

```进入项目所在的 gitlab 地址 -> settings -> CI/CD -> variables```

* CI\_ENVIRONMENT\_URL: 此项为填写的域名地址, 若有多个环境对应不同域名的话需重复填写并且以 Scope 进行区分, 例如测试的域名所对应的 Scope 为 beta。环境对应说明(测试: beta, 预发: release, 灰度: pre_production, 生产: production)

* KUBE\_NAMESPACE: Kubernetes 的项目命名空间,该 Scope 为 All environments, 所有环境下的项目均在该命名空间下(注意: Kubernetes 的命名空间不支持大小写命名), 所以在此推荐个命名范例: 例如 ReactBaieB2B 则推荐为 react-baie-b2b.

## 部署触发说明

部署方式分为全自动和半自动发布方式。

**全自动**: ```服务器上构建镜像 -> 执行 Kubernetes 的操作脚本更新其镜像```

**半自动**: ```本地构建镜像 -> 执行 Kubernetes 的操作脚本更新其镜像```

全自动的方式在服务器上构建镜像由于是在 docker in docker 中构建，所以每次构建都是在全新的环境内不具备上一次的已构建完成的镜像缓存其所需时间相比本地构建镜像较长，但其可靠性更高，适用场景相对不频繁发布。而本地发布适用于频繁发布的场景。

### 全自动发布方式

#### 分支触发

* 测试分支触发正则表达式: ```/^f_(.*)_beta$/```

* 预发分支触发正则表达式: ```/^f_(.*)_release$/```

* 灰度分支触发正则表达式: ```/^f_(.*)_pre_production$/```

### 半自动发布方式

### Pipiline trigger 触发
```
curl -X POST \
  -F token=$token \
  -F "ref=${branch}" \
  -F "variables[LOCAL_DEPLOY]=true" \
  -F "variables[CI_ENVIRONMENT_SLUG]=${ENV}" \
  https://gitlab.meiguipai.com/api/v4/projects/13/trigger/pipeline
```
**备注: 该步骤已经封装至 update-image.sh 脚本内**
