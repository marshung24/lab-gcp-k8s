# GKE Internal Gateway

## Create Cluster - Autopilot
```bash


```

## Create Gateway
```bash
# 佈署網關
kubectl apply -f gateway.yaml

# 移除網關
kubectl delete -f gateway.yaml
```

## Create Demo Deployment
```bash
# 佈署範例服務
kubectl apply -f store.yaml

# 移除範例服務
kubectl delete -f store.yaml

kubectl apply -f https://raw.githubusercontent.com/GoogleCloudPlatform/gke-networking-recipes/main/gateway/gke-gateway-controller/app/store.yaml

kubectl delete -f https://raw.githubusercontent.com/GoogleCloudPlatform/gke-networking-recipes/main/gateway/gke-gateway-controller/app/store.yaml
```

## Create HTTProute
```bash
# 佈署HTTProute
kubectl apply -f store-route.yaml

# 移除HTTProute
kubectl delete -f store-route.yaml
```

## Change tag
當範例服務用容器GKE無法佈署時，可將原容器推至GKE可讀取的Repostory
```bash
docker image tag us-docker.pkg.dev/google-samples/containers/gke/whereami:v1.2.20 asia-docker.pkg.dev/bpm-recovery/asia.gcr.io/whereami:v1.2.20

docker push asia-docker.pkg.dev/bpm-recovery/asia.gcr.io/whereami:v1.2.20
```