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
