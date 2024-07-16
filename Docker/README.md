# Docker Command Cheat Sheet

## Dockerネットワーク
Dockerネットワークの一覧を表示
```
docker network ls
```

特定のDockerネットワークに接続されているコンテナを表示
```
docker network inspect <network_name>
```

## Dockerのリポジトリが見つからないエラー
エラー内容
```
[+] Running 1/0
 ✘ selenium Error Get "https://registry-1.docker.io/v2/": dial tcp: lookup registry-1.docker.io on [::1]:53: read udp [::1]:48022->[::1]:53: read: connection refused                    0.0s 
Error response from daemon: Get "https://registry-1.docker.io/v2/": dial tcp: lookup registry-1.docker.io on [::1]:53: read udp [::1]:48022->[::1]:53: read: connection refused
```

DNSなどの設定が狂うとリポジトリが見つからないエラーになる
WSLで使用するDNSを設定すれば解決する
```
# resolve.conf（シンボリックリンク） のリンク向き先変更
sudo ln -nfs new_resolve.conf /etc/resolve.conf

# resolve.conf（シンボリックリンク） の修正
sudo vi new_resolve.conf

>nameserver 192.168.204.102
>nameserver 172.21.21.102

```
