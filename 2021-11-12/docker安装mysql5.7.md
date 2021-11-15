### docker安装mysql5.7

* 下载镜像

    ```shell
    docker pull mysql:5.7
    ```

* 运行容器

    ```shell
    docker run -p 3306:3306 --name mysql \
    -v /mydata/mysql/log:/var/log/mysql \
    -v /mydata/mysql/data:/vat/lib/mysql \
    -v /mydata/mysql/conf:/etc/mysql \
    -e MYSQL_ROOT_PASSWORD=root \
    -d mysql:5.7
    ```

* 修改mysql配置文件

  ```shell
  vi /mydata/mysql/conf/my.cnf
  
  [client]
  default-character-set=utf8
  
  [mysql]
  default-character-set=utf8
  
  [mysqld]
  init_connect='SET collation_connection = utf8_unicode_ci'
  init_connect='SET NAMES utf8'
  character-set-server=utf8
  collation-server=utf8_unicode_ci
  skip-character-set-client-handshake
  skip-name-resolve
  ```
  
* 解决MySQL连接慢的问题

  在配置文件中加入如下内容并重启mysql

  ```shell
  [mysqld]
  skip-name-resolve
  ```

  

