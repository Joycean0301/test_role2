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

## 
```


```

## 
```


```

## 
```


```

## 
```


```

## 
```


```

## 
```


```

## 
```


```
