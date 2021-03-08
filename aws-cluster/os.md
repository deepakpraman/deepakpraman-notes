# OS

\*\*\*\*

| Component | Description |
| :--- | :--- |
| Number of VMs | 3 |
| Operating System | **RHEL 8** |
| File System | XFS |
| Privileges | **ROOT** access prefered |

\*\*\*\*

**Kernel Limits**

There are three settings you must configure properly for the kernel.

* File Descriptors

  You can set these in Cloudera Manager via Kafka &gt; Configuration &gt; Maximum Process File Descriptors. We recommend a configuration of 100,000 or higher.

```text
echo "* hard nofile 100000 soft nofile 100000" | sudo tee --append /etc/security/limits.conf
```

* Max Memory Map

  You must configure this in your specific kernel settings. We recommend a configuration of 32000 or higher.

* Max Socket Buffer Size

  Set the buffer size larger than any Kafka send buffers that you define.

* VM Swappiness

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

