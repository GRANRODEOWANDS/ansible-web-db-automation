# Ansible Web / DB Automation

Ansibleを使用して、複数のLinuxサーバに対するWebサーバ・DBサーバの構築を自動化する学習用ポートフォリオです。

VirtualBox上に複数台のUbuntu Serverを構築し、controllerからAnsibleを使用してNginxおよびMariaDBを一括構成します。

## 目的

複数台のLinuxサーバを手作業で構築・設定すると、以下のような問題が発生します。

- サーバごとに設定差異が発生する
- 同じ作業を何度も繰り返す必要がある
- 作業漏れや設定ミスが発生しやすい
- サーバ台数が増えると作業負荷が大きくなる

そこでAnsibleを使用し、WebサーバとDBサーバの構築・設定をコード化しました。

## 環境構成

| ホスト | IPアドレス | 役割 |
|---|---|---|
| controller | 192.168.56.10 | Ansible Controller |
| web01 | 192.168.56.11 | Nginx Web Server |
| web02 | 192.168.56.12 | Nginx Web Server |
| db01 | 192.168.56.13 | MariaDB Server |

VirtualBoxのHost-only Networkを使用しています。

## 使用技術

- Ubuntu Server 24.04
- Ansible
- Nginx
- MariaDB
- Jinja2 Template
- Git / GitHub
- VirtualBox

## ディレクトリ構成

```text
ansible-intermediate/
├── ansible.cfg
├── inventory/
│   ├── hosts.yml
│   ├── group_vars/
│   │   └── web.yml
│   └── host_vars/
│       ├── web01.yml
│       └── web02.yml
├── roles/
│   ├── nginx/
│   │   ├── defaults/
│   │   │   └── main.yml
│   │   ├── handlers/
│   │   │   └── main.yml
│   │   ├── tasks/
│   │   │   └── main.yml
│   │   └── templates/
│   │       ├── default.j2
│   │       └── index.html.j2
│   └── mariadb/
│       ├── defaults/
│       │   └── main.yml
│       └── tasks/
│           └── main.yml
├── site.yml
└── README.md
