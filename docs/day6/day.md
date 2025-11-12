cat > docs/day6/day6_notes.md <<'EOF'
# Day6 - 端口扫描与主机探测 (nmap)

## 环境
- 扫描目标: 192.168.181.128 (本机 VM)
- 抓包文件: docs/day6_scan_local.pcap
- nmap 输出: docs/day6_nmap_vm_top100.txt, docs/day6_nmap_vm_sV_O.txt

## 流程与命令
- 启动抓包: sudo tcpdump -i any tcp -w docs/day6_scan_local.pcap
- 快速扫描: nmap -sS --top-ports 100 -v 192.168.181.128 -oN docs/day6_nmap_vm_top100.txt
- 服务探测: nmap -sS -sV -O 192.168.181.128 -oN docs/day6_nmap_vm_sV_O.txt

## 观察 (填入你的观察结果)
- 开放端口: ...
- 端口对应服务与版本: ...
- 抓包对应：SYN (client) -> SYN/ACK 或 RST (server) -> 对应 open/closed
- RTT 与异常: ...

## 安全注意
请仅扫描授权主机。NSE 脚本可能触发安全监控或破坏服务。
EOF
