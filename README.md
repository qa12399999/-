### 安装教程：
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
sudo docker pull rubyangxg/jd-qinglong:1.1
```
4. 下载配置文件模板，根据需要修改，不要缺少此文件
```
wget -O env.properties https://raw.githubusercontent.com/rubyangxg/jd-qinglong/master/env.template.properties
```
5. 启动，其中SE_NODE_MAX_SESSIONS=8请根据机器配置改，**_注意这是1条命令，全部复制执行_**
```
sudo docker run -d -p 5701:8080 --name=webapp --privileged=true \ 
-e "SE_NODE_MAX_SESSIONS=8" \
-v /var/run/docker.sock:/var/run/docker.sock \ 
-v [你的路径]/env.properties:/env.properties:ro \ 
rubyangxg/jd-qinglong:1.1
```
例如：**_注意这是1条命令，全部复制执行_**
```
sudo docker run -d -p 5701:8080 --name=webapp --privileged=true \
-e "SE_NODE_MAX_SESSIONS=8" \
-v /var/run/docker.sock:/var/run/docker.sock \
-v "$(pwd)"/env.properties:/env.properties:ro \
rubyangxg/jd-qinglong:1.1
``` 
### 更新教程：
```
docker rm -f webapp
docker rmi rubyangxg/jd-qinglong:1.1
```
**上面两条命令执行完毕后，重新运行启动命令(安装教程第5步)**

```
docker rm -f webapp
docker rmi rubyangxg/jd-qinglong:1.1
```
### 安装教程：
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
sudo docker pull rubyangxg/jd-qinglong:allinone
```
4. 下载配置文件模板，根据需要修改，不要缺少此文件
```
已经配置
```
5. 启动，其中SE_NODE_MAX_SESSIONS=8请根据机器配置改，**_注意这是1条命令，全部复制执行_**
```
sudo docker run -d -p 5701:8080 --name=webapp --privileged=true \ 
-e "SE_NODE_MAX_SESSIONS=8" \
-v /var/run/docker.sock:/var/run/docker.sock \ 
-v [你的路径]/env.properties:/env.properties:ro \ 
rubyangxg/jd-qinglong:1.1
```
例如：**_注意这是1条命令，全部复制执行_**
```
sudo docker run -d -p 5701:8080 --name=webapp --privileged=true \
-e "SE_NODE_MAX_SESSIONS=8" \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /root/env.properties:/env.properties:ro \
rubyangxg/jd-qinglong:allinone
``` 
### 更新教程：
```
docker rm -f webapp
docker rmi rubyangxg/jd-qinglong:1.1
```
**上面两条命令执行完毕后，重新运行启动命令(安装教程第5步)**

```
docker rm -f webapp
docker rmi rubyangxg/jd-qinglong:1.1
```
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
安装 Docker
Centos
```
yum install -y yum-utils
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
yum install docker-ce docker-ce-cli containerd.io -y
systemctl start docker
systemctl enable docker
```
安装Docker-compose
```
curl -fsSL https://get.docker.com | bash -s docker
curl -L "https://github.com/docker/compose/releases/download/1.26.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```
安装go环境
```
git clone https://github.com/letseeqiji/oneinstall.git && cd oneinstall/golang && sh goinstall.sh
```
