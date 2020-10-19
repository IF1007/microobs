# MicroObs

## Goals
* Make use of the API Gateway pattern to facilitate the consumption of observability data by interested (or external) parties;
* Offer an easy to use observability system for microservices based on containers that encompasses the main observability concerns like logs and metrics.

## Usage

Right now, the gateway image must be manually built before using docker-compose. That can be accomplished by running the following commands:
```sh
# clone the gateway repository
git clone https://github.com/microobs/gateway
cd dockprom

# build the image
sudo docker build -t api_gateway .
```

### API Gateway Configuration
The API Gateway uses the module [node-config](https://github.com/lorenwest/node-config) to load its settings like the url of the observability services. Those settings are load from a JSON file called default.json located at the [/config](https://github.com/microobs/gateway/blob/master/config/default.json) folder. To facilitate the load of custom settings, the folder [gateway-config](https://github.com/microobs/microobs/blob/master/gateway-config/default.json) has a JSON (same name and with the same settings as the one in the API gateway image) that can be used to do so. After editing, one just need to uncomment the volume section in the [docker-compose.yml](https://github.com/microobs/microobs/blob/master/docker-compose.yml) file under the gateway service section.

## Contribution
The project helped the creation of the open source JS module [Prom-GraphQL](https://github.com/carloszimm/prom-graphql) that as long as we know it's the first GraphQL wrapper on the Prometheus REST API.

## Acknowledgment
This project uses as a base the [dockprom](https://github.com/stefanprodan/dockprom) repository. Also, the [Grafana dashboard for Elasticsearch](https://github.com/monitoringartist/grafana-elasticsearch-dashboards) is used (with minor modification) as well.

## License
MicroObs is available under the MIT license. See the [LICENSE](https://github.com/microobs/microobs/blob/master/LICENSE) file for more info.
