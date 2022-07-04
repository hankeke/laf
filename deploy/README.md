# 安装教程

### 快速部署 `laf`

> 基于 Docker Compose 快速部署，需要你熟悉 Docker 以及 Docker Compose 的使用。

##### 安装 Docker

- 安装 Docker: https://docs.docker.com/engine/install/
- 安装 Docker Compose: https://docs.docker.com/compose/install/

##### 启动服务（docker-compose）

```sh
git clone https://github.com/labring/laf.git

cd laf/deploy/docker-compose

docker network create laf_shared_network --driver bridge || true
docker pull lafyun/app-service:latest

# 启动所有服务
docker-compose up

# 浏览器打开 http://console.127-0-0-1.nip.io:8000 访问
```

### 开发环境（开发者）

```sh
# install dependencies
npm install

# build & watch packages
npm run build && npm run watch

# create a shared network in docker
docker network create laf_shared_network --driver bridge || true

# download the app service image
docker pull lafyun/app-service:latest

# launch laf.js services
docker-compose up

# Now open http://console.127-0-0-1.nip.io:8080 in your browsers!

```

## 测试用例

### 启动 MongoDB 测试容器

```sh
docker run --rm -p 27018:27017 --name mongotest -d mongo
```

### 运行测试

```sh
# 运行测试用例
npx mocha ./packages/*/tests/**/*.test.js

# 清除测试容器
docker rm -f mongotest
```
