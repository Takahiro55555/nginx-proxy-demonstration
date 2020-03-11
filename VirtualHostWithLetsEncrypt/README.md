# VirtualHostWithLetsEncrypt

## これは何？

`VirtualHost`ディレクトリで行っていることをHTTPS（Let`s Encryptを使用）に対応させた例です。

このデモを動かすには、外部へ公開可能なサーバーとドメインが必要です。

## ファイルの編集
`app/docker-compose`ファイルを編集する必要があります。

具体的には以下の部分を編集する必要があります。
- `VIRTUAL_HOST`
- `LETSENCRYPT_HOST`
- `LETSENCRYPT_EMAIL`

## 動かし方

1. このREDMEがあるディレクトリに移動する

2. 以下のコマンドを実行し、コンテナを起動する
```
docker-compose up
```

3. 以下のリンクからウェブサイトへアクセスし動作を確認する

`example.com`の部分は適宜書き換えてください。
- サイト１：[https://httpd01.example.com/](https://httpd01.example.com/)
- サイト２：[https://httpd02.example.com/](https://httpd02.example.com/)


4. コンテナを停止させる
```
docker-compose down
```

## 参考
- [dockerでnginx導入と複数サービスの展開](https://qiita.com/asylum/items/05d8dc4cc4671d7a5d4f)