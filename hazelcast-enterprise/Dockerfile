FROM java:8-jre-alpine
ENV HZ_VERSION 3.6.4
ENV HZ_HOME /opt/hazelcast/

RUN \
  apk add --no-cache --virtual build-dependencies aria2 unzip && \
  mkdir -p /opt && cd /opt && \
  aria2c -x16 -s16 -k1M -o hz.zip http://download.hazelcast.com/enterprise/hazelcast-enterprise-$HZ_VERSION.zip && \
  unzip -q hz.zip && \
  rm -f hz.zip && \
  mv hazelcast-enterprise-$HZ_VERSION hazelcast && \
  apk del build-dependencies

ADD server.sh $HZ_HOME/server.sh
RUN chmod +x $HZ_HOME/server.sh

WORKDIR $HZ_HOME
CMD ./server.sh

EXPOSE 5701
