# Start with mapr 5.2 image
FROM mengdong/mapr-pacc-mxnet:5.2.2_3.0.1_ubuntu16_yarn_fuse_hbase_streams_flask 
MAINTAINER Dong Meng <mengdong0427@gmail.com>

RUN bin/bash && bash -c 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/mapr/lib:/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/amd64/server/' && \
    sudo pip install --global-option=build_ext --global-option="--library-dirs=/opt/mapr/lib" --global-option="--include-dirs=/opt/mapr/include/" http://package.mapr.com/releases/MEP/MEP-3.0/mac/mapr-streams-python-0.9.2.tar.gz



