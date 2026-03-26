# 故障排除指南

本文档收集了 Clash for Windows 最常见的问题及解决方案。

---

## 🔧 常见问题

### 1. Clash for Windows 无法启动

**症状**：双击图标没反应，或闪退

**解决方案**：

#### 方案A：以管理员身份运行
1. 右键 Clash for Windows 图标
2. 选择"以管理员身份运行"

#### 方案B：清理配置文件
```powershell
# 删除配置文件夹
Remove-Item -Recurse -Force "$env:USERPROFILE\.config\clash"
```

#### 方案C：检查防火墙/杀毒软件
1. 暂时关闭杀毒软件测试
2. 在防火墙中添加 Clash for Windows 白名单
3. Windows安全中心 → 防火墙 → 允许应用通过防火墙

#### 方案D：重新安装
1. 完全卸载当前版本
2. 从 [官网](https://clash-for-windows.net) 下载最新版
3. 安装时选择"为所有用户安装"

---

### 2. 无法访问任何网站

**症状**：开启代理后所有网站都打不开

**排查步骤**：

#### Step 1: 检查系统代理
```
设置 → 网络和Internet → 代理 → 使用代理服务器
```
确保系统代理已开启，地址为 `127.0.0.1`，端口为 `7890`

#### Step 2: 测试节点连通性
在 Clash 面板中点击节点测试按钮，确认节点可用

#### Step 3: 检查模式
- **全局模式**：所有流量都走代理
- **规则模式**：按规则分流
- **直连模式**：不走代理

推荐使用 **规则模式**

#### Step 4: 测试直连
```powershell
# 测试是否能连接到节点服务器
Test-NetConnection -ComputerName 节点域名 -Port 节点端口
```

---

### 3. 部分网站无法访问

**症状**：大部分网站正常，但某些特定网站打不开

**解决方案**：

#### 场景A：网站被错误地分配到直连
在配置文件中添加规则：
```yaml
rules:
  - DOMAIN-SUFFIX,example.com,Proxy
```

#### 场景B：需要TUN模式
某些应用（如游戏、命令行工具）不走系统代理：
1. Clash for Windows → General → Service Mode → Install
2. 开启 TUN Mode

#### 场景C：DNS污染
修改DNS设置：
```yaml
dns:
  enable: true
  listen: 0.0.0.0:53
  enhanced-mode: fake-ip
  nameserver:
    - 223.5.5.5
    - 119.29.29.29
  fallback:
    - 8.8.8.8
    - 1.1.1.1
```

---

### 4. Netflix/YouTube 显示"不可用"

**症状**：流媒体提示地区限制

**解决方案**：

#### Netflix
1. 使用支持 Netflix 解锁的节点
2. 在 [Netflux](https://netflux.netlify.app/) 检测节点支持情况
3. 选择标注"Netflix Full"或"Netflix Original"的节点

#### YouTube
1. 确认节点IP没有被封禁
2. 尝试切换节点
3. 清除浏览器缓存

#### Disney+/HBO
需要使用特定解锁节点，联系你的机场客服获取推荐节点

---

### 5. 速度很慢

**原因分析**：

| 原因 | 解决方案 |
|------|----------|
| 节点负载高 | 切换到低延迟节点 |
| 线路质量差 | 选择专线/中转节点 |
| 本地网络问题 | 测试直连速度 |
| DNS解析慢 | 启用DNS缓存 |

**优化建议**：

1. **选择合适的节点**
   - 游戏用户：选择延迟 < 100ms 的节点
   - 下载用户：选择带宽大的节点
   - 追剧用户：选择流媒体解锁节点

2. **开启负载均衡**
```yaml
proxy-groups:
  - name: LoadBalance
    type: load-balance
    proxies:
      - Node1
      - Node2
      - Node3
    url: 'http://www.gstatic.com/generate_204'
    interval: 300
```

---

### 6. 订阅更新失败

**症状**：点击更新订阅提示错误

**解决方案**：

#### 方案A：检查订阅链接
1. 登录机场官网确认订阅链接有效
2. 重置订阅链接（如果机场支持）

#### 方案B：手动下载
```powershell
# 下载订阅文件
Invoke-WebRequest -Uri "你的订阅链接" -OutFile "subscription.yaml"
```
然后在 Clash 中导入本地文件

#### 方案C：使用订阅转换
1. 访问 [ACL4SSR在线转换](https://acl4ssr-sub.github.io/)
2. 粘贴订阅链接
3. 选择目标格式并转换

---

### 7. 端口被占用

**症状**：提示端口 7890 已被占用

**解决方案**：

#### 查找占用进程
```powershell
netstat -ano | findstr :7890
```

#### 结束进程
```powershell
taskkill /PID 进程ID /F
```

#### 或修改端口
在 Clash 配置中修改：
```yaml
port: 7891  # 改为其他端口
socks-port: 7892
```

---

### 8. Mac版无法打开"来自身份不明开发者"

**解决方案**：

```bash
# 终端执行
sudo xattr -r -d com.apple.quarantine /Applications/Clash\ for\ Windows.app
```

---

## 📞 获取帮助

如果以上方案都无法解决问题：

1. **查看日志**：Clash → Logs → 查看错误信息
2. **社区求助**：[ClashHub社区](https://bbs.clashhub.net)
3. **联系客服**：通过机场官网工单系统或TG群

---

## 🔗 相关资源

- [Clash for Windows 官方下载](https://clash-for-windows.net)
- [ClashVIP 机场](https://clashvip.net)
- [ClashHub 机场](https://clashhub.net)
- [机场导航](https://nav.clashvip.net)

---

**最后更新**：2026-03-26
