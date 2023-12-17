![Alt text](image_05.jpg)

Install Docker on Windows?!

Solution 1: Install Docker on Windows
1. Download Docker Desktop From >> https://www.docker.com/products/docker-desktop/
2. Install Docker Desktop On Windows
3. More Information >> https://docs.docker.com/desktop/install/windows-install/
4. Test and Verify >> Docker Commands

Solution 2: Install VMware Workstation Player on Windows and Install Docker on Ubuntu 22.04 VM
1. Download VMware Workstation Player From >> https://www.vmware.com/nl/products/workstation-player/workstation-player-evaluation.html
2. Install VMware Workstation Player on Windows
3. Download Ubuntu Dekstop ISO File From >> https://releases.ubuntu.com/jammy/
4. Install Ubuntu 22.04 >> VMware Workstation Player
5. Install Docker on Ubuntu 22.04 VM
6. Test and Verify >> Docker Commands

Solution 3: Install Virtual Box on Windows and Install Docker on Ubuntu 22.04 VM
1. Download Virtual Box From >> https://www.virtualbox.org/wiki/Downloads
2. Install Virtual Box on Windows
3. Download Ubuntu Dekstop ISO File From >> https://releases.ubuntu.com/jammy/
4. Install Ubuntu 22.04 >> Virtual Box
5. Install Docker on Ubuntu 22.04 VM
6. Test and Verify >> Docker Commands

Solution 4 (Recommended): Install Virtual Box and Vagrant on Windows and Install Docker on Ubuntu 22.04 VM
Why? Because Easy to Install Multiple Servers and Docker + Docker Swarm and Cluster Infrastructure
1. Download Virtual Box From >> https://www.virtualbox.org/wiki/Downloads
2. Install Virtual Box on Windows
3. Download Vagrant From >> https://developer.hashicorp.com/vagrant/install
4. Install Vagrant on Windows
5. Start Ubuntu 22.04 VM >> Vagrant
6. Install Docker on Ubuntu 22.04 VM
7. Test and Verify >> Docker Commands
8. Destroy Ubuntu VM >> If You Do Not Need Anymore!


****************************************
Vagrant Commands >>>>

vagrant global-status

vagrant up

vagrant ssh ubuntu1


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

