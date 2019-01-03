



# 一 VmWare 安装
## 1.1 下载
* 下载地址 ：`https://my.vmware.com/cn/web/vmware/details?downloadGroup=WKST-1502-WIN&productId=799&rPId=28909`
* 点击 ： Workstation Pro
* 选择版本
* 选择要安装在什么操作系统上
* 下载
* 登陆账号

## 1.2 安装

* 点击下载好的安装包
* 下一步
* 选择安装目录
* 选择不安装增强型键盘驱动
* 产品更新不点
* 加入点不点都可以
* 下一步安装即可

* 输入许可证

## 1.3 使用

* VMware三种网络连接方式：
	* Bridged（桥接模式）：可连外网
	* Host-Only（仅主机模式）： 不可连外网
	* NAT（地址转换模式） ： 可连外网


# 2 CentOS6.5系统安装

## 2.1 下载镜像：
* 网易开源镜像站: `http://mirrors.163.com/`
* 选择CenOs -> 6.9 -> readme ->
* 打开readme文件
* 点击这一行中的地址 ： `level, go to http://vault.centos.org/ for packages.` 
* 选择版本 : 6.9
* 点击 isos/
* 点击x86_64/ : 64位
* 选择 `CentOS-6.9-x86_64-bin-DVD1.iso`
* 选择任意地址进入即可
* 进入6.9目录
* 进入isos/
* 进入x86_64/ : 64位
* 点击下载 CentOS-6.5-x86_64-bin-DVD1.iso 镜像文件
	​	
## 2.2 安装CenOS6.9

__教程 ： `https://blog.csdn.net/u014139887/article/details/80179467`__
​	
		文件 -> 新建虚拟主机
		选择自定义
		硬件兼容性 ： 默认
		选择稍后安装操作系统
		选择Linux(L) 选择CenOS6 64位
		填写虚拟机名称 安装位置
		默认或者按照需求配置
		虚拟机内存 : 2048
		使用NAT模式
		默认推荐
		默认推荐
		选择创建新磁盘
		最大磁盘大小 ： 自己配 / 将虚拟磁盘分为多个文件
		下一步...
		
		选择编辑虚拟机设置
		CD/DVD(IDE)
		使用ISO镜像文件
		选择我们预先下载好的镜像
		
		点击开启此虚拟机
		选择第一项 Enter
		选择Skip
		语言选择我们选择English
		键盘选择我们国内的一般都是美式键盘所以我们也选择English
		安装介质，如果你安装到本地硬盘选第一个，如果你装到移动硬盘上就选择第二个，因为我是在本地硬盘里安装，所以这里我选择第一个
		是否忽略所有数据，因为我们是新装的系统所以我们选yes
		给计算机命名
		时区选择，我们选择Asia/Shanghai
		设置用户名密码
				123456
				123456
				点击仍然使用
		选择最后一个手动分区 : Create Custom Layout
		选择 ： create
		继续选择create创建分区
		步骤省略。。。。。打开网址查看教程即可
		
		注意这个 : 
				-Desktop ：基本的桌面系统，包括常用的桌面软件，如文档查看工具。
				-Minimal Desktop：基本的桌面系统，包含的软件更少。
				-Minimal：基本的系统，不含有任何可选的软件包。
				-Basic Server ：安装的基本系统的平台支持，不包含桌面。
				-Database Server：基本系统平台，加上MySQL和PostgreSQL数据库，无桌面。
				-Web Server：基本系统平台，加上PHP，Web server，还有MySQL和PostgreSQL数据库的客户端，无桌面。
				-Virtual Host：基本系统加虚拟平台。
				-Software Development Workstation：包含软件包较多，基本系统，虚拟化平台，桌面环境，开发工具。
				-而安装Linux基本是用来构建服务器的，所以我们选择安装Basic Server

## 2.3  CenOS6.5 网络配置

* 1 首先确认两个服务是否开启 :
	* VMware DHCP Service
	* VMware NAT Service

* 进入linux系统
* 配置网络，输入命令`vi  /etc/sysconfig/network-script/ifcfg-eth0`
	* 修改信息：
    ``` shell
    ONBOOT=yes
    BOOTPROTO=static
    ```
	* 添加信息：
    ``` shell
    IPADDR=192.168.6.6（根据网关自行调整）
    NETMASK=255.255.255.0
    # 该地址是你的网关地址 : 
    # 进入虚拟网络编辑器
    # 点击VMnet8
    # 选择NAT设置
    # 查看你的网关IP,GATEWAY=网关IP.	
    GATEWAY=192.168.6.2
    ```
（按“i”键进入编辑模式，按“Esc”键退出编辑模式，在退出编辑模式时，按“zz”保存退出）
* 设置DNS服务，输入命令`vi /etc/resolv.conf`
* 添加内容
``` shell
# 该ip要和你的网关IP保持一致
nameserver	192.168.6.2 
```
* 编辑完成后，输入命令`service network restart`

* 测试外网是否联通
* 输入命令`ping www.baidu.com`
