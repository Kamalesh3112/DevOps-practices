To setup Test-kitchen:

sudo apt-get install ruby2.3-dev

chef gem install --no-user-install kitchen-docker

chef gem install --no-user-install kitchen-vagrant

create a chef repo
Make sure you have .kitchen.yml un chef Repo
cd chef_repo
kitchen create   #shall create kitchen setup based on configuration of .kitchen.yml

Other commands:

kitchen converge
kitchen test
kitchen verify
kitchen destroy
