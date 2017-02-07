# Redis Cluster

Redis Cluster provides a way to run a Redis installation where data is automatically sharded across multiple Redis nodes.
Redis Cluster also provides some degree of availability during partitions, that is in practical terms the ability to continue the operations when some nodes fail or are not able to communicate. However the cluster stops to operate in the event of larger failures (for example when the majority of masters are unavailable)." ~ Redis

## Getting Started

Clone this repository

`git clone https://github.com/developersworkspace/Docker-Samples.git`

Change your working directory to the 'Redis' sample

`cd ./Docker-Samples/redis-cluster`

Run the following commands in the sequence given below

`docker build -t redis7001 ./redis7001`

`docker build -t redis7002 ./redis7002`

`docker build -t redis7003 ./redis7003`

`docker build -t redis7004 ./redis7004`

`docker build -t redis7005 ./redis7005`

`docker build -t redis7006 ./redis7006`

This will the build individual docker containers for each of the 6 instances.

Before we continue we want to change to our home directory

`cd ~`

To run all the containers, run the following commands.

`docker run -d --net=host redis7001`

`docker run -d --net=host redis7002`

`docker run -d --net=host redis7003`

`docker run -d --net=host redis7004`

`docker run -d --net=host redis7005`

`docker run -d --net=host redis7006`

Now that all 6 instances is up and running we can start to cluster them.

To do so, we first need to download the redis source which contains the clustering script.

`wget http://download.redis.io/releases/redis-stable.tar.gz`

The source that we've downloaded is zipped, we can unzip this by running

`tar xzf redis-stable.tar.gz`

The script that we'll be using is a ruby script which will require some addtional installs.

`sudo apt-get install -y ruby & sudo gem install redis`

We can now navigate to the script

`cd ./redis-stable/src`

For this example we'll assume the IP Address of the machine is '192.168.1.125'

The script takes two sets of parameters, namely the number of replicas that you want in the cluster and a space separated list of instances.

NOTE: Replace the IP Addresses with the host machine's IP Address.

`sudo ruby redis-trib.rb create --replicas 1 192.168.1.125:7001 192.168.1.125:7002 192.168.1.125:7003 192.168.1.125:7004 192.168.1.125:7005 192.168.1.125:7006`

### Why haven't we used Docker Compose

Redis cluster is not compatible with the virtual networks. At the time of writing this document, Redis had no future plans to fix this issue.

