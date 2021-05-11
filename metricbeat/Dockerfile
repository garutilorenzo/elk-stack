# https://github.com/elastic/elasticsearch-docker
ARG elk_version
FROM docker.elastic.co/beats/metricbeat:${elk_version}
USER root
ARG DOCKER_GID=998
RUN groupadd -g ${DOCKER_GID} docker && \
    usermod -aG docker metricbeat
USER metricbeat