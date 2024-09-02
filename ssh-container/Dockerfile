FROM debian:bookworm

RUN apt update && apt install -y openssh-server

RUN sed -i 's/#LogLevel INFO/LogLevel VERBOSE/' /etc/ssh/sshd_config
RUN echo 'PermitUserEnvironment yes' >> /etc/ssh/sshd_config
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
RUN sed -i 's/#LogLevel INFO/LogLevel VERBOSE/' /etc/ssh/sshd_config
RUN adduser --disabled-password admin
RUN usermod -aG sudo admin
RUN echo 'admin:admin123123' | chpasswd
RUN cp /etc/ssh/sshd_config /config
RUN mkdir /run/sshd
RUN chmod 0755 /run/sshd
CMD ssh-keygen -A && /usr/sbin/sshd -f /config -D -e