# docker-composer-for-mindoc
 本文主要介绍，在centos/mac下，使用docker-composer快速部署MinDoc+mysql。其他部署方法，请参考，MinDoc中文帮助手册：https://www.iminho.me/wiki/docs/mindoc/mindoc-summary.md

前提：

1. 已安装docker

2. 已安装docker-composer (mac无需单独安装，装docker时已有。centos需要单独安装一下)

######安装docker-compose，只需要两条命令即可#####

假设要安装1.6.2版本，演示命令如下：

curl -L https://github.com/docker/compose/releases/download/1.6.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose

步骤：

1. git clone https://github.com/wasonchung/docker-composer-for-mindoc.git
2. cd docker-composer-for-mindoc
3. docker-composer up -d

4. 在mysql中新建库，以下是命令方式。使用mysql客户端工具也可以。

mysql -h部署这个应用的服务器IP -uroot -p123456

CREATE DATABASE mindoc_db  DEFAULT CHARSET utf8mb4 COLLATE utf8mb4_general_ci;

按ctl+D退出

5. 让mindoc初始化一下mysql。

docker-composer down

docker-composer up -d

6. 配置一下你的hosts, 就可以访问了。用户admin密码是123456




注意事项：

1. 你可以用回自己的mysql，不用容器的。更改/conf/mindoc/conf/app.conf 里的mysql配置。在你的mysql里创建数据库CREATE DATABASE mindoc_db  DEFAULT CHARSET utf8mb4 COLLATE utf8mb4_general_ci; 然后在项目目录中执行docker-composer up -d

2.https证书是自制证书，你可以换回你自己的。

3.如果你安装的docker版本比较旧，你可将docker-compose.yml内的version改为2


