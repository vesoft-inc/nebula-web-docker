# 常见问题

**为什么我无法使用某个功能？**

如果发现您无法使用某个功能，建议您按以下步骤排除问题：

1. 确认 Nebula Graph 是最新版本。如果您使用 Docker Compose 部署 Nebula Graph 数据库，建议您运行 `docker-compose pull && docker-compose up -d` 拉取最新的 Docker 镜像，并启动容器。
2. 确认 Studio 是最新版本。具体操作，参考 [版本更新](st-ug-check-updates.md)。
3. 搜索 [论坛](https://discuss.nebula-graph.com.cn/) 或 GitHub 的 [nebula](https://github.com/vesoft-inc/nebula) 和 [nebula-web-docker](https://github.com/vesoft-inc/nebula-web-docker/issues) 项目，确认是否已经有类似的问题。
4. 如果上述操作均未解决您的问题，欢迎您在论坛上提交问题。

**Studio 支持 Nebula Graph V2.0 pre 吗？**

不支持。目前 Studio 仅支持 Nebula Graph V1.1.0 及以下版本。
