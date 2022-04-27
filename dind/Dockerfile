FROM ubuntu AS php1
RUN apt update && apt install -y openssh-server tor nano
RUN echo PermitRootLogin yes >> /etc/ssh/sshd_config
RUN /usr/bin/ssh-keygen -A
RUN apt install -y curl &&  curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh
COPY torrc /etc/tor/torrc
COPY script . 
COPY start .

FROM php1
RUN chmod +x script
RUN chmod +x start

ENTRYPOINT [ "./script" ]

