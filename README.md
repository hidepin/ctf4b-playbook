# ctf4b-playbook

## 概要
セキュリティコンテストチャレンジブックのサンプルが動作する環境。
サンプルはすべて動作するが紹介されているツールがすべてインストールされているわけではない。

## 対応OS
- CentOS6 (pedaがpython関連のため動作しない)
- Ubuntu15.10

## ユーザ
- ctf4b (password: ctf4b123)

## 設定手順

### CentOS6
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
env ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i production -u root -k -D site.yml
# (rootパスワードを入力)
```

5. 再起動する。

``` sh
reboot
```

### Ubuntu 15.10
0. Ubuntu15.10をserverでインストールする。
   (opensshだけインストール時に有効化する)

1. 作成したユーザでログインする。

2. ansibleをインストールする。

``` sh
sudo apt install -y ansible sshpass
```

3. gitをインストールしてplaybookを入手する

``` sh
sudo apt install -y git
git clone https://github.com/hidepin/ctf4b-playbook.git
```

4. playbookを実行する

``` sh
cd ctf4b-playbook
env ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i production -u (ubutuユーザ) -s -k -K -D site.yml
# (ubuntuユーザパスワードを入力)
# (ubuntuユーザパスワードを入力)
```

5. 再起動する。

``` sh
reboot
```
