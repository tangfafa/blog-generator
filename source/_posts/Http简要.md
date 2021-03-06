---
title: Http简要
date: 2019-01-06 23:34:50
tags:
---


## HTTP简要介绍 ###

HTTP英文全称:HyperText Transfer Protocol,中文全称:超文本传输协议,HTTP是一个客户端终端（用户）和服务器端（网站）请求和应答的标准（TCP）。通过使用网页浏览器、网络爬虫或者其它的工具，客户端发起一个HTTP请求到服务器上指定端口（默认端口为80）。

#### 请求信息 ####
请求信息主要包括4个部分，

	1.请求行，以一个方法符号开头，后面跟着请求URI和协议的版本，例如GET /Test HTTP/1.1。
	2.请求头,(例如Accept-Language: en)，在HTTP/1.1协议中，所有的请求头，除Host外，都是可选的。
	3.空行(区别2和4之间的标识)
	4.其他消息体


下面介绍下使用chrome浏览器查看请求信息的步骤。

	1.F12打开开发者工具，或者右键点击检查。
	2.点击Network。
	3.点击任一文件资源请求或者接口请求。
	4.在Headers中查看Request Header, 点击右侧view source,即可查看请求信息。

#### 响应信息 ####

	1.协议版本状态以及描述，它表示通信所用的协议以及版本，返回服务器处理了客户端发出的请求，例如HTTP/1.1 200 OK代表通信所用的协议是HTTP1.1服务器已经成功的处理了客户端发出的请求（200表示成功）。
	2.响应头,也和请求头一样包含许多有用的信息，例如服务器类型、日期时间、内容类型和长度等。
	3.空行(区别2和4之间的标识)
	4.响应正文，服务器返回的HTML页面

响应返回的状态码，通常分为4类：

	1. 1XX－信息类(Information),表示收到Web浏览器请求，正在进一步的处理中
	2. 2XX－成功类（Successful）,表示用户请求被正确接收，理解和处理例如：200 OK
	3. 3XX-重定向类(Redirection),表示请求没有成功，客户必须采取进一步的动作。
	4. 4XX-客户端错误(Client Error)，表示客户端提交的请求有错误 例如：404 NOT Found，意味着请求中所引用的文档不存在。
	5. 5XX-服务器错误(Server Error)表示服务器不能完成对请求的处理：如 500

下面介绍下使用chrome浏览器查看响应信息的步骤。

	1.F12打开开发者工具，或者右键点击检查。
	2.点击Network。
	3.点击任一文件资源请求或者接口请求。
	4.在Headers中查看Response Header, 点击右侧view source,即可查看请求信息。

#### 请求方法 ####
HTTP/1.1协议中共定义了八种方法（也叫“动作”）来以不同方式操作指定的资源

	1.GET,向指定的资源发出“显示”请求。使用GET方法应该只用在读取数据，而不应当被用于产生“副作用”的操作中.
	2.HEAD,与GET方法一样，都是向服务器发出指定资源的请求。只不过服务器将不传回资源的本文部分。它的好处在于，使用这个方法可以在不必传输全部内容的情况下，就可以获取其中“关于该资源的信息”（元信息或称元数据）。
	3.POST,向指定资源提交数据，请求服务器进行处理（例如提交表单或者上传文件）。数据被包含在请求本文中。这个请求可能会创建新的资源或修改现有资源，或二者皆有。
	4.PUT,向指定资源位置上传其最新内容。
	5.DELETE,请求服务器删除Request-URI所标识的资源。
	6.TRACE,回显服务器收到的请求，主要用于测试或诊断。
	7.OPTIONS,这个方法可使服务器传回该资源所支持的所有HTTP请求方法。用'*'来代替资源名称，向Web服务器发送OPTIONS请求，可以测试服务器功能是否正常运作。
	8.CONNECT,HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。通常用于SSL加密服务器的链接（经由非加密的HTTP代理服务器）。

#### curl的使用 ####
在Linux中curl是一个利用URL规则在命令行下工作的文件传输工具，可以说是一款很强大的http命令行工具。它支持文件的上传和下载，是综合传输工具，但按传统，习惯称url为下载工具。

	语法：# curl [option] [url]
常见参数

	-A/--user-agent <string>              设置用户代理发送给服务器
	-b/--cookie <name=string/file>    cookie字符串或文件读取位置
	-c/--cookie-jar <file>                    操作结束后把cookie写入到这个文件中
	-C/--continue-at <offset>            断点续转
	-D/--dump-header <file>              把header信息写入到该文件中
	-e/--referer                                  来源网址
	-f/--fail                                          连接失败时不显示http错误
	-o/--output                                  把输出写到该文件中
	-O/--remote-name                      把输出写到该文件中，保留远程文件的文件名
	-r/--range <range>                      检索来自HTTP/1.1或FTP服务器字节范围
	-s/--silent                                    静音模式。不输出任何东西
	-T/--upload-file <file>                  上传文件
	-u/--user <user[:password]>      设置服务器的用户和密码
	-w/--write-out [format]                什么输出完成后
	-x/--proxy <host[:port]>              在给定的端口上使用HTTP代理
	-#/--progress-bar                        进度条显示当前的传送状态

例子：

	# curl http://www.linux.com
	执行后，www.linux.com 的html就会显示在屏幕上了，curl还有许多的操作，详细的可以google查看。
