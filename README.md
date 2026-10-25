# YOLO v11 Training with Custom Dataset on Local System

File All in One untuk Training YOLOv11 yang jalan secara lokal (100% offline) menggunakan dataset custom. Di tes pada sistem dengan spesifikasi berikut:  
- NVIDIA RTX 3050 6GB Laptop GPU
- 16 GB RAM DDR4 Single Channel
- CachyOS Linux (Arch-based) with fish shell.  

# Setup Environment
**NOTE!**
- Perintah berikut disesuaikan untuk sistem menggunakan sistem operasi Linux (CachyOS/Arch-based) dengan shell fish. Jika ingin dijalankan di sistem lain, bisa disesuaikan kembali.
- Pastikan perangkat kalian sudah terinstall Python, jika belum bisa menggunakan perintah berikut: `sudo pacman -S python`
- Untuk training ini akan menggunakan CUDA, pastikan perangkat kalian memiliki GPU NVIDIA dengan driver versi terbaru (bisa dicek menggunakan `nvidia-smi` dan `chwd` pada terminal). 
- Pastikan juga perangkat kalian punya ruang penyimpanan sebesar **5-6 GB**, RAM setidaknya **16 GB**, dan VRAM setidaknya **6 GB**, mengingat proses install dependensi dan training akan memakan penyimpanan, RAM dan VRAM yang cukup banyak. 


**Langkah Setup**
1. Clone repository ini  
```
git clone https://github.com/InnovaReborn2GD/yolov11-training/
```
2. Buat virtual environment Python  
 ```
 python -m venv ~/yolo-env
 source ~/yolo-env/bin/activate.fish
 ```
3. Install dependensi yang diperlukan  
**NOTE:** Proses ini memerlukan ruang penyimpanan yang cukup besar, sehingga pastikan perangkat kalian punya ruang sebesar 5-6 GB dan koneksi internet yang memadai.  
```
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu124
pip install ultralytics ipykernel matplotlib pandas seaborn opencv-python pyyaml
```
4. Jika sudah, akan muncul pilihan kernel yang bisa digunakan, pilih kernel **yolo-env** di notebook ini.
5. Selesai deh! Tinggal lanjut training melalui file `yolov11_local_training.ipynb` (semoga laptop kalian ga meledak wkwkw)