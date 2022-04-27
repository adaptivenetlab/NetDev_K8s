# Objective 2

## Environment
```
Kubernetes Cluster v1.21.9 from Kubeadm Hosted on Ubuntu Server 20.04 LTS on VirtualBox that provisioned with vagrant.
```

## Task

1. Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
2. Install metallb sebagai loadbalancer untuk mengekspose aplikasi
3. Buat Volume tipe hostpath dengan nama `mysql-volume` dan disimpan di path `/opt/netdev/mysql`'
4. Buat deployment database mysql dengan user `root` memiliki password `netdev123` yang diambil dari kubernetes secret, lalu buat database bernama `wordpress` setelah itu expose deployment tersebut menggunakan tipe ClusterIP dan juga jangan lupa mount `mysql-volume` yang dibuat ke deployment tersebut
5. Buat Volume tipe hostpath dengan nama `wordpress-volume` dan disimpan di path `/opt/netdev/wordpress`
6. Buat deployment wordpress dan konfigurasi database wordpress untuk menggunakan database yang dibuat sebelumnya jangan lupa untuk mount `wordpress-volume` ke deployment yang dibuat.
7. Ekspos wordpress tersebut menggunakan service dengan tipe LoadBalancer
8. pastikan bisa mengakses aplikasi wordpress tersebut dari IP LoadBalancer!


## Cheat Sheet

### Install Metallb
```bash
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.11.0/manifests/namespace.yaml
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.11.0/manifests/metallb.yaml
kubectl apply -f metallb.yaml
```

### Create Secret
```bash
kubectl apply -f secret.yaml
```
### Configure Mysql
```bash
kubectl apply -f mysql/secret.yaml
kubectl apply -f mysql/pv.yaml
kubectl apply -f mysql/pvc.yaml
kubectl apply -f mysql/mysql.yaml
kubectl apply -f mysql/mysql-service.yaml
```
### Create database for wordpress
```bash
kubectl get pod
kubectl exec -ti <mysql pod name> bash
mysql -u root -p
CREATE DATABASE wordpress;
show databases;
```

### Configure Wordpress
```bash
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
kubectl apply -f wordpress.yaml
kubectl apply -f loadbalancer.yaml
```

## Access Wordpress from Loadbalancer 
```bash
kubectl get svc
```
access the ip `http://<loadbalancer IP>`