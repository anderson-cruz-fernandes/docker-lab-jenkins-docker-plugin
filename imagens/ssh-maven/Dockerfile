FROM maven:3.5.4-jdk-8-alpine
MAINTAINER Equipe SAOPS "saops@tre-es.jus.br"

EXPOSE 22
ENTRYPOINT ["/entrypoint.sh"]

RUN apk --update add openssh \
  && sed -i s/#PermitRootLogin.*/PermitRootLogin\ yes/ /etc/ssh/sshd_config \
  && echo "root:root" | chpasswd \
  && rm -rf /var/cache/apk/*

COPY rootfs/entrypoint.sh /
RUN chmod +x /entrypoint.sh
ADD .m2 /root/.m2