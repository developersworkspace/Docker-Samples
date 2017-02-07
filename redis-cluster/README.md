# Running Redis Cluster in a Docker Container

Redis Cluster provides a way to run a Redis installation where data is automatically sharded across multiple Redis nodes.
Redis Cluster also provides some degree of availability during partitions, that is in practical terms the ability to continue the operations when some nodes fail or are not able to communicate. However the cluster stops to operate in the event of larger failures (for example when the majority of masters are unavailable)." ~ Redis

## Getting Started

Clone this repository

`git clone https://github.com/developersworkspace/Docker-Samples.git`

Change your working directory to the 'Redis-Cluster' sample

`cd ./Docker-Samples/redis-cluster`

Run the following commands in the sequence given below to build the individual containers for each of the 6 instances.

`docker build -t redis7001 ./redis7001`

`docker build -t redis7002 ./redis7002`

`docker build -t redis7003 ./redis7003`

`docker build -t redis7004 ./redis7004`

`docker build -t redis7005 ./redis7005`

`docker build -t redis7006 ./redis7006`


Before we continue we want to change to our home directory

`cd ~`

To run all the containers, execute the following commands

`docker run -d --net=host redis7001`

`docker run -d --net=host redis7002`

`docker run -d --net=host redis7003`

`docker run -d --net=host redis7004`

`docker run -d --net=host redis7005`

`docker run -d --net=host redis7006`

With all 6 instances running, we are able to start clustering the instances.

To do so, we first need to download the redis source which contains the script for clustering.

`wget http://download.redis.io/releases/redis-stable.tar.gz`

The source that we've downloaded is zipped, we can unzip this by running.

`tar xzf redis-stable.tar.gz`

The script that we'll be using is a ruby script which requires some additional installs.

`sudo apt-get install -y ruby & sudo gem install redis`

We can now navigate to the script

`cd ./redis-stable/src`

For this example we'll assume the IP Address of the machine is '192.168.1.125'

The script takes two sets of parameters, namely the number of replicas that you want in the cluster and a space separated list of instances.

NOTE: Replace the IP Addresses with the host machine's IP Address.

`sudo ruby redis-trib.rb create --replicas 1 192.168.1.125:7001 192.168.1.125:7002 192.168.1.125:7003 192.168.1.125:7004 192.168.1.125:7005 192.168.1.125:7006`

### Why haven't we used Docker Compose

Redis cluster is not compatible with the virtual networks. At the time of writing this document, Redis had no future plans to fix this issue.

The MIT License (MIT)
=====================

Copyright © `2017` `Barend Erasmus`

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the “Software”), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

