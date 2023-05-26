# 自分用 Docker サンプル

## コンテナ作成&起動
```
$ docker-compose up -d
```

## ログイン

### Ubuntu

```
$ docker container exec -it -u shimajiro myubuntu /bin/bash
```

### Centos

```
$ docker container exec -it -u shimajiro mycentos /bin/bash
```

## コンテナ停止

```
$ docker-compose stop
```

## コンテナ削除

```
$ docker-compose down --rmi local
```
