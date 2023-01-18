# Home Assignment for the Junior applicatioan integration role

## Step 1: build a Jenkins server on AWS env using EC2

a.Launch an EC2 instance and select the appropriate instance type(t2.micro).

b.Make sure the security group for your EC2 instance has an inbound rule for TCP port 8080, which is the default port that Jenkins uses.
![image](https://user-images.githubusercontent.com/106589153/212828879-4e6bbea7-68df-4af6-8270-1b5371cc01b3.png)
c.Install Jenkins: Run the following commands to install Jenkins on the EC2 instance:
```
sudo yum update -y
sudo systemctl reboot
sudo amazon-linux-extras install java-openjdk11(Hit the y key in your keyboard when asked before installation commences)
```
Add Jenkins repository to the ec2:
```
sudo tee /etc/yum.repos.d/jenkins.repo<<EOF
[jenkins]
name=Jenkins
baseurl=http://pkg.jenkins.io/redhat
gpgcheck=0
EOF
```
Import GPG repository key.
```
sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
```
Update the list of repositories to confirm it is working.
```
$ sudo yum repolist
Loaded plugins: langpacks, priorities, update-motd
jenkins                                                                                                                                    | 2.9 kB  00:00:00
jenkins/primary_db                                                                                                                         | 161 kB  00:00:00
repo id                                                                     repo name                                                                       status
amzn2-core/2/x86_64                                                         Amazon Linux 2 core repository                                                  22,852
amzn2extra-docker/2/x86_64                                                  Amazon Extras repo for docker                                                       36
amzn2extra-java-openjdk11/2/x86_64                                          Amazon Extras repo for java-openjdk11                                               64
jenkins         
```
Install jenkins server on ec2
```
sudo yum install jenkins
```
Start and enable the jenkins service
```
sudo systemctl start jenkins
sudo systemctl enable jenkins
```
Check the jenkins service status:
```
systemctl status jenkins
```
![image](https://user-images.githubusercontent.com/106589153/212835067-b750af5c-cb5e-44c7-b01d-70c34e46778f.png)

## Step 2: Access Jenkins Server on EC2
a. Web console can be accessed on:
http://44.202.218.107:8080
b. the default login password is store in this file:
```
$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
cf7c4824450c442cb9c8add2b03229ad
```
c. Copy the password and paste it in the jenkins setup wizard page
d. Choose "install suggested plugins" option.
e. Create first administartor user:

![image](https://user-images.githubusercontent.com/106589153/212836782-83e2f882-21c0-4fb1-b1e0-5c5e094b3b4d.png)
f. Create jenkins Url(in my case i route it to the int college url)
![image](https://github.com/SharonLeviDevops/CloudOpsExr/blob/8f48492687c5cff95d243c84845dee016a0c44a7/url.JPG)

## Step 3:  pull the Nginx image from the Docker Hub and run it on a Jenkins server:
a. install docker on the jenkins server:
```
sudo yum install docker
```
b. Enable docker service at AMI boot time:
```
sudo systemctl enable docker.service
```
c. Start the Docker service
```
sudo systemctl start docker.service
```
d. Check the docker service status:
```
sudo systemctl status docker.service
```
