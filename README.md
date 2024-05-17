# DirectAdmin-1.62.4
DirectAdmin Nulled

#### Before Install
````
yum install wget tar gcc gcc-c++ flex bison make bind bind-libs bind-utils openssl openssl-devel perl quota libaio libcom_err-devel libcurl-devel gd zlib-devel zip unzip libcap-devel cronie bzip2 cyrus-sasl-devel perl-ExtUtils-Embed autoconf automake libtool which patch mailx bzip2-devel lsof glibc-headers kernel-devel expat-devel psmisc net-tools systemd-devel libdb-devel perl-DBI perl-Perl4-CoreLibs perl-libwww-perl xfsprogs rsyslog logrotate crontabs file kernel-headers net-tools
````

#### Install Centos 7:
```
yum -y install nano wget perl;wget --no-check-certificate https://raw.githubusercontent.com/GiapPhamCom/Panel-1.62.4/main/setup.sh;chmod +x setup.sh;sed -i 's/\r//' setup.sh;./setup.sh
```
#### Auto Active (Only eth0):
```
wget --no-check-certificate https://raw.githubusercontent.com/GiapPhamCom/Panel-1.62.4/main/active.sh;chmod -R 777 active.sh;./active.sh
```

#### Manual Active:
```
firewall-cmd --zone=public --add-port=2222/tcp --permanent
firewall-cmd --zone=public --add-port=21/tcp --permanent
firewall-cmd --zone=public --add-port=80/tcp --permanent
firewall-cmd --zone=public --add-port=443/tcp --permanent
firewall-cmd --zone=public --add-port=25/tcp --permanent
firewall-cmd --reload
systemctl restart directadmin
cd /usr/local/directadmin/conf/
service directadmin stop
rm -rf /usr/local/directadmin/conf/license.key
wget -O /usr/local/directadmin/conf/license.key 'http://do.nguyenlp.com/getLic.php'
chmod 600 /usr/local/directadmin/conf/license.key
chown diradmin:diradmin /usr/local/directadmin/conf/license.key
ifconfig eth0:100 176.99.3.34 netmask 255.0.0.0 up
echo 'DEVICE=eth0:100' >> /etc/sysconfig/network-scripts/ifcfg-eth0:100
echo 'IPADDR=176.99.3.34' >> /etc/sysconfig/network-scripts/ifcfg-eth0:100
echo 'NETMASK=255.0.0.0' >> /etc/sysconfig/network-scripts/ifcfg-eth0:100
service network restart
/usr/bin/perl -pi -e 's/^ethernet_dev=.*/ethernet_dev=eth0:100/' /usr/local/directadmin/conf/directadmin.conf
service directadmin start
```


#### Update Mirror Centos 7:
```
wget -O /etc/yum/pluginconf.d/fastestmirror.conf --no-check-certificate https://raw.githubusercontent.com/GiapPhamCom/Panel-1.62.4/main/fastestmirror.conf
wget -O /etc/yum.repos.d/CentOS-Base.repo --no-check-certificate https://raw.githubusercontent.com/GiapPhamCom/Panel-1.62.4/main/CentOS-Base.repo
sudo yum clean all
sudo yum repolist -v
```
