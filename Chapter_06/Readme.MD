![Alt text](image_06.png)

Install Docker on Linux?!


Solution 1: Install Docker on Linux
1. Install Docker on Ubuntu 22.04 Desktop (Example)
4. Test and Verify >> Docker Commands

Solution 2: Install VMware Workstation Player on Linux and Install Docker on Ubuntu 22.04 VM
1. Download VMware Workstation Player From >> https://www.vmware.com/nl/products/workstation-player/workstation-player-evaluation.html
2. Install VMware Workstation Player on Linux
3. Download Ubuntu Dekstop ISO File From >> https://releases.ubuntu.com/jammy/
4. Install Ubuntu 22.04 >> VMware Workstation Player
5. Install Docker on Ubuntu 22.04 VM
6. Test and Verify >> Docker Commands

Solution 3: Install Virtual Box on Linux and Install Docker on Ubuntu 22.04 VM
1. Download Virtual Box From >> https://www.virtualbox.org/wiki/Downloads
2. Install Virtual Box on Linux
3. Download Ubuntu Dekstop ISO File From >> https://releases.ubuntu.com/jammy/
4. Install Ubuntu 22.04 >> Virtual Box
5. Install Docker on Ubuntu 22.04 VM
6. Test and Verify >> Docker Commands

Solution 4 (Recommended): Install Virtual Box and Vagrant on Linux and Install Docker on Ubuntu 22.04 VM
Why? Because Easy to Install Multiple Servers and Docker + Docker Swarm and Cluster Infrastructure
1. Download Virtual Box From >> https://www.virtualbox.org/wiki/Downloads
2. Install Virtual Box on Linux
3. Download Vagrant From >> https://developer.hashicorp.com/vagrant/install
4. Install Vagrant on Linux
5. Start Ubuntu 22.04 VM >> Vagrant
6. Install Docker on Ubuntu 22.04 VM
7. Test and Verify >> Docker Commands
8. Destroy Ubuntu VM >> If You Do Not Need Anymore!
9. Check Other OS Images >> Vagrant Cloud >> https://app.vagrantup.com/boxes/search


****************************************
Solution 4 Commands >>>>

sudo apt update -y

wget https://www.virtualbox.org/download/oracle_vbox_2016.asc 

cat oracle_vbox_2016.asc | gpg --dearmor | sudo tee /usr/share/keyrings/virtualbox.gpg > /dev/null 2>&1

echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/virtualbox.gpg] https://download.virtualbox.org/virtualbox/debian jammy contrib' | sudo tee -a /etc/apt/sources.list.d/virtualbox.list

sudo apt update && sudo apt install virtualbox-7.0 -y

wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update && sudo apt install vagrant -y


****************************************
Vagrant Commands >>>>

vagrant global-status

vagrant up

vagrant ssh ubuntu1

vagrant destroy ubuntu1


****************************************
Ubuntu Commands & Docker Installation Commands on Ubuntu 22.04 >>>

ip addr

sudo apt update -y

sudo apt install apt-transport-https ca-certificates curl software-properties-common lsb-release -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/docker-archive-keyring.gpg

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt update

apt-cache policy docker-ce

sudo apt install docker-ce -y

systemctl status docker

sudo usermod -aG docker ${USER}

newgrp docker


****************************************
Docker Test Commands >>>>

docker ps -a

docker run hello-world

