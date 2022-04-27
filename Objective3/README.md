# Objective 3
## Environment
```
Kubernetes Cluster v1.21.9 from Kubeadm Hosted on Ubuntu Server 20.04 LTS on VirtualBox that provisioned with vagrant.
```

## Task

1. Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
2. Buat Volume tipe hostpath dan disimpan di path `/opt/netdev`.
3. Buat deployment dengan nama `deploy-one` menggunakan image `nginx:latest`, lalu expose deployment tersebut dengan tipe Nodeport ( port = 32123)
4. mount volume yang dibuat ke container `deploy-one`, dan bind ke path dibawah
   ```
    volumeMounts:
    - mountPath: "/usr/share/nginx/html"
    name: <volume name>
    ```
5. tambahkan file index.html di path `/opt/netdev` dan isikan file `.html` bebas
6. Scale deployment tersebut jadi 3 replicas, lalu hapus deployment tersebut dan jelaskan yang terjadi!
7. Masuk ke dalam salah satu pod di deployment `deploy-one` menggunakan kubectl exec lalu buktikan bisa mengakses web dari localhost salah satu pod.
8. Buat satu namespace bernama netdev, lalu buat deployment dengan nama `deploy-two` menggunakan image `nginxdemos/hello` lalu expose deployment tersebut dengan service tipe ClusterIP.
9. Masuk ke pod deployment `deploy-one` lalu dan akses pod deplyment `deploy-two` menggunakan alamat ClusterIP yang sebelumnya dibuat.

## Cheat Sheet
## Default Namespace
### Create Volume
```bash
kubectl apply -f ./pv.yaml
kubectl apply -f ./pvc.yaml
```
### Create Deployment and Expose NodePort
```bash
kubectl apply -f ./`deploy-one`.yaml
kubectl apply -f ./nodeport.yaml
```
### Add Volume Content
ssh into kube worker
```bash
cd /etc/netdev
vi index.html
# edit with simple html
```
### Scale deployment
```bash
kubectl scale deployment `deploy-one` --replicas=3
kubectl get pod
kubectl delete pod <name one of the pod>
```
### Exec into container
```bash
kubectl exec -ti <name one of the pod> bash
pod$ curl localhost
```
## Netdev Namespace
### Create Namespace
```bash
kubectl apply -f ./namespace.yaml
```
### Create Deployment and Expose ClusterIP
```bash
kubectl apply -f `deploy-two`.yaml
kubectl apply -f clusterip.yaml
```
## Note ClusterIP address
```bash
kubectl get svc -n netdev
```
### Exec into container
```bash
kubectl get pod
kubectl exec -ti <name one of the pod> bash
pod$ curl <ClusterIP address>
```
>keep explore!