# SNMP 枚举

> 简单网络管理协议（SNMP），由一组网络管理的标准组成，包含一个应用层协议（application layer protocol）、数据库模型（database schema）和一组资源对象

## onesixtyone

> 确定指定设备是否支持某些特定SNMP字符串

```shell
onesixtyone 192.168.56.101
# 进行更细致的扫描
onesixtyone -d 192.168.56.101
```

## snmpcheck

> 收集SNMP设备的有关信息

```shell
snmpcheck -t 192.168.56.101
```