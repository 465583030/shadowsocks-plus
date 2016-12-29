2016.12.29: 近期 Shadowsocks Plus 将有重大更新。

# 功能

已实现：
- 原版 shadowsocks-go 所有功能
- 集成 kcptun 实现加速
- 多端口支持
- 支持动态增加用户（端口）
- 用户管理脚本和服务端一键安装脚本（在`tools`目录下）

Todo:
- 动态删除用户支持

# 使用

编译：
```
git clone https://github.com/shadowsocks-plus/shadowsocks-plus

cd shadowsocks-plus

go get ./...

go build server.go

go build local.go
```

客户端和服务端使用方法与原版 shadowsocks-go 完全相同，自带加速。

如果有需要使用单独的 kcptun 和 shadowsocks 客户端进行连接，请注意 kcptun 端口为 shadowsocks 端口号 + 10000。

HTTP API 调用方法：
- 增加用户：`http://[Server IP]:[API Port]/[hkey]/addUser/port=[port]&pw=[password]`
- 如需使用 HTTP API，请在启动 shadowsocks-plus 时指定监听地址和密钥 (hkey)，如：
  `./server -c config.json -api 127.0.0.1:2333 -hkey HelloAPIKey`

# Copyright

本项目采用 LGPL License.

引用了 shadowsocks-go, kcptun 的代码。感谢相关项目的作者 :-)
