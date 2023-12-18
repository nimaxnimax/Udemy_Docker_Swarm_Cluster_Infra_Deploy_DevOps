How To Install Docker Swarm On Ubuntu? 
And Create Docker Swarm Cluster? 
And Deploy Application in the Cluster! 
And Replicas and Scaling the Service!


Docker swarm is a tool used to create a cluster of docker hosts. With docker swarm, we can create a high availability and high performance cluster where applications are distributed among the hosts. Docker swarm consists of a manager and worker nodes and operations are performed from the manager.


********************
Step 1 >> Configure 3 Ubuntu VMs
1. Configure Vagrantfile
2. vagrant global-status
3. vagrant up
4. vagrant ssh ubuntu1
5. vagrant ssh ubuntu2
6. vagrant ssh ubuntu3


********************
Step 2 >> Prepare Your Nodes

** In my set up, I have one manager node and two worker nodes. On each host, configure hosts file to include all the other nodes.

sudo vim /etc/hosts

** Add the following content to the file (example - replace with your ubuntu vm IP addresses)

192.168.1.10	manager

192.168.1.11	worker-01

192.168.1.12	worker-02

# Save the file. Ensure that you can ping all the hosts from each host using hostname and not IP address.


********************
Step 3 >> Install Docker Container Engine >> on 3 Ubuntu VMs

sudo apt update -y

sudo apt install apt-transport-https ca-certificates curl software-properties-common lsb-release -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/docker-archive-keyring.gpg

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt update -y

apt-cache policy docker-ce

sudo apt install docker-ce -y

systemctl status docker

sudo usermod -aG docker ${USER}

newgrp docker


********************
Step 4 >> Create Docker Swarm Cluster

# To set up swarm cluster, we first need to initialize Docker Swarm mode on the manager node then add the worker nodes to the cluster.

# Get interface IP address

ip address

# For me the interface for which Docker manager will advertise on is enp1s0

INT_NAME="enp1s0" #replace accordingly

HOST_IP=$(ip addr show $INT_NAME | grep "inet\b" | awk '{print $2}' | cut -d/ -f1)

# Confirm IP address is saved correctly

echo $HOST_IP

# Run the below command to initialize Docker swarm node on the manager.

sudo docker swarm init --advertise-addr $HOST_IP


********************
Step 5 >> Join Worker Nodes to the Cluster

# We are now going to add the worker-01 and worker-02 nodes to the cluster manager using the join-token from the cluster manager node.

# Run the command printed in the init command output.

# Example Below (Replace token and IP with your own config)

sudo docker swarm join --token SWMTKN-1-13xo81gxpb3ttjh5e335pfrmz9fbnliikgfys7u8l4r8k4m575-2gsjwjs3y1i4kgeua2yu840hw 192.168.1.10:2377

# Check if the worker nodes are successfully added to the cluster by running the below command on the manager:

sudo docker node ls


********************
Step 6 >> Deploy application in the Cluster - Replicas and Scaling the Service

# Let’s create a service Nginx web server to run on default http port 80, and then expose it to the port 80 on the host.

sudo docker service create --name web-server --publish 80:80 nginx:1.13-alpine

# Confirm the created service by running the below command:

sudo docker service ls

# We are going to make 3 replicas of the web-server service so that it is accessible on the manager and the two worker nodes.

sudo docker service scale web-server=3

# Confirm created service replicas

sudo docker service ls

# Access the service from your browser using all the nodes IPs: http://192.168.1.10:80, http://192.168.1.11:80 and http://192.168.1.12:80 and you should get a nginx welcome page (this is an example - replace IP addresses with your own IP addresses)

