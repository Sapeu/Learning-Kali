# Kali Linux的网络服务

## service

> service命令是Redhat Linux兼容的发行版中用来控制系统服务的实用工具，它以启动、停止、重新启动和关闭系统服务，还可以显示所有系统服务的当前状态。
>> 常用服务： networking(网络)、apache2(http web服务)、mysql(数据库)、ssh(安全协议)

```shell
service < option > | --status-all | [ service_name [ command | --full-restart ] ]
service (选项) (参数)
```

- 启动服务

```shell
    service 服务名 start
```

- 停止服务

```shell
    service 服务名 stop
```

- 重启服务

```shell
    service 服务名 restart
```

- 查看全部服务的状态

```shell
    service --status-all
```

- 查看服务的状态
 
```shell
    service 服务名 status
```

## update-rc.d

> 此命令用于安装或移除System-V风格的初始化脚本连接。脚本是存放在 /etc/init.d/目录下的，当然可以在此目录创建连接文件连接到存放在其他地方的脚本文件。
>> 此命令可以指定脚本的执行序号，序号的取值范围是 0-99，序号越大，越迟执行。

```shell
update-rc.d [-n] [-f] name remove # 用于移除脚本。
update-rc.d [-n] name defaults [NN | SS KK] # NN表示执行序号（0-99），SS表示启动时的执行序号，KK表示关机时的执行序号，SS、KK主要用于在脚本直接的执行顺序上有依赖关系的情况下。
```

