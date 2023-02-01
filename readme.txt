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

$ suo yum install -y git 
$ git --version 
$ git config --global user.name "devsunset"
$ git config --global user.email "devsunset@gmail.com"
$ mkdir sample-repo 
$ cd sample-repo
$ git init 
$ echo "Hello" > README.md
$ cat README.md
$ git status
$ git add README.md   # git add .
$ git status 
$ git commit -m "commit message"
$ git status 
$ git log
$ git log --oneline
$ echo "Hello World" > README.md
$ git diff 
$ git add .
$ git status 
$ git reset
$ git status 
$ git reset --hard
$ git status 

* https://www.github.com 
* create sample-repo repository

$ git remote add origin https://github.com/devsunset/sample-repo.git
$ git push -u origin master

* delete sample-repo 

$ git clone https://github.com/devsunset/sample-repo.git

* https://www.github.com 
* modify sampe-repo README.md file

$ git pull
$ git log 

$ git branch
$ git branch develop
$ git branch 
$ git checkout develop
$ git branch
$ echo 'update test' >> README.md
$ cat README.md
$ git add .
$ git commit -m "updated README"
$ git push origin develop

* https://www.github.com 
1) Pull Requests   ( develop -> master  PR )
2) Review & Comment 
3) Comment 대응 
4) Reviw 및 병합 

$ git checkout master
$ git pull
$ cat README.md 

* git flow
https://nvie.com/posts/a-successful-git-branching-model/
http://scottchacon.com/2011/08/31/github-flow.html

########################################################
# Docker

https://www.docker.com/
https://hub.docker.com/

https://github.com/devsunset/docker-work

$ sudo yum install -y docker
$ systemctl start docker.service
$ docker version

#  관리자 계정(root) 가 아닌 일반 유저 계정으로 docker를 실행하는 법
1. 도커 그룹 생성 
    sudo groupadd docker
2. 현재 유저를 도커 그룹에 포함
    sudo usermod -aG docker $USER
3. 접근 에러가 발생하지 않도록 권한 부여
    sudo chmod 666 /var/run/docker.sock
4. docker 서비스 재시작 or reboot
    sudo service docker restart
5. 실행 확인
    docker run hello-world

$ docker login 
$ dockr search centos
$ docker pull docker.io/centos
$ docker pull docker.io/centos:centos7
$ docker images
$ docker run -td --name centos7 docker.io/centos:centos7
$ docker ps 
$ docker ps -a
$ docker exec centos7 cat /etc/redhat-release
$ docker exec -it centos7 /bin/bash
$ cat /etc/redhat-release
$ exit
$ docker stop centos7 
$ docker ps
$ docker ps -a
$ docker start centos7
$ docker ps
$ docker rm -f centos7 
$ docker ps -a 
$ docker pull docker.io/ubuntu
$ docker run -td --name ubuntu-latest docker.io/ubuntu:latest
$ docker exec -it ubuntu-latest cat /etc/os-release
$ dockr pull docker.io/nginx
$ docker run -d -p 8000:80 --name nginx-latest docker.io/nginx:latest
$ docker ps
$ curl http://localhost:8000/index.html
$ docker logs -f nginx-latest

* https://hub.docker.com/_/centos  : dockerfile
* https://hub.docker.com/_/nginx

$ docker run -td --name centos7 docker.io/centos:centos7

$ echo "Hello, Docker." > hello-docker.txt
$  vi Dockerfile
FROM docker.io/centos:latest
ADD hello-docker.txt /tmp
RUN yum install -y epel-release   
CMD ["/bin/bash"]

$ docker build -t devsunset/centos:1.0 ./

# 실행시 아래 에러 발생하면 Dockerfile 에서 RUN yum install -y epel-release 주석 처리 하고 진행 
Error: Failed to download metadata for repo 'appstream': Cannot prepare internal mirrorlist: No URLs in mirrorlist

$ docker images
$ docker run -td --name dev/centos devsunset/centos:1.0
$ docker ps
$ docker exec -it devcentos /bin/bash
$ cat /tmp/hello-docker.txt
$ yum install -y nginx 

# 위의 nginx 설치  명령어 실행시 에러 발생 하면 아래 명령어 실행 후 다시 재실행 
  $ sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-Linux-*
  $ sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-Linux-*

$ exit 
$ docker commit devcentos devsunset/centos:1.1
$ docker images
$ docker push devsunset/centos:1.1

* https://docs.docker.com/compose/install

$ sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
$ docker-compose --version

* https://github.com/docker/awesome-compose/

$ vi docker-compose.yml
services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: rootpwd
      MYSQL_DATABASE: databasename
      MYSQL_USER: user
      MYSQL_PASSWORD: userpwd

  wordpress:
    image: wordpress
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wp
      WORDPRESS_DB_PASSWORD: wp
      WORDPRESS_DB_NAME: wp
    depends_on:
      - db

volumes:
  db_data: {}

$ docker-compose up -d
$ docker ps
$ docker-compose stop 
$ docker-compose down
$ docker-compose scale 

########################################################
# Jenkins

https://www.jenkins.io/


