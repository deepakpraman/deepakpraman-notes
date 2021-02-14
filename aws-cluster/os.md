# OS

#### Kernel Limits

There are three settings you must configure properly for the kernel.

* File Descriptors

  You can set these in Cloudera Manager via Kafka &gt; Configuration &gt; Maximum Process File Descriptors. We recommend a configuration of 100,000 or higher.

* Max Memory Map

  You must configure this in your specific kernel settings. We recommend a configuration of 32000 or higher.

* Max Socket Buffer Size

  Set the buffer size larger than any Kafka send buffers that you define.

**VM Swappiness**

#### Synchronize time

