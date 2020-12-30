# docker環境をVagrantで構築する

## Vagrantfileのカスタマイズ

```
# vmのベースになるVagrantのbox
config.vm.box = "bento/centos-6"

# ポートフォワーディングの設定
config.vm.network "forwarded_port", guest: 80, host: 1080
config.vm.network "forwarded_port", guest: 443, host: 1443

# vmとの共有ディレクトリの設定
# 編集するプログラム資産などを指定する
config.vm.synced_folder "../data", "/vagrant_data"
config.vm.synced_folder "../data", "/vagrant_data", :mount_options => ['dmode=777', 'fmode=666']
```

## インストール
- VirtualBoxのインストール [https://www.virtualbox.org/](https://www.virtualbox.org/ "https://www.virtualbox.org/")
- Vagrantのインストール [https://www.vagrantup.com/](https://www.vagrantup.com/ "https://www.vagrantup.com/")

## よく使うコマンド

```
# ローカルにキャッシュされているVagrantのbox(vmのテンプレート)
$ vagrant box list

# Vagrantのbox(vmのテンプレート)をローカルにキャッシュ
$ vagrant box add bento/centos-8

# vmの起動
$ vagrant up

# vmへのsshログインまたはログイン情報の表示
$ vagrant ssh

# vmの初期構築の再実行
$ vagrant provision

# vmの再起動
$ vagrant reload

# vmの停止
$ vagrant halt

# vmの削除
$ vagrant destroy
```
