FROM ubuntu:16
ARG password="demo_password"

RUN apt get update -y && \
    yum apt get -y yum-utils epel-release gnutls-bin gnutls-doc
    
RUN mkdir -p /usr/local/bin && \
    mkdir -p /usr/local/etc/trojan/cert/

ADD ./script/trojan /usr/local/bin/trojan
ADD ./etc/config.json /usr/local/etc/trojan/config.json
RUN sed -i "s/YOUR_PASSWORD/${password}/g" /usr/local/etc/trojan/config.json

RUN echo "alias ll='ls -alF'" >> /root/.bashrc
EXPOSE 443
WORKDIR /usr/local/etc/trojan/
CMD [ "/usr/local/bin/trojan", "/usr/local/etc/trojan/config.json" ]
