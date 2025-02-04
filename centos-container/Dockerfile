FROM centos:7

RUN cd /etc/yum.repos.d/ && \
    sed -i 's/mirrorlist/#mirrorlist/g' CentOS-* && \
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' CentOS-* && \
    yum update -y && \
    yum install -y openssh-server sudo && \
    yum clean all

RUN useradd iti && \
    echo "iti:1234" | chpasswd && \
    usermod -aG wheel iti

CMD /usr/sbin/sshd -D & bash
