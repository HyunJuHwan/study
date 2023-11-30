FROM jenkins/jenkins:lts
USER root
RUN apt-get update && \
apt-get -y install apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common && \
curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
    $(lsb_release -cs) \
    stable" && \
apt-get update && \
apt-get -y install docker-ce

RUN usermod -a -G docker jenkins

#---- sshpass
RUN apt-get -y install sshpass

#---- locale
RUN apt-get install -y locales git \
    && localedef -f UTF-8 -i ko_KR ko_KR.UTF-8
ENV LC_ALL ko_KR.UTF-8

USER jenkins

#ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false"
#ENV JENKINS_USER admin
#ENV JENKINS_PASS admin
#COPY plugins.txt /usr/share/jenkins/ref/

# COPY security.groovy /usr/share/jenkins/ref/init.groovy.d/
#COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/

# image 생성 단계에서 에러 발생하여 주석처리 
#RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
#RUN jenkins-plugin-cli --plugins "blueocean docker-workflow"
#RUN jenkins-plugin-cli --plugins < /usr/share/jenkins/ref/plugins.txt
