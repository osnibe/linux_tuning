Linuxカーネルパラメータ　チューニング

受信バッファーの最大サイズ

受信バッファーサイズ
$ sysctl net.core.rmem_max
net.core.rmem_max = 212992 (208KB)
送信バッファーサイズ
$ sysctl net.core.wmem_max
net.core.wmem_max = 212992 (208KB)

受信バッファーサイズの自動チューニング機能

有効じゃないと設定した受信バッファーが最大サイズまで利用されない
$ sysctl net.ipv4.tcp_moderate_rcvbuf
net.ipv4.tcp_moderate_rcvbuf = 1

TCPソケットの送受信バッファーの最小・標準・最大サイズ

IPv4通信における受信バッファーサイズ
$ sysctl net.ipv4.tcp_rmem
net.ipv4.tcp_rmem = 4096        87380   6291456 (6144KB)
IPv4通信における送信バッファーサイズ
$ sysctl net.ipv4.tcp_wmem
net.ipv4.tcp_wmem = 4096        16384   4194304 (4096KB)

受信パケットの最大バッファー数

$ sysctl net.core.netdev_max_backlog
net.core.netdev_max_backlog = 1000

チューニング

$ sudo sysctl -w net.core.wmem_max=16777216 (16MB)
$ sudo sysctl -w net.core.rmem_max=16777216 (16MB)
$ sudo sysctl -w net.ipv4.tcp_rmem="4096 87380 16777216" (16MB)
$ sudo sysctl -w net.ipv4.tcp_wmem="4096 87380 16777216" (16MB)
$ sudo sysctl -w net.core.netdev_max_backlog=5000

設定ファイルに記述

$ sudo vi /etc/sysctl.conf
net.core.wmem_max = 16777216
net.core.rmem_max = 16777216
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 87380 16777216
net.core.netdev_max_backlog = 5000
