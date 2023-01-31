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

https://github.com/devsunset/vagrant-work

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
# Ansible
https://ansible.com
https://docs.ansible.com/ansible/latest/

https://github.com/devsunset/ansible-work

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
[vagrant@demo ansible-playbook-sample]$ ansible-playbook -i production site.yml --check --diff
[vagrant@demo ansible-playbook-sample]$ ansible-playbook -i production site.yml
[vagrant@demo ansible-playbook-sample]$ curl localhost

########################################################
# Serverspec
https://serverspec.org

vagrant/demo2 

[vagrant@demo ~] git clone https://github.com/devops-book/ansible-playbook-sample.git
[vagrant@demo ~]  cd ansible-playbook-sample
[vagrant@demo ansible-playbook-sample]$ vi stie.yml    # -serverspec 주석 제거 
[vagrant@demo ansible-playbook-sample]$ ansible-playbook -i development site.yml --diff

mkdir ~/serverspec && cd ~/serverspec

$ serverspec-init
Select OS type:

  1) UN*X
  2) Windows

Select number: 1

Select a backend type:

  1) SSH
  2) Exec (local)

Select number: 1

Vagrant instance y/n: n
Input target host name: www.example.jp
 + spec/
 + spec/www.example.jp/
 + spec/www.example.jp/sample_spec.rb
 + spec/spec_helper.rb
 + Rakefile
 + .rspec

 $ rake spec

[vagrant@demo ansible-playbook-sample]$ vi stie.yml    # -serverspec_sample 주석 제거 
[vagrant@demo ansible-playbook-sample]$ ansible-playbook -i development site.yml --diff
[vagrant@demo ansible-playbook-sample]$ ls -ld /tmp/serverspec_sample
[vagrant@demo ansible-playbook-sample]$  cd /tmp/serverspec_sample
$ rake spec 

$ gem install coderay
$ rake spec SPEC_OPTS="--format html" > ~/result.html 	`

########################################################
# Git

https://github.com/devsunset/git-github-work