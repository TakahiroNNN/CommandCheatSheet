# Zabbix

## とりあえず構築してみる用
公式が提供しているリポジトリをクローン
```
git clone https://github.com/zabbix/zabbix-docker.git
cd zabbix-docker
git checkout 7.0
```

使用する composeファイルにシンボリックリンク張り直し（docker compose 時に読み込むファイルを設定）
```
# CentOS で MySQL の最新バージョンを使用する場合
ln -sf docker-compose_v3_centos_mysql_latest.yaml compose.yaml
```

**composeファイル内の、使用するコンテナ、ネットワーク以外の dockerリソースを削除する**

nginxのコンテナが立ち上がり、apacheのコンテナが立ち上がらないのが謎


## 
