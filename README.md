# Net Development Kubernetes Path

## Objective 1

- Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
- Buat deployment aplikasi bebas, boleh nginx/apache/dsb.
- Buat service berbentuk cluster IP dan Ingress menggunakan Nginx Ingress.
- Buat Horizontal Pod Auto Scaller pada deployment yang ada.
- Lakukan test load ke endpoint ingress aplikasi, bisa menggunakan siege/dsb.
- Pantau perubahan banyaknya pod saat di berikkan load.
- Pantau perubahan banyaknya pod saat load dihentikan.
- Simpulkan dan jelaskan apa yang terjadi.


## Objective 2

- Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
- Buat deployment database postgress dengan username netdev dan password netdev123, lalu expose deployment tersebut menggunakan tipe cluster IP.
- buat deployment wordpress dan konfigurasi database wordpress untuk menggunakan database yang dibuat sebelumnya.
- install nginx ingress, lalu konfigurasi agar bisa mengakses wordpress menggunakan ingress tersebut.


## Objective 3

- Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
- Buat Volume tipe hostpath dan disimpan di /opt/netdev.
- Buat deployment dengan nama deploy_one menggunakan image nginxdemos/hello, lalu expose deployment tersebut dengan tipe Nodeport ( port = 33133) dan mount deployment tersebut ke volume yang dibuat.
- Scale deployment tersebut jadi 3 replicas, lalu hapus deployment tersebut dan jelaskan yang terjadi.
- Masuk ke dalam salah satu pod di deployment deploy_one menggunakan kubectl exec lalu buktikan bisa mengakses web dari localhost salah satu pod.
- Buat satu namespace bernama netdev, lalu buat deployment dengan nama deploy_two menggunakan image nginx:latest lalu expose deployment tersebut dengan service tipe ClusterIP.
- Masuk ke pod deployment deploy_two tersebut dan akses pod deplyment deploy_one menggunakan alamat dns kubernetes <namaservice.namespace.svc.cluster.local>.
- Masuk ke pod deployment deploy_one lalu dan akses pod deplyment deploy_two menggunakan alamat dns kubernetes <namaservice.namespace.svc.cluster.local>.
- Coba buat satu file didalam salah satu pod di deployment deploy_one, lalu buktikan bahwa file tersebut ada di volume yang dibuat di /opt/netdev.


## Objective 4
- Install Kubernetes menggunakan Kubeadm/Kubespray di 2VM (1 Master dan 1 Worker) => Boleh virtualBox/Proxmox/VMware ataupun public cloud seperti GCP/AWS/Azure.
- Buat deployment aplikasi monitoring, Prometheus & Grafana.
- Buat service berbentuk cluster IP (Prometheus & Grafana) dan Ingress menggunakan Nginx Ingress untuk aplikasi monitoring (Grafana).
- Buka dashboard grafana lewat endpoint ingress dan monitor kubernetes Cluster dari Grafana.
- Buat alerting ke Slack dari Grafana
- Coba buat deployment baru (bebas, bisa nginx/apache/dll) untuk men-trigger alerting ke slack