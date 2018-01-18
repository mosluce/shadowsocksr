ShadowsocksR
===========

[原說明詳見](https://github.com/shadowsocksr-backup/shadowsocksr)

## 運作環境

- 安裝 Docker 

```shell
curl -sSL get.docker.com | sh -
```

## 啟動服務 

> 選擇其中一種方法即可

1. 使用 Docker Hub
```shell
# 6440-6450 port mapping 範圍自行決定
docker run -d --restart=always \
  -p 6440-6450:6440-6450 \
  --name ssr \
  mosluce/5hadows0cksr-mudbjson
```
2. Build 自己的 image
```shell
git clone -b mujson https://github.com/mosluce/shadowsocksr

cd shadowsocksr

docker build -t [your/image:tag] .

docker run -d --restart=always \
  -p 6440-6450:6440-6450 \
  --name ssr \
  [your/image:tag]
```

## 管理使用者

```shell
# 說明非常詳細相信你會看 XD
docker exec -it ssr python mujson_mgr.py -h
```

## 簡短指令

```shell
alias mujson="docker exec -it ssr python mujson_mgr.py"

# 取得說明
mujson -h
```

## 其他研究中問題

- [ ] 多用戶 + Mysql = 多服務器架構