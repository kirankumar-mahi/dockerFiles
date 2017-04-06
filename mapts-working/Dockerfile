# Start with mapr 5.2 image
FROM maprtech/mapr-1base-hivespark:5.2.0
MAINTAINER Dong Meng <mengdong0427@gmail.com>

RUN unlink /etc/localtime && ln -s /usr/share/zoneinfo/America/Los_Angeles /etc/localtime
# Install build-essential, git, wget and other dependencies
RUN yum update -y && yum install -y \
    git \
    wget \
    mapr-nfs \
    mapr-hbase \
    mapr-kafka \
    mapr-kafka-0.9.0 \
    gnuplot \
    unzip \
    supervisor \
    ntp && \
  mkdir /mapr && \
  cd /root && \
  wget https://github.com/OpenTSDB/opentsdb/releases/download/v2.3.0/opentsdb-2.3.0.rpm && \
  rpm -ivh /root/opentsdb-2.3.0.rpm && \
  cp /usr/share/opentsdb/etc/init.d/opentsdb /usr/share/opentsdb/etc/init.d/opentsdb.orig && \
  sed -i -e 's/^USER=.*$/USER=mapr/' /etc/init.d/opentsdb && \
  mkdir /var/log/opentsdb && \
  chmod 755 /var/log/opentsdb && \
  chown mapr:mapr /var/log/opentsdb
 
RUN cd /home/mapr && su mapr -c "git clone https://github.com/mengdong/maprts-docker-jars.git"

