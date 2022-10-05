GKE From Github Actions
===

實驗-從Github佈署程式至GKE

# 安裝 google cloud cli sdk
- 下載[Cloud SDK](https://cloud.google.com/sdk)

# 建立服務帳戶
- 前往`IAM與管理`
- 在左側選單中選擇`服務帳戶`
- 點選`建立服務帳戶`
  - 啟用權限`Kubernetes Engine 開發人員`、`Storage 管理員`
- 新增金鑰 (保管好下載的金鑰)

# 建立GKE Cluster



# 建立Github Actions佈署
## 建立Runner
- Setting => Actions => Runners

## 建立環境變數
- Setting => Environments => New environment
  - Environment secrets
    - DEPLOYMENT_NAME
    - GKE_CLUSTER
    - GKE_ZONE


## 建立密鑰變數
- Setting => Secrets => Actions
  - Repository secrets
    - GKE_PROJECT
    - GKE_SA_KEY
      - 服務帳戶金鑰JSON的base64字串

## 建立Actions設定檔yml


## 建立佈署檔yml

## 推送至main分支


# 測試




# 參考
- [Google Kubernetes Engine - GitHub Actions](https://github.com/google-github-actions/setup-gcloud/tree/main/example-workflows/gke)

## 日誌
- 20221003: Mars.Hung整理-從Github Actions佈署GKE