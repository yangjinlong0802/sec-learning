cat > day5_notes.md <<'EOF'
# Day5 - DNS 与 HTTP 抓包分析

## 实验目的
- 观察 DNS 查询与响应（UDP 53）
- 观察 HTTP 请求与响应（TCP 80）
- 理解两种协议在抓包中的不同特征与过滤器

## 抓包文件
- pcap: day5_dns_http.pcap
- 摘要: day5_summary.txt

## 关键观察（示例）
- DNS 请求：客户端 -> DNS 解析服务器（UDP 53），查询域名 example.com。
- DNS 响应：服务器回复 A 记录（例如 93.184.216.34 / CDN 地址），用于后续 TCP 连接。
- HTTP 请求：客户端发起 TCP 三次握手后发送 HTTP 请求（GET / 或 HEAD），可在抓包中看到 `GET /` 和 `Host: example.com`。
- HTTP 响应：服务器返回 `HTTP/1.1 200 OK` 及 Content-Type 等头部字段。

## 常用 Display Filters（Wireshark）
- DNS 请求: `dns && dns.flags.response == 0`
- DNS 响应: `dns && dns.flags.response == 1`
- 所有 DNS: `dns`
- HTTP 请求: `http.request`
- HTTP 响应: `http.response`

## 安全注意
- pcap 可能包含敏感信息（内部 DNS、Cookie、Authorization）。除非脱敏或仅分享摘要，否则不要公开上传完整 pcap。

EOF
