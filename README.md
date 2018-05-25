## Docker-compose 构建LNMP环境

docker-compose 利用yml 文件实现多个容器的快速构建，帮助提高构建效率。
   
### Windows 7 安装
windows 7 需要安装docker toolbox 来实现Docker
  
* [下载docker toolbox](https://download.docker.com/win/stable/DockerToolbox.exe)
* [安装参考](https://docs.docker.com/toolbox/toolbox_install_windows/#step-2-install-docker-toolbox)

### Windows 10 安装
因 windows 10 专业版开始默认具有 Hyper-V 虚拟机，我们可以直接安装Docker。

* [docker 下载页](https://store.docker.com/editions/community/docker-ce-desktop-windows)

* 选择下载 Docker CE stable 版本



### 构建环境

* 拉取项目
* 执行命令构建
* 测试访问

1、 拉取项目

```
git clone https://github.com/merle-song/docker-lnmp.git
```

2、目录结构

```
lnmp
├── mysql
│   ├── data
│   └── my.cnf
├── nginx
│   ├── nginx.conf
│   ├── conf.d
│     └── default.conf   //默认nginx站点配置文件，请自行配置
│   ├── log
│      └── error.log
├── php
│   ├── Dockerfile
│   ├── www.conf
│   ├── php-fpm.conf
│   ├── php.ini
│   └── log
│       └── php-fpm.log
├── web
│   └── index.html
└── docker-compose.yml
```
3、执行构建命令，在项目目录下执行
```
docker-compose up
```
3.1、如需要后台执行
```
docker-compose up -d
```

4、测试访问
```
http://127.0.0.1
```

Ps.项目需要访问Mysql
```
DB_HOST=mysql  //不需要填写ip地址
```






