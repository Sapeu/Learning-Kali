# Kali Linux的网络服务
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
