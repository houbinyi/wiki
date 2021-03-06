Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-06-10T01:04:34+08:00

====== Redis ======

— Remote Dictionary Server

sudo apt-get install software-properties-common
sudo add-apt-repository ppa:chris-lea/redis-server
sudo apt-get update
sudo apt-get install redis-server

**Tools:**
redis-server
redis-cli
redis-benchmark
redis-check-aof
redis-check-dump
redis-sentinel

**Connection**
PING [message] Ping the server
ECHO message Echo the given string
QUIT Close the connection

**Instance**
INFO [section] Get information and statistics about the server
SHUTDOWN [NOSAVE|SAVE] Synchronously save the dataset to disk and then shut down the server
MONITOR Listen for all requests received by the server in real time
AUTH password Authenticate to the server
TIME Return the current server time
CONFIG SET parameter value Set a configuration parameter to the given value
CONFIG GET parameter Get the value of a configuration parameter
CONFIG REWRITE Rewrite the configuration file with the in memory configuration
CONFIG RESETSTAT Reset the stats returned by INFO
COMMAND Get array of Redis command details
COMMAND COUNT Get total number of Redis commands
COMMAND GETKEYS Extract keys given a full Redis command
COMMAND INFO command-name [command-name ...] Get array of specific Redis command details
DEBUG OBJECT key Get debugging information about a key
DEBUG SEGFAULT Make the server crash
OBJECT subcommand [arguments [arguments ...]] Inspect the internals of Redis objects
MIGRATE host port key|"" destination-db timeout [COPY] [REPLACE] [KEYS key [key ...]] Atomically transfer a key from a Redis instance to another one.

**Client**
CLIENT KILL [ip:port] [ID client-id] [TYPE normal|master|slave|pubsub] [ADDR ip:port] [SKIPME yes/no] Kill the connection of a client
CLIENT LIST Get the list of client connections
CLIENT GETNAME Get the current connection name
CLIENT SETNAME connection-name Set the current connection name
CLIENT PAUSE timeout Stop processing commands from clients for some time
CLIENT REPLY ON|OFF|SKIP Instruct the server whether to reply to commands

**Stroage**
SAVE Synchronously save the dataset to disk
BGSAVE Asynchronously save the dataset to disk
BGREWRITEAOF Asynchronously rewrite the append-only file
LASTSAVE Get the UNIX time stamp of the last successful save to disk

**Database**
SELECT index Change the selected database for the current connection
FLUSHALL Remove all keys from all databases
FLUSHDB Remove all keys from the current database
MOVE key db Move a key to another database
DBSIZE Return the number of keys in the selected database

**General **
KEYS pattern Find all keys matching the given pattern
EXISTS key [key ...] Determine if a key exists
TYPE key Determine the type stored at key
TTL key Get the time to live for a key
PTTL key Get the time to live for a key in milliseconds
DEL key [key ...] Delete a key
redis-cli KEYS "user:*" | xargs redis-cli DEL
redis-cli DEL `reis-cli KEYS "user:*"`
SCAN cursor [MATCH pattern] [COUNT count] Incrementally iterate the keys space
EXPIRE key seconds Set a key's time to live in seconds
EXPIREAT key timestamp Set the expiration for a key as a UNIX timestamp
PEXPIRE key milliseconds Set a key's time to live in milliseconds
PEXPIREAT key milliseconds-timestamp Set the expiration for a key as a UNIX timestamp specified in milliseconds
PERSIST key Remove the expiration from a key
RENAME key newkey Rename a key
RENAMENX key newkey Rename a key, only if the new key does not exist
RANDOMKEY Return a random key from the keyspace
DUMP key Return a serialized version of the value stored at the specified key.
RESTORE key ttl serialized-value [REPLACE] Create a key using the provided serialized value, previously obtained using DUMP.
SORT key [BY pattern] [LIMIT offset count] [GET pattern [GET pattern ...]] [ASC|DESC] [ALPHA] [STORE destination] Sort the elements in a list, set or sorted set

**String**
SET key value [EX seconds] [PX milliseconds] [NX|XX] Set the string value of a key
MSET key value [key value ...] Set multiple keys to multiple values
SETEX key seconds value Set the value and expiration of a key
SETNX key value Set the value of a key, only if the key does not exist
MSETNX key value [key value ...] Set multiple keys to multiple values, only if none of the keys exist
PSETEX key milliseconds value Set the value and expiration in milliseconds of a key
GET key Get the value of a key
MGET key [key ...] Get the values of all the given keys
GETSET key value Set the string value of a key and return its old value

APPEND key value Append a value to a key
STRLEN key Get the length of the value stored in a key
GETRANGE key start end Get a substring of the string stored at a key
SETRANGE key offset value Overwrite part of a string at key starting at the specified offset

INCR key Increment the integer value of a key by one
INCRBY key increment Increment the integer value of a key by the given amount
INCRBYFLOAT key increment Increment the float value of a key by the given amount
DECR key Decrement the integer value of a key by one
DECRBY key decrement Decrement the integer value of a key by the given number

**Bit**
GETBIT key offset Returns the bit value at offset in the string value stored at key
SETBIT key offset value Sets or clears the bit at offset in the string value stored at key
BITCOUNT key [start end] Count set bits in a string
BITOP operation destkey key [key ...] Perform bitwise operations between strings
BITPOS key bit [start] [end] Find first bit set or clear in a string
BITFIELD key [GET type offset] [SET type offset value] [INCRBY type offset increment] [OVERFLOW WRAP|SAT|FAIL] Perform arbitrary bitfield integer operations on strings

**Hash**
HSET key field value Set the string value of a hash field
HSETNX key field value Set the value of a hash field, only if the field does not exist
HGET key field Get the value of a hash field
HGETALL key Get all the fields and values in a hash
HKEYS key Get all the fields in a hash
HVALS key Get all the values in a hash
HDEL key field [field ...] Delete one or more hash fields
HEXISTS key field Determine if a hash field exists
HINCRBY key field increment Increment the integer value of a hash field by the given number
HINCRBYFLOAT key field increment Increment the float value of a hash field by the given amount
HLEN key Get the number of fields in a hash
HMGET key field [field ...] Get the values of all the given hash fields
HMSET key field value [field value ...] Set multiple hash fields to multiple values
HSTRLEN key field Get the length of the value of a hash field
HSCAN key cursor [MATCH pattern] [COUNT count] Incrementally iterate hash fields and associated values

**List**
LPUSH key value [value ...] Prepend one or multiple values to a list
LPUSHX key value Prepend a value to a list, only if the list exists
RPUSH key value [value ...] Append one or multiple values to a list
RPUSHX key value Append a value to a list, only if the list exists
LPOP key Remove and get the first element in a list
RPOP key Remove and get the last element in a list
RPOPLPUSH source destination Remove the last element in a list, prepend it to another list and return it
LLEN key Get the length of a list
LRANGE key start stop Get a range of elements from a list
LREM key count value Remove elements from a list
LINDEX key index Get an element from a list by its index
LSET key index value Set the value of an element in a list by its index
LINSERT key BEFORE|AFTER pivot value Insert an element before or after another element in a list
LTRIM key start stop Trim a list to the specified range
BLPOP key [key ...] timeout Remove and get the first element in a list, or block until one is available
BRPOP key [key ...] timeout Remove and get the last element in a list, or block until one is available
BRPOPLPUSH source destination timeout Pop a value from a list, push it to another list and return it; or block until one is available

**Set**
SADD key member [member ...] Add one or more members to a set
SREM key member [member ...] Remove one or more members from a set
SMEMBERS key Get all the members in a set
SISMEMBER key member Determine if a given value is a member of a set
SCARD key Get the number of members in a set
SRANDMEMBER key [count] Get one or multiple random members from a set
SPOP key [count] Remove and return one or multiple random members from a set
SMOVE source destination member Move a member from one set to another
SSCAN key cursor [MATCH pattern] [COUNT count] Incrementally iterate Set elements
SDIFF key [key ...] Subtract multiple sets
SDIFFSTORE destination key [key ...] Subtract multiple sets and store the resulting set in a key
SINTER key [key ...] Intersect multiple sets
SINTERSTORE destination key [key ...] Intersect multiple sets and store the resulting set in a key
SUNION key [key ...] Add multiple sets
SUNIONSTORE destination key [key ...] Add multiple sets and store the resulting set in a key

**Sorted Set**
ZADD key [NX|XX] [CH] [INCR] score member [score member ...] Add one or more members to a sorted set, or update its score if it already exists
ZSCORE key member Get the score associated with the given member in a sorted set
ZRANGE key start stop [WITHSCORES] Return a range of members in a sorted set, by index
ZREVRANGE key start stop [WITHSCORES] Return a range of members in a sorted set, by index, with scores ordered from high to low
ZRANGEBYSCORE key min max [WITHSCORES] [LIMIT offset count] Return a range of members in a sorted set, by score
ZREVRANGEBYSCORE key max min [WITHSCORES] [LIMIT offset count] Return a range of members in a sorted set, by score, with scores ordered from high to low
ZRANGEBYLEX key min max [LIMIT offset count] Return a range of members in a sorted set, by lexicographical range
ZREVRANGEBYLEX key max min [LIMIT offset count] Return a range of members in a sorted set, by lexicographical range, ordered from higher to lower strings.

ZRANK key member Determine the index of a member in a sorted set
ZREVRANK key member Determine the index of a member in a sorted set, with scores ordered from high to low

ZCARD key Get the number of members in a sorted set
ZCOUNT key min max Count the members in a sorted set with scores within the given values
ZLEXCOUNT key min max Count the number of members in a sorted set between a given lexicographical range

ZINCRBY key increment member Increment the score of a member in a sorted set
ZREM key member [member ...] Remove one or more members from a sorted set

ZREMRANGEBYRANK key start stop Remove all members in a sorted set within the given indexes
ZREMRANGEBYLEX key min max Remove all members in a sorted set between the given lexicographical range
ZREMRANGEBYSCORE key min max Remove all members in a sorted set within the given scores

ZINTERSTORE destination numkeys key [key ...] [WEIGHTS weight [weight ...]] [AGGREGATE SUM|MIN|MAX] Intersect multiple sorted sets and store the resulting sorted set in a new key
ZUNIONSTORE destination numkeys key [key ...] [WEIGHTS weight [weight ...]] [AGGREGATE SUM|MIN|MAX] Add multiple sorted sets and store the resulting sorted set in a new key

ZSCAN key cursor [MATCH pattern] [COUNT count] Incrementally iterate sorted sets elements and associated scores

**PubSub**
PUBSUB subcommand [argument [argument ...]] Inspect the state of the Pub/Sub subsystem
PUNSUBSCRIBE [pattern [pattern ...]] Stop listening for messages posted to channels matching the given patterns
PSUBSCRIBE pattern [pattern ...] Listen for messages published to channels matching the given patterns
PUBLISH channel message Post a message to a channel
SUBSCRIBE channel [channel ...] Listen for messages published to the given channels
UNSUBSCRIBE [channel [channel ...]] Stop listening for messages posted to the given channels

**Transaction**
MULTI Mark the start of a transaction block
EXEC Execute all commands issued after MULTI
DISCARD Discard all commands issued after MULTI
WATCH key [key ...] Watch the given keys to determine execution of the MULTI/EXEC block
UNWATCH Forget about all watched keys

**Script**
SCRIPT DEBUG YES|SYNC|NO Set the debug mode for executed scripts.
SCRIPT EXISTS script [script ...] Check existence of scripts in the script cache.
SCRIPT FLUSH Remove all the scripts from the script cache.
SCRIPT KILL Kill the script currently in execution.
SCRIPT LOAD script Load the specified Lua script into the script cache.
EVAL script numkeys key [key ...] arg [arg ...] Execute a Lua script server side
EVALSHA sha1 numkeys key [key ...] arg [arg ...] Execute a Lua script server side

**Replication**
READONLY Enables read queries for a connection to a cluster slave node
READWRITE Disables read queries for a connection to a cluster slave node
SLAVEOF host port Make the server a slave of another instance, or promote it as master
ROLE Return the role of the instance in the context of replication
SYNC Internal command used for replication
WAIT numslaves timeout Wait for the synchronous replication of all the write commands sent in the context of the current connection

**Cluster**
CLUSTER ADDSLOTS slot [slot ...] Assign new hash slots to receiving node
CLUSTER COUNT-FAILURE-REPORTS node-id Return the number of failure reports active for a given node
CLUSTER COUNTKEYSINSLOT slot Return the number of local keys in the specified hash slot
CLUSTER DELSLOTS slot [slot ...] Set hash slots as unbound in receiving node
CLUSTER FAILOVER [FORCE|TAKEOVER] Forces a slave to perform a manual failover of its master.
CLUSTER FORGET node-id Remove a node from the nodes table
CLUSTER GETKEYSINSLOT slot count Return local key names in the specified hash slot
CLUSTER INFO Provides info about Redis Cluster node state
CLUSTER KEYSLOT key Returns the hash slot of the specified key
CLUSTER MEET ip port Force a node cluster to handshake with another node
CLUSTER NODES Get Cluster config for the node
CLUSTER REPLICATE node-id Reconfigure a node as a slave of the specified master node
CLUSTER RESET [HARD|SOFT] Reset a Redis Cluster node
CLUSTER SAVECONFIG Forces the node to save cluster state on disk
CLUSTER SET-CONFIG-EPOCH config-epoch Set the configuration epoch in a new node
CLUSTER SETSLOT slot IMPORTING|MIGRATING|STABLE|NODE [node-id] Bind a hash slot to a specific node
CLUSTER SLAVES node-id List slave nodes of the specified master node
CLUSTER SLOTS Get array of Cluster slot to node mappings

CLUSTER INFO 打印集群的信息  
CLUSTER NODES 列出集群当前已知的所有节点（node），以及这些节点的相关信息。  
CLUSTER RESET  reset
CLUSTER SAVECONFIG  强制节点保存集群当前状态到磁盘上。
CLUSTER SLOTS 获得slot在节点上的映射关系
CLUSTER MEET <ip> <port> 将 ip 和 port 所指定的节点添加到集群当中，让它成为集群的一份子。  
CLUSTER FORGET <node_id> 从集群中移除 node_id 指定的节点。  
CLUSTER REPLICATE <node_id> 将当前节点设置为 node_id 指定的节点的从节点。    
CLUSTER SLAVES <node_id>  列出该slave节点的master节点
CLUSTER ADDSLOTS <slot> [slot ...] 将一个或多个槽（slot）指派（assign）给当前节点。  
CLUSTER DELSLOTS <slot> [slot ...] 移除一个或多个槽对当前节点的指派。  
CLUSTER FLUSHSLOTS 移除指派给当前节点的所有槽，让当前节点变成一个没有指派任何槽的节点。  
CLUSTER SETSLOT <slot> NODE <node_id> 将槽 slot 指派给 node_id 指定的节点，如果槽已经指派给另一个节点，那么先让另一个节点删除该槽>，然后再进行指派。  
CLUSTER SETSLOT <slot> MIGRATING <node_id> 将本节点的槽 slot 迁移到 node_id 指定的节点中。  
CLUSTER SETSLOT <slot> IMPORTING <node_id> 从 node_id 指定的节点中导入槽 slot 到本节点。  
CLUSTER SETSLOT <slot> STABLE 取消对槽 slot 的导入（import）或者迁移（migrate）。   
CLUSTER KEYSLOT <key> 计算键 key 应该被放置在哪个槽上。  
CLUSTER COUNTKEYSINSLOT <slot> 返回槽 slot 目前包含的键值对数量。  
CLUSTER GETKEYSINSLOT <slot> <count> 返回 count 个 slot 槽中的键
READONLY  在集群中的salve节点开启只读模式
READWRITE  禁止读取请求跳转到集群中的salve节点上

**Geo**
GEOADD key longitude latitude member [longitude latitude member ...] Add one or more geospatial items in the geospatial index represented using a sorted set
GEOHASH key member [member ...] Returns members of a geospatial index as standard geohash strings
GEOPOS key member [member ...] Returns longitude and latitude of members of a geospatial index
GEODIST key member1 member2 [unit] Returns the distance between two members of a geospatial index
GEORADIUS key longitude latitude radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count] [ASC|DESC] [STORE key] [STOREDIST key] Query a sorted set representing a geospatial index to fetch members matching a given maximum distance from a point
GEORADIUSBYMEMBER key member radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count] [ASC|DESC] [STORE key] [STOREDIST key] Query a sorted set representing a geospatial index to fetch members matching a given maximum distance from a member

**Misc**
PFADD key element [element ...] Adds the specified elements to the specified HyperLogLog.
PFCOUNT key [key ...] Return the approximated cardinality of the set(s) observed by the HyperLogLog at key(s).
PFMERGE destkey sourcekey [sourcekey ...] Merge N different HyperLogLogs into a single one.
SLOWLOG subcommand [argument] Manages the Redis slow queries log




