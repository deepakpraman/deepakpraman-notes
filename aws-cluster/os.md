# OS

| Component | Description |
| :--- | :--- |
| Operating System | **RHEL 8** |
| Privileges | **ROOT** access prefered |

## **Kernel Limits**

There are three settings you must configure properly for the kernel.

## File Descriptors

We recommend a configuration of 100,000 or higher.

```text
echo "* hard nofile 100000 soft nofile 100000" | sudo tee --append /etc/security/limits.conf
```

## Max Memory Map

You must configure this in your specific kernel settings. We recommend a configuration of 32000 or higher.

`vi /etc/sysctl.conf` 

`vm.max_map_count=32000`

to reload configuration with new value

 `sudo sysctl -p`

## Max Socket Buffer Size

Set the buffer size larger than any Kafka send buffers that you define.

## VM Swappiness

echo 1 &gt; /proc/sys/vm/swappiness

sysctl -w vm.swappiness=1

echo "vm.swappiness = 1" &gt;&gt; /etc/sysctl.conf

## Synchronize Time

* **Add Google NTP Server**

  sed -i '/^pool/c\pool time.google.com iburst' /etc/chrony.conf

  **Set timezone to Asia/Colombo**

  timedatectl set-timezone Asia/Colombo

  **Enable NTP time synchronization**

  timedatectl set-ntp true

## Start and enable chronyd service

systemctl enable --now chronyd && systemctl status chronyd

## Verify synchronisation state

ntpstat

## Check Chrony Source Statistics

chronyc sourcestats -v

## Start and enable NTP service.

systemctl restart ntpd.service && systemctl enable ntpd.service

