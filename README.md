# Nebula Graph Studio

<br> English | <a href="README-CN.md">中文</a><br/>

Nebula Graph Studio (Studio for short) is a web-based visualization tool for Nebula Graph. With Studio, you can create a graph schema, import data, edit nGQL statements for data queries, and explore graphs in one stop.

![Screenshot of Studio user interface](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-025.png "Studio user interface")

## Deploy

### docker-compose

To start Docker-based Studio for Nebula Graph v1.x or v2.x, run these commands:

1. Clone the `nebula-web-docker` repo.

    ```bash
    git clone https://github.com/vesoft-inc/nebula-web-docker.git
    ```

2. Select the proper version:

| git branch | nebula version|
| --- | --- |
| master | latest |
| v2 | 2.0 GA |
| v2-rc | 2.0-rc |
| v1 |  1.x |
```
// when use nebula 2.0 ga
git checkout v2
```

3. Pull the docker image of Studio.

    ```bash
    docker-compose pull
    ```

4. Build and start Docker-based Studio. `-d` is specified to run the containers in the background.

    ```bash
    docker-compose up -d
    ```
  
    If these lines return, Docker-based Studio is deployed and started.

    ```bash
    Creating docker_importer_1 ... done
    Creating docker_client_1   ... done
    Creating docker_web_1      ... done
    Creating docker_nginx_1    ... done
    ```

On Chrome, enter `localhost:7001` to get access to Studio. When a page as follows appears, Studio starts successfully.

![The Config Server page shows that Docker-based Studio is started successfully](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-052.png "Docker-based Studio is started")

5. Stop Server
```
$ docker-compose down
```

### RPM
| package | nebula version|
| ----- | ----- |
| [nebula-graph-studio-2.2.0-1.x86_64.rpm](https://oss-cdn.nebula-graph.io/nebula-graph-studio/nebula-graph-studio-2.2.0-1.x86_64.rpm) |  2.0.1 |
| [nebula-graph-studio-2.1.9-1.x86_64.rpm](https://oss-cdn.nebula-graph.io/nebula-graph-studio/nebula-graph-studio-2.1.9-1.x86_64.rpm) |  2.0 GA |
| [nebula-graph-studio-1.2.7-2.x86_64.rpm](https://oss-cdn.nebula-graph.io/nebula-graph-studio/nebula-graph-studio-1.2.7-1.x86_64.rpm) |  1.x |

#### Env Dependencies
- Node.js (v10.16.0 +)
- lsof

#### Setup
```
$ sudo rpm -i nebula-graph-studio-2.2.0-1.x86_64.rpm
```

#### Remove
```
$ sudo rpm -e nebula-graph-studio-2.2.0-1.x86_64.rpm
```

#### Some Scripts
```
// start server by hand
$ bash /usr/local/nebula-graph-studio/scripts/start.sh

// kill server by hand
$ bash /usr/local/nebula-graph-studio/scripts/stop.sh
```
## Connect to Nebula Graph

To connect to Nebula Graph v2.x:

1. Make sure that Nebula Graph 2.x is deployed. For more information, see [Deploy Nebula Graph with Docker Compose](https://docs.nebula-graph.io/2.0/2.quick-start/2.deploy-nebula-graph-with-docker-compose/ "Click to go to Nebula Graph website") or [Install Nebula Graph by compiling the source code](https://docs.nebula-graph.io/2.0/4.deployment-and-installation/2.compile-and-install-nebula-graph/1.install-nebula-graph-by-compiling-the-source-code/ "Click to go to Nebula Graph website").
   > **NOTE**: If you deployed Nebula Graph 2.0.0-alpha with Docker Compose, you must clone the nebula-docker-compose repository to update the Docker configuration.
2. Connect to Nebula Graph v2.x. For more information, see [Nebula Graph Studio User Guide](https://docs.nebula-graph.io/2.0.1/nebula-studio/install-configure/st-ug-connect/ "Click to go to Nebula Graph website").

To connect to Nebula Graph v1.x:

1. Make sure that Nebula Graph 1.x is deployed. For more information, see [Nebula Graph Manual](https://docs.nebula-graph.io/1.2.1/manual-EN/3.build-develop-and-administration/1.build/1.build-source-code/ "Click to go to Nebula Graph website").
2. Connect to Nebula Graph v1.x. For more information, see [Nebula Graph Studio User Guide](https://docs.nebula-graph.io/1.2.1/nebula-studio/install-configure/st-ug-connect/ "Click to go to Nebula Graph website").

## Documentation

Watch [this video](https://www.youtube.com/watch?v=kWg47hn_4Lo "Click to go to Youtube") to learn Nebula Graph Studio in two minutes.

For more information about Studio, see:

- [User Guide](https://docs.nebula-graph.io/2.0.1/nebula-studio/about-studio/st-ug-what-is-graph-studio/ "Click to go to Nebula Graph website")
- [用户手册](https://docs.nebula-graph.com.cn/nebula-studio/about-studio/st-ug-what-is-graph-studio/ "Click to go to Nebula Graph website")

## Updates

Do a check of these documents for the latest updates to Studio:

- [Changelog](docs/CHANGELOG-en.md)
- [更新日志](docs/CHANGELOG-zh.md)

## Feedback

If you have any questions about Studio, please feel free to leave your feedback on [Nebula Graph Forum](https://discuss.nebula-graph.io/ "Click to go to Nebula Graph Forum").

## Contact

- Twitter: [@NebulaGraph](https://twitter.com/NebulaGraph)
- [Facebook page](https://www.facebook.com/NebulaGraph/)
- [LinkedIn page](https://www.linkedin.com/company/vesoft-nebula-graph/)
- [Slack channel](https://join.slack.com/t/nebulagraph/shared_invite/enQtNjIzMjQ5MzE2OTQ2LTM0MjY0MWFlODg3ZTNjMjg3YWU5ZGY2NDM5MDhmOGU2OWI5ZWZjZDUwNTExMGIxZTk2ZmQxY2Q2MzM1OWJhMmY#)
- email: info@vesoft.com
