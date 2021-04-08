#!/bin/bash
 sudo yum update -y
 sudo yum install docker -y
 sudo systemctl start docker
 sudo systemctl enable docker
 sudo yum install git -y
 sudo chown -R ec2-user:ec2-user /opt
 cd /opt
 wget https://github.com/AdoptOpenJDK/openjdk8-binaries/releases/download/jdk8u275-b01/OpenJDK8U-jdk_x64_linux_hotspot_8u275b01.tar.gz
 tar -zxvf OpenJDK8U-jdk_x64_linux_hotspot_8u275b01.tar.gz
 rm -rf OpenJDK8U-jdk_x64_linux_hotspot_8u275b01.tar.gz
 mv jdk8u275-b01/ java8
 wget https://mirrors.estointernet.in/apache/tomcat/tomcat-8/v8.5.61/bin/apache-tomcat-8.5.61.tar.gz
 tar -zxvf  apache-tomcat-8.5.61.tar.gz
 rm -rf apache-tomcat-8.5.61.tar.gz
 mv apache-tomcat-8.5.61/ tomcat8
 wget https://mirrors.estointernet.in/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
 tar -zxvf apache-maven-3.6.3-bin.tar.gz
 rm -rf apache-maven-3.6.3-bin.tar.gz
 mv apache-maven-3.6.3/ maven3
 sudo chmod 007 /etc/profile
 echo "export JAVA_HOME=/opt/java8" >> /etc/profile
 echo "export PATH=$PATH:/opt/java8/bin" >> /etc/profile
 echo "export M2_HOME=/opt/maven3" >> /etc/profile
 echo "export PATH=$PATH:/opt/maven3/bin" >> /etc/profile
 source /etc/profile
 cd
 sudo chown -R ec2-user:ec2-user /opt
 cd /opt
 cd tomcat8/
 cd webapps/
 wget https://updates.jenkins-ci.org/download/war/2.274/jenkins.war
 sudo yum install fontconfig -y
 cd ..
 cd bin/
 sh startup.sh
