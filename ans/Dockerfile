FROM ubuntu:24.04
RUN apt-get update
RUN apt-get install -y python3 net-tools openssh-server python3-pip iputils-ping

ADD sshd_config /etc/ssh/sshd_config

RUN mkdir -p /run/sshd

COPY ./keys/id_rsa.pub /home
COPY ./keys/id_rsa2.pub /home

RUN mkdir -p ~/ssh && \
	echo "$(cat home/id_rsa.pub)" >> ~/.ssh/authorized_keys && \
	echo "$(cat home/id_rsa2.pub)" >> ~/.ssh/authorized_keys && \
	chmod 600 ~/.ssh/authorized_keys
	
CMD ["/usr/sbin/sshd", "-D"]
