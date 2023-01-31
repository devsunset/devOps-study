-------------------------------------------------

			# DEVOPS-WORK #

-------------------------------------------------

########################################################
### DEVOPS


########################################################
# Vagrant 
https://www.vagrantup.com/
https://www.vagrantup.com/docs
https://app.vagrantup.com/boxes/search

$ cd ./vagrant/demo1/
$ vagrant up 
$ vagrant ssh 
$ uname -n
$ ip addr show dev eth1
$ vagrant halt
$ vagrant destroy


$ cd ./vagrant/demo2/
$ vagrant up   
$ vagrant ssh 
$ uname -n
$ ip addr show dev eth1
$ exit
# curl http://192.168.33.10

########################################################
#Ansible
https://ansible.com

vagrant/demo2 

[vagrant@demo ~] $ sudo systemctl stop nginx.service
[vagrant@demo ~] $ sudo yum -y install epel-release
[vagrant@demo ~] $ sudo yum -y install ansible
[vagrant@demo ~] $ ansible --version
[vagrant@demo ~] $ sudo sh -c "echo \"localhost\" >> /etc/ansible/hosts"
[vagrant@demo ~] $ ansible localhost -b -c local -m service -a "name=nginx state=started"
[vagrant@demo ~]$ systemctl status nginx.service
[vagrant@demo ~] $ ansible localhost -b -c local -m service -a "name=nginx state=started"

[vagrant@demo ~] sudo yum -y install git 
[vagrant@demo ~] git clone https://github.com/devops-book/ansible-playbook-sample.git
[vagrant@demo ~]  cd ansible-playbook-sample
[vagrant@demo ansible-playbook-sample]$ ansible-playbook -i development site.yml
[vagrant@demo ansible-playbook-sample]$ curl localhost
[vagrant@demo ansible-playbook-sample]$ ansible-playbook -i production site.xml
[vagrant@demo ansible-playbook-sample]$ curl localhost