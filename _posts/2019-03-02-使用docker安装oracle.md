---
layout: post
title: 使用docker安装oracle,恢复数据库
date: 2019-03-02
tags: docker,oracle
---

* [拉取镜像](#get-image)
* [部署oracle环境](#set-env)
* [导入dmp数据文件](#dump)

### <a name="get-image"></a>拉取镜像

首先检测仓库里面可用的oracle版本

```
docker search oracle
```

如果远程仓库没有12c版本的话，添加阿里云仓库

```shell 
vi /etc/docker/daemon.json

## 添加一下内容
{
"registry-mirrors": ["https://pee6w651.mirror.aliyuncs.com"]
}
```

挑选12c版本

```
docker pull sath89/oracle-12c
```

也可以在官网上找寻合适的版本, [地址](https://container-registry.oracle.com/pls/apex/f?p=113:1:115813330162073::NO:1:P1_BUSINESS_AREA:3)

如果要安装的是12cR2,可以在阿里云上找，这里有现成的[方案](https://blog.csdn.net/another_liu/article/details/89436340)


拉取完成之后，进入容器

```shell
docker exec -it f8dbc1849055 /bin/bash
```



### <a name="set-env"></a>部署oracle环境

首先以管理员身份登录

```shell
sqlplus / as sysdba 
```

默认的用户名和密码
```
用户名： system
密码： oracle
```

更改超级管理员的密码，并且赋予连接权限

```
alter user sys identified by taxgm2016
grant connect to sys identified by taxgm2016
```

查看当前容器
```
show con_name

CON_NAME
------------------------------
xe
```

创建表空间
```
create  tablespace  [ tablespace  ]
        Datafile [‘D:\database\oracle_table_space\tablespace_name.dbf’] size [1024m]
        autoextend  [on|off] next [526k]  
        [ logging|nologging;]
```

+ tablespace_name是用户自定义的表空间名称，由用户随意命名。
+ datafile 是表空间在本地磁盘的存放路径，由用户自定义，需要注意的是在自定义表空间路径之前，用户要在本地磁盘创建好此路径，因为oracle在执行上述创建表空间SQL 语句时，是不会自动在本地磁盘创建由关键字datafile 指定的路径。
+ dbf格式的文件是oracle规定的表空间文件，也是我们所要创建的表空间，一般为了方便起见，此文件的名称与表空间名称相同，不同也不影响。
+ size 关键字，指定开辟的空间大小，其单位有k 和m。
+ autoextend 关键字，是否为自动扩展表空间，如果为 on，表示可以自动扩展表空间大小，反之为off。Next，用于定义表空间的增长量，即每次自动扩充多少k。
+ logging表示是否需要对DML进行日志记录，记录下的日志可以用于恢复数据。nologging  则表示不需要对DML进行日志记录。

创建新用户

```
create user test identified by 123456 default tablespace  tablespace_name  ;   //其中test为用户名，123456为密码
```

授权

```
grant connect,dba,exp_full_database,imp_full_database to  with  tablespace_name   admin option;
```

### <a name="dump"></a>导入dump数据文件

```
CREATE OR REPLACE DIRECTORY DMPDIR AS 'DIR';  // 引入挂载目录

grant read,write on directory DMPDIR to USERNAME;

impdp tax/taxgm2016@localhost/xe DIRECTORY=DMPDIR DUMPFILE=full.dmp  logfile=oracle.log
```

