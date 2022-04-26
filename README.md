# Net Development Kubernetes Path

## Objective 1
```
1. Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
2. Buat deployment aplikasi bebas, boleh nginx/apache/dsb.
3. Buat service berbentuk cluster IP dan Ingress menggunakan Nginx Ingress.
4. Buat Horizontal Pod Auto Scaller pada deployment yang ada.
5. Lakukan test load ke endpoint ingress aplikasi, bisa menggunakan siege/dsb.
6. Pantau perubahan banyaknya pod saat di berikkan load.
7. Pantau perubahan banyaknya pod saat load dihentikan.
8. Simpulkan dan jelaskan apa yang terjadi.
```

## Objective 2
```
1. Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
2. Buat deployment database postgress dengan username netdev dan password netdev123, lalu expose deployment tersebut menggunakan tipe cluster IP.
3. buat deployment wordpress dan konfigurasi database wordpress untuk menggunakan database yang dibuat sebelumnya.
4. install nginx ingress, lalu konfigurasi agar bisa mengakses wordpress menggunakan ingress tersebut.
```

## Objective 3
```
1. Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
2. Buat Volume tipe hostpath dan disimpan di /opt/netdev.
3. Buat deployment dengan nama deploy_one menggunakan image nginxdemos/hello, lalu expose deployment tersebut dengan tipe Nodeport ( port = 33133) dan mount deployment tersebut ke volume yang dibuat.
4. Scale deployment tersebut jadi 3 replicas, lalu hapus deployment tersebut dan jelaskan yang terjadi.
5. Masuk ke dalam salah satu pod di deployment deploy_one menggunakan kubectl exec lalu buktikan bisa mengakses web dari localhost salah satu pod.
6. Buat satu namespace bernama netdev, lalu buat deployment dengan nama deploy_two menggunakan image nginx:latest lalu expose deployment tersebut dengan service tipe ClusterIP.
7. Masuk ke pod deployment deploy_two tersebut dan akses pod deplyment deploy_one menggunakan alamat dns kubernetes <namaservice.namespace.svc.cluster.local>.
8. Masuk ke pod deployment deploy_one lalu dan akses pod deplyment deploy_two menggunakan alamat dns kubernetes <namaservice.namespace.svc.cluster.local>.
9. Coba buat satu file didalam salah satu pod di deployment deploy_one, lalu buktikan bahwa file tersebut ada di volume yang dibuat di /opt/netdev.
```