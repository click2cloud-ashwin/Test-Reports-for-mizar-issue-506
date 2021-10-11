#### Check zookeeper pod logs

```bash
./cluster/kubectl.sh logs zookeeper-6d5ff49b84-8s62z
```
##### Output

```bigquery
ZooKeeper JMX enabled by default
Using config: /opt/zookeeper-3.4.13/bin/../conf/zoo.cfg
2021-10-11 09:39:50,172 [myid:] - INFO  [main:QuorumPeerConfig@136] - Reading configuration from: /opt/zookeeper-3.4.13/bin/../conf/zoo.cfg
2021-10-11 09:39:50,179 [myid:] - INFO  [main:DatadirCleanupManager@78] - autopurge.snapRetainCount set to 3
2021-10-11 09:39:50,179 [myid:] - INFO  [main:DatadirCleanupManager@79] - autopurge.purgeInterval set to 1
2021-10-11 09:39:50,180 [myid:] - WARN  [main:QuorumPeerMain@116] - Either no config or no quorum defined in config, running  in standalone mode
2021-10-11 09:39:50,180 [myid:] - INFO  [PurgeTask:DatadirCleanupManager$PurgeTask@138] - Purge task started.
2021-10-11 09:39:50,198 [myid:] - INFO  [PurgeTask:DatadirCleanupManager$PurgeTask@144] - Purge task completed.
2021-10-11 09:39:50,200 [myid:] - INFO  [main:QuorumPeerConfig@136] - Reading configuration from: /opt/zookeeper-3.4.13/bin/../conf/zoo.cfg
2021-10-11 09:39:50,200 [myid:] - INFO  [main:ZooKeeperServerMain@98] - Starting server
2021-10-11 09:39:50,213 [myid:] - INFO  [main:Environment@100] - Server environment:zookeeper.version=3.4.13-2d71af4dbe22557fda74f9a9b4309b15a7487f03, built on 06/29/2018 04:05 GMT
2021-10-11 09:39:50,213 [myid:] - INFO  [main:Environment@100] - Server environment:host.name=zookeeper-6d5ff49b84-7lhsb
2021-10-11 09:39:50,214 [myid:] - INFO  [main:Environment@100] - Server environment:java.version=1.7.0_65
2021-10-11 09:39:50,214 [myid:] - INFO  [main:Environment@100] - Server environment:java.vendor=Oracle Corporation
2021-10-11 09:39:50,214 [myid:] - INFO  [main:Environment@100] - Server environment:java.home=/usr/lib/jvm/java-7-openjdk-amd64/jre
2021-10-11 09:39:50,214 [myid:] - INFO  [main:Environment@100] - Server environment:java.class.path=/opt/zookeeper-3.4.13/bin/../build/classes:/opt/zookeeper-3.4.13/bin/../build/lib/*.jar:/opt/zookeeper-3.4.13/bin/../lib/slf4j-log4j12-1.7.25.jar:/opt/zookeeper-3.4.13/bin/../lib/slf4j-api-1.7.25.jar:/opt/zookeeper-3.4.13/bin/../lib/netty-3.10.6.Final.jar:/opt/zookeeper-3.4.13/bin/../lib/log4j-1.2.17.jar:/opt/zookeeper-3.4.13/bin/../lib/jline-0.9.94.jar:/opt/zookeeper-3.4.13/bin/../lib/audience-annotations-0.5.0.jar:/opt/zookeeper-3.4.13/bin/../zookeeper-3.4.13.jar:/opt/zookeeper-3.4.13/bin/../src/java/lib/*.jar:/opt/zookeeper-3.4.13/bin/../conf:
2021-10-11 09:39:50,215 [myid:] - INFO  [main:Environment@100] - Server environment:java.library.path=/usr/java/packages/lib/amd64:/usr/lib/x86_64-linux-gnu/jni:/lib/x86_64-linux-gnu:/usr/lib/x86_64-linux-gnu:/usr/lib/jni:/lib:/usr/lib
2021-10-11 09:39:50,215 [myid:] - INFO  [main:Environment@100] - Server environment:java.io.tmpdir=/tmp
2021-10-11 09:39:50,218 [myid:] - INFO  [main:Environment@100] - Server environment:java.compiler=<NA>
2021-10-11 09:39:50,218 [myid:] - INFO  [main:Environment@100] - Server environment:os.name=Linux
2021-10-11 09:39:50,218 [myid:] - INFO  [main:Environment@100] - Server environment:os.arch=amd64
2021-10-11 09:39:50,218 [myid:] - INFO  [main:Environment@100] - Server environment:os.version=5.6.0-rc2
2021-10-11 09:39:50,219 [myid:] - INFO  [main:Environment@100] - Server environment:user.name=root
2021-10-11 09:39:50,219 [myid:] - INFO  [main:Environment@100] - Server environment:user.home=/root
2021-10-11 09:39:50,219 [myid:] - INFO  [main:Environment@100] - Server environment:user.dir=/opt/zookeeper-3.4.13
2021-10-11 09:39:50,222 [myid:] - INFO  [main:ZooKeeperServer@836] - tickTime set to 2000
2021-10-11 09:39:50,223 [myid:] - INFO  [main:ZooKeeperServer@845] - minSessionTimeout set to -1
2021-10-11 09:39:50,223 [myid:] - INFO  [main:ZooKeeperServer@854] - maxSessionTimeout set to -1
2021-10-11 09:39:50,237 [myid:] - INFO  [main:ServerCnxnFactory@117] - Using org.apache.zookeeper.server.NIOServerCnxnFactory as server connection factory
2021-10-11 09:39:50,243 [myid:] - INFO  [main:NIOServerCnxnFactory@89] - binding to port 0.0.0.0/0.0.0.0:2181
2021-10-11 09:40:09,505 [myid:] - INFO  [NIOServerCxn.Factory:0.0.0.0/0.0.0.0:2181:NIOServerCnxnFactory@215] - Accepted socket connection from /20.0.0.21:57538
2021-10-11 09:40:09,513 [myid:] - INFO  [NIOServerCxn.Factory:0.0.0.0/0.0.0.0:2181:ZooKeeperServer@949] - Client attempting to establish new session at /20.0.0.21:57538
2021-10-11 09:40:09,515 [myid:] - INFO  [SyncThread:0:FileTxnLog@213] - Creating new log file: log.1
2021-10-11 09:40:09,545 [myid:] - INFO  [SyncThread:0:ZooKeeperServer@694] - Established session 0x1000a3216940000 with negotiated timeout 6000 for client /20.0.0.21:57538
2021-10-11 09:40:09,671 [myid:] - INFO  [ProcessThread(sid:0 cport:2181)::PrepRequestProcessor@653] - Got user-level KeeperException when processing sessionid:0x1000a3216940000 type:create cxid:0x2 zxid:0x3 txntype:-1 reqpath:n/a Error Path:/brokers Error:KeeperErrorCode = NoNode for /brokers
2021-10-11 09:40:09,682 [myid:] - INFO  [ProcessThread(sid:0 cport:2181)::PrepRequestProcessor@653] - Got user-level KeeperException when processing sessionid:0x1000a3216940000 type:create cxid:0x6 zxid:0x7 txntype:-1 reqpath:n/a Error Path:/config Error:KeeperErrorCode = NoNode for /config
2021-10-11 09:40:09,692 [myid:] - INFO  [ProcessThread(sid:0 cport:2181)::PrepRequestProcessor@653] - Got user-level KeeperException when processing sessionid:0x1000a3216940000 type:create cxid:0x9 zxid:0xa txntype:-1 reqpath:n/a Error Path:/admin Error:KeeperErrorCode = NoNode for /admin
2021-10-11 09:40:10,024 [myid:] - INFO  [ProcessThread(sid:0 cport:2181)::PrepRequestProcessor@653] - Got user-level KeeperException when processing sessionid:0x1000a3216940000 type:create cxid:0x15 zxid:0x15 txntype:-1 reqpath:n/a Error Path:/cluster Error:KeeperErrorCode = NoNode for /cluster
2021-10-11 09:40:11,092 [myid:] - INFO  [ProcessThread(sid:0 cport:2181)::PrepRequestProcessor@653] - Got user-level KeeperException when processing sessionid:0x1000a3216940000 type:setData cxid:0x23 zxid:0x1b txntype:-1 reqpath:n/a Error Path:/controller_epoch Error:KeeperErrorCode = NoNode for /controller_epoch
2021-10-11 09:40:11,294 [myid:] - INFO  [ProcessThread(sid:0 cport:2181)::PrepRequestProcessor@653] - Got user-level KeeperException when processing sessionid:0x1000a3216940000 type:delete cxid:0x38 zxid:0x1e txntype:-1 reqpath:n/a Error Path:/admin/reassign_partitions Error:KeeperErrorCode = NoNode for /admin/reassign_partitions
2021-10-11 09:40:11,305 [myid:] - INFO  [ProcessThread(sid:0 cport:2181)::PrepRequestProcessor@653] - Got user-level KeeperException when processing sessionid:0x1000a3216940000 type:delete cxid:0x3a zxid:0x1f txntype:-1 reqpath:n/a Error Path:/admin/preferred_replica_election Error:KeeperErrorCode = NoNode for /admin/preferred_replica_election

```
