# laravel構築用のdockerファイル

・nginx
・php8.0
・mysql8.0
・phpmyadmin

## 環境の確認

```bash
docker-compose up -d --build
```

```bash
docker-compose exec app bash # phpのコンテナに入る
```

で中に入り、
/usr/share/nginx/htmlの中にindex.phpなどを作成して、ポート8080で表示されれば成功。

## laravelをインストール

その後、そのまま中でindex.phpを削除。
その場所にcomposerでlaravelをインストール。

```bash
composer create-project "laravel/laravel=8.*" .
```

## サーバーのルートを変更

exitして、
nginxのdefault.confのrootを
/usr/share/nginx/html/publicに変更してから

```conf:default.conf
server {
    listen 80;
    server_name example.com;
    root /usr/share/nginx/html/public;  # ルートをlaravelに合わせる

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-XSS-Protection "1; mode=block";
    add_header X-Content-Type-Options "nosniff";
    ....
    ....
```

再起動

```bash
docker-compose restart
```
