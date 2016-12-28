# VPN 枚举

> VPN：虚拟专用网络       
> - 基于IPSec技术的VPN   
> - OpenVPN     
> - 基于SSL技术的VPN     

## ike-scan

```shell
ike-scan [options] [hosts...]
# -M 将payload的解码信息分为多行显示
# -A 使用IKE的 aggressive mode
# -P 将aggressive mode 的预共享密钥的哈希值保存为文件
ike-scan -M -A -P ike-haskey 192.168.0.10
# 使用osk-crack破解VPN连接的哈希值，-d适用于指定字典文件
psk-crack -d rockyou.txt ike-haskey

# --showbackoff 远程IP进行VPN设备指纹识别
ike-scan -M --trans=5,2,1,2 --showbackoff 192.168.0.10
```

