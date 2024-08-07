FROM centos:8.2
ARG password="demo_password"

RUN yum makecache && \
    yum update -y && \
    yum install -y yum-utils epel-release gnutls-bin gnutls-doc
    
RUN mkdir -p /usr/local/bin && \
    mkdir -p /usr/local/etc/trojan/cert/

ADD ./script/trojan /usr/local/bin/trojan
ADD ./etc/config.json /usr/local/etc/trojan/config.json
RUN sed -i "s/YOUR_PASSWORD/${password}/g" /usr/local/etc/trojan/config.json

RUN echo "alias ll='ls -alF'" >> /root/.bashrc
EXPOSE 443
WORKDIR /usr/local/etc/trojan/
CMD [ "/usr/local/bin/trojan", "/usr/local/etc/trojan/config.json" ]
