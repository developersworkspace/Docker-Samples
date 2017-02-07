# Redis

"Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker. It supports data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs and geospatial indexes with radius queries. Redis has built-in replication, Lua scripting, LRU eviction, transactions and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster." ~ Redis
## Getting Started

Clone this repository

`git clone https://github.com/developersworkspace/Docker-Samples.git`

Change your working directory to the 'Redis' sample

`cd ./Docker-Samples/redis`

Build the container from the 'Dockerfile'

`docker build -t my_redis ./`

Run your container

`docker run -p 6379:6379 -t my_redis`

You can now connect to your redis instance using a tool such as [Redis Desktop Manager](https://redisdesktop.com)