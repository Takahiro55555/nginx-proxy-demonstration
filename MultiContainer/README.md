# MultiContainer

## これは何？

起動する両方のhttpdコンテナ（サーバー）に同一のホスト名を設定し、nginx-proxyコンテナをロードバランサとして機能させる（？？？）ためのデモです。

数回アクセスすると`Test Page 01`と表示される場合と、`Test Page 02`と表示される場合があります。

これは、nginx-proxyコンテナがロードバランサとして機能しているためではないかと考えています。
しかし、**きちんと調べたわけではないので確証は無い**です。

また、片方のhttpdコンテナを停止させても問題なくページが表示されることも確認できます。

## 動かし方

1. このREDMEがあるディレクトリに移動する

2. 以下のコマンドを実行し、コンテナを起動する
```
docker-compose up -d
```

3. 以下のリンクからウェブサイトへアクセスし動作を確認する
- [http://common.localhost/](http://common.localhost/)

何回かページをリロードし、表示内容の差異を確認する。


4. 片方のコンテナを停止させてみる
```
$ docker ps  # 起動中のコンテナを確認する
CONTAINER ID        IMAGE                 COMMAND                  CREATED             STATUS              PORTS                NAMES
52c0d8a6b609        httpd                 "httpd-foreground"       2 minutes ago       Up 2 minutes        80/tcp               httpd-02
d5cee5a8c720        httpd                 "httpd-foreground"       2 minutes ago       Up 1 second         80/tcp               httpd-01
88542d800d80        jwilder/nginx-proxy   "/app/docker-entrypo…"   2 minutes ago       Up 2 minutes        0.0.0.0:80->80/tcp   nginx-proxy

$ docker stop httpd-02  # コンテナ名を指定して停止させる
```

何回かページをリロードし、表示内容の差異が**無い**ことを確認する。

5. 停止させたコンテナを再起動し、表示内容の差異を確認する
```
$ docker start httpd-02  # 先ほど停止させたコンテナを再起動する
```
何回かページをリロードし、表示内容の差異を確認する。

6. コンテナを停止させる
実験が終わったら、以下のコマンドを実行して全てのコンテナを停止させる。

```
docker-compose down
```

## 参考
- [dockerでnginx導入と複数サービスの展開](https://qiita.com/asylum/items/05d8dc4cc4671d7a5d4f)