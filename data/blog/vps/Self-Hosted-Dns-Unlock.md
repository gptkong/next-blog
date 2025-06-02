---
title: "自建DNS解锁流媒体"
date: "2025-06-02"
summary: "利用解锁服务器搭建DNS解锁流媒体"
---

## 使用AdguardHome搭建DNS服务器

具体安装教程参考
- [adguardhome github](https://github.com/AdguardTeam/AdGuardHome)
- [adguard docker hub](https://hub.docker.com/r/adguard/adguardhome)

### 一键脚本
```bash
curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
```

### docker
```bash
docker run --name adguardhome\
    --restart unless-stopped\
    -v /my/own/workdir:/opt/adguardhome/work\
    -v /my/own/confdir:/opt/adguardhome/conf\
    -p 53:53/tcp -p 53:53/udp\
    -p 67:67/udp -p 68:68/udp\
    -p 80:80/tcp -p 443:443/tcp -p 443:443/udp -p 3000:3000/tcp\
    -p 853:853/tcp\
    -p 784:784/udp -p 853:853/udp -p 8853:8853/udp\
    -p 5443:5443/tcp -p 5443:5443/udp\
    -d adguard/adguardhome
```

### 配置上游DNS
#### 打开过滤器
![image](https://i.111666.best/image/fd2t5mNb0Vl8GV0iC3uq1V.png)

#### 一般使用`8.8.8.8`|`1.1.1.1`
![image](https://i.111666.best/image/k0Xv3MCF73ELFBMCk31Ehp.png)

#### 配置adghome的自定义过滤规则
使用[DNS解锁配置生成器](https://dnsconfig.072899.xyz/)

![image](https://i.111666.best/image/O7pEaqbEULVpeWCfEgZ1ub.png)

#### 填入自定义过滤规则
![image](https://i.111666.best/image/gZ9OVYQTLNAL6SBM10jkQ9.png)