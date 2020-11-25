# Nebula Graph Studio

Nebula Graph Studio (Studio for short) is a web-based visualization tool for Nebula Graph. With Studio, you can create a graph schema, import data, edit nGQL statements for data queries, and explore graphs in one stop.

![Screenshot of Studio user interface](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-025.png "Studio user interface")

## Start Docker-based Studio

To start Docker-based Studio for Nebula Graph v1.x or v2.0.0, run these commands:

1. Clone the `nebula-web-docker` repo.

    ```bash
    git clone git@github.com:vesoft-inc/nebula-web-docker.git
    ```

2. Change the directory:
   - For Nebula Graph v2.0.0, run `cd nebula-web-docker/v2`.
   - For Nebula Graph v1.x, run `cd nebula-web-docker`.

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

## Connect to Nebula Graph

To connect to Nebula Graph v2.0.0:

1. Make sure that Nebula Graph 2.0.0 is deployed. For more information, see [Deploy Nebula Graph with Docker Compose](https://docs.nebula-graph.io/2.0/2.quick-start/2.deploy-nebula-graph-with-docker-compose/ "Click to go to Nebula Graph website") or [Install Nebula Graph by compiling the source code](https://docs.nebula-graph.io/2.0/4.deployment-and-installation/2.compile-and-install-nebula-graph/1.install-nebula-graph-by-compiling-the-source-code/ "Click to go to Nebula Graph website").
   > **NOTE**: If you deployed Nebula Graph 2.0.0-alpha with Docker Compose, run `docker-compose pull && docker-compose up -d` to update the Docker image.
2. Connect to Nebula Graph v2.0.0. For more information, see [Nebula Graph Studio User Guide](https://docs.nebula-graph.io/1.1/nebula-studio/install-configure/st-ug-connect/ "Click to go to Nebula Graph website").

To connect to Nebula Graph v1.x:

1. Make sure that Nebula Graph 1.x is deployed. For more information, see [Nebula Graph Manual](https://docs.nebula-graph.io/1.1/manual-EN/3.build-develop-and-administration/1.build/1.build-source-code/ "Click to go to Nebula Graph website").
2. Connect to Nebula Graph v1.x. For more information, see [Nebula Graph Studio User Guide](https://docs.nebula-graph.io/1.1/nebula-studio/install-configure/st-ug-connect/ "Click to go to Nebula Graph website").

## Documentation

Watch [this video](https://www.youtube.com/watch?v=kWg47hn_4Lo "Click to go to Youtube") to learn Nebula Graph Studio in two minutes.

For more information about Studio, see:

- [User Guide](https://docs.nebula-graph.io/1.1/nebula-studio/about-studio/st-ug-what-is-graph-studio/)
- [用户手册](https://github.com/vesoft-inc/nebula-docs-cn/blob/master/nebula-studio/st-ug-toc.md)

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
