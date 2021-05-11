# https://github.com/elastic/elasticsearch-docker
ARG elk_version
#FROM docker.elastic.co/beats/filebeat-oss:${elk_version}
FROM docker.elastic.co/beats/filebeat:${elk_version}

# Add your elasticsearch plugins setup here
# Example: RUN elasticsearch-plugin install analysis-icu
USER root
RUN usermod -aG root filebeat
USER filebeat
#RUN mkdir -p /logs/{mm,ma,sr} && chown -R filebeat:filebeat /logs/{mm,ma,sr}
