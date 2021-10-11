### Check kafka pod logs 

```bash
./cluster/kubectl.sh logs kafka-556d74b878-9r6lq
```
#### Output
```bigquery
Excluding KAFKA_HOME from broker config
[Configuring] 'port.9092.tcp.port' in '/opt/kafka/config/server.properties'
[Configuring] 'port' in '/opt/kafka/config/server.properties'
[Configuring] 'advertised.listeners' in '/opt/kafka/config/server.properties'
[Configuring] 'port.9092.tcp' in '/opt/kafka/config/server.properties'
[Configuring] 'service.port.9092' in '/opt/kafka/config/server.properties'
[Configuring] 'service.host' in '/opt/kafka/config/server.properties'
[Configuring] 'service.port' in '/opt/kafka/config/server.properties'
[Configuring] 'broker.id' in '/opt/kafka/config/server.properties'
Excluding KAFKA_VERSION from broker config
[Configuring] 'listeners' in '/opt/kafka/config/server.properties'
[Configuring] 'port.9092.tcp.addr' in '/opt/kafka/config/server.properties'
[Configuring] 'zookeeper.connect' in '/opt/kafka/config/server.properties'
[Configuring] 'log.dirs' in '/opt/kafka/config/server.properties'
[Configuring] 'port.9092.tcp.proto' in '/opt/kafka/config/server.properties'
[2021-10-11 09:40:08,955] INFO Registered kafka:type=kafka.Log4jController MBean (kafka.utils.Log4jControllerRegistration$)
[2021-10-11 09:40:09,434] INFO starting (kafka.server.KafkaServer)
[2021-10-11 09:40:09,435] INFO Connecting to zookeeper on zookeeper:2181 (kafka.server.KafkaServer)
[2021-10-11 09:40:09,457] INFO [ZooKeeperClient] Initializing a new session to zookeeper:2181. (kafka.zookeeper.ZooKeeperClient)
[2021-10-11 09:40:09,465] INFO Client environment:zookeeper.version=3.4.13-2d71af4dbe22557fda74f9a9b4309b15a7487f03, built on 06/29/2018 00:39 GMT (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,465] INFO Client environment:host.name=kafka-556d74b878-b9rhz (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,465] INFO Client environment:java.version=1.8.0_181 (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,465] INFO Client environment:java.vendor=Oracle Corporation (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,466] INFO Client environment:java.home=/usr/lib/jvm/java-1.8-openjdk/jre (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,466] INFO Client environment:java.class.path=/opt/kafka/bin/../libs/activation-1.1.1.jar:/opt/kafka/bin/../libs/aopalliance-repackaged-2.5.0-b42.jar:/opt/kafka/bin/../libs/argparse4j-0.7.0.jar:/opt/kafka/bin/../libs/audience-annotations-0.5.0.jar:/opt/kafka/bin/../libs/commons-lang3-3.5.jar:/opt/kafka/bin/../libs/connect-api-2.0.1.jar:/opt/kafka/bin/../libs/connect-basic-auth-extension-2.0.1.jar:/opt/kafka/bin/../libs/connect-file-2.0.1.jar:/opt/kafka/bin/../libs/connect-json-2.0.1.jar:/opt/kafka/bin/../libs/connect-runtime-2.0.1.jar:/opt/kafka/bin/../libs/connect-transforms-2.0.1.jar:/opt/kafka/bin/../libs/guava-20.0.jar:/opt/kafka/bin/../libs/hk2-api-2.5.0-b42.jar:/opt/kafka/bin/../libs/hk2-locator-2.5.0-b42.jar:/opt/kafka/bin/../libs/hk2-utils-2.5.0-b42.jar:/opt/kafka/bin/../libs/jackson-annotations-2.9.7.jar:/opt/kafka/bin/../libs/jackson-core-2.9.7.jar:/opt/kafka/bin/../libs/jackson-databind-2.9.7.jar:/opt/kafka/bin/../libs/jackson-jaxrs-base-2.9.7.jar:/opt/kafka/bin/../libs/jackson-jaxrs-json-provider-2.9.7.jar:/opt/kafka/bin/../libs/jackson-module-jaxb-annotations-2.9.7.jar:/opt/kafka/bin/../libs/javassist-3.22.0-CR2.jar:/opt/kafka/bin/../libs/javax.annotation-api-1.2.jar:/opt/kafka/bin/../libs/javax.inject-1.jar:/opt/kafka/bin/../libs/javax.inject-2.5.0-b42.jar:/opt/kafka/bin/../libs/javax.servlet-api-3.1.0.jar:/opt/kafka/bin/../libs/javax.ws.rs-api-2.1.jar:/opt/kafka/bin/../libs/jaxb-api-2.3.0.jar:/opt/kafka/bin/../libs/jersey-client-2.27.jar:/opt/kafka/bin/../libs/jersey-common-2.27.jar:/opt/kafka/bin/../libs/jersey-container-servlet-2.27.jar:/opt/kafka/bin/../libs/jersey-container-servlet-core-2.27.jar:/opt/kafka/bin/../libs/jersey-hk2-2.27.jar:/opt/kafka/bin/../libs/jersey-media-jaxb-2.27.jar:/opt/kafka/bin/../libs/jersey-server-2.27.jar:/opt/kafka/bin/../libs/jetty-client-9.4.11.v20180605.jar:/opt/kafka/bin/../libs/jetty-continuation-9.4.11.v20180605.jar:/opt/kafka/bin/../libs/jetty-http-9.4.11.v20180605.jar:/opt/kafka/bin/../libs/jetty-io-9.4.11.v20180605.jar:/opt/kafka/bin/../libs/jetty-security-9.4.11.v20180605.jar:/opt/kafka/bin/../libs/jetty-server-9.4.11.v20180605.jar:/opt/kafka/bin/../libs/jetty-servlet-9.4.11.v20180605.jar:/opt/kafka/bin/../libs/jetty-servlets-9.4.11.v20180605.jar:/opt/kafka/bin/../libs/jetty-util-9.4.11.v20180605.jar:/opt/kafka/bin/../libs/jopt-simple-5.0.4.jar:/opt/kafka/bin/../libs/kafka-clients-2.0.1.jar:/opt/kafka/bin/../libs/kafka-log4j-appender-2.0.1.jar:/opt/kafka/bin/../libs/kafka-streams-2.0.1.jar:/opt/kafka/bin/../libs/kafka-streams-examples-2.0.1.jar:/opt/kafka/bin/../libs/kafka-streams-scala_2.11-2.0.1.jar:/opt/kafka/bin/../libs/kafka-streams-test-utils-2.0.1.jar:/opt/kafka/bin/../libs/kafka-tools-2.0.1.jar:/opt/kafka/bin/../libs/kafka_2.11-2.0.1-sources.jar:/opt/kafka/bin/../libs/kafka_2.11-2.0.1.jar:/opt/kafka/bin/../libs/log4j-1.2.17.jar:/opt/kafka/bin/../libs/lz4-java-1.4.1.jar:/opt/kafka/bin/../libs/maven-artifact-3.5.3.jar:/opt/kafka/bin/../libs/metrics-core-2.2.0.jar:/opt/kafka/bin/../libs/osgi-resource-locator-1.0.1.jar:/opt/kafka/bin/../libs/plexus-utils-3.1.0.jar:/opt/kafka/bin/../libs/reflections-0.9.11.jar:/opt/kafka/bin/../libs/rocksdbjni-5.7.3.jar:/opt/kafka/bin/../libs/scala-library-2.11.12.jar:/opt/kafka/bin/../libs/scala-logging_2.11-3.9.0.jar:/opt/kafka/bin/../libs/scala-reflect-2.11.12.jar:/opt/kafka/bin/../libs/slf4j-api-1.7.25.jar:/opt/kafka/bin/../libs/slf4j-log4j12-1.7.25.jar:/opt/kafka/bin/../libs/snappy-java-1.1.7.1.jar:/opt/kafka/bin/../libs/validation-api-1.1.0.Final.jar:/opt/kafka/bin/../libs/zkclient-0.10.jar:/opt/kafka/bin/../libs/zookeeper-3.4.13.jar (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,466] INFO Client environment:java.library.path=/usr/lib/jvm/java-1.8-openjdk/jre/lib/amd64/server:/usr/lib/jvm/java-1.8-openjdk/jre/lib/amd64:/usr/lib/jvm/java-1.8-openjdk/jre/../lib/amd64:/usr/java/packages/lib/amd64:/usr/lib64:/lib64:/lib:/usr/lib (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,467] INFO Client environment:java.io.tmpdir=/tmp (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,467] INFO Client environment:java.compiler=<NA> (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,467] INFO Client environment:os.name=Linux (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,467] INFO Client environment:os.arch=amd64 (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,467] INFO Client environment:os.version=5.6.0-rc2 (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,467] INFO Client environment:user.name=root (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,467] INFO Client environment:user.home=/root (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,468] INFO Client environment:user.dir=/ (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,469] INFO Initiating client connection, connectString=zookeeper:2181 sessionTimeout=6000 watcher=kafka.zookeeper.ZooKeeperClient$ZooKeeperClientWatcher$@223d2c72 (org.apache.zookeeper.ZooKeeper)
[2021-10-11 09:40:09,489] INFO [ZooKeeperClient] Waiting until connected. (kafka.zookeeper.ZooKeeperClient)
[2021-10-11 09:40:09,493] INFO Opening socket connection to server zookeeper/10.0.0.244:2181. Will not attempt to authenticate using SASL (unknown error) (org.apache.zookeeper.ClientCnxn)
[2021-10-11 09:40:09,504] INFO Socket connection established to zookeeper/10.0.0.244:2181, initiating session (org.apache.zookeeper.ClientCnxn)
[2021-10-11 09:40:09,548] INFO Session establishment complete on server zookeeper/10.0.0.244:2181, sessionid = 0x1000a3216940000, negotiated timeout = 6000 (org.apache.zookeeper.ClientCnxn)
[2021-10-11 09:40:09,552] INFO [ZooKeeperClient] Connected. (kafka.zookeeper.ZooKeeperClient)
[2021-10-11 09:40:10,034] INFO Cluster ID = noST-tr5RnCzYIxN8vb43w (kafka.server.KafkaServer)
[2021-10-11 09:40:10,048] WARN No meta.properties file under dir /kafka/kafka-logs-kafka-556d74b878-b9rhz/meta.properties (kafka.server.BrokerMetadataCheckpoint)
[2021-10-11 09:40:10,139] INFO KafkaConfig values: 
	advertised.host.name = null
	advertised.listeners = PLAINTEXT://kafka:9092
	advertised.port = null
	alter.config.policy.class.name = null
	alter.log.dirs.replication.quota.window.num = 11
	alter.log.dirs.replication.quota.window.size.seconds = 1
	authorizer.class.name = 
	auto.create.topics.enable = true
	auto.leader.rebalance.enable = true
	background.threads = 10
	broker.id = -1
	broker.id.generation.enable = true
	broker.rack = null
	client.quota.callback.class = null
	compression.type = producer
	connections.max.idle.ms = 600000
	controlled.shutdown.enable = true
	controlled.shutdown.max.retries = 3
	controlled.shutdown.retry.backoff.ms = 5000
	controller.socket.timeout.ms = 30000
	create.topic.policy.class.name = null
	default.replication.factor = 1
	delegation.token.expiry.check.interval.ms = 3600000
	delegation.token.expiry.time.ms = 86400000
	delegation.token.master.key = null
	delegation.token.max.lifetime.ms = 604800000
	delete.records.purgatory.purge.interval.requests = 1
	delete.topic.enable = true
	fetch.purgatory.purge.interval.requests = 1000
	group.initial.rebalance.delay.ms = 0
	group.max.session.timeout.ms = 300000
	group.min.session.timeout.ms = 6000
	host.name = 
	inter.broker.listener.name = null
	inter.broker.protocol.version = 2.0-IV1
	leader.imbalance.check.interval.seconds = 300
	leader.imbalance.per.broker.percentage = 10
	listener.security.protocol.map = PLAINTEXT:PLAINTEXT,SSL:SSL,SASL_PLAINTEXT:SASL_PLAINTEXT,SASL_SSL:SASL_SSL
	listeners = PLAINTEXT://:9092
	log.cleaner.backoff.ms = 15000
	log.cleaner.dedupe.buffer.size = 134217728
	log.cleaner.delete.retention.ms = 86400000
	log.cleaner.enable = true
	log.cleaner.io.buffer.load.factor = 0.9
	log.cleaner.io.buffer.size = 524288
	log.cleaner.io.max.bytes.per.second = 1.7976931348623157E308
	log.cleaner.min.cleanable.ratio = 0.5
	log.cleaner.min.compaction.lag.ms = 0
	log.cleaner.threads = 1
	log.cleanup.policy = [delete]
	log.dir = /tmp/kafka-logs
	log.dirs = /kafka/kafka-logs-kafka-556d74b878-b9rhz
	log.flush.interval.messages = 9223372036854775807
	log.flush.interval.ms = null
	log.flush.offset.checkpoint.interval.ms = 60000
	log.flush.scheduler.interval.ms = 9223372036854775807
	log.flush.start.offset.checkpoint.interval.ms = 60000
	log.index.interval.bytes = 4096
	log.index.size.max.bytes = 10485760
	log.message.downconversion.enable = true
	log.message.format.version = 2.0-IV1
	log.message.timestamp.difference.max.ms = 9223372036854775807
	log.message.timestamp.type = CreateTime
	log.preallocate = false
	log.retention.bytes = -1
	log.retention.check.interval.ms = 300000
	log.retention.hours = 168
	log.retention.minutes = null
	log.retention.ms = null
	log.roll.hours = 168
	log.roll.jitter.hours = 0
	log.roll.jitter.ms = null
	log.roll.ms = null
	log.segment.bytes = 1073741824
	log.segment.delete.delay.ms = 60000
	max.connections.per.ip = 2147483647
	max.connections.per.ip.overrides = 
	max.incremental.fetch.session.cache.slots = 1000
	message.max.bytes = 1000012
	metric.reporters = []
	metrics.num.samples = 2
	metrics.recording.level = INFO
	metrics.sample.window.ms = 30000
	min.insync.replicas = 1
	num.io.threads = 8
	num.network.threads = 3
	num.partitions = 1
	num.recovery.threads.per.data.dir = 1
	num.replica.alter.log.dirs.threads = null
	num.replica.fetchers = 1
	offset.metadata.max.bytes = 4096
	offsets.commit.required.acks = -1
	offsets.commit.timeout.ms = 5000
	offsets.load.buffer.size = 5242880
	offsets.retention.check.interval.ms = 600000
	offsets.retention.minutes = 10080
	offsets.topic.compression.codec = 0
	offsets.topic.num.partitions = 50
	offsets.topic.replication.factor = 1
	offsets.topic.segment.bytes = 104857600
	password.encoder.cipher.algorithm = AES/CBC/PKCS5Padding
	password.encoder.iterations = 4096
	password.encoder.key.length = 128
	password.encoder.keyfactory.algorithm = null
	password.encoder.old.secret = null
	password.encoder.secret = null
	port = 9092
	principal.builder.class = null
	producer.purgatory.purge.interval.requests = 1000
	queued.max.request.bytes = -1
	queued.max.requests = 500
	quota.consumer.default = 9223372036854775807
	quota.producer.default = 9223372036854775807
	quota.window.num = 11
	quota.window.size.seconds = 1
	replica.fetch.backoff.ms = 1000
	replica.fetch.max.bytes = 1048576
	replica.fetch.min.bytes = 1
	replica.fetch.response.max.bytes = 10485760
	replica.fetch.wait.max.ms = 500
	replica.high.watermark.checkpoint.interval.ms = 5000
	replica.lag.time.max.ms = 10000
	replica.socket.receive.buffer.bytes = 65536
	replica.socket.timeout.ms = 30000
	replication.quota.window.num = 11
	replication.quota.window.size.seconds = 1
	request.timeout.ms = 30000
	reserved.broker.max.id = 1000
	sasl.client.callback.handler.class = null
	sasl.enabled.mechanisms = [GSSAPI]
	sasl.jaas.config = null
	sasl.kerberos.kinit.cmd = /usr/bin/kinit
	sasl.kerberos.min.time.before.relogin = 60000
	sasl.kerberos.principal.to.local.rules = [DEFAULT]
	sasl.kerberos.service.name = null
	sasl.kerberos.ticket.renew.jitter = 0.05
	sasl.kerberos.ticket.renew.window.factor = 0.8
	sasl.login.callback.handler.class = null
	sasl.login.class = null
	sasl.login.refresh.buffer.seconds = 300
	sasl.login.refresh.min.period.seconds = 60
	sasl.login.refresh.window.factor = 0.8
	sasl.login.refresh.window.jitter = 0.05
	sasl.mechanism.inter.broker.protocol = GSSAPI
	sasl.server.callback.handler.class = null
	security.inter.broker.protocol = PLAINTEXT
	socket.receive.buffer.bytes = 102400
	socket.request.max.bytes = 104857600
	socket.send.buffer.bytes = 102400
	ssl.cipher.suites = []
	ssl.client.auth = none
	ssl.enabled.protocols = [TLSv1.2, TLSv1.1, TLSv1]
	ssl.endpoint.identification.algorithm = https
	ssl.key.password = null
	ssl.keymanager.algorithm = SunX509
	ssl.keystore.location = null
	ssl.keystore.password = null
	ssl.keystore.type = JKS
	ssl.protocol = TLS
	ssl.provider = null
	ssl.secure.random.implementation = null
	ssl.trustmanager.algorithm = PKIX
	ssl.truststore.location = null
	ssl.truststore.password = null
	ssl.truststore.type = JKS
	transaction.abort.timed.out.transaction.cleanup.interval.ms = 60000
	transaction.max.timeout.ms = 900000
	transaction.remove.expired.transaction.cleanup.interval.ms = 3600000
	transaction.state.log.load.buffer.size = 5242880
	transaction.state.log.min.isr = 1
	transaction.state.log.num.partitions = 50
	transaction.state.log.replication.factor = 1
	transaction.state.log.segment.bytes = 104857600
	transactional.id.expiration.ms = 604800000
	unclean.leader.election.enable = false
	zookeeper.connect = zookeeper:2181
	zookeeper.connection.timeout.ms = 6000
	zookeeper.max.in.flight.requests = 10
	zookeeper.session.timeout.ms = 6000
	zookeeper.set.acl = false
	zookeeper.sync.time.ms = 2000
 (kafka.server.KafkaConfig)
[2021-10-11 09:40:10,150] INFO KafkaConfig values: 
	advertised.host.name = null
	advertised.listeners = PLAINTEXT://kafka:9092
	advertised.port = null
	alter.config.policy.class.name = null
	alter.log.dirs.replication.quota.window.num = 11
	alter.log.dirs.replication.quota.window.size.seconds = 1
	authorizer.class.name = 
	auto.create.topics.enable = true
	auto.leader.rebalance.enable = true
	background.threads = 10
	broker.id = -1
	broker.id.generation.enable = true
	broker.rack = null
	client.quota.callback.class = null
	compression.type = producer
	connections.max.idle.ms = 600000
	controlled.shutdown.enable = true
	controlled.shutdown.max.retries = 3
	controlled.shutdown.retry.backoff.ms = 5000
	controller.socket.timeout.ms = 30000
	create.topic.policy.class.name = null
	default.replication.factor = 1
	delegation.token.expiry.check.interval.ms = 3600000
	delegation.token.expiry.time.ms = 86400000
	delegation.token.master.key = null
	delegation.token.max.lifetime.ms = 604800000
	delete.records.purgatory.purge.interval.requests = 1
	delete.topic.enable = true
	fetch.purgatory.purge.interval.requests = 1000
	group.initial.rebalance.delay.ms = 0
	group.max.session.timeout.ms = 300000
	group.min.session.timeout.ms = 6000
	host.name = 
	inter.broker.listener.name = null
	inter.broker.protocol.version = 2.0-IV1
	leader.imbalance.check.interval.seconds = 300
	leader.imbalance.per.broker.percentage = 10
	listener.security.protocol.map = PLAINTEXT:PLAINTEXT,SSL:SSL,SASL_PLAINTEXT:SASL_PLAINTEXT,SASL_SSL:SASL_SSL
	listeners = PLAINTEXT://:9092
	log.cleaner.backoff.ms = 15000
	log.cleaner.dedupe.buffer.size = 134217728
	log.cleaner.delete.retention.ms = 86400000
	log.cleaner.enable = true
	log.cleaner.io.buffer.load.factor = 0.9
	log.cleaner.io.buffer.size = 524288
	log.cleaner.io.max.bytes.per.second = 1.7976931348623157E308
	log.cleaner.min.cleanable.ratio = 0.5
	log.cleaner.min.compaction.lag.ms = 0
	log.cleaner.threads = 1
	log.cleanup.policy = [delete]
	log.dir = /tmp/kafka-logs
	log.dirs = /kafka/kafka-logs-kafka-556d74b878-b9rhz
	log.flush.interval.messages = 9223372036854775807
	log.flush.interval.ms = null
	log.flush.offset.checkpoint.interval.ms = 60000
	log.flush.scheduler.interval.ms = 9223372036854775807
	log.flush.start.offset.checkpoint.interval.ms = 60000
	log.index.interval.bytes = 4096
	log.index.size.max.bytes = 10485760
	log.message.downconversion.enable = true
	log.message.format.version = 2.0-IV1
	log.message.timestamp.difference.max.ms = 9223372036854775807
	log.message.timestamp.type = CreateTime
	log.preallocate = false
	log.retention.bytes = -1
	log.retention.check.interval.ms = 300000
	log.retention.hours = 168
	log.retention.minutes = null
	log.retention.ms = null
	log.roll.hours = 168
	log.roll.jitter.hours = 0
	log.roll.jitter.ms = null
	log.roll.ms = null
	log.segment.bytes = 1073741824
	log.segment.delete.delay.ms = 60000
	max.connections.per.ip = 2147483647
	max.connections.per.ip.overrides = 
	max.incremental.fetch.session.cache.slots = 1000
	message.max.bytes = 1000012
	metric.reporters = []
	metrics.num.samples = 2
	metrics.recording.level = INFO
	metrics.sample.window.ms = 30000
	min.insync.replicas = 1
	num.io.threads = 8
	num.network.threads = 3
	num.partitions = 1
	num.recovery.threads.per.data.dir = 1
	num.replica.alter.log.dirs.threads = null
	num.replica.fetchers = 1
	offset.metadata.max.bytes = 4096
	offsets.commit.required.acks = -1
	offsets.commit.timeout.ms = 5000
	offsets.load.buffer.size = 5242880
	offsets.retention.check.interval.ms = 600000
	offsets.retention.minutes = 10080
	offsets.topic.compression.codec = 0
	offsets.topic.num.partitions = 50
	offsets.topic.replication.factor = 1
	offsets.topic.segment.bytes = 104857600
	password.encoder.cipher.algorithm = AES/CBC/PKCS5Padding
	password.encoder.iterations = 4096
	password.encoder.key.length = 128
	password.encoder.keyfactory.algorithm = null
	password.encoder.old.secret = null
	password.encoder.secret = null
	port = 9092
	principal.builder.class = null
	producer.purgatory.purge.interval.requests = 1000
	queued.max.request.bytes = -1
	queued.max.requests = 500
	quota.consumer.default = 9223372036854775807
	quota.producer.default = 9223372036854775807
	quota.window.num = 11
	quota.window.size.seconds = 1
	replica.fetch.backoff.ms = 1000
	replica.fetch.max.bytes = 1048576
	replica.fetch.min.bytes = 1
	replica.fetch.response.max.bytes = 10485760
	replica.fetch.wait.max.ms = 500
	replica.high.watermark.checkpoint.interval.ms = 5000
	replica.lag.time.max.ms = 10000
	replica.socket.receive.buffer.bytes = 65536
	replica.socket.timeout.ms = 30000
	replication.quota.window.num = 11
	replication.quota.window.size.seconds = 1
	request.timeout.ms = 30000
	reserved.broker.max.id = 1000
	sasl.client.callback.handler.class = null
	sasl.enabled.mechanisms = [GSSAPI]
	sasl.jaas.config = null
	sasl.kerberos.kinit.cmd = /usr/bin/kinit
	sasl.kerberos.min.time.before.relogin = 60000
	sasl.kerberos.principal.to.local.rules = [DEFAULT]
	sasl.kerberos.service.name = null
	sasl.kerberos.ticket.renew.jitter = 0.05
	sasl.kerberos.ticket.renew.window.factor = 0.8
	sasl.login.callback.handler.class = null
	sasl.login.class = null
	sasl.login.refresh.buffer.seconds = 300
	sasl.login.refresh.min.period.seconds = 60
	sasl.login.refresh.window.factor = 0.8
	sasl.login.refresh.window.jitter = 0.05
	sasl.mechanism.inter.broker.protocol = GSSAPI
	sasl.server.callback.handler.class = null
	security.inter.broker.protocol = PLAINTEXT
	socket.receive.buffer.bytes = 102400
	socket.request.max.bytes = 104857600
	socket.send.buffer.bytes = 102400
	ssl.cipher.suites = []
	ssl.client.auth = none
	ssl.enabled.protocols = [TLSv1.2, TLSv1.1, TLSv1]
	ssl.endpoint.identification.algorithm = https
	ssl.key.password = null
	ssl.keymanager.algorithm = SunX509
	ssl.keystore.location = null
	ssl.keystore.password = null
	ssl.keystore.type = JKS
	ssl.protocol = TLS
	ssl.provider = null
	ssl.secure.random.implementation = null
	ssl.trustmanager.algorithm = PKIX
	ssl.truststore.location = null
	ssl.truststore.password = null
	ssl.truststore.type = JKS
	transaction.abort.timed.out.transaction.cleanup.interval.ms = 60000
	transaction.max.timeout.ms = 900000
	transaction.remove.expired.transaction.cleanup.interval.ms = 3600000
	transaction.state.log.load.buffer.size = 5242880
	transaction.state.log.min.isr = 1
	transaction.state.log.num.partitions = 50
	transaction.state.log.replication.factor = 1
	transaction.state.log.segment.bytes = 104857600
	transactional.id.expiration.ms = 604800000
	unclean.leader.election.enable = false
	zookeeper.connect = zookeeper:2181
	zookeeper.connection.timeout.ms = 6000
	zookeeper.max.in.flight.requests = 10
	zookeeper.session.timeout.ms = 6000
	zookeeper.set.acl = false
	zookeeper.sync.time.ms = 2000
 (kafka.server.KafkaConfig)
[2021-10-11 09:40:10,183] INFO [ThrottledChannelReaper-Fetch]: Starting (kafka.server.ClientQuotaManager$ThrottledChannelReaper)
[2021-10-11 09:40:10,184] INFO [ThrottledChannelReaper-Produce]: Starting (kafka.server.ClientQuotaManager$ThrottledChannelReaper)
[2021-10-11 09:40:10,185] INFO [ThrottledChannelReaper-Request]: Starting (kafka.server.ClientQuotaManager$ThrottledChannelReaper)
[2021-10-11 09:40:10,219] INFO Log directory /kafka/kafka-logs-kafka-556d74b878-b9rhz not found, creating it. (kafka.log.LogManager)
[2021-10-11 09:40:10,231] INFO Loading logs. (kafka.log.LogManager)
[2021-10-11 09:40:10,239] INFO Logs loading complete in 8 ms. (kafka.log.LogManager)
[2021-10-11 09:40:10,251] INFO Starting log cleanup with a period of 300000 ms. (kafka.log.LogManager)
[2021-10-11 09:40:10,253] INFO Starting log flusher with a default period of 9223372036854775807 ms. (kafka.log.LogManager)
[2021-10-11 09:40:10,837] INFO Awaiting socket connections on 0.0.0.0:9092. (kafka.network.Acceptor)
[2021-10-11 09:40:10,882] INFO [SocketServer brokerId=1001] Started 1 acceptor threads (kafka.network.SocketServer)
[2021-10-11 09:40:10,910] INFO [ExpirationReaper-1001-Produce]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2021-10-11 09:40:10,911] INFO [ExpirationReaper-1001-Fetch]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2021-10-11 09:40:10,912] INFO [ExpirationReaper-1001-DeleteRecords]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2021-10-11 09:40:10,929] INFO [LogDirFailureHandler]: Starting (kafka.server.ReplicaManager$LogDirFailureHandler)
[2021-10-11 09:40:10,980] INFO Creating /brokers/ids/1001 (is it secure? false) (kafka.zk.KafkaZkClient)
[2021-10-11 09:40:10,986] INFO Result of znode creation at /brokers/ids/1001 is: OK (kafka.zk.KafkaZkClient)
[2021-10-11 09:40:10,987] INFO Registered broker 1001 at path /brokers/ids/1001 with addresses: ArrayBuffer(EndPoint(kafka,9092,ListenerName(PLAINTEXT),PLAINTEXT)) (kafka.zk.KafkaZkClient)
[2021-10-11 09:40:10,990] WARN No meta.properties file under dir /kafka/kafka-logs-kafka-556d74b878-b9rhz/meta.properties (kafka.server.BrokerMetadataCheckpoint)
[2021-10-11 09:40:11,067] INFO [ExpirationReaper-1001-topic]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2021-10-11 09:40:11,071] INFO [ExpirationReaper-1001-Heartbeat]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2021-10-11 09:40:11,073] INFO [ExpirationReaper-1001-Rebalance]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2021-10-11 09:40:11,073] INFO Creating /controller (is it secure? false) (kafka.zk.KafkaZkClient)
[2021-10-11 09:40:11,080] INFO Result of znode creation at /controller is: OK (kafka.zk.KafkaZkClient)
[2021-10-11 09:40:11,099] INFO [GroupCoordinator 1001]: Starting up. (kafka.coordinator.group.GroupCoordinator)
[2021-10-11 09:40:11,101] INFO [GroupCoordinator 1001]: Startup complete. (kafka.coordinator.group.GroupCoordinator)
[2021-10-11 09:40:11,103] INFO [GroupMetadataManager brokerId=1001] Removed 0 expired offsets in 3 milliseconds. (kafka.coordinator.group.GroupMetadataManager)
[2021-10-11 09:40:11,118] INFO [ProducerId Manager 1001]: Acquired new producerId block (brokerId:1001,blockStartProducerId:0,blockEndProducerId:999) by writing to Zk with path version 1 (kafka.coordinator.transaction.ProducerIdManager)
[2021-10-11 09:40:11,149] INFO [TransactionCoordinator id=1001] Starting up. (kafka.coordinator.transaction.TransactionCoordinator)
[2021-10-11 09:40:11,151] INFO [Transaction Marker Channel Manager 1001]: Starting (kafka.coordinator.transaction.TransactionMarkerChannelManager)
[2021-10-11 09:40:11,152] INFO [TransactionCoordinator id=1001] Startup complete. (kafka.coordinator.transaction.TransactionCoordinator)
[2021-10-11 09:40:11,206] INFO [/config/changes-event-process-thread]: Starting (kafka.common.ZkNodeChangeNotificationListener$ChangeEventProcessThread)
[2021-10-11 09:40:11,225] INFO [SocketServer brokerId=1001] Started processors for 1 acceptors (kafka.network.SocketServer)
[2021-10-11 09:40:11,228] INFO Kafka version : 2.0.1 (org.apache.kafka.common.utils.AppInfoParser)
[2021-10-11 09:40:11,228] INFO Kafka commitId : fa14705e51bd2ce5 (org.apache.kafka.common.utils.AppInfoParser)
[2021-10-11 09:40:11,230] INFO [KafkaServer id=1001] started (kafka.server.KafkaServer)

 ```
