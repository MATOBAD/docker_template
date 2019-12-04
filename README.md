# Dockerのテンプレート（個人用）
## 一括削除コマンド
### 停止コンテナ
```
docker container prune
```
### 全コンテナ
```
docker rm -f `docker ps -a -q`
```
### タグ無しイメージ
```
docker rmi `docker images -f "dangling=true" -q`
```
### 未使用イメージ
```
docker image prune
```
### 全イメージ
```
docker rmi `docker images -a -q`
```
### 未使用ボリューム
```
docker volume prune
```
### 未使用ネットワーク
```
docker network prune
```
### 上記全て
```
docker system prune
```
