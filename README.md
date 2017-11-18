# ansible-playbooks
My Ansible Playbooks

# 事前準備

事前に準備が必要な作業を記載します。

## [ansible-vault](http://docs.ansible.com/ansible/latest/playbooks_vault.html) のパスワードの設置

プロジェクトルートに `.vault_password` というファイルを追加して下さい。

これは [ansible-vault](http://docs.ansible.com/ansible/latest/playbooks_vault.html) によって暗号化されているファイルを複合する為に必要です。

`.vault_password` の中身は下記の内容を入力して下さい。

```text
xRbRzCYbWTZ4xbZS
```

このパスワードは復号化を行う為の鍵なので非常に重要です。

もし本リポジトリをベースに運用を行うのであれば、絶対に上記のパスワードを使いまわさないで下さい。

今のところ、暗号化されているファイルと定義されている変数は下記の通りになります。

- hosts/local/group_vars/vault.yml
    - mysql_root_password
    - laravel_api_sample_db_password

プロジェクトルートで `ansible-vault view hosts/local/group_vars/vault.yml` を実行してみて下さい。

暗号化されたファイルの中身が確認出来るかと思います。
