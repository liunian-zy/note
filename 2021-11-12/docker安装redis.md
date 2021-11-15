### docker安装redis

* 下载镜像

  ```shell
  docker pull redis
  ```

* 运行容器（预先创建redis.conf文件避免在挂载目录时将其当做目录）

  ```shell
  mkdir -p /mydata/redis/conf
  touch /mydata/redis/conf/redis.conf
  
  docker run -p 6379:6379 --name redis \
  -v /mydata/redis/data:/data \
  -v /mydata/redis/conf/redis.conf:/etc/redis/redis.conf \
  -d redis redis-server /etc/redis/redis.conf
  ```

* 设置持久化，在配置文件中添加如下内容

  ```shell
  appendonly yes
  ```

  

