# AdsPower浏览器Local API接口与Headless模式操作指南

## 功能概述
AdsPower客户端（v3.3.2及以上版本，内核v2.4.2.8+）现已支持通过headless模式配合api-key启动无界面服务，并调用Local API接口。

> 注意：该功能需单独申请权限，请联系在线客服开通

### 核心概念解析
- **Headless模式**：无需图形界面即可运行浏览器的参数配置
- **API-Key**：操作Local API接口的唯一身份凭证，支持多设备同时操作

👉 [【点击查看】2025年最新 AdsPower优惠码及特价活动方案汇总](https://bit.ly/adspower_free)

## 详细操作步骤

### 一、获取API-Key
1. 启动AdsPower客户端
2. 进入`账号管理 > 设置`
3. 在"基础API接口"区域点击`生成api-key`
4. 复制生成的密钥字符串

### 二、启动无界面服务
#### 准备工作
- 确保已打开AdsPower主目录的CMD/Terminal
- Windows默认路径：`C:\Program Files (x86)\AdsPower`

#### 命令行参数说明
| 参数 | 必填 | 说明 |
|------|------|------|
| `--headless` | 是 | 设为true启用无界面模式 |
| `--api-key` | 是 | 接口调用的身份凭证 |
| `--api-port` | 否 | 指定Local API服务端口 |

#### 各系统启动命令
- **Windows**：
  bash
  AdsPower.exe --headless=true --api-key=XXXX --api-port=50325
  
- **MacOS**：
  bash
  /Applications/adsPower.app/Contents/MacOS/Adspower --args --headless=true --api-key=XXXX --api-port=50325
  

#### 启动验证
成功后会返回Local API访问地址，格式为：`http://127.0.0.1:[端口]`

## 模式对比
| 特性 | 有界面服务 | 无界面服务 |
|------|-----------|-----------|
| 多设备登录 | 不支持 | 支持 |
| 自动化需求 | 受限 | 完美适配 |

## 常见问题解答
**Q：更换api-key后旧值是否仍可用？**  
A：不可用，系统会返回失效提示，需使用新密钥重新启动服务

**Q：如何重置api-key？**  
A：在`账号管理 > 设置`点击`重置api-key`，请注意保存新密钥

**Q：能否动态更新已启动服务的api-key？**  
A：不支持，需先关闭服务再用新密钥重新启动