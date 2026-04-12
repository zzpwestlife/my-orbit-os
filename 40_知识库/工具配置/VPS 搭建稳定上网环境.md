---
title: "VPS 搭建稳定上网环境"
type: wiki
created: 2026-03-26
tags: [知识卡片, 工具配置, VPS, 网络, VLESS, REALITY]
---
# VPS 搭建稳定上网环境

## 概述
通过购买海外 VPS，使用 VLESS + REALITY 协议搭建稳定的科学上网环境。相比机场（共享节点），自建 VPS 拥有专属 IP、更高稳定性和隐私性。月费约 $9.99（DMIT 洛杉矶优化线路），可畅通访问各类海外服务。

## 总体架构
```
浏览器/应用
  │（系统代理/PAC）
  ▼
v2rayN / v2rayNG（本地 Xray Core）
  │（加密通道：VLESS + REALITY）
  ▼
海外 VPS（Xray 服务端 + 3X-UI 面板）
  ▼
海外网站/服务
```

## 核心概念

| 概念 | 说明 |
|------|------|
| **VPS** | 云端租用的 24 小时在线服务器 |
| **静态 IP** | 固定不变的 IP 地址，登录稳定不易被封 |
| **VLESS + REALITY** | 加密通信协议，伪装为正常 HTTPS 流量 |
| **机房 IP vs 住宅 IP** | 机房 IP 速度快价格低，住宅 IP 更像真人（教程用机房 IP） |
| **机场 vs 自建** | 机场=公交（共享、可能不稳定），自建=私家车（专属、稳定） |

## 关键步骤

### 1. 购买 VPS
- **推荐**: DMIT 洛杉矶 Premium 线路（CN2 GIA / CMIN2 直连线路）
- **系统**: Debian 12
- **配置建议**: 1Gbps 带宽、1TB 月流量、必须有 IPv4
- **注意**: Hostname 只能用字母数字和 `-`，不要空格/中文/特殊符号

### 2. SSH 登录 VPS
```bash
# 密码方式
ssh root@<VPS_IPv4>
# 私钥方式
ssh -i /path/to/id_rsa.pem root@<VPS_IPv4>
```

### 3. 安装 3X-UI 面板
```bash
bash <(curl -Ls https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh)
```
- 自定义面板端口（10000-65000，避开 80/443/8080/22）
- SSL 证书选 **Let's Encrypt for IP Address**
- 安装完成后记录：用户名、密码、端口、WebBasePath、Access URL

### 4. 创建 VLESS + REALITY 入站
在 3X-UI 面板中配置：
- 协议: VLESS
- 安全: REALITY
- uTLS: chrome
- Target: `www.microsoft.com:443`（或默认值）
- **必须点击 Get New Keys 生成公钥/私钥**（否则握手失败显示 -1ms）

### 5. 导出节点链接
入站列表 → 操作 → 复制链接，得到 `vless://` 开头的链接

### 6. 客户端配置

#### Windows（v2rayN）
- 下载: [v2rayN](https://github.com/2dust/v2rayN/releases) 选 `windows-64.zip`
- 右键 exe → 属性 → 兼容性 → 勾选"以管理员身份运行"
- 从剪贴板导入节点链接
- 日常配置: 系统代理=自动配置 / 路由=绕过大陆(Whitelist) / Tun=关闭

#### 安卓（v2rayNG）
- 下载: [v2rayNG](https://github.com/2dust/v2rayNG/releases) 选 `arm64-v8a.apk`
- 通过 3X-UI 面板的二维码扫码导入
- 路由设置: 绕过局域网及大陆地址
- 关闭电池优化防止系统杀后台

## 常见问题

| 问题 | 原因 | 解决 |
|------|------|------|
| 延迟显示 -1ms | 公钥/私钥为空 | 面板中点 Get New Keys 生成密钥 |
| 延迟显示 -1ms | 服务端端口未通 | 检查防火墙/安全组/iptables |
| 连接不稳定 | 两个代理抢控制权 | 彻底退出机场软件后重设系统代理 |
| Let's Encrypt 证书失败 | 80 端口被占用 | 确保 VPS 80 端口开放 |
| 关掉 v2rayN 就没网 | 正常现象 | 最小化到托盘后台运行 |
| UNPROTECTED PRIVATE KEY | .pem 文件权限太松 | 修复文件权限（仅当前用户可访问） |
| 在 PowerShell 敲 iptables | iptables 是 Linux 命令 | 先 SSH 登录 VPS 再执行 |

## 来源
- 原文: [如何用 VPS 搭建电脑端和移动端的稳定上网环境](https://x.com/gengdaJ/status/2029570219354845577)