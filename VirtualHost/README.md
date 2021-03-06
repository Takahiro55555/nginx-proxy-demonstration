# VirtualHost

## これは何？
nginx-proxyをのVirtualHost機能を使用し、1台のホストで複数のウェブサイトやウェブアプリを動作させる際の例です。

通常VirtualHost機能を使用せずに、1台のホストで複数のウェブサイトやウェブアプリを動作させる場合は、それぞれ別のポート番号を用いて動作させる必要があります。しかし、VirtualHost機能を使用すると80番や443番などのウェルノウンポートなどを複数のウェブサイトやウェブアプリで使用し、サブドメインなどを変更するだけで動作させることができます。

今回は2つの異なるウェブサイトをApachコンテナを用いて1台のPC上で動作させ、ブラウザから確認します。

## 動かし方

1. このREDMEがあるディレクトリに移動する

2. 以下のコマンドを実行し、コンテナを起動する
```
docker-compose up
```

3. 以下のリンクからウェブサイトへアクセスし動作を確認する
- サイト１：[http://httpd01.localhost/](http://httpd01.localhost/)
- サイト２：[http://httpd02.localhost/](http://httpd02.localhost/)

4. コンテナを停止させる
```
docker-compose down
```

## 参考
- [VirtualHostをお手軽に実現できるDockerコンテナnginx-proxyの起動方法](https://suin.io/531)