### 安装教程：
安装docker
```
bash <(curl -sSL https://gitee.com/SuperManito/LinuxMirrors/raw/main/DockerInstallation.sh)

```
1. 确保docker.sock存在(只要安装了docker一般都会有)
```
ls -alh /var/run/docker.sock
```
2. 下载chrome镜像（仅需执行一次，后续更新不用重新下载)
```
sudo docker pull selenoid/chrome:89.0
```
3. 下载rubyangxg/jd-qinglong镜像
```
sudo docker pull rubyangxg/jd-qinglong:1.7
```
4. 下载配置文件模板，根据需要修改，不要缺少此文件
```
wget -O env.properties https://raw.githubusercontent.com/rubyangxg/jd-qinglong/master/env.template.properties
```
国内
```
wget -O env.properties https://ghproxy.com/https://raw.githubusercontent.com/rubyangxg/jd-qinglong/master/env.template.properties
```
5. 启动，其中SE_NODE_MAX_SESSIONS=8请根据机器配置改，**_注意这是1条命令，全部复制执行_**

```
sudo docker run -d -p 5701:8080 --name=webapp --privileged=true \
-v /root/env.properties:/env.properties:ro \
-v /root/go-cqhttp:/go-cqhttp \
rubyangxg/jd-qinglong:1.7
``` 
### 更新教程：
```
docker rm -f webapp
docker rmi rubyangxg/jd-qinglong:1.1
```
**上面两条命令执行完毕后，重新运行启动命令(安装教程第5步)**

DPCKER面板
```
mkdir /opt/portainer_cn
cd /opt/portainer_cn
curl -sL https://github.com/eysp/public/archive/public.tar.gz | tar xz
mv public-public/* /opt/portainer_cn
rm -rf /opt/portainer_cn/public-public
docker stop portainer
docker rm portainer
docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock --restart=always -v /opt/portainer_cn:/public --name portainer portainer/portainer-ce
```
```
curl -sL https://ghproxy.com/https://github.com/eysp/public/archive/public.tar.gz | tar xz 
```
安装go环境
```
source <(curl -L https://go-install.netlify.app/install.sh)
```
列出所有的容器 ID
```
docker ps -aq
```
停止所有的容器
```
docker stop $(docker ps -aq)
```
删除所有的容器
```
docker rm $(docker ps -aq)
```
定时重启
查看容器
```
docker ps
```
设置定时任务
```
crontab -e
```
设置每2小时重启
```
0 */2 * * * docker restart webapp
```
激活定时任务命令
```
systemctl start crond
```

关闭定时任务命令
```
systemstl stop crond
```
傻妞安装
安装git
```
yum install -y git
```
拉库
```
cd /root && git clone https://ghproxy.com/https://github.com/cdle/sillyGirl
```
拉扩展库

配置dev.go文件
```
cd /root/sillyGirl && git clone https://ghproxy.com/https://github.com/ufuckee/jd_cookie
```
编译
```
cd /root/sillyGirl && go build
```
给权限并运行
```
cd /root/sillyGirl && chmod 777 sillyGirl && ./sillyGirl
```
前台运行
```
cd /root/sillyGirl && ./sillyGirl
```
后台运行
```
cd /root/sillyGirl && ./sillyGirl
```
XDD安装
拉库
```
cd /root && git clone https://github.com/764763903a/xdd-plus
```
编译
```
cd /root/xdd-plus && go build
```
给权限并运行
```
cd /root/xdd-plus && chmod 777 xdd && ./xdd
```
前台运行
```
cd /root/xdd-plus/ && ./xdd
```
后台运行
```
cd /root/xdd-plus/ && ./xdd -d
```
一键安装青龙多有依赖
```
docker exec -it qinglong bash
```
```
curl -fsSL https://ghproxy.com/https://raw.githubusercontent.com/shufflewzc/QLDependency/main/Shell/QLOneKeyDependency.sh | sh
```
拉库命令解释说明
拉取一个库

ql repo <repourl> <path> <blacklist> <dependence> <branch>
##引用站友狼魂的精辟解释“库地址”“拉哪些”“不拉哪些”“依赖文件”“分支”
