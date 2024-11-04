FROM ubuntu:20.04

RUN apt-get update && \
    apt-get install openssh-server -y

RUN mkdir /var/run/sshd
RUN echo 'root:senha' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

CMD ["/usr/sbin/sshd", "-D"]
