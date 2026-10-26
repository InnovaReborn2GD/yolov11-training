# YOLO v11 Training with Custom Dataset on Local System

Repository All in One untuk Training dan Inferensi YOLOv11 yang jalan secara lokal (100% offline) menggunakan dataset custom. Dites pada sistem dengan NVIDIA RTX 3050 6GB Laptop GPU, RAM 16 GB DDR4 Single Channel, serta CachyOS Linux (Arch-based) dengan shell fish dan Windwows 11 26H2 dengan PowerShell 7.6.7.

## Setup Environment

### NOTE BEFORE SETUP !!

- Perintah berikut disesuaikan untuk perangkat menggunakan sistem operasi Linux (CachyOS/Arch-based) dengan shell fish. Tersedia pula versi yang disesuaikan untuk Windows (10/11) dengan PowerShell. Jika ingin dijalankan di perangkat dengan sistem operasi lain, bisa disesuaikan kembali.
- **Untuk perangkat menggunakan Windows (10/11), gunakan file `yolov11_local_training_windows.ipynb`**
- Pastikan perangkat kalian sudah terinstall Python, jika belum bisa menggunakan perintah berikut: `sudo pacman -S python` atau bisa [klik di sini](https://www.python.org/downloads/).
- Untuk training ini akan menggunakan CUDA, pastikan perangkat kalian memiliki GPU NVIDIA dengan driver versi terbaru (bisa dicek menggunakan `nvidia-smi` dan `chwd` pada terminal).

### System Requirements

- OS: **Windows 10/11** atau **Linux** distro apapun (di sini dites menggunakan Arch-based, bisa disesuaikan kembali perintahnya jika ingin pakai distro lain).
- RAM: **16 GB** untuk model small (s), **8 GB** untuk model nano (n).
- GPU: **NVIDIA** seri apapun dengan **VRAM 4 GB** (recommended 6 atau 8 GB keatas) dan support **CUDA 13.0** (driver minimal versi 615.xx).
- Storage: **7-10 GB free**, beberapa dependensi kayak PyTorch ukurannya bisa sampe 2 GB an.
- Koneksi internet yang memadai, karena harus mengunduh beberapa dependensi secara online.

Tambahan: karena disini training menggunakan model small (s), untuk perangkat dengan RAM di bawah 16 GB dan VRAM dibawah 4 GB dapat menggunakan model nano (n). Ganti `yolo11s.pt` di `model = YOLO('yolo11s.pt')` menjadi `yolo11n.pt`.

### Langkah Setup

1. Clone repository ini  

    ``` bash
    git clone https://github.com/InnovaReborn2GD/yolov11-training/
    ```

2. Buat virtual environment Python  

    Linux (fish):

    ```bash
    python -m venv ~/yolo-env
    source ~/yolo-env/bin/activate.fish
    ```

    Windows (PowerShell):

    ```powershell
    python -m venv yolo-env
    .\yolo-env\Scripts\Activate.ps1
    python -m pip install --upgrade pip
    ```

    Jika sudah, akan muncul pilihan kernel yang bisa digunakan, pilih kernel `yolo-env` di notebook ini.

3. Install dependensi yang diperlukan  
**NOTE:** Proses ini memerlukan ruang penyimpanan yang cukup besar, sehingga pastikan perangkat kalian punya ruang sebesar 7-10 GB dan koneksi internet yang memadai.  

    ```bash
    pip install torch torchvision --index-url https://download.pytorch.org/whl/cu130
    pip install ultralytics ipykernel matplotlib pandas seaborn opencv-python pyyaml ipykernel
    ```

4. Selesai deh! Tinggal lanjut training melalui file `yolov11_local_training.ipynb` (semoga laptop kalian ga meledak wkwkw)

## Catatan Tambahan  

- Pastikan dataset kalian punya struktur folder seperti berikut:

    ```txt
    Dataset-elu-disini-bray/
    ├── images/
    │   ├── train/
    │   └── val/
    ├── labels/
    │   ├── train/
    │   └── val/
    ├── test/
    │   ├── images/
    │   └── labels/
    ```

    Jika ternyata dataset yang kalian download strukturnya berbeda, disesuaikan lagi agar strukturnya seperti berikut. Contoh struktur yang benar dapat dilihat di `/datasets/.example-dataset/`.

- Kalian juga dapat melakukan inferensi menggunakan video, tinggal drop video kalian di folder `/data`. Pastikan video menggunakan format `.mp4`.

- Jika dirasa VRAM dan RAM kalian tidak cukup, ubah nilai `BATCH_SIZE` dari `16` ke `8` (bisa diturunkan ke `4` jika masi berat juga). Tutup juga aplikasi yang jalan di background sebelum training untuk membebaskan RAM.

- udeh itu aje wkwkw, selamat bereksperimen! klo ada pertanyaan/kendala boleh hubungi aku ato open issue aja di repo inii yahh
