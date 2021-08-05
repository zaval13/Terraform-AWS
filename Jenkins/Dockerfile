FROM jenkins/jenkins:lts-jdk11
# change user to root
USER root
# install Ansible
RUN echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main" >> /etc/apt/sources.list
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
RUN apt update -y  && apt install -y ansible
# install terraform
COPY terraform /usr/local/bin
# copy aws key for ssh
COPY awskey.pem /var
# drop back to the regular jenkins user
USER jenkins
EXPOSE 8080
