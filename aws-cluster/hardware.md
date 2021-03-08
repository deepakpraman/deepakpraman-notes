# Hardware



#### Setup VMs

* sudo yum update
* sudo yum -y install wget ca-certificates zip net-tools vim nano tar netcat
* Add hosts entries \(mocking DNS\) - put relevant IPs here

```text
echo "ip1 kafka1 
      /ip2 zookeeper1 
      /ip3 kafka2 
      /ip4 zookeeper2 
      /ip5 kafka3 
      /ip6 zookeeper3" 
      /| sudo tee --append /etc/hosts
```



## Storage 

* add storage ssds
* mount the drives 
* define storage paths for brokers

### **Production Configurations**

Refer : [https://docs.confluent.io/5.5.0/installation/system-requirements.html](https://docs.confluent.io/5.5.0/installation/system-requirements.html)

