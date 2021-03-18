# CUC-ACM-OJ-Front-End

**This repository is ARCHIVED on March 19th, 2021.**

用于OJ的二次开发。

Base on [QingdaoU/OnlineJudgeFE](https://github.com/QingdaoU/OnlineJudgeFE)

（原文件太大了fork后下载不到本地 (╯‵□′)╯︵┻━┻）

## Environment

- WSL2 Ubuntu 20.04.1 Server
- nodejs v8.12.0

## Use

```bash
npm install
# we use webpack DllReference to decrease the build time,
# this command only needs execute once unless you upgrade the package in build/webpack.dll.conf.js
export NODE_ENV=development 
npm run build:dll

# the dev-server will set proxy table to your backend
export TARGET=http://Your-backend

# serve with hot reload at localhost:8080
npm run dev
```

## Pack to Docker Image

```bash
# Delete changes on original docker-compose.yml
docker pull registry.cn-hangzhou.aliyuncs.com/onlinejudge/oj_backend
NODE_ENV=production npm run build:dll
npm run build
docker cp ./dist CONTAINERID:/app/

# push to Aliyun
sudo docker images
sudo docker login --username=lyulumos registry.cn-hangzhou.aliyuncs.com
sudo docker tag [ImageId] registry.cn-hangzhou.aliyuncs.com/lyulumos/cuc-acmoj:[镜像版本号]
sudo docker push registry.cn-hangzhou.aliyuncs.com/lyulumos/cuc-acmoj:[镜像版本号]
```
