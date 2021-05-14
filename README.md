# docker-compose 编排LNMP环境  
App list：
- PHP7.2  
- Nginx  
- MySQL5.7  
- Redis  
- PHPmysqladmin  
- PHPredisadmin  
  
默认关闭mysqladmin和redisadmin，如需要，需自行修改docker-compose-fast.yml配置文件  
# 目录结构  
lnmp  
|----docker                             Docker目录  
|--------config                         配置文件目录  
|------------nginx                      nginx配置文件目录  
|--------files                          DockerFile文件目录  
|------------php                        php-fpm DockerFile文件目录  
|----------------Dockerfile             php-fpm DockerFile文件  
|----------------docker-entrypoint.sh   php-fpm 启动脚本  
|------------nginx                      nginx DockerFile文件目录  
|----------------Dockerfile             nginx DockerFile文件  
|----------------docker-entrypoint.sh   nginx 启动脚本  
|--------log                            日志文件目录  
|------------php                        php-fpm日志文件目录  
|------------nginx                      nginx日志文件目录  
|----www                                应用根目录  
|--------index.php                      PHP例程  
|----README.md                          说明文件  
|----docker-compose-fast.yml            docker compose 配置文件  

# 准备  
安装docker和docker-compose  
```
yum -y install epel-release 
yum -y install docker docker-compose
```
# 启动docker服务  
```
systemctl enable docker  
systemctl start docker  
```  

# 安装
1. 克隆项目  
`git clone https://github.com/godxihua/lnmp.git`  
2. 进入目录,容器编排    
```
cd lnmp    
docker-compose -f docker-compose-fast.yml up -d  
```
