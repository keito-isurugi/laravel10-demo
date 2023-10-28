# Laravel10のデモ環境
## 環境構築
- 参考：
  [Laravel 10 の開発環境をdockerで実現する方法](https://qiita.com/hitotch/items/869070c3a9f474a358ea)
- Docker起動
```
$ docker compose up -d
```
- Laravel10インストール
```.shell
# コンテナに入る
$ docker compose exec laravel10-demo-app bash

# サブフォルダを作ってそこにLaravelをインストール
$ cd /src
$ mkdir laravel10_demo_tmp
$ cd laravel10_demo_tmp
$ composer create-project "laravel/laravel=10.*" . --prefer-dist

# 中身をプロジェクトフォルダに移動し、一時サブフォルダを削除。
$ cd /src
$ mv laravel10_demo_tmp/* ./
$ mv laravel10_demo_tmp/.* ./
$ rm laravel10_demo_tmp -rf

# 依存のインストール
$ cd /src
$ composer install
$ npm install

# 書き込み権限を設定
$ chmod -R guo+w storage

# storageのシンボリックリンクを設置
$ php artisan storage:link
```

## TODO
- .envファイルで定義されたものをdocker-compose.ymlで使う
- seedファイル作成
