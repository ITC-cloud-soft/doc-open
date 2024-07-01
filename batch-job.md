# Kubernetes 上で Helm をインストールし、batch-job Helm Chart をデプロイする方法
### 1. Helm のインストール
まず、Helm をインストールします。以下の手順は Linux と macOS 向けです。Windows ユーザーはHelm の公式ドキュメントを参照してください。
スクリプトを使用して Helm をインストール
```shell
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```
### 2. Helm リポジトリの設定
```shell
helm repo add batch-job-helm
helm repo update

```
### 3. Kubernetes ネームスペースの作成（オプション）
Helm Chart のために個別のネームスペースを作成することをお勧めします。
```shell
kubectl create namespace batch-job
```
### 4. Kubernetes に batch-job Helm Chart をデプロイ
```shell
helm install batch-job batch-job-helm --namespace batch-job
```
### 5. デプロイの確認
```shell
helm list --namespace batch-job
```
### 実行例
```
$ helm list --namespace batch-job
NAME            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                   APP VERSION
batch-job       batch-job       1               2024-07-01 12:00:00.000000000 +0000 UTC deployed        batch-job-helm-0.1.0    1.0
```