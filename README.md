gitops_argocd_project

## Set Up a Jenkins server and Installations

 Go to AWS and create a Ubuntu EC2 and then install the Jenkins using the following commands

 First install JDK cause Jenkins runs on Java
 
```bash
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
```

## Writing the Jenkins File
```bash
setting the environment variables

Stage 1: Cleaning the workspace 

stage 2: Git checkout SCM

stage 3: Build Docker image 

stage 4: Push the docker images

stage 5: Delete the docker images (cleaning the old docker images)
```







