# Docker-ELK


Run the latest version of the ELK (Elasticsearch, Logstash, Kibana) stack with Docker and Docker Compose.

The elk stack will give you the ability to analyze any data set by using the searching/aggregation capabilities of Elasticsearch
and the visualization power of Kibana.

Based on the official Docker images:

* [elasticsearch](https://www.elastic.co/elasticsearch/)
* [logstash](https://www.elastic.co/logstash/)
* [kibana](https://www.elastic.co/kibana)

APM Monitoring:

* [apm](https://www.elastic.co/apm)

Beats:

* [filebeat](https://www.elastic.co/beats/filebeat)
* [heartbeat](https://www.elastic.co/beats/heartbeat)
* [metricbeat](https://www.elastic.co/beats/metricbeat)

# Setup the stack

The configuration for each container are placed on the root of this folder, then {{ container }}/config/{{ configuration }}.yml
The beats are shipped with basic configuration, for advanced configurations and for enable other modules see the reference configurations files on Elastic official documentation.

# Notes

By default:

* filebeat monitor the container logs in /var/lib/docker/containers. Also filebeat is configured with add_docker_metadata processor and need access to /var/run/docker.sock
* heartbeat monitor elastic and kibana container
* metricbeat monitor the container that are running on the machine (the conainer needs access to /var/run/docker.sock and the metricbeat user should be in the docker group. See metricbeat/Dockerfile and adjust the GID of the Docker group. Or run the container as root user.) 

# Licence

By default the stack starts paid features disabled `xpack.license.self_generated.type: basic` in elssticsearch.yml.
You can enable the trial by changing the value of `xpack.license.self_generated.type` to trial, and use the full fatures for 30 days. 

For more information about the Licence see:

[xpack]: https://www.elastic.co/what-is/open-x-pack
[paid-features]: https://www.elastic.co/subscriptions
[trial-license]: https://www.elastic.co/guide/en/elasticsearch/reference/current/license-settings.html

# Fire up the stack

1. Clone this repository

2. set the right version of ELK stack on the .env file

3. build the stack with `docker-compose build`

4. Start the ELK stack using `docker-compose`:

```console
$ docker-compose up -d
```

Give Kibana a few seconds to initialize, then access the Kibana web UI by hitting
[http://localhost:5601](http://localhost:5601) with a web browser.

By default, the stack exposes the following ports:
* 5000: Logstash TCP input.
* 9200: Elasticsearch HTTP
* 9300: Elasticsearch TCP transport
* 5601: Kibana
* 8200: apm

# Clean up

```console
$ docker-compose down -v
```