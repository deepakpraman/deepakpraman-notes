# Broker Configs

## Zookeeper Configs

* **zookeeper.connect**

  Specifies the ZooKeeper connection string in the form `hostname:port` where host and port are the host and port of a ZooKeeper server. To allow connecting through other ZooKeeper nodes when that ZooKeeper machine is down you can also specify multiple hosts in the form `hostname1:port1,hostname2:port2,hostname3:port3`.  
  The server can also have a ZooKeeper chroot path as part of its ZooKeeper connection string which puts its data under some path in the global ZooKeeper namespace. For example to give a chroot path of `/chroot/path` you would give the connection string as `hostname1:port1,hostname2:port2,hostname3:port3/chroot/path`.

  | Type: | string |
  | :--- | :--- |
  | Default: |  |
  | Valid Values: |  |
  | Importance: | high |
  | Update Mode: | read-only |

* **zookeeper.connection.timeout.ms**

  The max time that the client waits to establish a connection to zookeeper. If not set, the value in zookeeper.session.timeout.ms is used

  | Type: | int |
  | :--- | :--- |
  | Default: | null |
  | Valid Values: |  |
  | Importance: | high |
  | Update Mode: | read-only |

## Server Basics

* **broker.id**

  The broker id for this server. If unset, a unique broker id will be generated.To avoid conflicts between zookeeper generated broker id's and user configured broker id's, generated broker ids start from reserved.broker.max.id + 1.

  | Type: | int |
  | :--- | :--- |
  | Default: | -1 |
  | Valid Values: |  |
  | Importance: | high |
  | Update Mode: | read-only |

## Socket Settings

* **listeners**

  Listener List - Comma-separated list of URIs we will listen on and the listener names. If the listener name is not a security protocol, listener.security.protocol.map must also be set.  
  Specify hostname as 0.0.0.0 to bind to all interfaces.  
  Leave hostname empty to bind to default interface.  
  Examples of legal listener lists:  
  PLAINTEXT://myhost:9092,SSL://:9091  
  CLIENT://0.0.0.0:9092,REPLICATION://localhost:9093

| Type: | string |
| :--- | :--- |
| Default: | null |
| Valid Values: |  |
| Importance: | high |
| Update Mode: | per-broker |

* **advertised.listeners**

  Listeners to publish to ZooKeeper for clients to use, if different than the `listeners` config property. In IaaS environments, this may need to be different from the interface to which the broker binds. If this is not set, the value for `listeners` will be used. Unlike `listeners` it is not valid to advertise the 0.0.0.0 meta-address.

  * | Type: | string |
    | :--- | :--- |
    | Default: | null |
    | Valid Values: |  |
    | Importance: | high |
    | Update Mode: | per-broker |

* **advertised.port**

  DEPRECATED: only used when `advertised.listeners` or `listeners` are not set. Use `advertised.listeners` instead.  
  The port to publish to ZooKeeper for clients to use. In IaaS environments, this may need to be different from the port to which the broker binds. If this is not set, it will publish the same port that the broker binds to.

  | Type: | int |
  | :--- | :--- |
  | Default: | null |
  | Valid Values: |  |
  | Importance: | high |
  | Update Mode: | read-only |

* **host.name**

  DEPRECATED: only used when `listeners` is not set. Use `listeners` instead.  
  hostname of broker. If this is set, it will only bind to this address. If this is not set, it will bind to all interfaces

  | Type: | string |
  | :--- | :--- |
  | Default: | "" |
  | Valid Values: |  |
  | Importance: | high |
  | Update Mode: | read-only |

* **advertised.host.name**

  DEPRECATED: only used when `advertised.listeners` or `listeners` are not set. Use `advertised.listeners` instead.  
  Hostname to publish to ZooKeeper for clients to use. In IaaS environments, this may need to be different from the interface to which the broker binds. If this is not set, it will use the value for `host.name` if configured. Otherwise it will use the value returned from java.net.InetAddress.getCanonicalHostName\(\).

  | Type: | string |
  | :--- | :--- |
  | Default: | null |
  | Valid Values: |  |
  | Importance: | high |
  | Update Mode: | read-only |

## Transaction Topic Default Configuration

* **auto.create.topics.enable**

  Enable auto creation of topic on the server

  | Type: | boolean |
  | :--- | :--- |
  | Default: | true |
  | Valid Values: |  |
  | Importance: | high |
  | Update Mode: | cluster-wide |

* **num.partitions**

  The default number of log partitions per topic

  | Type: | int |
  | :--- | :--- |
  | Default: | 1 |
  | Valid Values: | \[1,...\] |
  | Importance: | medium |
  | Update Mode: | read-only |

* **min.insync.replicas**

  When a producer sets acks to "all" \(or "-1"\), min.insync.replicas specifies the minimum number of replicas that must acknowledge a write for the write to be considered successful. If this minimum cannot be met, then the producer will raise an exception \(either NotEnoughReplicas or NotEnoughReplicasAfterAppend\).  
  When used together, min.insync.replicas and acks allow you to enforce greater durability guarantees. A typical scenario would be to create a topic with a replication factor of 3, set min.insync.replicas to 2, and produce with acks of "all". This will ensure that the producer raises an exception if a majority of replicas do not receive a write.

  | Type: | int |
  | :--- | :--- |
  | Default: | 1 |
  | Valid Values: | \[1,...\] |
  | Importance: | high |
  | Update Mode: | cluster-wide |

* **transaction.state.log.num.partitions**

  The number of partitions for the transaction topic \(should not change after deployment\).

  | Type: | int |
  | :--- | :--- |
  | Default: | 50 |
  | Valid Values: | \[1,...\] |
  | Importance: | high |
  | Update Mode: | read-only |

* **transaction.state.log.replication.factor**

  The replication factor for the transaction topic \(set higher to ensure availability\). Internal topic creation will fail until the cluster size meets this replication factor requirement.

  | Type: | short |
  | :--- | :--- |
  | Default: | 3 |
  | Valid Values: | \[1,...\] |
  | Importance: | high |
  | Update Mode: | read-only |

* **transaction.state.log.min.isr**

  Overridden min.insync.replicas config for the transaction topic.

  | Type: | int |
  | :--- | :--- |
  | Default: | 2 |
  | Valid Values: | \[1,...\] |
  | Importance: | high |
  | Update Mode: | read-only |

## Thread Configuration

* **background.threads**

  The number of threads to use for various background processing tasks

  | Type: | int |
  | :--- | :--- |
  | Default: | 10 |
  | Valid Values: | \[1,...\] |
  | Importance: | high |
  | Update Mode: | cluster-wide |

* **num.io.threads**

  The number of threads that the server uses for processing requests, which may include disk I/O

  | Type: | int |
  | :--- | :--- |
  | Default: | 8 |
  | Valid Values: | \[1,...\] |
  | Importance: | high |
  | Update Mode: | cluster-wide |

* **num.network.threads**

  The number of threads that the server uses for receiving requests from the network and sending responses to the network

  | Type: | int |
  | :--- | :--- |
  | Default: | 3 |
  | Valid Values: | \[1,...\] |
  | Importance: | high |
  | Update Mode: | cluster-wide |

## Log Configuration

* **log.dirs**

  The directories in which the log data is kept. If not set, the value in log.dir is used

  | Type: | string |
  | :--- | :--- |
  | Default: | null |
  | Valid Values: |  |
  | Importance: | high |
  | Update Mode: | read-only |

* **log.retention.hours**

  The number of hours to keep a log file before deleting it \(in hours\), tertiary to log.retention.ms property

  | Type: | int |
  | :--- | :--- |
  | Default: | 168 |
  | Valid Values: |  |
  | Importance: | high |
  | Update Mode: | read-only |

## Offset Topics Configuration

* **offsets.topic.num.partitions**

  The number of partitions for the offset commit topic \(should not change after deployment\)

  | Type: | int |
  | :--- | :--- |
  | Default: | 50 |
  | Valid Values: | \[1,...\] |
  | Importance: | high |
  | Update Mode: | read-only |

* **offsets.topic.replication.factor**

  The replication factor for the offsets topic \(set higher to ensure availability\). Internal topic creation will fail until the cluster size meets this replication factor requirement.

  | Type: | short |
  | :--- | :--- |
  | Default: | 3 |
  | Valid Values: | \[1,...\] |
  | Importance: | high |
  | Update Mode: | read-only |

