FROM andychentw/ssh-pass:latest

WORKDIR /app

ARG JAR_FILE=target/*jar
ARG remoteJarName=fromComposeFile.jar
ARG remoteIp=192.168.130.91
ARG commJarName=itms-api-2.0.0.psql-SNAPSHOT.jar

COPY ${JAR_FILE} build/${remoteJarName}
#COPY target target
#
#RUN cp target/comm-lib/${commJarName} build/${commJarName}
COPY target/comm-lib/${commJarName} build/${commJarName}

COPY docker/secret secret

COPY docker/script/backup_script.sh build/backup_script.sh
COPY docker/script/execute_script.sh build/execute_script.sh

RUN mkdir -p ~/.ssh

RUN ssh-keyscan $remoteIp >> ~/.ssh/known_hosts

ENTRYPOINT [ "sshpass" ,"-f", "secret", "rsync"]

CMD [ "--help" ]


