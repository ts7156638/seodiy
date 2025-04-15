# 自建聊天服务器全攻略：VoceChat与鸭信部署指南

## 前言：为什么选择自建聊天服务器？

在数字化时代，数据隐私和自主控制变得愈发重要。本文将详细介绍两款优秀的开源即时通讯工具——VoceChat和鸭信的部署方法，帮助您快速搭建专属聊天服务器。

## 一、服务器环境准备

### 1.1 云服务器选择与配置

部署聊天服务首先需要一台性能适中的云服务器：

- **推荐配置**：2核CPU/2GB内存
- **带宽选择**：根据预期用户量选择1-5Mbps
- **操作系统**：CentOS/Debian/Ubuntu均可

👉 [【点击查看】2025年最新雨云优惠码及特价云服务器方案汇总](https://bit.ly/RainYun)

### 1.2 远程连接设置

推荐使用MobaXterm进行服务器管理：

1. 下载安装MobaXterm免费版
2. 新建SSH会话，输入服务器IP地址
3. 使用root账号和密码登录

## 二、VoceChat部署方案

### 2.1 Docker部署方式（推荐）

bash
docker run -d --restart=always \
  -p 3009:3000 \
  --name vocechat-server \
  -v ~/.vocechat-server/data:/home/vocechat-server/data \
  privoce/vocechat-server:latest \
  --network.frontend_url "http://您的域名或IP:3009"

### 2.2 Shell脚本安装

bash
curl -sSf https://s.voce.chat/install.sh | sh

安装完成后，默认访问端口为3000。

## 三、鸭信(DuckChat)安装指南

### 3.1 基础安装步骤

1. 克隆项目代码：
   bash
   git clone https://gitee.com/mirrors/DuckChat.git
   cd DuckChat
   

2. 执行安装脚本：
   bash
   bash duckchat.sh
   

### 3.2 宝塔面板安装方案

1. 在宝塔面板创建PHP站点
2. 将源码复制到网站根目录
3. 通过网页完成初始化配置

## 四、进阶配置技巧

### 4.1 Nginx反向代理设置

通过反向代理可以实现：
- 域名绑定
- HTTPS加密
- 端口标准化（使用80/443端口）

### 4.2 数据库配置选项

两种数据库方案可选：
1. **MySQL**：适合高并发场景
2. **SQLite**：轻量级单机方案

## 五、移动端使用方案

两款应用均提供：
- 官方iOS/Android客户端
- 网页版访问接口
- API对接能力

## 结语：私有化部署的优势

自建聊天服务器不仅能保障数据安全，还能根据需求进行深度定制。无论是团队协作还是个人使用，VoceChat和鸭信都是优秀的开源解决方案。

**延伸阅读**：后续我们将介绍如何为这些服务配置HTTPS证书，提升通信安全性。