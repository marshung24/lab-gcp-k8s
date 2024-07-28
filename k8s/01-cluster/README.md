# GKE Cluster

## Create Cluster - Autopilot
```bash
# 變數設定
PROJECT_ID="mars-lab-424008"
REGION="asia-east1"
NETWORK="projects/mars-lab-424008/global/networks/mars-lab-1"
SUBNETWORK="projects/mars-lab-424008/regions/asia-east1/subnetworks/tw"
CLUSTER_NAME="autopilot-cluster-lab"
AUTHORIZED_NETWORK="203.69.238.76/30"
CLUSTER_IPV4="192.168.112.0/21"
SERVICES_IPV4="192.168.16.0/21"

# 建構指令-Autopilot
gcloud container clusters create-auto ${CLUSTER_NAME} \
  --release-channel "stable" \
  --enable-private-nodes \
  --enable-master-authorized-networks \
  --master-authorized-networks ${AUTHORIZED_NETWORK}\
  --network ${NETWORK} \
  --subnetwork ${SUBNETWORK} \
  --cluster-ipv4-cidr ${CLUSTER_IPV4} \
  --services-ipv4-cidr ${SERVICES_IPV4} \
  --project ${PROJECT_ID} \
  --region ${REGION}


```