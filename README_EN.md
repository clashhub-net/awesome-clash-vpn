# Awesome Clash VPN 馃敟

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![GitHub stars](https://img.shields.io/github/stars/clashhub-net/awesome-clash-vpn.svg?style=flat-square)](https://github.com/clashhub-net/awesome-clash-vpn/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/clashhub-net/awesome-clash-vpn.svg?style=flat-square)](https://github.com/clashhub-net/awesome-clash-vpn/network)
[![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-blue.svg)](LICENSE)

> 馃殌 **A curated list of Clash proxy tools, premium VPN nodes, and internet freedom resources**
> 
> Continuously updated | Last updated: 2026-03-26

**[涓枃鏂囨。](docs/zh/README.md)** | **English**

---

## 馃搼 Table of Contents

- [馃専 Recommended VPN Services](#-recommended-vpn-services)
- [馃捇 Client Tools](#-client-tools)
- [馃摎 Tutorials & Guides](#-tutorials--guides)
- [馃洜 Configuration Resources](#-configuration-resources)
- [馃摫 Mobile Solutions](#-mobile-solutions)
- [馃攳 Rules & Routing](#-rules--routing)
- [鉂?FAQ](#-faq)
- [馃 Contributing](#-contributing)

---

## 馃専 Recommended VPN Services

> 鈿?Tested and verified: Fast speeds, high stability, responsive support

| Name | Features | Protocols | Rating |
|------|----------|-----------|--------|
| [**ClashVIP**](https://clashvip.net) | Great value, global nodes, streaming unlocked (Netflix/HBO) | SSR/V2Ray/Trojan | 猸愨瓙猸愨瓙猸?|
| [**ClashHub**](https://clashhub.net) | Optimized routing, low latency, gaming-friendly | Shadowsocks/V2Ray | 猸愨瓙猸愨瓙猸?|
| [**Clash for Windows Official**](https://clash-for-windows.net) | Official recommendation, reliable nodes | All protocols | 猸愨瓙猸愨瓙 |

### 馃幆 How to Choose a VPN Service?

1. **Know your needs**: Streaming 鈫?look for Netflix/Disney+ unlock; Gaming 鈫?look for low latency
2. **Check routing**: Dedicated line > Relay > Direct (for stability)
3. **Check support**: TG group/ticket system = better service
4. **Try first**: Most services offer free trials

### 馃挕 VPN Navigation

- [**ClashVIP Navigator**](https://nav.clashvip.net) - VPN comparison, deals & promotions
- [**ClashHub Community**](https://bbs.clashhub.net) - Tutorials, Q&A, node reviews

---

## 馃捇 Client Tools

### Windows

| Tool | Features | Download |
|------|----------|----------|
| [**Clash for Windows**](https://clash-for-windows.net) | GUI interface, rule-based routing, most popular | [Download](https://clash-for-windows.net/download) |
| Clash Verge | Open-source, Rust-based, lightweight | [GitHub](https://github.com/clash-verge-rev/clash-verge-rev) |
| v2rayN | Multi-protocol support, feature-rich | [GitHub](https://github.com/2dust/v2rayN) |

### macOS

| Tool | Features | Download |
|------|----------|----------|
| [**Clash for Windows Mac**](https://clash-for-windows.net) | Same experience as Windows | [Download](https://clash-for-windows.net/download) |
| ClashX Pro | Native macOS, menu bar integration | [GitHub](https://github.com/yichengchen/clashX) |

### Linux

| Tool | Features | Download |
|------|----------|----------|
| Clash Verge | Cross-platform, modern UI | [GitHub](https://github.com/clash-verge-rev/clash-verge-rev) |
| Clash for Windows | Via Wine | [Tutorial](https://clash-for-windows.net/linux) |

---

## 馃摎 Tutorials & Guides

### Getting Started

- [**Complete Beginner's Guide**](docs/en/beginner-guide.md) - From zero to hero
- [Clash Rule Configuration](https://lancellc.gitbook.io/clash/) - Official docs
- [Subscription Conversion](docs/en/subscription-converter.md) - Format conversion

### Advanced Topics

- [Custom Rule Routing](docs/en/custom-rules.md) - Fine-grained traffic control
- [TUN Mode Setup](docs/en/tun-mode.md) - System-wide proxy for all apps
- [Script Enhancement](docs/en/script-enhancement.md) - Auto-switch, load balancing

### Streaming Unlock

- [Netflix Unlock Check](docs/en/netflix-check.md)
- [Disney+/HBO Max/Amazon Prime Guide](docs/en/streaming-unlock.md)
- [ChatGPT Node Configuration](docs/en/chatgpt-config.md)

---

## 馃洜 Configuration Resources

### Subscription Converters

| Tool | Description | Link |
|------|-------------|------|
| subconverter | Most popular conversion tool | [GitHub](https://github.com/tindy2013/subconverter) |
| ACL4SSR Online | Free online converter, rich rules | [Web](https://acl4ssr-sub.github.io/) |

### Preset Rules

```yaml
# Example: Ad blocking + China direct + Global proxy
Rule:
  - DOMAIN-SUFFIX,google.com,Proxy
  - DOMAIN-SUFFIX,github.com,Proxy
  - DOMAIN-SUFFIX,bilibili.com,Direct
  - DOMAIN-KEYWORD,adserver,REJECT
  - GEOIP,CN,Direct
  - MATCH,Proxy
```

More config templates in [config/](config/) directory.

---

## 馃摫 Mobile Solutions

### iOS

| Tool | Features | Price |
|------|----------|-------|
| Shadowrocket | Full-featured, multi-protocol | $3 (one-time) |
| Stash | Clash core, rich rules | $3 (one-time) |
| Surge 5 | Professional, powerful debugging | $99/year |

### Android

| Tool | Features | Download |
|------|----------|----------|
| Clash for Android | Open-source, user-friendly | [GitHub](https://github.com/Kr328/ClashForAndroid) |
| v2rayNG | Lightweight, multi-protocol | [GitHub](https://github.com/2dust/v2rayNG) |

---

## 馃攳 Rules & Routing

### Recommended Rule Sets

- [Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat) - Comprehensive
- [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) - Various routing rules
- [ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR) - Clash-compatible

### Routing Strategy Examples

| Group | Purpose |
|-------|---------|
| Proxy | Access foreign services |
| Direct | Direct connection for local services |
| Streaming | Streaming-specific nodes |
| AdBlock | Block advertisements |
| Final | Fallback rule |

---

## 鉂?FAQ

<details>
<summary><b>Q: Clash for Windows won't open?</b></summary>

**A:** Common solutions:
1. Run as administrator
2. Check firewall/antivirus blocking
3. Delete `.config/clash` folder and retry
4. Re-download latest version

Detailed troubleshooting: [Troubleshooting Guide](docs/en/troubleshooting.md)
</details>

<details>
<summary><b>Q: How to check if a node supports Netflix?</b></summary>

**A:** Methods:
1. Visit [Netflix.com](https://netflix.com) - check for regional restrictions
2. Use [Netflux](https://netflux.netlify.app/) to test
3. Play test video [test-patterns](https://www.netflix.com/watch/70143404)
</details>

<details>
<summary><b>Q: Why can't I access some websites?</b></summary>

**A:** Troubleshooting steps:
1. Check if the rule is correct (not wrongly assigned to Direct)
2. Try switching nodes
3. Enable TUN mode (some apps don't use system proxy)
4. Check DNS settings
</details>

---

## 馃 Contributing

Contributions are welcome!

1. Fork this repository
2. Create a branch (`git checkout -b feature/add-resource`)
3. Commit changes (`git commit -m 'Add new resource'`)
4. Push to branch (`git push origin feature/add-resource`)
5. Create a Pull Request

### Contribution Guidelines

- Ensure resources are valid and useful
- Add brief descriptions and reasons for recommendation
- Place in appropriate category
- Maintain consistent formatting

---

## 鈿狅笍 Disclaimer

This project is for technical exchange and educational purposes only. Please comply with local laws and regulations. Do not use for illegal purposes. Users are responsible for any consequences resulting from the use of this project.

---

## 馃摟 Contact

- Issue Tracker: [Issues](https://github.com/clashhub-net/awesome-clash-vpn/issues)
- Telegram: [Join Discussion](https://t.me/clashvpn)

---

## 馃摐 License

[CC BY-NC-SA 4.0](LICENSE) 漏 2026

---

**猸?If this project helps you, please give it a Star!**

---

<p align="center">
  <a href="https://clashvip.net">ClashVIP</a> 鈥?  <a href="https://clashhub.net">ClashHub</a> 鈥?  <a href="https://clash-for-windows.net">CFW Download</a> 鈥?  <a href="https://bbs.clashhub.net">Community</a> 鈥?  <a href="https://nav.clashvip.net">Navigator</a>
</p>
