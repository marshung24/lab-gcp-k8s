gcloud
===

## 常用指令
### Components
> 套件管理，各式套件安裝

- 查看
  ```sh
  $ gcloud components list
  ```
- 安裝
  ```sh
  $ gcloud components install COMPONENT_ID
    # or
  $ sudo apt-get install kubectl
  ```
  > GCE中預設已安裝好相關工具
- 移除
  ```sh
  $ gcloud components remove COMPONENT_ID
  ```
- 更新
  ```sh
  $ gcloud components update
  ```

### Config
> 設定管理，連線GCP專案相關設定

- 初始化權限
  ```sh
  # 本機
  $ gcloud init

  # 使用SSH連線時
  $ gcloud init --console-only
  ```

## 帳號認證
```sh
# CLI模式
$ gcloud auth login --no-launch-browser
```

## 設定預設專案/帳戶
```sh
$ gcloud config set project <PROJECT-ID>

$ gcloud config set account <ACCOUNT>
```

### container clusters
- 查看
  ```sh
  $ gcloud container clusters list
  ```
- 建立(自動)
  ```sh
  $ gcloud container clusters create-auto hello-cluster --region=COMPUTE_REGION
  ```
  > `COMPUTE_REGION`如台灣區`asia-east1`
- 刪除
  ```sh
  $ gcloud container clusters delete hello-cluster --region COMPUTE_REGION
  ```
- 取得金鑰
  ```sh
  $ gcloud container clusters get-credentials hello-cluster --region COMPUTE_REGION
  ```
  > - `COMPUTE_REGION`如台灣區`asia-east1`
  > - This command configures kubectl to use the cluster you created.


## 參考
- [Cloud SDK](https://cloud.google.com/sdk)
- [Install the Google Cloud CLI](https://cloud.google.com/sdk/docs/install-sdk)

## 日誌
- 20220929: Mars.Hung整理