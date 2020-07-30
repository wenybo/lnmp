Docker-Compose 编排LNMP环境

清单
	PHP7.2
	Nginx
	MySQL5.6
	Redis
	phpMyAdmin
	phpRedisAdmin


PHP7.2
Nginx
MySQL5.6
Redis
目录结构
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
|----docker-compose.yml                 docker compose 配置文件(完整版: LNMP+Redis+phpMyAdmin+phpRedisAdmin)
|----docker-compose-simplify.yml        docker compose 配置文件(精简版: LNMP+Redis)
准备
# 安装docker和docker-compose
yum -y install epel-release 
yum -y install docker docker-compose

# 启动docker服务
service docker start

# 配置阿里云docker镜像加速器(建议配置加速器, 可以提升docker拉取镜像的速度)
mkdir -p /etc/docker
vim /etc/docker/daemon.json
# 新增下面内容
{
    "registry-mirrors": ["https://8auvmfwy.mirror.aliyuncs.com"]
}
# 重新加载配置、重启docker
systemctl daemon-reload 
systemctl restart docker 
安装
# 克隆项目
git clone https://github.com/godxihua/lnmp.git
# 进入目录
cd Docker-LNMP
# 容器编排
docker-compose -f docker-compose-fast.yml up -d

测试
执行成功

Creating php ... done
Creating nginx ... done
Creating mysql ...
Creating php ...
Creating nginx ...
#Creating phpmyadmin ...
#Creating phpredisadmin ...
