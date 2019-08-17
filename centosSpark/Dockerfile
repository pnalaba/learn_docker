FROM centos:7.4.1708

#install java8
RUN yum install -y git java-1.8.0-openjdk which wget
RUN echo 'export JAVA_HOME=/usr/lib/jvm/jre-1.8.0-openjdk' | tee -a /etc/profile
RUN echo 'export JRE_HOME=/usr/lib/jvm/jre' | tee -a /etc/profile

#install spark
RUN cd /opt && \ 
 wget https://archive.apache.org/dist/spark/spark-2.3.1/spark-2.3.1-bin-hadoop2.7.tgz &&\ 
 tar -xzf spark-2.3.1-bin-hadoop2.7.tgz && \  
 ln -s /opt/spark-2.3.1-bin-hadoop2.7 /opt/spark && \ 
 rm spark-2.3.1-bin-hadoop2.7.tgz

RUN echo "export SPARK_HOME=/opt/spark" | tee -a /etc/profile
RUN echo 'export PATH=$PATH:$SPARK_HOME/bin' | tee -a /etc/profile
#install sbt
RUN curl https://bintray.com/sbt/rpm/rpm | tee /etc/yum.repos.d/bintray-sbt-rpm.repo
RUN yum install -y sbt
#install scala
RUN cd /tmp/ && wget http://downloads.lightbend.com/scala/2.11.8/scala-2.11.8.rpm && \ 
   yum install -y scala-2.11.8.rpm && rm -f /tmp/scala-2.11.8.rpm 
#install system
RUN yum install -y initscripts
#install elasticsearch
RUN cd /tmp && wget https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-1.7.3.noarch.rpm && \ 
  rpm -ivh elasticsearch-1.7.3.noarch.rpm
RUN systemctl enable elasticsearch.service
RUN service elasticsearch start
#install node
RUN curl -sL https://rpm.nodesource.com/setup_10.x | bash -
RUN yum install -y nodejs

#create user mapr
RUN yum install -y openssl sudo screen
RUN useradd -rm -d /home/mapr -s /bin/bash -G wheel -p "$(openssl passwd -1 mapr)"  mapr
USER mapr
WORKDIR /home/mapr
CMD ["source", "/etc/profile"]


CMD ["/bin/bash"]
