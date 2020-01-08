# Nebula Console 工具 - 镜像启动手册
## 环境准备
- [docker 环境](https://docs.docker.com/v17.09/engine/installation/)
- Nebula数据库
  - 本地启动:
    - 镜像启动：[教程](https://github.com/vesoft-inc/nebula-docker-compose)
  - 远程：
    - 服务地址 及 相应账号密码：Host、Username、Password
  - 更多信息：[Nebula](https://github.com/vesoft-inc/nebula)

- 操作文件目录配置
  - 配置环境变量 [WORKING_DIR](./.env)

- 浏览器: [Chrome](https://www.google.com/intl/zh-CN/chrome/)

## 启动
```shell
docker-compose up
```

## 停止/清除
```shell
docker-compose down
```

## 应用访问
http://0.0.0.0:7001

## 更多
[用户手册](https://www.yuque.com/nebulagraph/bh6cky/kx7aug)
[测试数据](./example/follow.csv)

## 常见问题
- 建立数据库连接时: 即使是本机数据库，不要使用`127.0.0.1:3699`地址，请使用真实ip，应用运行在独立的网络环境需要真实ip寻址。
