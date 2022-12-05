Select appropriate rpm for your machine and download:

$wget https://packages.chef.io/files/stable/chefdk/1.3.43/el/7/chefdk-1.3.43-1.el7.x86_64.rpm
install the rpm:
$rpm -i chefdk-1.3.43-1.el7.x86_64.rpm

Give the user root permissions:
$usermod -g wheel ec2-user
Test if chef is working fine:
$ chef-client --local-mode
 
 
Reference:
https://docs.chef.io/install_dk.html
https://www.agileweboperations.com/amazon-ec2-instances-with-opscode-chef-using-knife

Identify the Chef server type: hosted or on-premises
Review the prerequisites
Download and run the ChefDK installer
Set the system Ruby
Install git
Set up the chef-repo
Create the .chef directory
Get the .pem files and knife.rb files
Move files to the .chef directory
Add omnibus Ruby to the $PATH environment variable
Get SSL certificates from the Chef server
Verify the chef-client install

 https://packages.chef.io/files/stable/chefdk/2.4.17/el/6/chefdk-2.4.17-1.el6.x86_64.rpm
 $ which ruby
 TO let chef use its own ruby system do this:
 echo 'eval "$(chef shell-init bash)"' >> ~/.bash_profile
 and 
 eval "$(chef shell-init bash)"

  Run which ruby again. It should return /opt/chefdk/embedded/bin/ruby.
    $ which ruby

Copy keypair.pem file in the ec2-instance
Store the downloaded private key keypair.pem in ~/.ssh/keypair.pem

Edit /root/.ssh/config file:
Host ec2*compute-1.amazonaws.com
  StrictHostKeyChecking no
  User ec2-user
  IdentityFile  /root/.ssh/FirstInstanceKP.pem


Create a directory /root/.chef
Create a file /root/.chef/.knife.rb


 $gem install knife-ec2
 
In /root/.chef/.knife.rb   :
knife[:aws_access_key_id] = "***"
knife[:aws_secret_access_key] = "***"
knife[:region] = "ap-south-1"
knife[:chef_mode] = "solo"
knife[:node_name] = "client"


try command:
knife ec2  server list
This shall show list of all ec2-instances in your account

Use knife command to create the instance in your aws account:
 knife ec2 server create -I ami-52c7b43d -f t2.micro -S FirstInstanceKP -i /root/.chef/FirstInstanceKP.pem  --ssh-user ec2-user --region ap-south-1 -Z ap-south-1a

A client.pem is needed in /etc/chef/client.pem ??
