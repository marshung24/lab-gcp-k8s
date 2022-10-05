# lab-gcp-k8s
實驗-從github佈署程式至GCP K8S

# 安裝 google cloud cli sdk
- 下載[Cloud SDK](https://cloud.google.com/sdk)

# 建立服務帳戶
- 前往`IAM與管理`
- 在左側選單中選擇`服務帳戶`
- 點選`建立服務帳戶`
  - 啟用權限`Kubernetes Engine 開發人員`、`Storage 管理員`
- 新增金鑰 (保管好下載的金鑰)

# 建立Github專案

# 建立Github Actions佈署

# 測試


# 參考
- [GKE overview](https://cloud.google.com/kubernetes-engine/docs/concepts/kubernetes-engine-overview)
- [Quickstarts-Deploy an app to a GKE cluster](https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster)
- [Google Kubernetes Engine - GitHub Actions](https://github.com/google-github-actions/setup-gcloud/tree/main/example-workflows/gke)
- [GCP - 使用 Github Actions 部署 React 到 GKE](https://dotblogs.com.tw/explooosion/2020/10/10/040358)
- [[手把手教學] 如何在 GKE 上部署容器應用程式及 HTTP(S) Load Balancer](https://ikala.cloud/tutorials-kubernetes-engine-load-balancer/)


gcloud container clusters get-credentials hello-cluster \
    --region asia-east1

https://console.cloud.google.com/flows/enableapi?apiid=containerregistry.googleapis.com,container.googleapis.com&authuser=1&project=firm-streamer-339509




- 問題：
  - GKE Load Balance
    - 拿掉http
    - 參數試調
      - 安全資料傳輸層 (SSL) 政策
    - 多主機
    - 固定IP
  - namespace