# Steps to install maven 
Tested on AWS ec2-instance running on Amazon Linux 2 AMI

    sudo wget http://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo
    sudo sed -i s/\$releasever/6/g /etc/yum.repos.d/epel-apache-maven.repo  ## replace releasever by 6 in .repo file
    sudo yum install -y apache-maven
    export PATH=$PATH:<path of bin directory of maven>
    export MAVEN_HOME=/usr/share/apache-maven
    mvn --version

Go to your maven-project's directory and check if the maven is working:

    mvn test


If you have 2 versions of java on system run below commands to select appropriate version of java
#after each command you will need to give your choice

    sudo alternatives --config java
    sudo alternatives --config javac
    sudo alternatives --config jre_openjdk
    sudo alternatives --config java_sdk_openjdk
