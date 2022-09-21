FROM andychentw/ssh-pass:latest

WORKDIR /app

ARG remoteIp=192.168.130.91

RUN mkdir -p ~/.ssh
RUN ssh-keyscan $remoteIp >> ~/.ssh/known_hosts

COPY docker/secret secret

ENTRYPOINT [ "sshpass" ,"-f", "secret"]
