# Change Log

## 2020.4.23 - v1.0.4-beta

- 优化：
  - 支持移除已探索出的点
  - 支持同时选择多条边进行探索
  - 支持同时点击选中多个点的操作：click + 按住cmd/win
- 其他：
  - 修复一些体验上的反馈## 2020.1.16 - v1.0.0-beta

- 功能：
  - 控制台
  - 导数据
  - 可视化
- [用户手册](nebula-graph-studio-user-guide-cn.md)

## 2020.4.15 - v1.0.3-beta

- 功能
  - 导入功能优化, 支持将Studio部署在远端，用户可以从本地访问并导入数据，不再限制导入数据必须与服务共同部署在本机
  - 图探索节点拓展，支持用户选择正反向查询节点，选择拓展出新节点的颜色显示逻辑(步骤or类型)
- 不兼容变更
  - 为了适应项目可以远端部署，修改了文件结构[仓库](https://github.com/vesoft-inc/nebula-web-docker)有更新，需要拉取最新代码：`git pull origin master && docker-compose pull`

## 2020.3.31 - v1.0.2-beta

- 功能
  - 图探索增加边属性显示及点标记配置

## 2020.3.2 - v1.0.1-beta

- 优化：
  - 支持控制台执行是space选择和缓存
  - 控制台多行编辑器显示

## 2020.1.16 - v1.0.0-beta

- 功能：
  - 控制台
  - 导数据
  - 可视化
- [用户手册](nebula-graph-studio-user-guide-cn.md)
