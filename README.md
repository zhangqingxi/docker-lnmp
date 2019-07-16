# Docker LNMP

**Docker** = `docker-compose`

**LNMP** = `Linux` + `NGINX` + `MYSQL` + `PHP`

---

## 目录结构

``` bash
├── .env                        环境配置文件
├── server                      配置文件目录
│   ├── mysql                   MySQL 配置目录
│   │   ├── mysql.cnf           MySQL 用户配置文件
│   │── nginx                   Nginx 配置目录
│   │   ├── conf.d              Nginx 站点配置目录
│   │   │   ├──default.conf     Nginx 站点默认配置
│   │   ├── nginx.conf          Nginx 默认配置文件
│   ├── php73                   PHP73 配置目录
│   │   ├── Doclerfile          PHP73 镜像构建文件
│   │   ├── php.ini             PHP 配置文件  
│   ├── redis                   Redis 配置目录
│   │   ├── redis.conf          Redis 配置文件
├── logs                        日志目录
├── data                        数据数据
├── docker-compose.yml          服务配置文件
```

## 快速使用

``` bash
$ git clone https://github.com/zhangqingxi/docker-lnmp.git --recursive
$ cd docker-lnmp
# 服务选项：nginx、php、mysql、mongo、redis
$ docker-compose up -d php nginx mysql redis
```

OK，环境已经启动，默认站点已经生效 `code/localhost/`，浏览器访问 [http://localhost](http://localhost)


## 基本使用

``` bash
# 服务选项：nginx、php、mysql、redis

# 创建并且启动容器
$ docker-compose up 服务1 服务2 ...

# 创建并且启动所有容器
$ docker-compose up

# 创建并且已后台运行的方式启动容器
$ docker-compose up -d 服务1 服务2 ...

# 启动服务
$ docker-compose start 服务1 服务2 ...

# 停止服务
$ docker-compose stop 服务1 服务2 ...

# 重启服务
$ docker-compose restart 服务1 服务2 ...

# 构建或者重新构建服务
$ docker-compose build 服务1 服务2 ...

# 进入命令行容器
$ docker-compose exec 服务 bash

# 删除并且停止容器
$ docker-compose rm 服务1 服务2 ...

# 停止并删除容器，网络，图像和挂载卷
$ docker-compose down 服务1 服务2 ...
```

## License

[MIT](LICENSE)
