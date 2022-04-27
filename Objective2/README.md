# Objective 2

## Environment
```
Kubernetes Cluster v1.21.9 from Kubeadm Hosted on Ubuntu Server 20.04 LTS on VirtualBox that provisioned with vagrant.
```

## Task
```
1. Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
2. Buat deployment database postgress dengan username netdev dan password netdev123, lalu expose deployment tersebut menggunakan tipe cluster IP.
3. buat deployment wordpress dan konfigurasi database wordpress untuk menggunakan database yang dibuat sebelumnya.
4. install nginx ingress, lalu konfigurasi agar bisa mengakses wordpress menggunakan ingress tersebut.

