# Net Development Kubernetes Path

## [Objective 1](./Objective1)

- Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
- Buat deployment aplikasi bebas, boleh nginx/apache/dsb.
- Buat service berbentuk cluster IP dan Ingress menggunakan Nginx Ingress.
- Buat Horizontal Pod Auto Scaller pada deployment yang ada.
- Lakukan test load ke endpoint ingress aplikasi, bisa menggunakan siege/dsb.
- Pantau perubahan banyaknya pod saat di berikkan load.
- Pantau perubahan banyaknya pod saat load dihentikan.
- Simpulkan dan jelaskan apa yang terjadi.


## [Objective 2](./Objective2)

- Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
- Buat deployment database postgress dengan username netdev dan password netdev123, lalu expose deployment tersebut menggunakan tipe cluster IP.
- buat deployment wordpress dan konfigurasi database wordpress untuk menggunakan database yang dibuat sebelumnya.
- install nginx ingress, lalu konfigurasi agar bisa mengakses wordpress menggunakan ingress tersebut.


## [Objective 3](./Objective3)

- Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
- Buat Volume tipe hostpath dan disimpan di path /opt/netdev.
- Buat deployment dengan nama deploy-one menggunakan image nginx:latest, lalu expose deployment tersebut dengan tipe Nodeport ( port = 32123)
- mount volume yang dibuat ke container deploy-one, dan bind ke path dibawah
   ```
    volumeMounts:
    - mountPath: "/usr/share/nginx/html"
    name: <volume name>
    ```
    
- tambahkan file index.html di path /opt/netdev dan isikan file .html bebas
- Scale deployment tersebut jadi 3 replicas, lalu hapus deployment tersebut dan jelaskan yang terjadi!
- Masuk ke dalam salah satu pod di deployment deploy-one menggunakan kubectl exec lalu buktikan bisa mengakses web dari localhost salah satu pod.
- Buat satu namespace bernama netdev, lalu buat deployment dengan nama deploy-two menggunakan image nginxdemos/hello lalu expose deployment tersebut dengan service tipe ClusterIP.
- Masuk ke pod deployment deploy-one lalu dan akses pod deplyment deploy-two menggunakan alamat ClusterIP yang sebelumnya dibuat.

## [Objective 4](./Objective4)

- Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
- Buat deployment aplikasi monitoring, Prometheus & Grafana.
- Buat service berbentuk cluster IP (Prometheus & Grafana) dan Ingress menggunakan Nginx Ingress untuk aplikasi monitoring (Grafana).
- Buka dashboard grafana lewat endpoint ingress dan monitor kubernetes Cluster dari Grafana.
- Buat alerting ke Slack dari Grafana
- Coba buat deployment baru (bebas, bisa nginx/apache/dll) untuk men-trigger alerting ke slack