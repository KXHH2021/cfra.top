---
title: mysql的npm包安装
date: 2024-1-4 09:57:03
categories:
  - install mysql
tags:
  - mysql

cover: https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202401040958001.png
---

#### 1.wget

![image-20240104093800958](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202401040938039.png)

`wget https://dev.mysql.com/get/mysql80-community-release-el7-11.noarch.rpm`

#### 2.rpm

![image-20240104094050261](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202401040940285.png)

`rpm -ivh mysql80-community-release-el7-11.noarch.rpm`

#### 3.yum.repos.d

![image-20240104094231219](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202401040942238.png)



`cd /etc/yum.repos.d/`

`ls` and `cat /etc/yum.repos.d/`

发现mysql-community-debuginfo.repo

#### 4.cache

`yum clean all`

`yum makecache`

#### 5.yum install （默认安装mysql 8.0）

`yum install -r mysql-server`

![image-20240104094750388](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202401040947421.png)

yum会自动删除mariadb的一些文件(会影响mysql正常运行)

#### 6.启动mysql服务

`systemctl start mysqld`

#### 7.查看mysql密码

` grep "password" /var/log/mysqld.log`

passw： #,Cgd4n?lrcr

![image-20240104095034858](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202401040950875.png)

#### 8.登录mysql，首次登录需要修改密码才能操作

login：` mysql -uroot -p`

passw： #,Cgd4n?lrcr

#### 9.修改密码

`set password for uname@localhost = password('new password');`