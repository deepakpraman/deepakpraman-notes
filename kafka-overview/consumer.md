# Consumer

## Console Consumer

```java
./bin/kafka-console-consumer --bootstrap-server localhost:9076 --topic myTopic  --from-beginning
```

## Read records from the \(x\) partition starting at \(y\)offset

```text
./bin/kafka-console-consumer --topic myTopic --bootstrap-server localhost:9072  --property print.key=true  --property key.separator=":"  --partition x  --offset y
```

**Consumer Group Info**

```text
./bin/kafka-consumer-groups  --bootstrap-server kb1:9092 --all-groups --describe --timeout 50000
```

