FROM jenkins/jenkins:jdk17

USER root
RUN apt-get update 
RUN apt-get install software-properties-common -y
RUN apt-add-repository ppa:ansible/ansible
RUN apt-get install ansible -y
RUN apt-get install sshpass -y
USER jenkins