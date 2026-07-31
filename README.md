# Mihomo 配置

基于 [sing-mix](https://github.com/Sakyvo/sing-mix) 二次定制，增强 DNS 管理和隐私防护。

## 版本

| 文件 | 说明 |
|------|------|
| `标准版.txt` | sing-mix 原版，mrs 规则集，主流 7 地区 |
| `DNS覆写（26.7.28）.txt` | 规则集包含13 地区，DNS 防泄漏 |
| `DNS覆写（26.7.31）.txt` | 开启读取系统 hosts 文件选项 |

### DNS覆写（26.7.28）

- **13 地区覆盖**：HK/TW/SG/JP/KR/AS/US/DE/UK/AU/TR/IN/CA，中文名称标识
- **AI 分流**：独立策略组处理 OpenAI / Anthropic / Gemini
- **DNS 分区**：`nameserver-policy` 精确控制域名走代理 DNS 或国内 DNS，杜绝泄露
- **Fake IP 过滤**：`fake-ip-filter` 合并 `geosite:cn`，国内域名返回真实 IP
- **广告拦截**：`doubleclick`、`googlesyndication`、`category-ads-all` 规则集
- **直连修复**：`DIRECT_FIX_RULES` 处理部分服务强制后门 IP 问题

## DNS 泄露检测

配置生效后，确认以下网站显示的 DNS 不属于你的本地运营商：

- https://ipleak.net/
- https://meowvps.com/tools/detector/

## 更新日志

### 26.7.31
- 新增 `"use-system-hosts": true`，恢复读取 Windows 系统 hosts 文件
- **用途**：在校园网等存在 DNS 污染/劫持的环境下，通过 hosts 静态映射绕过封锁网络的 DNS 查询，直接指定域名的真实 IP

### 26.7.28
- 修复 Google 登录"下一步"无响应：`GoogleCN` 规则改为走代理，不再直连
