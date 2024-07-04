# Zabbix

## とりあえず構築してみる用
公式が提供しているリポジトリをクローン
```
git clone https://github.com/zabbix/zabbix-docker.git
cd zabbix-docker
git checkout 7.0
```

コンテナ起動
```
docker compose up -d --build
```

nginxのコンテナが立ち上がり、apacheのコンテナが立ち上がらないのが謎


## 
