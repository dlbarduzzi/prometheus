# prometheus

This repository contains information about how to run a [Prometheus monitoring](https://prometheus.io/) in your local machine with [docker-compose](https://docs.docker.com/compose/).

## Running docker-compose

Start the container with docker-compose.

```sh
# Add `-d` to the end of the command to run the container in the background.
docker-compose up
```

### Running prometheus with docker command

```sh
docker run \
    --name prometheus-lab \
    --restart always \
    -v $(pwd)/config:/etc/prometheus \
    -v $(pwd)/alerts:/etc/prometheus/alerts \
    -v prometheus_data:/prometheus \
    -p 9090:9090 \
    prom/prometheus --config.file=/etc/prometheus/prometheus.yml --web.enable-lifecycle
```

## Reload prometheus configs

If you make any changes to the configs or alerts file, you can reload the prometheus configs by running the command below.

```sh
curl -v -X POST http://localhost:9090/-/reload
```

## License

MIT License
