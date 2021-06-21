前置：
青龙面板安装：
首先安装docker

```jsx
sudo yum check-update
curl -fsSL https://get.docker.com/ | sh
sudo systemctl start docker
sudo systemctl status docker
sudo systemctl enable docker
```

安装完成后配置青龙面板

```jsx
docker run -dit \
  --name QL \
  --hostname QL \
  --restart always \
  -p 5700:5700 \
  -v $PWD/QL/config:/ql/config \
  -v $PWD/QL/log:/ql/log \
  -v $PWD/QL/db:/ql/db \
  -v $PWD/QL/scripts:/ql/scripts \
  -v $PWD/QL/jbot:/ql/jbot \
  whyour/qinglong:latest
  limoe/qinglong:latest //2.2.0版本
```

等待一段时间后，在浏览器输入ip:5700 即可登录青龙面板
用户名为admin 密码是 adminadmin

重置密码
登录成功后，在/root/QL/config 中找到auth.json

### **软件介绍**

本程序仅限青龙面板 2.0 对接使用，添加自助扫码功能。更多功能如下：

扫码添加 / 更新 cookie删除 cookie查看单用户日志




### **第一步 安装依赖**

用finalshell连接上服务器。安装wget和unzip（一般的centos系统都已经安装过）

```jsx
//ubuntu
apt install wget unzip
//centos
yum install wget unzip -y
```
### 第二步 停止进程（新安装的忽略，跳到第三步看）

如果你已经安装了旧版程序，请按以下步骤删除原程序，再按照上述教程进行部署。

首先 kill 掉原来的程序。

```jsx
//查看原程序PID,第一行第二列为程序的PID
ps -ajx|grep JDC
//结束程序（*****改为你的PID，本文为24303）
kill -9 *****
```

删除原有的文件

```jsx
rm -rf JDC config.toml
```

### 第三步 后端安装

选择好自己的机型下载

```
//如果你是amd64架构（服务器，PC等）

wget https://ghproxy.com/https://github.com/Corvus091/JDC/releases/download/v2.0.2/linux_amd64.zip && unzip linux_amd64.zip

//如果你是arm架构（N1，路由器，树莓派等）

wget https://ghproxy.com/https://github.com/Corvus091/JDC/releases/download/v2.0.2/linux_arm.zip && unzip linux_arm.zip

```

然后赋777权限 安装

```
chmod 777 JDC
./JDC

```

第一次运行，自动生成配置文件并且程序会自动退出。

然后输入

```
nohup ./JDC &

```

开始后台运行程序。程序默认端口为 5701。打开 [http://ip:5701/info](http://ip:5701/info) 看到 “JDC is Already！” 即说明安装成功！

如果无法打开请检查端口是否放行！

### 第四步 前端安装

首先 cd 到 JDC 同级目录下（一般是root）的 public 文件夹中（如果没有请新建），并下载解压前端文件

```
cd public

wget https://ghproxy.com/https://github.com/Corvus091/JDC-web/releases/download/v2.0.2/dist.zip && unzip dist.zip

```

然后直接访问 IP + 端口即可看到面板
