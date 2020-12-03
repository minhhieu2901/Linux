# Hướng dẫn cài đặt email server zimbra trên CentOS 7

## 1. Chuẩn bị

- Phiên bản: zimbra 8.8 trên CentOS 7

- Cấu hình tối thiểu: RAM: 2GB, Disk: 30GB, CPU: 2 core

- Chuẩn bị tên miền: Một tên miền đã trỏ bản ghi mail (điều này là cần thiết vì trong quá trình cài đặt sẽ yêu cầu tên miền phân giải được bản ghi mail).

Tên miền: hieunm29198.xyz

- **Update OS**
```
yum install epel-release -y
yum update -y
```
- **Cài đặt NTP đồng bộ thời gian**
```
yum install chrony -y 
systemctl start chronyd 
systemctl enable chronyd
systemctl restart chronyd 
chronyc sources -v
ln -f -s /usr/share/zoneinfo/Asia/Ho_Chi_Minh /etc/localtime
```

- Thiết lập Firewall, selinux và một số package cơ bản
```
sudo systemctl disable firewalld
sudo systemctl stop firewalld
sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux
sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/selinux/config
yum install -y git wget byobu


service sendmail stop
service iptables stop
service ip6tables stop
chkconfig sendmail off
chkconfig iptables off
chkconfig ip6tables off
service httpd stop
chkconfig httpd off

init 6
```

## 2. Cài đặt email server zimbra

- **Cài package cần thiết**
```
yum install unzip net-tools sysstat openssh-clients perl-core libaio nmap-ncat libstdc++.so.6 nano wget -y 
```

- **Đổi host name, add hostname**
```
hostnamectl set-hostname mail.hieunm29198.xyz
cat << EOF >> /etc/hosts
103.124.95.237 mail.hieunm29198.xyz
EOF

init 6
```

<img src="https://image.prntscr.com/image/oAx4auAMQj620PRS04c1_Q.png" >

Lưu ý: File `/etc/resolv.conf` phải khai báo `nameserver 8.8.8.8` để có thể connect tới server download bộ cài zimbra.

- **Download bộ cài đặt zimbra 8.8**
```
wget https://files.zimbra.com/downloads/8.8.12_GA/zcs-8.8.12_GA_3794.RHEL7_64.20190329045002.tgz
```

- **Giải nén và cài đặt**
```
tar -xvf zcs-8.8.12_GA_3794.RHEL7_64.20190329045002.tgz
cd zcs-8.8.12_GA_3794.RHEL7_64.20190329045002
./install.sh
```
Ở bước này lưu ý một số tùy chọn cài đặt như sau:
```
Do you agree with the terms of the software license agreement? [N] Y

Use Zimbra's package repository [Y] Y

Select the packages to install

Install zimbra-ldap [Y] Y

Install zimbra-logger [Y] Y

Install zimbra-mta [Y] Y

Install zimbra-dnscache [Y] N

Install zimbra-snmp [Y] Y

Install zimbra-store [Y] Y

Install zimbra-apache [Y] Y

Install zimbra-spell [Y] Y

Install zimbra-memcached [Y] Y

Install zimbra-proxy [Y] Y

Install zimbra-drive [Y] Y

Install zimbra-imapd (BETA - for evaluation only) [N] N

The system will be modified.  Continue? [N] Y
```

<img src=https://image.prntscr.com/image/t-bNpL7jT8iR1TKx99gXvA.png>
<img src=https://image.prntscr.com/image/wqsRHWTHRlmsHjghxqbkEw.png>

Xác nhận thay đổi tên domain và nhập domain

```
It is suggested that the domain name have an MX record configured in DNS
Change domain name? [Yes] Yes
Create domain: [mail.hieunm29198.xyz] hieunm29198.xyz
```
<img src=https://image.prntscr.com/image/R7jC3KTLQmmjHPfSDhH3LQ.png>

- **Hệ thống sẽ báo password account admin zimbra chưa được nhập, cần đặt lại password admin zimbra**
```
Chọn 6 -> Chọn 4 -> Nhập pass => Enter

Address unconfigured (**) items  (? - help) 6

Select, or 'r' for previous menu [r] 4

Password for admin@hieunm29198.xyz (min 6 characters): [94llsjSBXp] 14032016Ht
```

Chọn `r` để quay lại menu chính

```
Select from menu, or press 'a' to apply config (? - help)
*** CONFIGURATION COMPLETE - press 'a' to apply
Select from menu, or press 'a' to apply config (? - help) a
Save configuration data to a file? [Yes] Yes
Save config in file: [/opt/zimbra/config.16239]
Saving config in /opt/zimbra/config.16239...done.
The system will be modified - continue? [No] Yes
Operations logged to /tmp/zmsetup.20200321-225029.log
Setting local config values...
```

<img src=https://image.prntscr.com/image/hJIEMUY1Qx2-bwqlJfAgXQ.png>

Chờ quá trình lưu cấu hình hoàn tất.

```
Notify Zimbra of your installation? [Yes] Yes
Configuration complete - press return to exit
```
- **Truy cập**

```
https://mail.hieunm29198.xyz:7071
```

Hoặc

```
https://103.124.95.237:7071
```

<img src=https://image.prntscr.com/image/9NvT2NsZSYOOWBqR4aSffw.png>

<img src="https://image.prntscr.com/image/Doe49u32TqOgIuEFjxxS5Q.png">

## 3. Kiểm tra gửi - nhận
Đảm bảo các server zimbra chạy
```
service zimbra status
```
<img src="https://image.prntscr.com/image/JQSainG5TjmxEBadzucIMA.png">

