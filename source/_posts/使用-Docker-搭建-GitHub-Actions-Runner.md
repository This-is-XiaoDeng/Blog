---
title: Docker 搭建 GitHub Actions Runner 配置参考
date: 2023-10-04 09:01:34
categories: 教程
tags: Docker
---

> 我们相信您已经对 Docker 有了一定了解，如果没有，请自行百度。以下脚本为作者自用，仅供参考，不保证绝对的通用性

# Dockerfile

```dockerfile
FROM ubuntu:latest

# set the github runner version
ARG RUNNER_VERSION="2.309.0"

# update the base packages and add a non-sudo user
RUN apt-get update -y && apt-get upgrade -y && useradd -m docker &&\
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends curl libssl-dev python3 python3-pip\
    && cd /home/docker && mkdir actions-runner && cd actions-runner \
    && curl -O -L https://github.com/actions/runner/releases/download/v${RUNNER_VERSION}/actions-runner-linux-x64-${RUNNER_VERSION}.tar.gz \
    && tar xzf ./actions-runner-linux-x64-${RUNNER_VERSION}.tar.gz \
    && rm ./actions-runner-linux-x64-${RUNNER_VERSION}.tar.gz\
    && chown -R docker ~docker && /home/docker/actions-runner/bin/installdependencies.sh \
    && apt remove curl libssl-dev python3 python3-pip -y \
    && apt autoremove -y && apt clean\
    && apt-get update && apt-get install -y sudo lsb-release && apt-get clean all \
    && echo "docker ALL=(ALL:ALL)  NOPASSWD:ALL" >> /etc/sudoers \
    && sudo -u docker ./config.sh --url https://github.com/<YOUR_ORG_OR_REPO_HERE> --token <YOUR_TOKEN_HERE>

# since the config and run script for actions are not allowed to be run by root,
# set the user to "docker" so all subsequent commands are run as the docker user
USER docker

WORKDIR /home/docker/actions-runner

COPY start.sh start.sh

# set the entrypoint to the start.sh script
CMD ["/home/docker/actions-runner/start.sh"]

```

# start.sh

> 请在构建前确保此脚本有执行权限

```bash
#!/bin/sh

./run.sh
```

# reset.sh

> 请在开启自动重置前确认此脚本有执行权限

```bash
#!/bin/sh

# 定义容器和镜像的名称
CONTAINER_NAME="actions-runner"
IMAGE_NAME="actions-runner"

# 停止并删除容器（如果存在）
docker stop $CONTAINER_NAME
docker rm $CONTAINER_NAME

# 创建并启动新容器
docker run --name $CONTAINER_NAME -d $IMAGE_NAME

# 输出提示信息
echo "The container $CONTAINER_NAME has been reset."

```

# auto_reset.sh

> 自动重置脚本，需要 root 权限

```bash
while (true);
do
    ./reset.sh
    sleep 86400
done
```
