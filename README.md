# 自分用 Docker サンプル

## コンテナ作成&起動
```
$ docker-compose up -d
```

## ログイン

### Ubuntu

```
$ docker container exec -it -d shimajiro myubuntu /bin/bash
```

### Centos

```
$ docker container exec -it -d shimajiro mycentos /bin/bash
```