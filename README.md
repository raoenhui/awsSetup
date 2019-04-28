# awsSetup
用亚马逊云AWS免费搭建VPN服务

### 一 、注册亚马逊AWS云

1.1 浏览器输入[https://aws.amazon.com/free](https://aws.amazon.com/free)

![image.png](https://upload-images.jianshu.io/upload_images/9902136-65bb89826de60215.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 注册过程需要绑定信用卡，我用的是visa卡绑定的,只有一年免费的，所以一年后记得删掉所有实例，解绑信用卡，关闭掉AWS账户。

本妹子薅羊毛不亦乐乎> < ![image](http://upload-images.jianshu.io/upload_images/9902136-b31760c6051b6c05.gif?imageMogr2/auto-orient/strip)


1.2 注册后登录，选择services->EC2

![image.png](https://upload-images.jianshu.io/upload_images/9902136-79cd7d94a812260a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> Amazon EC2全称Amazon Elastic Compute Cloud，亚马逊弹性云服务器，是一个虚拟机，用户将可以在这个虚拟机上运行任何自己想要的软件或应用程序。

1.3 生成实例

![image.png](https://upload-images.jianshu.io/upload_images/9902136-c71d1e701c0d3f29.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1.4 在亚马逊镜像库中搜索你最熟悉的系统
    我习惯用的是`centos7`，所以我选择了它。
    
![image.png](https://upload-images.jianshu.io/upload_images/9902136-d710f9fa6a8f0929.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1.5 选择免费类型，其他选择按照默认就好

![image.png](https://upload-images.jianshu.io/upload_images/9902136-bef2a50a92f98fbe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1.6 生成添加秘钥，并将秘钥下载到本地

![image.png](https://upload-images.jianshu.io/upload_images/9902136-f0500859154ab7d5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1.7 生成实例成功

![image.png](https://upload-images.jianshu.io/upload_images/9902136-2829ace8133f7c92.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1.8 添加安全组，更改成添加的安全组

![image.png](https://upload-images.jianshu.io/upload_images/9902136-4bd8186004415228.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 如上配置是所以端口都能被访问，如果想要做限制的话，可以选择特殊的`IP`和端口


### 二 、安装ss服务
2.1 服务端开启ss服务
```bash
#用ssh登录
ssh -i "a.pem" centos@ec2-3-16-129-69.us-east-2.compute.amazonaws.com
#切换root用户
sudo su

#开始真正安装啦
#用pip安装ss服务
yum install python-setuptools && easy_install pip
#安装小飞机
pip install shadowsocks
#启动ssserver
ssserver -p 443 -k MyPass -m rc4-md5 -d start
```
> ssserver命令中 443是指端口 MyPass是指密码 rc4-md5是指加密方式，这些小伙伴们都可以自定义修改

> 停止ss服务可用 ssserver -d stop

2.2 客户端链接
下载`shadowsocks`软件，编辑server，Address输入公网IP，Password输入MyPass，其他按截图所示即可

![image.png](https://upload-images.jianshu.io/upload_images/9902136-56c2d685a00383ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 手机端可下载NetShuttle软件访问

2.3 哈哈，愉快的访问`youtobe`了

![PC.png](https://upload-images.jianshu.io/upload_images/9902136-d4176fbe31178ccb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![MOBILE.png](https://upload-images.jianshu.io/upload_images/9902136-935844438d8002ef.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 三 、注意事项

1.只有一年免费的,一年后扣信用卡的钱

2.每月流量有上限，上限为15G;

  限制详情可看 [https://aws.amazon.com/cn/free/faqs/](https://aws.amazon.com/cn/free/faqs/);
  
  建议实时查看下自己的流量使用情况，具体操作可查看 [https://www.peels.cn/225.html](https://www.peels.cn/225.html);


## 其他链接
> * [https://docs.aws.amazon.com/zh_cn/vpc/latest/userguide/vpn-connections.html](https://docs.aws.amazon.com/zh_cn/vpc/latest/userguide/vpn-connections.html)
> * [http://www.gengzhibo.com/2017/02/05/vpn/](http://www.gengzhibo.com/2017/02/05/vpn/)
> * [https://aws.amazon.com/cn/free/faqs/](https://aws.amazon.com/cn/free/faqs/)
> * [https://www.peels.cn/225.html](https://www.peels.cn/225.html)

Happy coding .. :)








