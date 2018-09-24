# mysql_2_master
mysql cluster for 2 master,test by docker mysql:5.7 image.
- 测试步骤
```
# git clone https://github.com/simonzhu2019/mysql_2_master.git
# cd mysql_2_master
# docker-compose up -d
```

- 配置说明
```
# cat m1/mysqld.cnf
[mysqld]
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
datadir         = /var/lib/mysql
#log-error      = /var/log/mysql/error.log
# By default we only accept connections from localhost
#bind-address   = 127.0.0.1
# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0

# [mysqld] 
#启用二进制事务log
log-bin=mysql-bin
# 定义不同的服务器ID
server-id=11

# 双主服务，避免自增主键冲突，步长设置2
# 不同服务器设置不同起始点
auto_increment_increment=2
auto_increment_offset=1
```
