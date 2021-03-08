# Java Configurations

_Java 8 and Java 11 are supported_

* sudo yum -y install openjdk-8-jdk

```text
vi ~/.bash_profile
export JAVA_HOME=/apps/jdk1.8.0_131/ export PATH=$PATH:/apps/jdk1.8.0_131/bin
source ~/.bash_profile
echo $JAVA_HOME
echo $PATH
java -version
```



* export KAFKA\_HEAP\_OPTS="-Xmx512m -Xms512M"

### Production Configuration

-Xmx6g -Xms6g -XX:MetaspaceSize=96m -XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:InitiatingHeapOccupancyPercent=35 -XX:G1HeapRegionSize=16M -XX:MinMetaspaceFreeRatio=50 -XX:MaxMetaspaceFreeRatio=80 -XX:+ExplicitGCInvokesConcurrent

