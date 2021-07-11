### Nginx

---

企业产品出现瓶颈?

企业项目刚刚上线的时候, 并发量小、用户需求量少, 所以在低并发的情况下, 一个 jar 包启动应用就可以了, 然后调用内部 Tomcat 返回内容给用户.

但是随着用户的增加, 并发量也慢慢的增大, 这时候一台服务器就满足不了我们的需求了.

于是我们横向扩展, 又增加了服务器, 这个时候几个项目启动在不同的服务器上, 用户要访问, 就需要增加一个代理服务器, 通过代理服务器来帮我们转发和处理请求.

我们希望这个代理服务器可以帮助我们接受用户的请求, 然后将用户的请求按照规则帮我们转发到不同的服务器节点上, 这个过程用户是无感知的, 用户并不知道是哪个服务器返回的结果, 我们还希望他可以按照服务器的性能提供不同的权重选择, 保证最佳体验, 所以我们选择了 Nginx.



#### 什么是 Nginx

Nginx(engine x)是一个高性能的HTTP和反向代理Web服务器, 同时也提供了IMAP/POP3/SMTP服务. 

Nginx的特点是占用内存少、并发能力强, 并且nginx的并发能力在同类型的网页服务器中表现较好,中国大陆上使用nginx网站用户有:百度、京东、新浪、网易、腾讯、淘宝等

Nginx是一个安装非常简单、配置文件非常简洁(还可以支持Perl语法)、Bug非常少的服务. Nginx启动非常容易, 并且几乎可以做到7*24不间断运行, 即使运行数个月也不需要重新启动, 你还可以不间断服务的情况下进行软件版本的升级.

Nginx代码完全是用C语言从头写成, 官方数据测试表明能够支持高达50000个并发连接数的响应.



#### Nginx 的作用

`Http代理, 反向代理: 作为web服务器最常用的功能之一, 尤其是反向代理`

**正向代理**

<img src="https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210222181550.png" alt="截屏2021-02-22 下午6.15.45" style="zoom:75%;" />

**反向代理**

<img src="https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210222182110.png" alt="截屏2021-02-22 下午6.21.08" style="zoom:75%;" />

**负载均衡**

`Nginx提供的负载均衡策略有两种: 内置策略和扩展策略. 内置策略为轮询、加权轮询, Ip hash. 扩展策略就是天马行空, 只有你想不到, 没有他做不到.`

**轮询**

<img src="https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210222190643.png" alt="截屏2021-02-22 下午7.06.41" style="zoom:75%;" />

**加权轮询**

<img src="https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210222190732.png" alt="截屏2021-02-22 下午7.07.30" style="zoom:75%;" />

**Ip hash**

<img src="https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210222190829.png" alt="截屏2021-02-22 下午7.08.28" style="zoom:75%;" />

**动静分离**

```txt
动静分离, 在我们的软件开发中, 有些请求是需要后台处理的, 有些请求是不需要经过后台处理的(如css、html、jpg等文件), 这些不需要经过后台处理的文件称为静态文件, 让动态网站里的动态网页根据一定规则把不变的资源和经常变的资源区分开来, 动静资源做好了拆分以后, 我们就可以根据静态资源的特点将其做成缓存操作, 提高资源的响应速度
```

 

![截屏2021-02-22 下午7.14.56](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210222191604.png)



### Mac 上安装 Nginx

1. 安装 Homebrew

```shell
/usr/bin/ruby -e "$(curl -fsSL https://cdn.jsdeliver.net/gh/inen6/homebrew-install-install)"
# 注意这里的速度, 上百Kib/s或者几Mib/s是正常的, 否则键入 Ctrl+C 中断脚本
```

2. 安装完 Homebrew 后换源

   - 替换 brew.gitz

   ```shell
   git -C "$(brew --repo)" remote set-url origin https://mirrors.ustc.edu.cn/brew.git
   ```

   - 替换 homebrew-core.git

   ```shell
   git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
   ```

3. 安装 Nginx

```shell
brew install nginx
```

4. 安装完成



#### Nginx 的常用命令

1. `nginx` 	启动
2. `nginx -s stop`       停止
3. `nginx -s quit`       安全退出
4. `nginx -s reload`               重新加载配置文件
5. `ps aux|grep nginx`           查看nginx进程 



#### Nginx 实战

1. 运行两个web项目, 可以用本地的两个端口, 或者用多台服务器的相同或不同端口
2. 修改 nginx.conf 文件, 添加反向代理和负载均衡配置

```perl
# 负载均衡配置
upstream 域名/任意值 {
	server 127.0.0.1:8080(服务器IP地址:端口号) weight=1(权重);
	server 127.0.0.1:8081 weight=3(与上面那台服务器的权重比为3:1);
}
server {
	listen 80;
	server_name  localhost;
	
	#charset koi8-r;

  #access_log  logs/host.access.log  main;

  location / {
    root   html;
    index  index.html index.htm;
		
		# 代理
		proxy_pass http://(域名/任意值)		(与上方负载均衡名称相同)
  }
}
```

3. 访问 `localhost` 便可以看见`8080端口`和`8081端口`的web内容



#### 全站 HTTP 跳转 HTTPS 协议

以 ` http://www.a.com`  为例, 要求所有访问该页面的请求全部跳转到 ` https://www.a.com/`, 且请求的`URL`和参数`$query_string`要保留下来.

1. 使用 `if` 进行协议判断 ---- 最差

```perl
server {
	listen	80 default_server;
	listen	443 ssl default_server;
	server_name	www.a.com;
	ssl_certificate	"/data/nginx/ssl/nginx.crt";
	ssl_certificate_key	"/data/nginx/ssl/nginx.key";
	root	/data/nginx/a;
	charset	utf-8;
	if($schema = http){
		rewrite ^/(.*)$	https://www.a.com/$1	permanent;
	}
}

# 这种配置方法看起来简洁很多, 但是性能是最差的, 首先每次链接进来都需要Nginx进行协议判断, 其次判断为http协议时进行地址匹配、重写、返回、再次判断、最后还有正则表达式的处理······所以, 生产上我们极不建议这种写法, 另外, 能少用if就尽量不用, 如果一定要用, 也最好在location字段, 并且结合return或者rewrite···last来使用
```



