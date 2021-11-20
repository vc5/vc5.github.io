---
title: Unraid国内网络加速
date: 2021-11-20 04:44:37
tags:
---
# 配置CA以使用代理
- 新建`/boot/config/plugins/community.applications/proxy.cfg`，记得修改代理IP和端口，其内容如下
```ini
port=1081
tunnel=1
proxy=http://192.168.5.1
```
- 源代码逻辑在这个位置[Squidly271/community.applications](https://github.com/Squidly271/community.applications/blob/722f7f489dfbc71382e6dc4a524ee013e29cb344/source/community.applications/usr/local/emhttp/plugins/community.applications/include/helpers.php#L63)



# 配置Docker镜像源
在`/boot/config/go`中添加以下内容，重启生效
```bash
# docker国内镜像
mkdir -p /etc/docker
cat << EOF >/etc/docker/daemon.json
{
"registry-mirrors": [
    "http://hub-mirror.c.163.com",
    "https://registry.docker-cn.com",
    ]
}
EOF
```