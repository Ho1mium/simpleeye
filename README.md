
# 中文
## 什么是 SimpleEye？    
    单个python文件的cloudeye 实现,支持http协议和dns协议方式进行 OOB(out of bound)攻击。

## 配置
* 首先在dns域名注册出自定义dns，填写自己的服务器公网ip，然后有几个配置项：

    * allowkeys web方式访问本服务的key,默认情况如果当前主机域名是e.qy.kim,那么web查看log地址是
     ```e.qy.kim:8899/e_e ```
     ```resolveconfig```可以自定义域名解析记录，```blacklist```可以配置黑名单域名（系统不会记录解析这些域名的记录）。

    ```python
    resolveconfig={"e.qy.kim":"1.63.65.182",'qy.kim':"1.63.65.182"}
    
    allowkeys=["e_e"] 
    
    blacklist=["x.qy.kim","e.qy.kim","ns1.qy.kim","ns2.qy.kim"]```

* 举个例子，如果你注册的域名是qy.kim，使用方式如下：
* 配置自定义dns，指向你自己域名服务器所在的IP地址。然后在域名服务器上执行如下命令启动dns服务。
    ```shell
nohup python simpleeye.py >log.txt&
    ```

## 使用举例
* 第一步 ```ping test.qy.kim```

    ```shell
    PS C:\Users\maocz> ping test.qc.kim
    
    Pinging test.qc.kim [127.0.0.1] with 32 bytes of data: Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
    
    Ping statistics for 127.0.0.1: Packets: Sent = 1, Received = 1, Lost = 0 (0% loss), Approximate round trip times in milli-seconds: Minimum = 0ms, Maximum = 0ms, Average = 0ms
    ```

* 第二步,```http://e.qy.kim:8899/jndi_oob_exploit```

* 然后访问 ```http://e.qy.kim:8899/e_e```

* dns记录会有如下记录内容如下，其中122.22.22.22 是发起dns查询的主机ip：

    ```test.qy.kim.  122.22.22.22   2017_12_07 03:16```

* web访问记录如下:
```
weblog /e_e 2017_12_07 03:17 /jndi_oob_exploit 2017_12_07 03:17
```








# Eglish
## What is SimpleEye？
    A simple blind exploit tool( a dns server and a web app) that all in one python file。

* specify ip to reserved domins
    
    ```python
    resolveconfig={"e.qy.kim":"1.63.65.182",'qy.kim':"1.63.65.182"}
    
    access key allowkeys=["e_e"]
    
    blacklist=["x.qy.kim","e.qy.kim","ns1.qy.kim","ns2.qy.kim"]
    
    ```

## usage

* First
```shell
ping test.qy.kim
```

* then HTTP access 
  ```http://e.qy.kim:8899/jndi_oob_exploit```

* At Last view access log
```http://e.qy.kim:8899/e_e```

* DNS records

    ```test.qy.kim. 2017_12_07 03:16```

* Web access log

    ```
    /e_e 2017_12_07 03:17
    
    /jndi_oob_exploit 2017_12_07 03:17
    ```
