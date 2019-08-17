FROM dsmodernization_base:latest
VOLUME ["/user/mapr/projects/SparkStreaming/"]

RUN echo '\
    . /etc/profile ; \
 ' >> ~/.profile

RUN mkdir projects && cd projects
RUN git clone https://github.com/pnalaba/DeployDemo ~/projects/DeployDemo 

CMD ["/bin/bash"]
