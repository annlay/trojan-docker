FROM centos:8
ARG password="demo_password"

RUN   yum makecache 
RUN rm -rf /etc/yum.repos.d/*.repo && \
    curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-8.repo 
RUN   yum makecache 
RUN   yum update -y 
RUN   yum install -y yum-utils epel-release gnutls-bin gnutls-doc
    
RUN mkdir -p /usr/local/bin && \
    mkdir -p /usr/local/etc/trojan/cert/

ADD ./script/trojan /usr/local/bin/trojan
ADD ./etc/config.json /usr/local/etc/trojan/config.json
RUN sed -i "s/YOUR_PASSWORD/${password}/g" /usr/local/etc/trojan/config.json

RUN echo "alias ll='ls -alF'" >> /root/.bashrc
EXPOSE 443
WORKDIR /usr/local/etc/trojan/
CMD [ "/usr/local/bin/trojan", "/usr/local/etc/trojan/config.json" ]
