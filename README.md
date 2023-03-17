# gitops_argocd_project

Step by step process

1. Set Up a Jenkins server 
Go to AWS and create a Ubuntu EC2 and then install the Jenkins using the following commands

First install JDK cause Jenkins runs on Java

sudo apt update -y
sudo apt install default-jre -y
java -version
sudo apt update -y
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update -y
sudo add-apt-repository universe -y
sudo apt-get install jenkins -y
sudo service jenkins start
cat /var/lib/jenkins/secrets/initialAdminPassword. 
You this password to login into Jenkins (By default it runs on Port 8080)

#sudo service jenkins status


