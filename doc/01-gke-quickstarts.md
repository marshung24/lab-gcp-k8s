GKE快速入門
===

> 整理者: Mars.Hung 2022-09-29

在本快速入門中，您將一個簡單的 Web 服務器 容器化應用程序部署 到 Google Kubernetes Engine (GKE) 集群。您將學習如何創建集群，以及如何將應用程序部署到集群中，以便用戶可以訪問它。

## 步驟

## 安裝工具
- [Google Cloud CLI](https://cloud.google.com/sdk/gcloud)
- [kubectl](https://kubernetes.io/docs/reference/kubectl/)
> 使用GCE時預設已安裝

## 建立GKE Cluster
- 指定專案/帳號
```sh
# 預設專案
$ gcloud config set project PROJECT_ID

# 預設服務帳號
$ gcloud config set account ACCOUNT
```
> - `PROJECT_ID`為目標專案ID
> - `ACCOUNT`為目標服務帳號

- 建立GKE Cluster
```sh
$ gcloud container clusters create-auto hello-cluster \
    --region=COMPUTE_REGION
```
> - `hello-cluster`為Cluster名稱
> - `COMPUTE_REGION`如台灣區`asia-east1`
> - 本範例`create-auto`使用預設參數

- 取得K8S使用憑證
```sh
$ gcloud container clusters get-credentials hello-cluster \
    --region COMPUTE_REGION
```
> - `hello-cluster`為Cluster名稱，可自定
> - `COMPUTE_REGION`如台灣區`asia-east1`
> - 取得之憑證供後續`kubectl`使用此GKE Cluster

## 佈署容器
- 建立佈署容器
```sh
$ kubectl create deployment hello-server \
    --image=us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0
```
> - 使用`範本網頁伺服器容器`佈署，--image=xxx
> - `hello-server`為服務名稱，可自定

- 連結網路
```sh
$ kubectl expose deployment hello-server --type LoadBalancer --port 80 --target-port 8080
```
> 使用`Load Balancer`管理網路連線

## 查看結果
- 查看pods名稱
```sh
$ kubectl get pods --namespace NAMESPACE
```
> `NAMESPACE` 為pods命名空間

- 查看service
```sh
$ kubectl get service hello-server --namespace NAMESPACE
```
> `NAMESPACE` 為pods命名空間

- 查看目標服務網頁
```sh
http://EXTERNAL_IP
```
> `EXTERNAL_IP`為GKE服務的`External-IP`

## 移除設定
- 移除服務
```sh
$ kubectl delete service hello-server
```
> `hello-server`為待移除服務名稱

- 移除Cluster
```sh
$ gcloud container clusters delete hello-cluster \
    --region COMPUTE_REGION
```
> - `hello-cluster`為待移除Cluster名稱
> - `COMPUTE_REGION`為待移除Cluster區域，如台灣區`asia-east1`

## 前往容器內部執行指令
```
$ kubectl exec -it PODS_NAME -c CONAINER_NAME --namespace NAMESPACE -- sh
```
> - `PODS_NAME` 為pods名稱
> - `CONAINER_NAME` 為Containers名稱
> - `NAMESPACE` 為pods命名空間

## 參考
- [Quickstarts-Deploy an app to a GKE cluster](https://cloud.google.com/kubernetes-engine/docs/)
- [Cloud SDK](https://cloud.google.com/sdk)
- [Install the Google Cloud CLI](https://cloud.google.com/sdk/docs/install-sdk)

## 日誌
- 20220929: Mars.Hung整理GKE快速入門步驟
- 20230223: Mars.Hung補充namespace及前往容器內部執行指令







