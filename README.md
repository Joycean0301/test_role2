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

## 
```


```
