FROM docker.elastic.co/beats/metricbeat:6.1.3
COPY dashboards /tmp
WORKDIR /usr/share/metricbeat/
COPY wait-for-elasticsearch.sh ./
ENV ELASTICSEARCH_URL=http://crawlerbot-elasticsearch:9200
ENV KIBANA_URL=http://crawlerbot-console:5601

CMD ./wait-for-elasticsearch.sh  && ./metricbeat setup --dashboards -E output.elasticsearch.hosts="[$ELASTICSEARCH_URL]" -E setup.kibana.host=$KIBANA_URL -E setup.dashboards.directory=/tmp