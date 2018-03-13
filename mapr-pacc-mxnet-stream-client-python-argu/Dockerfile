# Start with mapr 5.2 image
FROM mengdong/mapr-pacc-mxnet:5.2.2_3.0.1_ubuntu16_yarn_fuse_hbase_streams_flask_client
MAINTAINER Dong Meng <mengdong0427@gmail.com>

RUN cd /tmp && git clone https://github.com/mengdong/mapr-streams-mxnet-face.git && \
    cd /tmp/mapr-streams-mxnet-face/consumer/deploy && \
    echo 'LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/opt/mapr/lib:/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/amd64/server/"' >> /etc/environment

WORKDIR /tmp/mapr-streams-mxnet-face/consumer/deploy
CMD python flask_consumer.py --groupid $GROUPID --stream $STREAM --topic $TOPIC --timeout $TIMEOUT --port $PORT


