# 鏁呴殰鎺掗櫎鎸囧崡

鏈枃妗ｆ敹闆嗕簡 Clash for Windows 鏈€甯歌鐨勯棶棰樺強瑙ｅ喅鏂规銆?
---

## 馃敡 甯歌闂

### 1. Clash for Windows 鏃犳硶鍚姩

**鐥囩姸**锛氬弻鍑诲浘鏍囨病鍙嶅簲锛屾垨闂€€

**瑙ｅ喅鏂规**锛?
#### 鏂规A锛氫互绠＄悊鍛樿韩浠借繍琛?1. 鍙抽敭 Clash for Windows 鍥炬爣
2. 閫夋嫨"浠ョ鐞嗗憳韬唤杩愯"

#### 鏂规B锛氭竻鐞嗛厤缃枃浠?```powershell
# 鍒犻櫎閰嶇疆鏂囦欢澶?Remove-Item -Recurse -Force "$env:USERPROFILE\.config\clash"
```

#### 鏂规C锛氭鏌ラ槻鐏/鏉€姣掕蒋浠?1. 鏆傛椂鍏抽棴鏉€姣掕蒋浠舵祴璇?2. 鍦ㄩ槻鐏涓坊鍔?Clash for Windows 鐧藉悕鍗?3. Windows瀹夊叏涓績 鈫?闃茬伀澧?鈫?鍏佽搴旂敤閫氳繃闃茬伀澧?
#### 鏂规D锛氶噸鏂板畨瑁?1. 瀹屽叏鍗歌浇褰撳墠鐗堟湰
2. 浠?[瀹樼綉](https://clash-for-windows.net) 涓嬭浇鏈€鏂扮増
3. 瀹夎鏃堕€夋嫨"涓烘墍鏈夌敤鎴峰畨瑁?

---

### 2. 鏃犳硶璁块棶浠讳綍缃戠珯

**鐥囩姸**锛氬紑鍚唬鐞嗗悗鎵€鏈夌綉绔欓兘鎵撲笉寮€

**鎺掓煡姝ラ**锛?
#### Step 1: 妫€鏌ョ郴缁熶唬鐞?```
璁剧疆 鈫?缃戠粶鍜孖nternet 鈫?浠ｇ悊 鈫?浣跨敤浠ｇ悊鏈嶅姟鍣?```
纭繚绯荤粺浠ｇ悊宸插紑鍚紝鍦板潃涓?`127.0.0.1`锛岀鍙ｄ负 `7890`

#### Step 2: 娴嬭瘯鑺傜偣杩為€氭€?鍦?Clash 闈㈡澘涓偣鍑昏妭鐐规祴璇曟寜閽紝纭鑺傜偣鍙敤

#### Step 3: 妫€鏌ユā寮?- **鍏ㄥ眬妯″紡**锛氭墍鏈夋祦閲忛兘璧颁唬鐞?- **瑙勫垯妯″紡**锛氭寜瑙勫垯鍒嗘祦
- **鐩磋繛妯″紡**锛氫笉璧颁唬鐞?
鎺ㄨ崘浣跨敤 **瑙勫垯妯″紡**

#### Step 4: 娴嬭瘯鐩磋繛
```powershell
# 娴嬭瘯鏄惁鑳借繛鎺ュ埌鑺傜偣鏈嶅姟鍣?Test-NetConnection -ComputerName 鑺傜偣鍩熷悕 -Port 鑺傜偣绔彛
```

---

### 3. 閮ㄥ垎缃戠珯鏃犳硶璁块棶

**鐥囩姸**锛氬ぇ閮ㄥ垎缃戠珯姝ｅ父锛屼絾鏌愪簺鐗瑰畾缃戠珯鎵撲笉寮€

**瑙ｅ喅鏂规**锛?
#### 鍦烘櫙A锛氱綉绔欒閿欒鍦板垎閰嶅埌鐩磋繛
鍦ㄩ厤缃枃浠朵腑娣诲姞瑙勫垯锛?```yaml
rules:
  - DOMAIN-SUFFIX,example.com,Proxy
```

#### 鍦烘櫙B锛氶渶瑕乀UN妯″紡
鏌愪簺搴旂敤锛堝娓告垙銆佸懡浠よ宸ュ叿锛変笉璧扮郴缁熶唬鐞嗭細
1. Clash for Windows 鈫?General 鈫?Service Mode 鈫?Install
2. 寮€鍚?TUN Mode

#### 鍦烘櫙C锛欴NS姹℃煋
淇敼DNS璁剧疆锛?```yaml
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

### 4. Netflix/YouTube 鏄剧ず"涓嶅彲鐢?

**鐥囩姸**锛氭祦濯掍綋鎻愮ず鍦板尯闄愬埗

**瑙ｅ喅鏂规**锛?
#### Netflix
1. 浣跨敤鏀寔 Netflix 瑙ｉ攣鐨勮妭鐐?2. 鍦?[Netflux](https://netflux.netlify.app/) 妫€娴嬭妭鐐规敮鎸佹儏鍐?3. 閫夋嫨鏍囨敞"Netflix Full"鎴?Netflix Original"鐨勮妭鐐?
#### YouTube
1. 纭鑺傜偣IP娌℃湁琚皝绂?2. 灏濊瘯鍒囨崲鑺傜偣
3. 娓呴櫎娴忚鍣ㄧ紦瀛?
#### Disney+/HBO
闇€瑕佷娇鐢ㄧ壒瀹氳В閿佽妭鐐癸紝鑱旂郴浣犵殑鏈哄満瀹㈡湇鑾峰彇鎺ㄨ崘鑺傜偣

---

### 5. 閫熷害寰堟參

**鍘熷洜鍒嗘瀽**锛?
| 鍘熷洜 | 瑙ｅ喅鏂规 |
|------|----------|
| 鑺傜偣璐熻浇楂?| 鍒囨崲鍒颁綆寤惰繜鑺傜偣 |
| 绾胯矾璐ㄩ噺宸?| 閫夋嫨涓撶嚎/涓浆鑺傜偣 |
| 鏈湴缃戠粶闂 | 娴嬭瘯鐩磋繛閫熷害 |
| DNS瑙ｆ瀽鎱?| 鍚敤DNS缂撳瓨 |

**浼樺寲寤鸿**锛?
1. **閫夋嫨鍚堥€傜殑鑺傜偣**
   - 娓告垙鐢ㄦ埛锛氶€夋嫨寤惰繜 < 100ms 鐨勮妭鐐?   - 涓嬭浇鐢ㄦ埛锛氶€夋嫨甯﹀澶х殑鑺傜偣
   - 杩藉墽鐢ㄦ埛锛氶€夋嫨娴佸獟浣撹В閿佽妭鐐?
2. **寮€鍚礋杞藉潎琛?*
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

### 6. 璁㈤槄鏇存柊澶辫触

**鐥囩姸**锛氱偣鍑绘洿鏂拌闃呮彁绀洪敊璇?
**瑙ｅ喅鏂规**锛?
#### 鏂规A锛氭鏌ヨ闃呴摼鎺?1. 鐧诲綍鏈哄満瀹樼綉纭璁㈤槄閾炬帴鏈夋晥
2. 閲嶇疆璁㈤槄閾炬帴锛堝鏋滄満鍦烘敮鎸侊級

#### 鏂规B锛氭墜鍔ㄤ笅杞?```powershell
# 涓嬭浇璁㈤槄鏂囦欢
Invoke-WebRequest -Uri "浣犵殑璁㈤槄閾炬帴" -OutFile "subscription.yaml"
```
鐒跺悗鍦?Clash 涓鍏ユ湰鍦版枃浠?
#### 鏂规C锛氫娇鐢ㄨ闃呰浆鎹?1. 璁块棶 [ACL4SSR鍦ㄧ嚎杞崲](https://acl4ssr-sub.github.io/)
2. 绮樿创璁㈤槄閾炬帴
3. 閫夋嫨鐩爣鏍煎紡骞惰浆鎹?
---

### 7. 绔彛琚崰鐢?
**鐥囩姸**锛氭彁绀虹鍙?7890 宸茶鍗犵敤

**瑙ｅ喅鏂规**锛?
#### 鏌ユ壘鍗犵敤杩涚▼
```powershell
netstat -ano | findstr :7890
```

#### 缁撴潫杩涚▼
```powershell
taskkill /PID 杩涚▼ID /F
```

#### 鎴栦慨鏀圭鍙?鍦?Clash 閰嶇疆涓慨鏀癸細
```yaml
port: 7891  # 鏀逛负鍏朵粬绔彛
socks-port: 7892
```

---

### 8. Mac鐗堟棤娉曟墦寮€"鏉ヨ嚜韬唤涓嶆槑寮€鍙戣€?

**瑙ｅ喅鏂规**锛?
```bash
# 缁堢鎵ц
sudo xattr -r -d com.apple.quarantine /Applications/Clash\ for\ Windows.app
```

---

## 馃摓 鑾峰彇甯姪

濡傛灉浠ヤ笂鏂规閮芥棤娉曡В鍐抽棶棰橈細

1. **鏌ョ湅鏃ュ織**锛欳lash 鈫?Logs 鈫?鏌ョ湅閿欒淇℃伅
2. **绀惧尯姹傚姪**锛歔ClashHub绀惧尯](https://bbs.clashhub.net)
3. **鑱旂郴瀹㈡湇**锛氶€氳繃鏈哄満瀹樼綉宸ュ崟绯荤粺鎴朤G缇?
---

## 馃敆 鐩稿叧璧勬簮

- [Clash for Windows 瀹樻柟涓嬭浇](https://clash-for-windows.net)
- [ClashVIP 鏈哄満](https://clashvip.net)
- [ClashHub 鏈哄満](https://clashhub.net)
- [鏈哄満瀵艰埅](https://nav.clashvip.net)

---

**鏈€鍚庢洿鏂?*锛?026-03-26
