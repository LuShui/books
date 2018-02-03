记一次数据库只从同步配置
	1、主从同步概述



	2、配置

		1、在 master 数据库服务器中创建账号
			GRANT REPLICATION SLAVE,RELOAD,SUPER ON *.*  TO master@'192.168.1.1'  IDENTIFIED BY '1234';
				备注：在master数据库中创建账号，账号名为 master ， 秘密为1234  。可以自己定义

		2、配置master
			server-id=1
			log-bin=mysql-bin
			server-id：为主服务器A的ID值
			log-bin：二进制变更日值

			配置完后重启master数据库


		3、配置slave
			CHANGE MASTER TO MASTER_HOST='192.168.1.1', MASTER_USER='master', MASTER_PASSWORD='1234', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=0;
				MASTER_HOST='192.168.1.1'				master服务器ip	
				MASTER_USER='master'					创建的用户名
				MASTER_PASSWORD='1234'					用户密码

				以下两个可以通过在master中SHOW MASTER STATUS查看
				MASTER_LOG_FILE='mysql-bin.000001'		日志文件名
				MASTER_LOG_POS=0						从哪个位置开始

			重启slave数据库


		4、START SLAVE   开启服务


		以上就是一个最简单的数据库主从配置
		其中mysql版本为	5.5


