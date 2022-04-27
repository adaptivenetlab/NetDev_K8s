# Net Development Kubernetes Path

## TeamMate
| Anggota|  Minggu|
|--|--|
|**KELOMPOK 1**|**MINGGU 4**|
|  Shevira Feby Christavia|  Minggu 4 #1|
|  Rafsanjani Nurul Irsyad|  Minggu 4 #1|
|  Rayhan Aziz Budiana|  Minggu 4 #1|
|**KELOMPOK 2**|**MINGGU 4**|
|  Salwa Aulia Farida Yudistira|  Minggu 4 #2|
|  Arga Valen Lazuardi|  Minggu 4 #2|
|  Xavier Samuel Muhammad Fidel Piljai|  Minggu 4 #2|
|**KELOMPOK 3**|**MINGGU 5**|
| Muhammad Litfan Rahmansyah |  Minggu 5 #1|
| Faishal Dzaki Ferdiansyah |  Minggu 5 #1|
| Rashid Muhammad Fajri |  Minggu 5 #1|
|**KELOMPOK 4**|**MINGGU 5**|
|  Syekh Maulana Wijaya|  Minggu 5 #2|
|  Salman Alfarizi Novel Bajri|  Minggu 5 #2|
|  Faishal Yusuf Baqir|  Minggu 5 #2|

|KELOMPOK  | BAGIAN|
|--|--|
| KELOMPOK 1 |  [Objective 4](./Objective4)|
| KELOMPOK 2 |  [Objective 2](./Objective2)|
| KELOMPOK 3 |  [Objective 3](./Objective3)|
| KELOMPOK 4 |  [Objective 1](./Objective1)|

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
- Install metallb sebagai loadbalancer untuk mengekspose aplikasi
- Buat Volume tipe hostpath dengan nama `mysql-volume` dan disimpan di path `/opt/netdev/mysql`
- Buat deployment database mysql dengan user `root` memiliki password `netdev123` yang diambil dari kubernetes secret, lalu buat database bernama `wordpress` setelah itu expose deployment tersebut menggunakan tipe ClusterIP dan juga jangan lupa mount `mysql-volume` yang dibuat ke deployment tersebut
- Buat Volume tipe hostpath dengan nama `wordpress-volume` dan disimpan di path `/opt/netdev/mysql`'
- Buat deployment wordpress dan konfigurasi database wordpress untuk menggunakan database yang dibuat sebelumnya jangan lupa untuk mount `wordpress-volume` ke deployment yang dibuat.
- Ekspos wordpress tersebut menggunakan service dengan tipe LoadBalancer
- pastikan bisa mengakses aplikasi wordpress tersebut dari IP LoadBalancer!



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
- Buat alerting ke Slack dari Grafana `OPTIONAL`
- Coba buat deployment baru (bebas, bisa nginx/apache/dll) untuk men-trigger alerting ke slack `OPTIONAL`