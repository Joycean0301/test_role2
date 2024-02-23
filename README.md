## Open port
```
firewall-cmd --add-port={3306/tcp,4444/tcp,4567/tcp,4568/tcp} --permanent
firewall-cmd --reload
firewall-cmd --list-ports

```

## SELinux
```
setenforce 0
sed -i 's/SELINUX=enforcing/SELINUX=permissive/g' /etc/selinux/config

```

## Percona Repo
```
yum install -y https://repo.percona.com/yum/percona-release-latest.noarch.rpm
percona-release setup pxc-57

```

## Clean
```
yum clean all
yum update -y --skip-broken

```

## 
```


```

## 
```


```

## 
```
ALTER USER 'root'@'localhost' IDENTIFIED BY 'rootPassword';
CREATE USER 'sstuser'@'localhost' IDENTIFIED BY 'sstUserPassword';
GRANT RELOAD, LOCK TABLES, PROCESS, REPLICATION CLIENT ON *.* TO 'sstuser'@'localhost';
FLUSH PRIVILEGES;
exit;

```

## 
```


```

## etc/cnf
```
[mysqld]
pxc_encrypt_cluster_traffic=ON
max_connections= 451
max_allowed_packet= 256M

wsrep_provider=/usr/lib64/galera3/libgalera_smm.so
wsrep_provider_options="cert.optimistic_pa=NO"
wsrep_certification_rules='OPTIMIZED'

wsrep_cluster_name=morpheusdb-cluster
wsrep_cluster_address=gcomm://10.200.4.21,10.200.4.22

wsrep_node_name=morpheus-db-node01
wsrep_node_address=10.200.4.21

wsrep_sst_method=xtrabackup-v2
wsrep_sst_auth=sstuser:sstUserPassword
pxc_strict_mode=PERMISSIVE
wsrep_sync_wait=2

skip-log-bin
default_storage_engine=InnoDB
innodb_autoinc_lock_mode=2
character-set-server=utf8
default_time_zone="+07:00"

```
