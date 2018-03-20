# Start with mapr 5.2 image
FROM mengdong/mapr-pacc-mxnet:5.2.2_3.0.1_ubuntu16_yarn_fuse_hbase_streams_flask_client
MAINTAINER Dong Meng <mengdong0427@gmail.com>

RUN sudo pip install easydict scipy tensorflow sklearn scikit-image && \
    echo 'LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/opt/mapr/lib:/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/amd64/server/"' >> /etc/environment

WORKDIR /tmp/mapr-streams-mxnet-face/consumer/deploy
CMD python new_face_producer.py --groupid $GROUPID --gpuid $GPUID --readstream $READSTREAM \
                            --writestream $WRITESTREAM --threshold $THRESHOLD --writetostream $WRITETOSTREAM \
                            --writetopic $WRITETOPIC --readtopic $READTOPIC \ 
                            --timeout $TIMEOUT --port $PORT --filename $FILENAME


