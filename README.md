#!/bin/bash

#Author: Emile, June 13 2022

sudo yum install java-1.8.0-openjdk-devel -y

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

# Enable the Jenkins repository

sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

#Install the latest stable version of Jenkins

sudo yum install jenkins -y

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

# Start the Jenkins service#
 sudo systemctl start jenkins

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

sudo firewall-cmd --reload

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

sudo yum install java-1.8.0-openjdk-devel -y

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

# Enable the Jenkins repository

sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

sudo sed -i 's/gpgcheck=1/gpgcheck=0/g' /etc/yum.repos.d/jenkins.repo

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

#Install the latest stable version of Jenkins

sudo yum install jenkins -y

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

# Start the Jenkins service#
 sudo systemctl start jenkins

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

## Script to open necessary port for Jenkins

sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

sudo firewall-cmd --reload

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

## Setting up Jenkins in the browser
  # install utilities to display web page
    sudo yum install curl wget lynx w3m elinks -y

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi
   # Provide Initial Admin Password to user
     echo "Copy Password to login as Admin to Jenkins page"
       sudo cat /var/lib/jenkins/secrets/initialAdminPassword
          sleep 30

if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi

   # opening Jenkins page from the browser

   elinks  http://192.168.56.32:8080
  
   if [ $? -ne 0 ]
then
echo "Installation failed, please check the error and try again"
exit 1
fi