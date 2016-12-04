# DNS记录分析
> 使用DNS分析工具收集DNS服务器信息和有关域名的相应记录

## DNS记录分为下述几种类型
类型 | 描述
-|-
SOA|授权管理该域的服务器（权威记录）
NS|名称解析服务器记录
A|IPv4地址记录
MX|邮箱服务器地址
PTR|逆向解析记录
AAAA|IPv6地址记录
CNAME|别名记录

## host

```shell
host [-aCdlriTwv] [-c class] [-N ndots] [-t type] [-W time]
            [-R number] [-m flag] hostname [server]

-a：显示详细的DNS信息
-c<类型>：指定查询类型，默认值为“IN“
-C：查询指定主机的完整的SOA记录
-l :域传输
-r：在查询域名时，不使用递归的查询方式
-t<类型>：指定查询的域名信息类型
-v：显示指令执行的详细信息
-w：如果域名服务器没有给出应答信息，则总是等待，直到域名服务器给出应答
-W<时间>：指定域名查询的最长时间，如果在指定时间内域名服务器没有给出应答信息，则退出指令
-4：使用IPv4
-6：使用IPv6
```

## dig

```shell
# 默认情况下会返回该域的A记录
dig example.com

# 查询全部的DNS数据
dig example any

# 域传输
dig @ns4.isp.com example.com axfr

dig [@global-server] [domain] [q-type] [q-class] {q-opt}
            {global-d-opt} host [@local-server] {local-d-opt}
            [ host [@local-server] {local-d-opt} [...]]

@<服务器地址>：指定进行域名解析的域名服务器
-c：可以设置协议类型（class），包括IN(默认)、CH和HS
-b：当主机具有多个IP地址，指定使用本机的哪个IP地址向域名服务器发送域名查询请求
-f<文件名称>：指定dig以批处理的方式运行，指定的文件中保存着需要批处理查询的DNS任务信息
-P：指定域名服务器所使用端口号
-t<类型>：指定要查询的DNS数据类型
-x：执行逆向域名查询
-4：使用IPv4
-6：使用IPv6
-h：显示指令帮助信息
```

## dnsenum

```shell
dnsenum example.com
dnsenum -f dns.txt example # 使用字典文件dns.txt

dnsenum [Options] <domain> 
```

## dnsdict6

```shell
dnsdict6 example.com
dnsdict6 -d -4 example.com

dnsdict6 [-d46] [-s|-m|-l|-x] [-t THREADS] [-D] domain [dictionary-file]

 -4  也转储ipv4地址
 -t  num  指定要使用的线程数（默认：8，最大：32）
 -D   转储所选择的内置列表，不扫描
 -d   显示在NS和MX DNS域的IPv6信息
 -s   执行SRV服务名称猜测
 -[smlx] 指定字典大小 -s(mall=50), -m(edium=796) (DEFAULT) -l(arge=1416),  -x( treme=3211)
```

## fierce

```shell
fierce -dns example.com -theads 3
```

## dmitry

```shell
dmitry [-winsepfb] [-t 0-9] [-o %host.txt] host

# 搜索子域名、电子邮件地址、netcraft.com网站上收集的相关信息、whois查询结果
dmitry -winse targethost

# 简单的扫描目标端口
dmitry -pfb targethost

-0 结果输出到文件
-i whois查询，后跟IPv4地址
-w whois查询，后跟字符串形式的主机名
-n 获取相关主机的netcraft.com信息，包括主机操作系统、web服务上线和运行时间信息
-s 执行子域名查询
-e 针对目标主机执行Email地址查询
-p 在目标主机上执行TCP端口扫描，这是个相对基础简单的模块
-f 让TCP扫描器输出过滤的端口信息
-b 让TCP扫描器输出端口banner
-t 设置端口扫描的TTL，默认是2秒
```

## maltego

> Maltego是开源的情报收集和法证调查程序
>> 需要VPN