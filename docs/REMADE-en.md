# Nebula Console

## Enviroment Required
- [Docker](https://docs.docker.com/v17.09/engine/installation/)
- Nebula Server
  - local start:
    - [Nebula Docker](https://github.com/vesoft-inc/nebula-docker-compose)
  - remote host:
    - host、username、password required
  - more info: [Nebula](https://github.com/vesoft-inc/nebula) 
- File directory Path
  - [WORKING_DIR](./.env)

- Browser: [Chrome](https://www.google.com/intl/zh-CN/chrome/)

## Start
```shell
docker-compose up --quiet-pull
```

## Stop/Clear
```shell
docker-compose down
```

## Update
```shell
docker-compose pull
```

## Vist
http://0.0.0.0:7001


## More
[User Manual](https://www.yuque.com/nebulagraph/bh6cky/kx7aug)
[Sample Data](./example/follow.csv)

## FAQ
- Config Nebula Server: when use local nebula server, use the real ip host instead of `127.0.0.1:3699` due to the docker container isolated enviroment.