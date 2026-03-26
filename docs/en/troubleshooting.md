# Troubleshooting Guide

This document collects the most common issues with Clash for Windows and their solutions.

---

## 🔧 Common Issues

### 1. Clash for Windows Won't Start

**Symptoms**: Double-clicking icon shows no response, or crashes immediately

**Solutions**:

#### Option A: Run as Administrator
1. Right-click Clash for Windows icon
2. Select "Run as administrator"

#### Option B: Clear Config Files
```powershell
# Delete configuration folder
Remove-Item -Recurse -Force "$env:USERPROFILE\.config\clash"
```

#### Option C: Check Firewall/Antivirus
1. Temporarily disable antivirus software to test
2. Add Clash for Windows to firewall whitelist
3. Windows Security → Firewall → Allow app through firewall

#### Option D: Reinstall
1. Completely uninstall current version
2. Download latest version from [Official Site](https://clash-for-windows.net)
3. Choose "Install for all users" during installation

---

### 2. Cannot Access Any Websites

**Symptoms**: All websites inaccessible after enabling proxy

**Troubleshooting Steps**:

#### Step 1: Check System Proxy
```
Settings → Network & Internet → Proxy → Use a proxy server
```
Ensure system proxy is enabled, address is `127.0.0.1`, port is `7890`

#### Step 2: Test Node Connectivity
Click node test button in Clash panel to confirm nodes are working

#### Step 3: Check Mode
- **Global Mode**: All traffic goes through proxy
- **Rule Mode**: Traffic routed by rules
- **Direct Mode**: No proxy

**Recommended**: Use **Rule Mode**

#### Step 4: Test Direct Connection
```powershell
# Test if you can connect to node server
Test-NetConnection -ComputerName node-domain -Port node-port
```

---

### 3. Some Websites Won't Load

**Symptoms**: Most sites work, but specific sites fail

**Solutions**:

#### Scenario A: Website wrongly assigned to direct
Add rule in config file:
```yaml
rules:
  - DOMAIN-SUFFIX,example.com,Proxy
```

#### Scenario B: Need TUN Mode
Some apps (games, CLI tools) don't use system proxy:
1. Clash for Windows → General → Service Mode → Install
2. Enable TUN Mode

#### Scenario C: DNS Pollution
Modify DNS settings:
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

### 4. Netflix/YouTube Shows "Not Available"

**Symptoms**: Streaming services show regional restrictions

**Solutions**:

#### Netflix
1. Use Netflix-unlock supported nodes
2. Check node support at [Netflux](https://netflux.netlify.app/)
3. Select nodes marked "Netflix Full" or "Netflix Original"

#### YouTube
1. Confirm node IP isn't blocked
2. Try switching nodes
3. Clear browser cache

#### Disney+/HBO
Need specific unlock nodes - contact your provider support for recommendations

---

### 5. Slow Speeds

**Cause Analysis**:

| Cause | Solution |
|-------|----------|
| High node load | Switch to low-latency node |
| Poor line quality | Choose dedicated/relay nodes |
| Local network issues | Test direct connection speed |
| Slow DNS resolution | Enable DNS caching |

**Optimization Tips**:

1. **Choose Right Node**
   - Gaming: Select latency < 100ms
   - Downloading: Select high bandwidth nodes
   - Streaming: Select streaming-unlock nodes

2. **Enable Load Balancing**
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

### 6. Subscription Update Failed

**Symptoms**: Error when clicking update subscription

**Solutions**:

#### Option A: Check Subscription Link
1. Login to provider website to confirm subscription link is valid
2. Reset subscription link (if supported by provider)

#### Option B: Manual Download
```powershell
# Download subscription file
Invoke-WebRequest -Uri "your-subscription-link" -OutFile "subscription.yaml"
```
Then import local file in Clash

#### Option C: Use Subscription Converter
1. Visit [ACL4SSR Online Converter](https://acl4ssr-sub.github.io/)
2. Paste subscription link
3. Select target format and convert

---

### 7. Port Already in Use

**Symptoms**: Port 7890 already in use

**Solutions**:

#### Find Process Using Port
```powershell
netstat -ano | findstr :7890
```

#### End Process
```powershell
taskkill /PID process-id /F
```

#### Or Change Port
Modify in Clash config:
```yaml
port: 7891  # Change to other port
socks-port: 7892
```

---

### 8. Mac Version "Unidentified Developer"

**Solution**:

```bash
# Run in Terminal
sudo xattr -r -d com.apple.quarantine /Applications/Clash\ for\ Windows.app
```

---

## 📞 Getting Help

If above solutions don't work:

1. **Check Logs**: Clash → Logs → View error messages
2. **Community Help**: [ClashHub Community](https://bbs.clashhub.net)
3. **Contact Support**: Via provider ticket system or TG group

---

## 🔗 Related Resources

- [Clash for Windows Download](https://clash-for-windows.net)
- [ClashVIP Service](https://clashvip.net)
- [ClashHub Service](https://clashhub.net)
- [VPN Navigator](https://nav.clashvip.net)

---

**Last Updated**: 2026-03-26
