# Objective 4 - KubeWatch Edition

## Environment
```
Kubernetes Cluster v1.21.9 from KubeSpray Hosted on Ubuntu Server 20.04LTS on VMWare Workstation Pro.
```

## Task
```
1. Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
2. Buat deployment aplikasi monitoring, Prometheus & Grafana.
3. Buat service berbentuk cluster IP (Prometheus & Grafana) dan Ingress menggunakan Nginx Ingress untuk aplikasi monitoring (Grafana).
4. Buka dashboard grafana lewat endpoint ingress dan monitor kubernetes Cluster dari Grafana.
5. Buat alerting ke Slack dari Grafana
6. Coba buat deployment baru (bebas, bisa nginx/apache/dll) untuk men-trigger alerting ke slack
```

## 1. Kubernetes Cluster Provision with Kube Spray
```
https://gist.github.com/gilangvperdana/886bc80cefdcd1be7ea356e41fa2871d
```
![](./docs/img/image1.png)

## 2. Deploy Prometheus & Grafana Bundled from KubeWatch
- Install Helm
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

- Deploy KubeWatch
```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm show values bitnami/kubewatch > ~/kubewatch.yaml
```

- Configure Slack BOT
```
https://my.slack.com/services/new/bot
Create a new BOT, then copy API TOKEN
```

- Configure KubeWatch
```
nano ~/kubewatch.yaml
```
```
slack:
  enabled: true
  channel: "your_channel_slack_name"
  token: "your_API_TOKEN_bot"
```
```
rbac:
  create: true
```
```
kubectl create ns monitoring
helm install my-kubewatch bitnami/kubewatch --values ~/kubewatch.yaml -n monitoring
```

## 3-5 Same with README.md

## 6. Alerting Test
```
kubectl create deployment nginx-web --image=gilangvperdana/apps:rlinear
```
![](./docs/img/image-kubewatch.png)