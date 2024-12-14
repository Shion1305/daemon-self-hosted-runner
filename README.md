# GitHub Actions Self-hosted Runner as Daemon の構築手順

## 1. Self Hosted runnerを実行するユーザーを作成

```bash
sudo adduser --disabled-password gh-runner
```

## 2. GitHubのページに従ってrunner実行環境の構築

`sudo su gh-runner` で `gh-runner` ユーザーに切り替える。
`Runner` ページにセットアップ方法の記載がある。そのページに従ってファイルをダウンロード+認証を行う。
`./run.sh` ができるはず。

## 2. Daemonの作成

`./daemon/gh-runner.service` の内容を参考に `/etc systemd/system/gh-runner.service` を作成する。

## 3. Daemonの登録+起動

root権限に戻って、以下を実行する。

```bash
sudo systemctl daemon-reload
sudo systemctl enable gh-runner
sudo systemctl start gh-runner
```
