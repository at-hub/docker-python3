# docker-python3

* MacBook Proのデフォルトでは古いVer(Python2.7x)がインストールされているので、現在スタンダードな3.xを使える環境を構築しました。

## 環境構築手順
[参考サイト docker-composeでシンプルにpython環境構築](https://qiita.com/A-Kira/items/7aaa1a16f8f6c8ed4040)

1. Docker For Macをインストール
[参考サイト DockerをMacにインストールする](https://qiita.com/kurkuru/items/127fa99ef5b2f0288b81)
インストールしてDockerのVersionが確認できればOK

2. at-hub用アカウントでこのリポジトリにアクセスして、自分のアカウントをcollaboratorに追加する

3. ローカルPCで適当なディレクトリに移動

4. リポジトリをclone
`git clone https://github.com/at-hub/docker-python3.git`
※private repositoryのため、3で正しく追加できていないとエラーになるので要注意
* cloneした一式をチェック。こんな構成になってればOK
```
.
├── docker
│   └── python
│       └── Dockerfile
├── docker-compose.yml
└── html
    └── hello.py
```

5. dockerコンテナを起動する
* `docker-compose.yml`のある階層で`docker-compose up -d`を実行

6. dockerコンテナにアクセスする
* `docker-compose.yml`のある階層で`docker-compose exec app bash`を実行。
* アクセスできたら、`python --version`を実行してインストールされているpythonのVerを確認。`Python 3.7.6`になっていればOK。
```
root@xxxxx:/var/www/html# python --version
Python 3.7.6
```
* アクセス直後、`/var/www/html`にいることを確認して`ls -l`を実行するとローカルの`html`ディレクトリに保存されている`hello.py`が見えるはず。
```
root@xxxxx:/var/www/html# ls -l
total 4
-rw-r--r-- 1 root root 21 Dec 28 02:03 hello.py
```

7. `hello.py`を実行してみる
* ターミナル上で以下のように出力されれば環境構築は成功!!!!
```
root@xxxxx:/var/www/html# python hello.py
Hello world
```
