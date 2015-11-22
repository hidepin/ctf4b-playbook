# ctf4b-playbook

## 概要
セキュリティコンテストチャレンジブックのサンプルが動作する環境。
サンプルはすべて動作するが紹介されているツールがすべてインストールされているわけではない。

## 対応OS
- CentOS6 (pedaがpython関連のため動作しない)

## ユーザ
- ctf4b (password: ctf4b123)

## 設定手順
0. CentOS6をminimalでインストールする。

1. ログインしrootになる。

2. epelリポジトリを有効化してansibleをインストールする。

``` sh
yum install -y epel-release
yum install -y ansible sshpass
```

3. gitをインストールしてplaybookを入手する

``` sh
yum install -y git
git clone https://github.com/hidepin/ctf4b-playbook.git
```

4. playbookを実行する

``` sh
cd ctf4b-playbook
env ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i production -k -D site.yml
# (rootパスワードを入力)
```

5. 再起動する。

``` sh
reboot
```
