# Home Assignment for the Junior applicatioan integration role

Step 1: build a Jenkins server on AWS env using EC2

1.Launch an EC2 instance and select the appropriate instance type(t2.micro).

2.Install Jenkins: Run the following commands to install Jenkins on the EC2 instance:
```
sudo yum update -y
sudo yum install java-1.8.0-openjdk-devel -y
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo yum install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

