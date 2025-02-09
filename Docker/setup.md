
### Docker（Comunity Edition）
Docker公式のGPGキー（GPGというオープンソースのツールの公開鍵）登録
```
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
Docker公式のGPGキーを使って、aptが参照するリポジトリを追加
```
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
リポジトリ更新後、DockerCE のインストール
```
sudo apt update -y
sudo apt install -y docker-ce
```
Docker daemon 起動
```
sudo service docker start
```
正常にインストールされたか、下記コマンドで確認
```
sudo docker run hello-world
```

#### Docker の簡易化・便利設定
現在のユーザが sudo 無しで dockerコマンドが動くように
```
# 現ユーザを docker グループに追加
sudo gpasswd -a $USER docker
# docker グループの書き込み権限付与
sudo chgrp docker /var/run/docker.sock
```
Docker daemon の自動起動（.bashrc に下記を記載）
```
# start docker service
if test $(service docker status | awk '{print $4}') = 'not'; then 
  sudo /usr/sbin/service docker start
fi
```
