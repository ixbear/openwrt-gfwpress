gfwpress for OpenWrt
===

[![Download][B]][4]  

简介
---

 本项目是 [gfwpress][1] 在 OpenWrt 上的移植  

特性
---

软件包可下载到相应openwrt路由的SDK编译成 [gfwpress][1] 的可执行文件, 可与 [luci-app-gfwpress][3] 搭配使用  
可编译两种版本  

 - gfwpress

   ```
   客户端/
   └── usr/
       └── bin/
           └── gfwpress       // 提供 SOCKS 代理
   ```

编译
---

 - 从 OpenWrt 的 [SDK][2] 编译

   ```bash
   # 以 ar71xx 平台为例
   tar xjf OpenWrt-SDK-ar71xx-for-linux-x86_64-gcc-4.8-linaro_uClibc-0.9.33.2.tar.bz2
   cd OpenWrt-SDK-ar71xx-*
   # 获取 gfwpress
   git clone https://github.com/peter-tank/openwrt-gfwpress.git package/gfwpress
   # 选择要编译的包 Network -> gfwpress
   make menuconfig
   # 开始编译
   make package/gfwpress/compile V=99
   ```

配置
---

   软件包本身并不包含配置文件, 配置文件内容为 JSON 格式, 支持的键:  

   键名            | 数据类型 | 说明
   ---------------|---------|-----------------------------------------------
   ServerHost     | 字符串   | 服务器地址, 可以是 IP 或者域名
   ServerPort     | 整数值   | 服务器端口号
   ProxyPort      | 整数值   | 本地绑定的端口号
   Password       | 字符串   | 服务端设置的密码

  [1]: https://github.com/chinashiyu/gfw.press.c
  [2]: http://downloads.openwrt.org/barrier_breaker/14.07/ar71xx/nand/ "SDK 下载"
  [3]: https://github.com/peter-tank/luci-app-gfwpress
  [B]: https://api.bintray.com/packages/peter-tank/opkg/shadowsocks-libev/images/download.svg
  [4]: https://bintray.com/peter-tank/opkg/shadowsocks-libev/_latestVersion "预编译 IPK 下载"
