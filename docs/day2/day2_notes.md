# Day2 - 抓包与三次握手验证

**抓包文件**: `docs/day2_traffic.pcap`  
**提取的握手 pcap**: `docs/day2_handshake.pcap`  

## 观察到的三次握手（摘要）
- 客户端 (Kali): `192.168.181.128:46774`
- 服务器 (example.com): `23.215.0.136:80`

三条握手包（按顺序）：
1. SYN — from `192.168.181.128:46774` → `23.215.0.136:80` (tcp.flags.syn=1, tcp.flags.ack=0)
2. SYN+ACK — from `23.215.0.136:80` → `192.168.181.128:46774` (tcp.flags.syn=1, tcp.flags.ack=1)
3. ACK — from `192.168.181.128:46774` → `23.215.0.136:80` (tcp.flags.syn=0, tcp.flags.ack=1)

后续还有多条 ACK/Data 包，说明连接建立后进行了数据传输。

> **安全提示**：完整 pcap 可能包含敏感信息（HTTP headers、Cookie、IP 等）。仅上传或分享经过脱敏或仅含握手的 pcap。

