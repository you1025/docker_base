# 自分用 Docker サンプル

CentOS の終了により対象外とする(2025.01.18)

## コンテナ作成&起動
```
$ docker-compose up -d
```

## ログイン

### Ubuntu

```
$ docker container exec -it -u shimajiro myubuntu /bin/bash
```

## コンテナ停止

```
$ docker-compose stop
```

## コンテナ削除

```
$ docker-compose down --rmi local
```
